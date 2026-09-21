# DIY Night Vision Headset

A head-mounted night vision viewer made from an analog starlight camera, a zoomable infrared light and a small display, mounted on a modified Utopia 360 phone VR headset.

for Hack Club Forge.

**Status:** Planning. The parts list is finalized and parts will be ordered. CAD and the wiring diagram are not started yet. See [JOURNAL.md] for progress.

## Goal

See in the dark with no video lag, and zoom in and out quickly without swapping lenses. Analog video was chosen on purpose because it has almost no delay, which matters when walking.

I'm starting with a one-eye view, because a single monitor can't show different images to each eye. A two-eye version is a stretch goal.

## How it works

```
3x 18650 (3S) -> 3S balanced protection board -> 3A fuse -> switch -> XL6009 boost (~13V) -+-> 4.3" monitor (12-24V)
                                                                                            +-> RunCam Phoenix 2 Nite (5-24V)

Camera video (composite/CVBS) -> monitor AV input (RCA)
850nm IR flashlight: runs on its own 18650 cell, separate from the main pack
```

- The camera has no IR filter, so it sees the light from the 850nm VCSEL flashlight.
- The 6-22mm varifocal lens zooms by hand. I'm designing a lever or knob so it can be adjusted with one hand.
- The boost converter is needed because the monitor needs at least 12V, and a 3S pack is 12.6V full and drops well below 12V as it drains. I set it to about 13V.

## Parts list (BOM)

