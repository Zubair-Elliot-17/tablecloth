# Tablecloth

A website for **Tablecloth**, a fictional wine estate in Constantia, Cape Town. I built it as a portfolio piece.

**Live:** https://tablecloth-sage.vercel.app

## Why a wine estate

I wanted the most typical Cape Town business I could find. Tourism is the city's biggest visitor draw (R24.5 billion in direct spend in 2025, according to Cape Town Tourism), and wine estates lead it. So the client is a cellar door.

## The idea

Most summer afternoons the south-easter pulls a cloud over Table Mountain, and locals call it the tablecloth. On the far side of the ridge, that cloud cools the vineyards. That's why Constantia can grow cool-climate wine in a hot city. I named the estate after the cloud and made the site about it.

## What's on the page

| Section | Motion | How |
|---|---|---|
| Hero | The tablecloth rests on the mountain, then pours down the face and evaporates as it sinks. Moving the cursor pushes the cloud around. | Canvas: ~400 soft particles (~220 on phones) that rest on the table, then fall and stretch into streaks. They fade as they drop into warmer air. |
| Headline | Letters start thin and widen into place on load. They stretch further the harder you "blow" with the cursor. | The variable `wdth` axis of Anybody, driven by smoothed cursor speed. The wind readout climbs too. |
| A February day | Pinned scroll scrub from 06:00 to 20:00. The sky changes colour and the sun arcs across. The cloud spills over at 13:30, and the city and vineyard temperatures pull apart. | GSAP ScrollTrigger scrub. All five moments stay listed as a timeline, and the current one is highlighted. |
| Wines | Each glass fills with its wine as it scrolls into view. | SVG clip path with a CSS transform. |
| Visit | Tasting booking with real validation: closed Mondays, tomorrow to six months ahead, 1–12 guests. | Client-side only. Nothing is sent, and the page says so. |

## Design choices

- **Palette:** cool fog, mountain slate, vineyard green, pale Sauvignon gold and a protea pink for focus and errors. I avoided the warm cream every wine site uses, because this estate's story is about cold.
- **Type:** Anybody (a variable-width grotesque) for display, so the type can react to the wind. Newsreader for reading.
- **One bold thing:** the cloud. Everything else stays quiet.

## Stack

One `index.html`. GSAP 3.13 + ScrollTrigger from cdnjs, Lenis for smooth scroll. There's no build step and there are no images: the mountain, cloud and glasses are drawn in code.

```sh
python3 -m http.server 8790
```

## Details

- `prefers-reduced-motion`: no smooth scroll, no intro, and the cloud is drawn as a still frame. The day scrub follows the scrollbar directly.
- Phones get a tighter crop on the mountain, fewer particles, a single-column layout and only the current timeline moment.
- Visible focus rings, labelled form fields, and error messages tied to their inputs.

Tablecloth, its address, wines and temperatures are made up.
