# Minuit Munchies

A customizable chicken-box concept built around boldly marinated chicken thigh,
fresh toppings and a signature mayo-based sauce — customers choose how to
complete the meal.

`index.html` is the site: a single self-contained page, no build step, no
dependencies beyond Google Fonts.

## Before it goes live

1. **WhatsApp number** — `index.html`, `WHATSAPP_NUMBER` at the top of the
   script block. Digits only, with country code, no `+` or spaces
   (e.g. `15145550123`). Until it's set, the order button shows a setup notice
   instead of opening a broken chat.
2. **Prices** — the `SIDES` and `EXTRAS` arrays in the same config block. The
   three sided boxes are set to $18; the Simple Chicken Box is set to $15,
   which is an assumption and needs confirming.
3. **Photos** — see `images/README.md`.

## Still to decide

- Delivery area, delivery fee and pickup. The FAQ currently sidesteps this by
  asking customers to confirm their address in the WhatsApp chat.
- Social handles and a phone number for the footer.
- `Minuit_munchies.html` is the previous baguette-era page. It is no longer
  linked from anywhere and can be deleted once you're happy with the new site.
