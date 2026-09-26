[README.md](https://github.com/user-attachments/files/32688459/README.md)
# Clip Compare

Compare two video clips on one synced playhead, then measure which one holds more detail.

**Open it:** https://dangpublishing.github.io/video-compare/

Built for judging AI video renders side by side (for example a one-pass vs two-pass MiniMax H3 render, or the same shot from two different tools), but it works on any two clips.

## What it does

- **Three views:** Wipe (drag across the picture to move the split line), Side by side, and A/B flip (click the picture or press X to swap).
- **Frame-accurate playback:** both clips share one playhead. Step one frame at a time, scrub, slow to ¼× or ½×, loop, zoom up to 4× and pan.
- **Timecode and frame number**, with a frames-per-second setting (default 24).
- **Sound from A or B**, one at a time.
- **Warnings** when the two clips differ in length or resolution, or when the clip picked for sound has no sound track.
- **Measure:** scores both clips frame by frame and reports:
  - fine detail (sharp edges and texture), overall, with brightness and contrast evened out, and on the calmest quarter of frames
  - flicker in still areas (lower is steadier)
  - amount of motion, brightness and contrast
  - how many frames B is sharper on
  - a per-frame chart; click it to jump to that frame

## How to use

1. For each slot, **Choose file…**, drag a clip onto it, or paste a video link and click **Load**. Dropping two files on the picture loads both (first file goes to A).
2. Give each clip a label, for example "Single pass" and "Multipass".
3. Pick a view and play, or step through with the arrow keys.
4. Click **Measure A vs B** for the numbers.

### Keyboard

| Key | Action |
|---|---|
| Space | Play / pause |
| ← → | One frame back / forward |
| Shift + ← → | One second back / forward |
| Home | Back to the start |
| 1 / 2 / 3 | Wipe / Side by side / A/B flip |
| X | Flip between A and B |
| Shift + drag | Pan when zoomed in |

### Sharing a comparison

When both clips are loaded from links, the page shows a **Copy link** button. That link opens the same comparison with both clips and labels:

```
https://dangpublishing.github.io/video-compare/?a=<link to clip A>&b=<link to clip B>&la=Single%20pass&lb=Multipass
```

Links from RunningHub results work while RunningHub keeps the files; they may expire.

## Good to know

- **Your files stay on your computer.** Clips you choose from your computer are played and measured in your browser; nothing is uploaded anywhere.
- **Use 8-bit H.264 MP4.** Browsers can't play 10-bit video (for example RunningHub two-stage "Stage 2" files). Re-export those as 8-bit first.
- **ComfyUI saves two files per clip.** The video save node writes `name_00001.mp4` (no sound) and `name_00001-audio.mp4` (with sound). Load the `-audio` one if you want sound.
- **Measuring links.** A pasted link can only be measured if its server lets the page read the video. If it can't, the page says so; download the clip and load it as a file instead.
- **What the numbers mean.** Both clips are measured at the same reduced size (688 px wide) so different resolutions compare fairly. The numbers are relative: use them to compare A with B, not as absolute scores. Fine detail is the average difference between each frame and a blurred copy of itself; flicker is the average frame-to-frame change in the stillest 30% of the picture.
- **It judges the picture, not the performance.** A clip can score sharper because less happens in it. Watch whether the action actually works too.

## Files

Everything is in one file, `index.html`. The only outside requests are two fonts from Google Fonts; the page still works without them.
