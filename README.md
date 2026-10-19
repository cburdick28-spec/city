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
| Tools | `1`–`8`, `F` fire station, `B` bus stop, `G` stadium, `H` spire, `M` metro station, `J` school, `K` police, `L` hospital, `N` wind farm, `O` plaza, `I` library, `V` solar, `C` mall, `Y` museum, `T` amusement park, `U` university, `Z` airport, `R` upgrade, `9` zoo, `0` cathedral, `,` lighthouse, `.` harbor, `;` fountain, `'` clock tower, `P` photo mode, `[` cycle weather |
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
- Services: School, Police station, Wind farm (Village), Hospital and Plaza (Town). Each lifts mood for homes in range (school 6 tiles, police 6, hospital 7, plaza 3). Wind farms add 30 MW with no pollution.
- Bigger landmarks: Library (Village), Solar farm (+55 MW, Town), Shopping mall and Museum (Large town), Amusement park and University (City), Airport (City). Landmarks earn monthly income, add jobs or lift mood; the Tourism board policy doubles the tourist ones.
- Upgrades: pick the Upgrade tool (`R`) and click a service or landmark to level it up for a fee. School becomes a Campus, Hospital a Medical center, Fire station a Fire HQ (9 tile reach), Airport an International airport, and so on. Upgraded buildings get a gold ring and star, reach 50% further, and earn more (or add power and jobs) for extra upkeep.
- Bigger map: the map is now 88 x 88 tiles with two islands. Older 36 and 56 tile saves are centered in it automatically.
- More landmarks: Lighthouse (Town, rotating beam at night), Zoo and Cathedral (Large town). They lift mood and earn tourist income, and all three can be upgraded.
- Harbor (City rank, 3x3): must touch water, turns to face it, with a crane, containers and a moored ship; upgrades to a Container port. Fountain (Hamlet+) and Clock tower (Town) are cheap 1x1 mood boosters, each upgradeable.
- Disasters: earthquakes (with aftershock fires), coastal floods and meteor strikes hit now and then once a city is a few months old (not in Creative). Zoned lots drop levels and regrow on their own; landmarks and plants turn to rubble you bulldoze and rebuild. A relief fund pays part of the damage, fire stations clear rubble faster, and the Seismic code and Flood levees policies cut the damage. The Disaster drill buttons in the side panel let you trigger any of them, in any mode.
- Minimap in the side panel: shows roads, buildings, water and fires, and a white box for your view. Click or drag it to jump around.
- Weather: clear, rain and snow roll in on their own (press `[` to cycle). Rain dims the sky and makes fires 65% less likely.
- Photo mode (`P` or the panel button): hides the UI, eases to golden hour and slowly orbits. `P` or Esc to leave.
- Footprints: big landmarks take more land. Airport 4x4; Stadium, University, Amusement park and Zoo 3x3; Mall, Hospital, Museum, Cathedral and Solar farm 2x2. The hover box shows the footprint, bulldozing any tile removes the whole building, and bigger buildings reach a bit further.
- Second island: a round island sits in the east of the map, ringed by water. Water can't be built on except roads, which become bridges (6x road price, unlock at Town). There's a goal for settling the island, and the generated cities build their own bridges.
- Night life: the mall sign, amusement park and airport runway lights glow after dark, and an airport sends jets landing and taking off.
- Policies (the **Policies** button): Clean air act, Green belt, Fire code, Free transit, Business tax break, Night economy, Tourism board, High-rise incentives and Austerity. Each one trades money, taxes or mood for something else, and the higher ones unlock with rank.
- Past about 800 residents the city also pays for services, so very big cities are not free money. Watch the tax rate.
- Fires start at random once the city is a few weeks old. A fire station puts out any fire within 6 tiles. Without one, fires spread and burn lots down, so build a station or bulldoze a firebreak.
- The game autosaves to your browser's local storage.

## Graphics

Bloom, a soft miniature-style blur at the screen edges and a vignette are on by default. If the frame rate drops, the game turns them off by itself. Press `X` to toggle them. The effects use three.js post-processing scripts self-hosted in `vendor/fx/`.

## Starting points

The start menu (also behind the **New game / menu** button) has two tabs:

- **Sandbox**: Blank land, Hamlet, Town, City, Metropolis and Megacity (very heavy). The Town, City and Metropolis presets are generated fresh each time, so no two are the same.
- **City blocks**: five road-only starts with the streets already laid and no buildings: Grid blocks, Rings and spokes, Superblocks, Ring road, and Island link (a causeway to the second island). You zone, power and build everything.
- **Scenarios**: Blackout (one power plant left), Firestorm (fires burning, no fire station), Debt Spiral (deep in debt with heavy upkeep) and Ghost Town (the town is half empty and unhappy). Each has objectives, a time limit and a win/lose screen. They start paused so you can plan.

Creative mode (pick it under Difficulty) gives infinite money, zero upkeep, no fires, no blackouts, max mood and every building and policy unlocked from the start. It's sandbox only; scenarios fall back to Normal.

Difficulty (Easy, Normal, Hard, Brutal) changes starting cash, income, upkeep, fire frequency, citizen mood and goal rewards. Metropolis is heavy; the game drops effects and then shadows by itself if the frame rate falls.
