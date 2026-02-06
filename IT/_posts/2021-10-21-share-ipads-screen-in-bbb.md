---
title:		"How to share iPad screen in BigBlueButton on Linux PC using Android phone"
categories: Software
mathjax: 	false
utterances: true
---

# How to share iPad screen in BigBlueButton on Linux PC using Android phone

I will explain how to share the screen of an [iPad Pro][iPad] (I) in a [BigBlueButton][BBB] session (BBB) using only a Linux PC (L) and an Android Phone (A).

Note that it is also possible to stream live handwriting to BBB using a [digitizer board][Wacom]
or a simple [document camera][Kamera] connected to (L).
In the first case, one can use the whiteboard app [Xournal][Xournal] on (L) to save the notes in the form of a PDF afterwards.

I encountered the following problems while trying to share the screen of (I) in (BBB):
1. Although BBB offers a collaborative whiteboard, it is currently not possible to download it together with the writing in the end.
2. Although it is possible to join a BBB session from (I), it is currently not possible to share the screen.
3. One can currently share the screen of (I) only in the following two scenarios: either via AirPlay to machines running an AirPlay receiver which are connected to the same ''friendly'' WiFi network (Eduroam does not work), or to a Mac via cable.

## Prerequisities

1. Install [scrcpy][scrcpy] on (L).
2. Install [AirReceiver][AirReceiver] on (A). This is a commercial product, which currently costs 3€.
3. Allow USB-debugging in the developer's options of (A).
 
## Steps

1. Create a WiFi mobile hotspot on (A) and connect to it with (I).
2. Connect (A) to (L) via USB and switch the connection type on (A) to *USB-tethering* (also disable all sounds and notifications or better put it in the plane mode).
3. Run *AirReceiver* on (A), click share screen on (I), and select (A) as the target. 
   The screen of (A) should now mirror the screen of (I).
5. Run *scrcpy* on (L), so that a window with the screen of (A) appears. This screen can be now streamed in BBB (if you are using a tiling manager, put the BBB and scrpy window on the the same virtual desktop and switch to the monocycle mode). 

## Example

* (A): *Samsung A71* with screen resolution 2400x1080 in the horizontal position with the bottom part to the rigt.
* (I): *iPad Pro 12.9'* with screen resolution 2732x2048.
* Commands to start *scrcpy*:
	```
	% iPad in portrait position
	scrcpy --lock-video-orientation=1 -w --disable-screensaver -S --crop 1080:902:0:794

	% iPad in landscape position
	scrcpy --lock-video-orientation=1 -w --disable-screensaver -S --crop 1080:1680:0:400
	```
Here `--lock-video-orientation=1` assures that the screen of (A) is mirrored horizontally independently of its rotation, `-w` prevents (A) from falling asleep, `-S` turns off the screen of (A), `--crop 1080:902:0:794` crops the mirrored window.

## Other ideas

* Create a virtual video device using [v4l2loopback][v4l2loopback] or [akvcam][akvcam] and redirect the *scrcpy* window there.
* Run a free Airplay server [RPiPlay][RPiPlay] or [shairplay][shairplay] on (L) directly and bypass `scrcpy` and `AirReceiver`. It should work if (A) is connected via USB tethering but needs to be properly configured.
  In case that it doesn't work, get an USB WiFi adapter and create a hotspot on (L).
* Buy an HDMI/USB-A video grabber for (L) and an USB-C/HDMI adapter for (I) to connect them, bypass (A) completely. However, the quality will depend on the grabber and the HDMI bandwidth.
* There is a [BBB app][BBBapp] for Android and iOS under development which will hopefully implement the screen sharing.

[BBB]: https://github.com/bigbluebutton
[Xournal]: https://xournal.sourceforge.net/
[scrcpy]: https://github.com/Genymobile/scrcpy
[AirReceiver]: https://www.remotetogo.com/?page_id=29
[v4l2loopback]: https://github.com/umlaeute/v4l2loopback
[akvcam]: https://github.com/webcamoid/akvcam
[RPiPlay]: https://github.com/FD-/RPiPlay
[shairplay]: https://github.com/juhovh/shairplay
[iPad]: https://www.amazon.de/Neu-Apple-iPad-Wi-Fi-256-GB/dp/B0863V7LBW/ref=sr_1_3?__mk_de_DE=%C3%85M%C3%85%C5%BD%C3%95%C3%91&dchild=1&keywords=ipad%2Bpro%2B12.9%2B2020&qid=1634863285&qsid=258-9789889-5375117&sr=8-3&sres=B08644KPGW%2CB0932WWH7Y%2CB083J6BNSB%2CB0863BPRKX%2CB083R7RTBX%2CB083R6WS3Z%2CB092DRHLNQ%2CB07ZLS9DKJ%2CB08YD68TXP%2CB083R88D46%2CB07KF3S4NJ%2CB08B1Q9LZW%2CB07ZJ3P7XR%2CB08KY5F2VB%2CB083R83QRG%2CB099NVVWD7&srpt=TABLET_COMPUTER&th=1
[Wacom]: https://www.amazon.de/Wacom-ctl-4100-K-s-Kreative-Eingabestift-Schwarz/dp/B079MQZM4X/ref=sr_1_2?__mk_de_DE=%C3%85M%C3%85%C5%BD%C3%95%C3%91&crid=3TEQ4YPFJNYK5&dchild=1&keywords=wacom+intuos+s&qid=1634863080&qsid=258-9789889-5375117&sprefix=wacom+intuos%2Caps%2C204&sr=8-2&sres=B079QBDTDF%2CB079MQZM4X%2CB079JD3V8M%2CB07QZJWW3H%2CB079JF5K78%2CB07GBBCC9Y%2CB013ATUFUC%2CB007EB6534%2CB07RC6F518%2CB07N525974%2CB01MZ0KLO0%2CB08J7NT8BW%2CB079JCJCM3%2CB07LBGH67J%2CB082BD75W1%2CB079HL9YSF&srpt=GRAPHIC_TABLET
[Kamera]: https://www.amazon.de/IPEVO-5-880-4-01-00-Definition-USB-Dokumentenkamera-Ziggi-HD/dp/B079DLTG9F/ref=sr_1_1?__mk_de_DE=%C3%85M%C3%85%C5%BD%C3%95%C3%91&dchild=1&keywords=%5BIPEVO+V4K+Ultra+High+Definition&qid=1634863114&qsid=258-9789889-5375117&sr=8-1&sres=B079DLTG9F%2CB08P3SZB9Q%2CB08WWH5SCN%2CB0827LLG8P%2C3898947424%2CB0868H9NN8%2CB08Q87C1GT%2CB0915LX4RY%2CB08XMD2TG4%2CB088NGLQL4%2CB0894CC4TK%2CB07PQJZK66%2CB095BRWJZF%2CB095RW28TL%2CB096TTJ33S%2CB0784RZNKT&srpt=CAMCORDER
[BBBapp]: https://github.com/bennyboer/bbb_app
