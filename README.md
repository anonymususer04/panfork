# panfork

Termux with Pre-installed Mesa Panfork (Custom Build)

https://github.com/anonymususer04/panfork/releases

This is a Termux setup with Mesa Panfork pre-installed. Panfork was created some time ago when the Gallium Panfrost driver in Mesa 23.0.0 did not support the Mali-G610 GPU and the Panthor didn't exist yet. Developer icecream95 forked Mesa and implemented a custom UAPI called pan_base, which utilized kbase (ARM’s proprietary kernel driver) and provided ready-to-use functions for Gallium Panfrost code integration.

Eventually, icecream95 abandoned the project and deleted the repository, but by then others had already forked it. Later on, saikatsaha forked the Panfork Mesa and made several improvements, including SW winsys — a software-based windowing system backend — to allow rendering without needing a panfrost.ko DRM kernel module,

Afterward, I forked and modified it further to compile successfully on Termux and achieve better runtime behavior. On some devices like Mali-G615, the rendering works well with X11 and provides excellent FPS with no terminal errors. I believe the same is true for other Valhall V10 (CSF) GPUs such as G610 and G710.

However, on Bifrost GPUs like Mali-G57 or G52 (non-CSF), the performance is poor. glmark2 shows errors like:

syncobj 0xb4000079ea2dbf40 wait timeout
Atom X reported event 0x58!

And the rendering is extremely slow, averaging around 1 FPS.

---

How to Test

1. Install the Termux-X11 app.
2. Run the following commands inside Termux:

   glmark2
   glxgears -info
   glxinfo -B

---

Installation

1. Place the termux-panfork.tgz file in the root of your internal storage.
2. Run the following commands in Termux:

   cd .. && termux-setup-storage && tar -xvzf /sdcard/termux-panfork.tgz

---

Source Code

My fork (optimized for Termux):
https://github.com/anonymususer04/mesa-Panfork-android

Saikatsaha's fork (Mali G610 focus):
https://github.com/Saikatsaha1996/mesa-Panfrost-G610

One of the preserved forks from icecream95's original Panfork:
https://gitlab.com/Peter756729890/panfork-mesa

---

Required Apps

Termux (v0.118.3):
https://github.com/termux/termux-app/releases/tag/v0.118.3

Termux-X11:
https://github.com/termux/t
ermux-x11/releases

---
~ $




























