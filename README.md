# Minuit Munchies

A customizable chicken-box concept built around 250 g of marinated chicken
thigh, fresh tomatoes and onions, and a signature mayo-based sauce — customers
choose how to complete the meal.

`index.html` is the whole site: one self-contained file, no build step, no
runtime dependencies beyond Google Fonts.

## The animated hero

The hero is a scroll-linked canvas sequence. The page pins the stage with
`position: sticky` and maps scroll distance to a 0→1 playhead, which drives both
the frames and the copy beats.

There is deliberately **no animation library**. GSAP + ScrollTrigger is roughly
70 KB gzipped to do what native sticky positioning and one `requestAnimationFrame`
loop do here in about 4 KB — and the brief put Lighthouse ahead of convenience.
What's implemented instead:

- **Pinned stage, native scroll.** Scrolling is never hijacked or intercepted,
  so the page stays navigable and the scrollbar keeps telling the truth.
- **Cinematic easing.** The playhead chases the scroll position through a
  smoothed lerp, so motion decelerates into rest instead of snapping. No spring,
  no bounce.
- **Demand loading.** Frames load nearest-the-playhead first with a coarse
  keyframe pass underneath, capped at six concurrent requests. Scrubbing to an
  unloaded part of the timeline shows the nearest decoded frame rather than
  blanking.
- **Format probing.** AVIF, then WebP, then JPG — the first that decodes wins.
- **It stops.** The render loop exits once the playhead settles and nothing is
  in flight, and only runs while the hero is actually on screen.
- **Placeholder mode.** With no frames uploaded, the hero renders the
  choreography procedurally. Every act, transition and copy beat is scrubable
  today, so the edit can be judged before anything is shot.

Timing lives in two arrays near the top of the script: `PHASES` (the nine acts,
with relative `share` weights that are normalised automatically) and `BEATS`
(the copy, positioned on the same timeline). Retiming the edit means changing
numbers, not code.

Reduced-motion, Save-Data and very low-memory visitors get `.still` mode: a
static hero image, the full copy, and every CTA intact.

## Before it goes live

1. **WhatsApp number** — `WHATSAPP_NUMBER` at the top of the script. Digits
   only, with country code, no `+` or spaces (e.g. `15145550123`). Until it's
   set, the order button shows a setup notice instead of opening a broken chat.
2. **Prices** — the `SIDES` and `EXTRAS` arrays in the same config block. The
   three sided boxes are $18; the Simple Box is $15, which is an assumption and
   needs confirming.
3. **Photos** — see `images/README.md`.
4. **Hero frames** — see `images/seq/README.md`.

## Still to decide

- Delivery area, delivery fee and pickup. The FAQ currently sidesteps this by
  asking customers to confirm their address in the WhatsApp chat.
- Social handles and a phone number for the footer.
- `Minuit_munchies.html` is the previous baguette-era page. Nothing links to it
  and it can be deleted whenever you're ready.
