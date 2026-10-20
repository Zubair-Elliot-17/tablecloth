# Tablecloth

A website for **Tablecloth**, a fictional wine estate in Constantia, Cape Town. I built it as a portfolio piece.

[**Live site**](https://tablecloth-sage.vercel.app) · [**What's on the page**](#whats-on-the-page)

<a href="https://tablecloth-sage.vercel.app"><img src="docs/home.jpg" alt="The Tablecloth homepage" width="820"></a>

## Why a wine estate

I wanted the most typical Cape Town business I could find. Tourism is the city's biggest visitor draw (R24.5 billion in direct spend in 2025, according to Cape Town Tourism), and wine estates lead it. So the client is a cellar door.

## The idea

Most summer afternoons the south-easter pulls a cloud over Table Mountain, and locals call it the tablecloth. On the far side of the ridge, that cloud cools the vineyards. That's why Constantia can grow cool-climate wine in a hot city. I named the estate after the cloud and made the site about it.

## What's on the page

The page reads like a short book: a prologue, then four chapters separated by full-width photographs.

| Part | What it does | How |
|---|---|---|
| Hero | The tablecloth pouring down the face of Table Mountain, with the estate's name and the contents set small above it. | One photograph and a slow settle on load. Nothing else moves. |
| Prologue | What the estate is and why the cloud matters, signed by the winemaker, with the chapter list. | Static. |
| I. The cloud | How the south-easter makes the tablecloth, with a framed print. Then a pinned February day from 06:00 to 20:00: a clock, the city and vineyard temperatures pulling apart, and one line on what's happening. The photo behind it is washed in the sky's colour for that hour. | GSAP ScrollTrigger scrub, one screen long. The wash is a `mix-blend-mode: multiply` layer whose colour is set per hour. |
| II. The slope | A map of the five blocks. As you scroll, the blocks draw in, the grapes ripen to their own colour, and harvest bins roll down the farm tracks to the cellar while a tonnage counter climbs. Tap a block for its grape, height, planting year and wine. | SVG built from one data list. Outlines and vine rows draw with `pathLength="1"` dash offsets, and the bins follow each track with `getPointAtLength`. |
| III. The wines | Hold a glass (finger, mouse, Space or Enter) and a bottle lifts, tips and pours until you let go. Tap a full glass to empty it. | Each glass is a button. Fill level, bottle tilt and stream are set every animation frame on an SVG clipped to the bowl. A click from assistive tech pours a full glass by itself. |
| IV. The cellar door | Tasting booking with real validation: closed Mondays, tomorrow to six months ahead, 1–12 guests. | Client-side only. Nothing is sent, and the page says so. |

## Design choices

I took the structure from [Promontory](https://www.promontory.wine), the Harlan family's Napa estate, which I think is the best wine site there is. Its story is fog, like this estate's story is cloud. It lets toned landscape photographs carry the page, keeps the type small and quiet, and tells the estate as numbered chapters.

- **Photographs:** seven Creative Commons photos of Table Mountain, Constantia and a cellar, all toned to one cool monochrome (slate to cloud white) so they read as a series. Promontory tones everything sepia. This estate's story is cold, so the tone is grey. The only colour on the page is the wine, the ripening grapes on the map, the sky wash in the February day, and one red for chapter numbers and the booking button.
- **Type:** Libre Caslon only, from the century when Constantia wine was famous enough for Napoleon to order it on St Helena. Spaced capitals are kept for the wordmark, nav and chapter titles. Text is set in one narrow, justified column with italic subtitles. The signature is Mrs Saint Delafield.
- **Details:** framed inset prints with a white border, a winemaker's signature, and a slim bar with the name and "Book a tasting" that slides in once the masthead has gone.

## Stack

One `index.html` plus `img/`. GSAP 3.13 + ScrollTrigger from cdnjs, Lenis for smooth scroll. There's no build step. Each photo is served at 1200 and 2400 px wide (600/1000 for the inset prints) through `srcset`.

```sh
python3 -m http.server 8790
```

## Photographs

From Wikimedia Commons, cropped and toned to monochrome. The toned versions are shared under the same licences.

- [The tablecloth over Table Mountain (hero)](https://commons.wikimedia.org/wiki/File:Cape_Town,_Table_Mountain,_Table_Cloth.jpg) by KodachromeFan, [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0)
- [Cloud around the peaks (February day)](https://commons.wikimedia.org/wiki/File:Table_Mountain_clouds.jpg) by Selsong, [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0)
- [Cloud pouring off the table (chapter I print)](https://commons.wikimedia.org/wiki/File:Clouds_in_table_mountain_(14584234627).jpg) by David Rosen from London, UK, [CC BY 2.0](https://creativecommons.org/licenses/by/2.0)
- [Constantia vineyards](https://commons.wikimedia.org/wiki/File:Constantia_vineyards.jpg) by Barry haynes, [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0)
- [Morning fog in a vineyard (chapter II print)](https://commons.wikimedia.org/wiki/File:Early_morning_fog_in_Nebbiolo_vineyard.jpg) by Blue moon in her eyes, [CC BY 2.0](https://creativecommons.org/licenses/by/2.0)
- [Old wine barrels](https://commons.wikimedia.org/wiki/File:Old_Wine_Barrels.jpg) by Eric Kilby, [CC BY-SA 2.0](https://creativecommons.org/licenses/by-sa/2.0)
- [Constantia Nek](https://commons.wikimedia.org/wiki/File:Walking_up_Constantia_Nek.jpg) by Michael Rowe, [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0)

## Details

- `prefers-reduced-motion`: no smooth scroll and no settle on load. The day scrub follows the scrollbar directly.
- Phones get a single column, prints that sit between paragraphs instead of floating, and left-aligned text instead of justified.
- Visible focus rings, labelled form fields, and error messages tied to their inputs.

Tablecloth, its address, wines and temperatures are made up.
