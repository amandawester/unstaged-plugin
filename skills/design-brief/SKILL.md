---
name: design-brief
description: Write a design brief for a florist, stylist, stationer, baker or planner from the couple's own UNSTAGED moodboards, palette, creative direction and Decor ideas, or suggest decor in the same tone. Use when the user asks what their style is, wants something to send a vendor, asks for ideas for tables, flowers, lighting or a moment of the day, or wants to save a reference image.
---

The couple has already done the looking. The brief should sound like their references, not like a wedding in general.

## Gather

1. `get_creative_direction`: vibe words, the written vision, the palettes with hex values, and what to avoid.
2. `list_moodboards`, then `get_moodboard` for the boards that matter to this vendor. It returns the images themselves, eight per call; use `offset` for more. Look at them before writing a word.
3. `list_decor_ideas`, and `get_decor_idea` for the ones in this vendor's area, with their images and what is left to do.
4. `get_wedding_overview` for the date, place and guest count, and `get_timeline` when the brief depends on the order of the day or the light at a certain hour.

## Write the brief

Describe what is in the images: materials, how full or spare the tables are, the height of the arrangements, the kind of light, what is repeated from board to board. "Low, loose arrangements in bud vases, a lot of bare linen, candlelight rather than uplighting" is a brief. "Romantic and timeless" is not.

One page, in this order:

1. The day in two sentences: date, place, guest count, the feeling.
2. Palette, with hex values, and which colours carry and which are accents.
3. What we want, by moment of the day (ceremony, dinner, party), in the vendor's own terms.
4. What we do not want. Take this from the creative direction's "avoid" and from what is absent in every image.
5. Practical: what the couple has already decided or bought (from the Decor ideas), and the open questions for the vendor.

Where the boards disagree with each other, say so instead of averaging them. That is useful for the couple to see before a vendor does.

Mention that the Wedding Deck (`get_deck`) is a link they can send along with the brief.

## Ideas and references

When asked for ideas, tie each one to something in their own boards. To keep an idea, offer `add_decor_idea` under the right moment, and `add_decor_todo` for what it takes to make it happen.

To save a reference from the web, use `save_image_from_link` with the moodboard or Decor idea it belongs to. A Decor idea holds six images. For photos on the user's own phone or computer, call `create_upload_link` and pass the link on exactly as it is returned; it is valid for 20 minutes.
