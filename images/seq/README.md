# Hero frame sequence

The cinematic hero is a scroll-linked canvas animation. It plays a numbered
frame sequence that lives in this folder. **Until the frames exist the hero
runs in placeholder mode** — the full choreography, timing and copy still work,
so you can scrub the sequence and judge the pacing before shooting anything.

## Naming

    images/seq/frame-0001.webp
    images/seq/frame-0002.webp
    ...
    images/seq/frame-0180.webp

Four-digit, 1-indexed, zero-padded. Set `SEQ.count` in `index.html` to however
many frames you actually deliver — the whole timeline rescales automatically.

## Formats

The loader probes `avif`, then `webp`, then `jpg` on the first frame and uses
whichever the browser accepts. Ship one format; AVIF is smallest, WebP is the
safe default. Do not mix formats within a sequence.

## Specs

| Property   | Value                                                        |
|------------|--------------------------------------------------------------|
| Resolution | 1920 × 1080 desktop. Optionally 1080 × 1350 in `seq-portrait/`|
| Frame rate | Shoot at 30 fps, export every other frame (~15 fps effective) |
| Length     | 150–200 frames total. More than ~240 is wasted bandwidth      |
| Weight     | Target ≤ 55 KB per frame. 180 frames × 55 KB ≈ 10 MB total   |
| Framing    | Keep the food centred — the canvas cover-crops on narrow screens |

## The shot list

The timeline is defined by `PHASES` in `index.html`. Each phase maps to a slice
of the scroll. Shoot it as one continuous move if you can — the whole point is
that it reads as a single take.

| #  | Phase                | Share | What happens                                  |
|----|----------------------|-------|-----------------------------------------------|
| 1  | Marinade             |  10%  | Macro on raw marinated thigh, spice, gloss    |
| 2  | To the grill         |  12%  | Chicken lands on the hot surface              |
| 3  | Char                 |  16%  | Browning, char marks, steam, sizzle           |
| 4  | Into the box         |  12%  | Chopped pieces fall into the kraft box        |
| 5  | Tomatoes and onion   |  10%  | Fresh veg drops in                            |
| 6  | The sauce            |  12%  | Signature sauce drizzled over the top         |
| 7  | The Simple Box       |   8%  | Camera pulls back, full box visible           |
| 8  | Choose your side     |  12%  | Plantain, then fries, then bread enter frame  |
| 9  | Made to satisfy      |   8%  | Finished box centred, branding, CTA           |

Adjust the `share` values in `PHASES` to match how the edit actually cuts.

## Static fallback

    images/hero-still.jpg

Shown instead of the sequence when the visitor prefers reduced motion, has
Save-Data on, or is on a very low-memory device. Make it the best single frame
in the whole sequence — for a lot of people this is the only hero they see.
