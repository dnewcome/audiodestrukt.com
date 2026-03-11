---
title: "Headless DAWs"
date: 2024-01-26T14:31:34-08:00
url: https://audiodestrukt.wordpress.com/2024/01/26/headless-daws/
id: 1018
categories: Uncategorized
tags: 
---

# Headless DAWs

I’m interested in getting something working headless for a project. I did some research and found the Non mixer stuff. I looked like what I wanted since it’s a way of decoupling the parts of a DAW and using them independently. I’m interested mostly in the mixer.

However it looks like these are still UI-based components that can’t be run without at least a virtual framebuffer. I’d like to find something that doesn’t have any UI at all.

Well it turns out that Reaper on Linux can be built as a headless app with some flags to libswell. Swell is an abstraction library for UI functionality so that the app can be ported between other non-Windows systems.

I’m going to give this a shot and see where I get. So far I’m getting errors when trying to build. https://forum.cockos.com/showthread.php?t=263372

I tried changing to clang as the compiler and still got some errors.

swell-wnd-generic.cpp:4694:32: error: use of bitwise '|' with boolean operands [-Werror,-Wbitwise-instead-of-logical]
                bool changed = lvs->clear_sel() | lvs->set_sel(offs,true);
                               ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
                                                ||
swell-wnd-generic.cpp:4694:32: note: cast one or both operands to int to silence this warning
1 error generated.

Compiling with GCC I got the following errors:

swell-miscdlg-generic.cpp: In function ‘LRESULT swellFileSelectProc(HWND, UINT, WPARAM, LPARAM)’:
swell-types.h:94:31: error: value computed is not used [-Werror=unused-value]
   94 | #define CreateDirectory(x,y) (!mkdir((x),0755))
      |                              ~^~~~~~~~~~~~~~~~~
swell-miscdlg-generic.cpp:855:22: note: in expansion of macro ‘CreateDirectory’
  855 |                      CreateDirectory(buf,NULL);
      |                      ^~~~~~~~~~~~~~~
In file included from swell-miscdlg-generic.cpp:42:
In function ‘bool WDL_hasStringsEx2(const char**, int, const LineParser*)’,
    inlined from ‘bool WDL_hasStrings(const char*, const LineParser*)’ at ../has_strings.h:446:27,
    inlined from ‘void BrowseFile_State::viewlist_sort(const char*)’ at swell-miscdlg-generic.cpp:230:40:
../has_strings.h:248:28: error: array subscript 1 is outside array bounds of ‘const char [1]’ [-Werror=array-bounds]
  248 |     if (n[0] == '(' && !n[1] && !lp->gettoken_quotingchar(x))
      |                         ~~~^
cc1plus: all warnings being treated as errors
make: *** [<builtin>: swell-miscdlg-generic.o] Error 1

I’m not sure if there are other configuration steps here that I missed. This project doesn’t seem to use autotools and just has a makefile included.

I compiled with ALLOW_WARNINGS and it worked. I supposed the code snapshot I got was not totally clean.