| Part | Purpose | Price (EUR) | Link |
|---|---|---|---|
| RunCam Phoenix 2 Nite camera | Starlight analog camera, no IR filter, 1500TVL, 5-24V | 55.17 | [https://www.aliexpress.com/item/1005010693751353.html?pdp_ext_f=%7B%22sku_id%22%3A%2212000053209871131%22%7D&sourceType=1&spm=a2g0o.wish-manage-detail.0.0] |
| 6-22mm M12 varifocal lens (1/2.5", F1.6) | Zoom lens | 14.67 | [https://www.aliexpress.com/item/1005008242802353.html?pdp_ext_f=%7B%22sku_id%22%3A%2212000044349302343%22%7D&sourceType=1&spm=a2g0o.wish-manage-detail.0.0] |
| 4.3" AHD/CVBS monitor (12-24V, up to 6W) | Display | 17.86 | [https://www.aliexpress.com/item/1005010226690107.html?pdp_ext_f=%7B%22sku_id%22%3A%2212000051594828936%22%7D&sourceType=1&spm=a2g0o.wish-manage-detail.0.0] |
| 7W 850nm VCSEL zoom IR flashlight set | Infrared light (includes cell and USB charger) | 21.03 | [https://www.aliexpress.com/item/1005006500875898.html?pdp_ext_f=%7B%22sku_id%22%3A%2212000037431637360%22%7D&sourceType=1&spm=a2g0o.wish-manage-detail.0.0] |
| 3x Samsung 18650 cells (~3500mAh) | Main battery | 7.77 | [https://www.nkon.nl/en/samsung-inr18650-35e.html] |
| 3S SMT 18650 holder | Holds cells, tabs for balance wires | 1.82 | [https://www.aliexpress.com/item/1005006016303983.html?pdp_ext_f=%7B%22sku_id%22%3A%2212000035418389952%22%7D&sourceType=1&spm=a2g0o.wish-manage-detail.0.0] |
| 3S 40A balanced protection board | Cell protection and balancing | 1.37 | [https://www.aliexpress.com/item/1005004308277431.html?pdp_ext_f=%7B%22sku_id%22%3A%2212000028702197401%22%7D&sourceType=1&spm=a2g0o.wish-manage-detail.0.0]
| XL6009 boost converter | 3S pack to ~13V | 1.02 | [https://www.aliexpress.com/item/1005012006084118.html?pdp_ext_f=%7B%22sku_id%22%3A%2212000060288631764%22%7D&sourceType=1&spm=a2g0o.wish-manage-detail.0.0] |
| 3A mini blade fuses + inline holder | Short-circuit protection | 2.60 + 4.87 | [https://www.aliexpress.com/item/1005003741873928.html?pdp_ext_f=%7B%22sku_id%22%3A%2212000027004943501%22%7D&sourceType=1&spm=a2g0o.wish-manage-detail.0.0] + [https://www.aliexpress.com/item/1005006286934036.html?pdp_ext_f=%7B%22sku_id%22%3A%2212000036617728072%22%7D&sourceType=1&spm=a2g0o.wish-manage-detail.0.0] |
| KCD11 rocker switch | Power switch | 0.65 | [https://www.aliexpress.com/item/1005005546068119.html?pdp_ext_f=%7B%22sku_id%22%3A%2212000033486765329%22%7D&sourceType=1&spm=a2g0o.wish-manage-detail.0.0] |
| Silicone wire | Wiring | 0.55 | [https://www.aliexpress.com/item/1005004746235954.html?pdp_ext_f=%7B%22sku_id%22%3A%2212000030322326562%22%7D&sourceType=1&spm=a2g0o.wish-manage-detail.0.0] |

Total: about EUR [110] before shipping. Prices are from AliExpress at the time of planning.

## Power estimate

- Monitor: up to 6W. Camera: about 1W. Total: about 7W, or about 0.55A at 13V.
- Battery: 3 x 3500mAh at 3.7V is about 39Wh, so roughly 4 hours of runtime (estimate, to be measured).

## Expected performance (estimates, to be tested)

Assumptions: 22mm zoom lens, 1/2.8" sensor, about 960 pixels across the display, and the standard security-camera levels of detail.

| Task | Distance |
|---|---|
| Notice something is there | about 150 m |
| Tell that it's a person | about 60 m |
| Recognize someone I know | about 30 m |
| Identify a stranger | about 15 m |

The view is about 50 degrees at 6mm and about 14 degrees at 22mm. This is not a device for recognizing faces at 100 m. I'll measure the real numbers at night and publish them here, including anything that falls short.

## What I'm designing myself

- CAD for the headset modification: camera mount, IR light mount, display holder, battery pack (at the back of the strap as a counterweight)
- A lever or knob for the lens zoom and focus rings
- The wiring diagram and power design

I'm using ready-made modules (protection board, boost converter), not a custom PCB. I do my own soldering.

## Safety

- Balanced 3S protection board, 3A fuse, and insulated joints on all wiring.
- Cells from a reputable seller. I avoid unbranded cells with inflated capacity claims.
- I set and check the boost converter output with a multimeter before connecting the camera or monitor.
- Never charge the battery unattended.
- The 850nm light is invisible. Don't shine it at anyone's eyes at close range.

## Open questions and risks

- Which video input connector the monitor uses (RCA or 4-pin). I'll check when it arrives.
- Whether the camera's lens mount and sensor size match the 6-22mm lens without dark corners.
- Exact dimensions of the Utopia 360 phone tray, lens spacing and lens focal length. I need to measure them before the CAD.
- Real range, runtime and noise levels. All estimates above are untested.

## Planned repo structure

```
README.md
JOURNAL.md          progress log with dated entries
BOM.md              full parts list with links (coming)
cad/                CAD source files and STL files (coming)
docs/               wiring diagram, calculations, test results (coming)
photos/             build photos (coming)
```

## Test plan

1. Check the boost converter output and total current draw with a multimeter.
2. Measure runtime on a full battery.
3. At night, test what I can notice and recognize at different distances, with and without the IR light, and note how visible the light's glow is.
4. Record results in docs/ with photos.

## License

MIT (see LICENSE).

## Acknowledgements

Thanks to Hack Club Forge. I used an AI assistant (Claude) to research parts, compare options and check compatibility. The design, CAD and build are my own work.
