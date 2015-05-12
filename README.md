Quick proof of concept for http://www.cs.columbia.edu/~mikepo/papers/gpukeylogger.eurosec13.pdf

Objective:
- Undetection. Our jellyfish rootkit utilized a common LD_PRELOAD technique to hide in userland. For Demon we're going with code
injection.

Requirements for use:
- OpenCL drivers/icd's installed
- AMD or NVIDIA card (although AMDAPPSDK does support intel)
- linux kernel headers

Details on what this PoC does:
- CPU kernel module bootstrap to locate keyboard buffer via DMA in usb struct
- keyboard buffer gets stored in userland file
- kernel module deletes itself
- OpenCL stores that keyboard buffer inside gpu and deletes file due to evidence

Our thoughts:
- We personally feel the use of a kernel module is loud, but in the beginning
stages of our research work, we googled around and looked for "theories" on
gpu malware documented by *.edu's, and wanted to turn those theories into
reality. This was how we interpreted the eurosec 2013 research paper.

Disclaimer: 
- We are not associated with the creators of this paper. We only PoC'd what was described in it, plus a little more.

PLEASE READ:
- For some arbitrary reason this project as well as jellyfish, has been getting a decent amount of attention. That being said, we just
want to notify everyone reading this that Demon is not complete nor has it even reached the expectations we wanted it to yet. We're 
still circling around ideas and pseudo code upon what we think is cool, so apologies to anyone disappointed that they still have
a buggy still-in-beta application. Our goal was to make everyone AWARE that gpu based malware IS REAL; and obviously, telling
from what's been publicized, we succeeded.

Also, to an individual that commented on an arstechnica article about us. Yes, we're very early in development for both projects,
so sit tight and enjoy the show.

Heads up:
- Windows GPU remote access tool (RAT) PoC official release @ /WIN_JELLY
