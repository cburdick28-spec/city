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
| Tools | `1`–`8`, `F` fire station, `B` bus stop, `G` stadium, `H` spire, `M` metro station |
| Effects on/off | `X` |
| Pause | Space |

On touch screens, pick the Look around tool to orbit, and use two fingers to pan and zoom.

## How the city works

- Zoned lots grow within 2 tiles of a road, and only while the city has enough power.
- Lots upgrade through three levels as demand rises. Demand depends on residents, jobs, tax rate and mood.
- Mood rises with parks and falls with pollution, high taxes and blackouts.
- Each month the city collects taxes and pays upkeep for roads, plants and parks.
- Goals pay out cash. Finish the one shown in the side panel to get the next.
- Landmarks unlock by rank: the Stadium at Large town and the Spire at City. They lift mood and earn monthly income.
- Mega complexes: when a 2x2 patch of level 3 lots of the same type is in demand and the city is happy, it merges into one big complex (more homes or jobs, bigger model). Bulldoze or let demand collapse and it breaks back into regular lots.
- Transit: bus stops go on road tiles and cover 4 tiles, metro stations (Large town) cover 7. Residents in range raise mood, pay fares and cut car traffic. Buses run the streets.
- Past about 800 residents the city also pays for services, so very big cities are not free money. Watch the tax rate.
- Fires start at random once the city is a few weeks old. A fire station puts out any fire within 6 tiles. Without one, fires spread and burn lots down, so build a station or bulldoze a firebreak.
- The game autosaves to your browser's local storage.

## Graphics

Bloom, a soft miniature-style blur at the screen edges and a vignette are on by default. If the frame rate drops, the game turns them off by itself. Press `X` to toggle them. The effects use three.js post-processing scripts self-hosted in `vendor/fx/`.

## Starting points

The start menu (also behind the **New game / menu** button) has two tabs:

- **Sandbox**: Blank land, Hamlet, Town, City and Metropolis. The Town, City and Metropolis presets are generated fresh each time, so no two are the same.
- **Scenarios**: Blackout (one power plant left), Firestorm (fires burning, no fire station), Debt Spiral (deep in debt with heavy upkeep) and Ghost Town (the town is half empty and unhappy). Each has objectives, a time limit and a win/lose screen. They start paused so you can plan.

Difficulty (Easy, Normal, Hard, Brutal) changes starting cash, income, upkeep, fire frequency, citizen mood and goal rewards. Metropolis is heavy; the game drops effects and then shadows by itself if the frame rate falls.
