---
title: "Simple USB Midi footswitch using Arduino"
date: 2012-04-25T23:16:02-08:00
url: https://audiodestrukt.wordpress.com/2012/04/25/simple-usb-midi-footswitch-using-arduino/
id: 218
categories: Uncategorized
tags: Live PA
---

# Simple USB Midi footswitch using Arduino

I wrote about getting USB Midi working on the Arduino recently, and now here is my first attempt at getting it to do something useful. I have a momentary pushbutton installed in a small plastic junction box from the hardware store. I need to update my prototyping techniques notes here, as I’ve begun to explore the use of cheap plastic enclosures since they are so easy to work with compared to the difficulty of drilling galvanized metal boxes.

The purpose of this project was to test out my approach for reading the Arduino’s inputs and sending a corresponding Midi message out. In this test I wanted to send note-on and note-off messages when the button was pushed and released. I decided to use middle C on the keyboard which is C4 or Midi note number 60. The code is a simple polling loop with state so that we can send messages only when the state changes, in other words, we can hold the button down without sending duplicate messages every polling cycle.

Using interrupts would be a nicer way of handling this, but I wanted to keep this test as simple as possible for now.

Here is the code:

```

#define MIDI_COMMAND_NOTE_OFF 0x80
#define MIDI_COMMAND_NOTE_ON 0x90
#define MIDI_COMMAND_CONTROL_CHANGE 0xB0

int button_state = 0;

/* The format of the message to send via serial */
typedef struct {
 uint8_t command;
 uint8_t channel;
 uint8_t data2;
 uint8_t data3;
} t_midiMsg;

void setup();
void loop();

void setup() 
{
 pinMode(9, INPUT); 
 digitalWrite(9, HIGH); /* enable internal pullups */

 Serial.begin(115200);
 delay(200); 
}

void loop() 
{
 int button_state_prev = button_state;
 button_state = digitalRead(9);
 
 t_midiMsg msg;

 /* Send the notes */
 if( button_state == 1 && button_state_prev == 0 ) {
 msg.command = MIDI_COMMAND_NOTE_ON;
	msg.channel = 1;
	msg.data2 = 60; /* middle c */
	msg.data3 = 127;	/* max velocity */
	Serial.write((uint8_t *)&msg, sizeof(msg));
 }
 else if( button_state == 0 && button_state_prev == 1 ) {
 msg.command = MIDI_COMMAND_NOTE_OFF;
	msg.channel = 1;
	msg.data2 = 60; /* middle c */
	msg.data3 = 127;	/* max velocity */
	Serial.write((uint8_t *)&msg, sizeof(msg));
 } 
}

```
