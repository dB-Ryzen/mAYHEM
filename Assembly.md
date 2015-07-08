The PortaPack H1 must be attached to a HackRF One. Here are the steps:

### Extract the HackRF One Circuit Board

Starting with a HackRF One in its case:

* Disconnect all cables and antennas from the HackRF One.
* For each of the three SMA connectors:
    * Remove the red "nipple".
    * Loosen the gold nut.
    * Remove the gold nut, crown washer, and flat washer.
* Using the yellow ShareBrained "spudger" tool (also known as a 0.73mm Dunlop Tortex guitar pick):
    * Insert the edge of the spudger tool into the gap in the plastic case.
    * Slide the tool along the gap while pushing it into the gap, perpendicular to the case.
    * At some point, the tool will slide in a bit further. Run the tool along the gap to separate the internal locking tabs between the two case pieces.

Here's a video of how it's done (links to YouTube):

[![On YouTube: How to Open a HackRF One Case](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/hackrf_one_decase_youtube.jpg)](https://youtu.be/zuXJtpTSEJM "How to Open a HackRF One Case")

### Attach PortaPack H1 to HackRF One

The PortaPack H1 and HackRF One attach via three headers. The HackRF One has three black female header sockets. The PortaPack H1 has three black and silver male header pin arrays.

* Remove the placement caps (little black caps) from the three headers on the PortaPack.
* Line up the PortaPack header pin arrays with the header sockets on the HackRF. The PortaPack should line up directly above the HackRF, and the five mounting holes should line up, too.
* With the headers lined up, rest the PortaPack on top of the HackRF. Gently squeeze the two boards together near where the headers are. The gap between the HackRF's sockets and the PortaPack's pins should shrink and disappear once the boards come together.

(TODO: photos/video still needed)

### Install PortaPack Board Assembly into Case

If you got the optional aluminum case, here's how to install the PortaPack + HackRF board assembly into the case. All the necessary hardware and tools are included with the case.

* For each of the five mounting holes:
    * Take a bolt and thread a tooth-lock washer on to it.
    * Take a spacer and insert it between the PortaPack and HackRF boards, at the position of the mounting hole.
    * Insert the bolt-washer combination through the PortaPack, the spacer, and the HackRF.
* One side of the board stack has two gold SMA connectors. Insert those connectors through the corresponding large, round holes inside the case.
* The two bolts closest to the two SMA connectors need to be pulled up about one centimeter (half an inch) to clear the bottom of the case.
* Gently rock the opposite edge of the board assembly so that it drops into the case. This does _not_ require any force. If it does require force, something is wrong.
* Using the provided 2.5mm hex/Allen wrench, _gently_ tighten the five bolts.
* Re-attach the gold washers and nuts onto the three SMA connectors. Install them in this order: smooth washer, tooth-lock washer, nut. Finger-tightening the nuts is enough.
* Re-attach the three red "nipples".

Here's a video of how it's done (links to YouTube):

[![On YouTube: Installing a PortaPack into the Aluminum Case](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/portapack_encase_youtube.jpg)](https://youtu.be/5r_7QCcSUEA "Installing a PortaPack into the Aluminum Case")
