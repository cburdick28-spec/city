# Blocktown

A 3D city-builder that runs in the browser. Paint roads, zone residential, commercial and industrial lots, keep the power on, and watch the skyline grow through day and night.

It is a static site: `index.html` holds the whole game, and three.js (r128, MIT) is self-hosted in `vendor/`. There is no build step.

## Run it locally

```bash
npm run dev
```

Then open http://localhost:3000.

## Deploy to Vercel

1. In Vercel, choose **Add New → Project** and import this repository.
2. Leave the framework preset as **Other**. No build command or output directory is needed; `vercel.json` already sets them.
3. Click **Deploy**.

Or from the command line: `npx vercel --prod`.

## Controls

| Action | Input |
| --- | --- |
| Build / paint | Left-click or drag with a building tool |
| Orbit | Right-drag, or the Look around tool |
| Pan | Shift + right-drag, WASD or arrow keys |
| Zoom | Mouse wheel, `+` / `-`, or pinch |
| Rotate | `Q` / `E` |
| Tools | `1`–`8`, `F` fire station, `G` stadium, `H` spire |
| Effects on/off | `X` |
| Pause | Space |

On touch screens, pick the Look around tool to orbit, and use two fingers to pan and zoom.

## How the city works

- Zoned lots only grow next to a road and while the city has enough power.
- Lots upgrade through three levels as demand rises. Demand depends on residents, jobs, tax rate and mood.
- Mood rises with parks and falls with pollution, high taxes and blackouts.
- Each month the city collects taxes and pays upkeep for roads, plants and parks.
- Goals pay out cash. Finish the one shown in the side panel to get the next.
- Landmarks unlock by rank: the Stadium at Large town and the Spire at City. They lift mood and earn monthly income.
- Fires start at random once the city is a few weeks old. A fire station puts out any fire within 6 tiles. Without one, fires spread and burn lots down, so build a station or bulldoze a firebreak.
- The game autosaves to your browser's local storage.

## Graphics

Bloom, a soft miniature-style blur at the screen edges and a vignette are on by default. If the frame rate drops, the game turns them off by itself. Press `X` to toggle them. The effects use three.js post-processing scripts self-hosted in `vendor/fx/`.
