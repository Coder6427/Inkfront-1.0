# Inkfront Arena

An original top-down arena game with two rival squads, four match sizes, six playable specialists, and signature abilities.

## Play locally

Open `dist/index.html` directly, or serve the `dist` folder with any static web server. No installation is required.

## Match setup

Setup follows three steps in one panel: **Match → Character → Upgrade**.

1. Choose the team size, game mode, your team, and rival difficulty.
2. Pick a character and review its primary, secondary, and special in a single loadout card.
3. Choose one of three upgrade cards to deploy.

Choose Volt (aqua diamonds) or Flare (coral circles). AI fills every other slot; these are local player-versus-bot matches. Each squad uses different characters within its own team.

| Format | Players per side | Arena | Dimensions |
| --- | --- | --- | --- |
| 1v1 | 1 | Duel yard · Compact | 1,200 × 750 |
| 2v2 | 2 | Switchyard · Standard | 1,600 × 900 |
| 3v3 | 3 | Switchyard East · Expanded | 1,800 × 1,050 |
| 4v4 | 4 | Switchyard Grand · Large | 2,000 × 1,150 |

The 3v3 and 4v4 maps have more space and extra flank cover. Paint, navigation, spawn positions, control zones, the minimap, and camera boundaries all use the selected dimensions.

## Characters and upgrades

| Character | Primary | Secondary: E / right click | Special: F |
| --- | --- | --- | --- |
| Rook | Bastion repeater | Rampart disc: a shield that absorbs rival bullets and lets friendly shots pass | Citadel: a healing dome with 65% damage reduction |
| Vex | Prism carbine | Bankshot blade: a heavy projectile with three ricochets | Prism bloom: three radial volleys |
| Miso | Petal sprayer | Seedling station: a healing and ink-refill garden | Wildgarden: a large garden that heals allies and stings enemies |
| Kilo | Slugger cannon | Pop mortar: a delayed explosive lobbed over cover | Starfall: three staggered artillery strikes |
| Nyx | Needle driver | Afterimage mine: a proximity trap | Echo drive: seven seconds of twin shots, speed, and damage resistance |
| Tess | Arc caster | Static snare: a field that slows rivals | Stormwheel: a large storm that slows, damages, and repaints |

Secondary weapons cost 20 ink and have their own cooldowns. Specials charge through time, damage, and painting. Spawn shields, cover, and friendly-fire rules apply to ability damage. Mines and rival effects respect team visibility.

Before every deployment, choose exactly one of three randomly drawn upgrades:

- Supercharger: 45% faster special charge
- Pocket Workshop: 30% shorter secondary cooldown
- Deep Reservoir: 30% lower primary ink cost and 25% faster refill
- Kinetic Soles: 16% faster movement and 25% shorter dash cooldown
- Dense Ink: 20% more primary damage
- Reinforced Shell: 35 extra maximum hull

The chosen upgrade lasts for the match and survives respawns. Bots choose from the same heroes and upgrades and use the same ability rules.

## Match modes

- **Turf Claim** — paint more of the arena than the opposing team before the 90-second clock expires.
- **Sector Lock** — capture and hold the three marked sectors to earn points. First to 100 wins; otherwise the leader after 1:45 takes the match.
- **Team Clash** — disable opponents to score for the squad. First to 15 wins; otherwise the leader after 1:15 takes the match.

Friendly paint speeds movement and restores chroma in every mode, so painting remains useful even when territory is not the primary score.

## Camera and team vision

- The camera is zoomed in and smoothly follows the player.
- Every living teammate projects a circular field of view; those circles combine into shared team vision.
- The square minimap marks Volt in aqua and Flare in coral. Your whole squad is shown; rival dots appear only while a teammate can currently see them.
- Hidden opponents are not rendered or targetable. Obstacles still block line of sight, and a teammate spotting an opponent never enables a lock through a wall.
- Paint, arena geometry, and mode objectives remain readable outside the vision circles so players can still navigate and understand the match.
- Auto-lock can be toggled with `Q` or the **AUTO LOCK** button. It assists only against an eligible visible target and releases when that target leaves vision, line of sight, or range; manual aim always remains available.

## Controls

- `WASD` — move
- Mouse — aim
- Hold left click — spray
- `Space` — boost dash
- `E` or right click — secondary weapon
- `F` — charged special
- `Q` — toggle auto-lock
- `B` — toggle the AI lens (paths, goals, and danger heat)
- `P` or `Esc` — pause
- `M` — toggle sound

Touch devices use twin virtual sticks plus dash and on-screen ability buttons. A twin-stick gamepad is also supported: right trigger sprays, A dashes, left bumper uses the secondary, and right bumper uses the special.

## AI systems

- Utility-based Paint, Pressure, Recover, Defend, and Support intents
- Dynamic Coater, Vanguard, Anchor, and Rover roles
- A* navigation weighted by friendly paint, enemy paint, and learned danger
- Shared sightings and focus targets constrained by the same team-vision rules as the player
- Destination claims to keep teammates from crowding one patch
- Mode-aware plans for territory, sector ownership, and coordinated combat
- Ability decisions based on visible opponents, incoming fire, injured teammates, and contested objectives
- Zone neutralization and sudden-death overtime
- No-contact sweeps toward known rival spawn areas so duel bots can find a fight
- Late-match strategy shifts based on score, territory lead, and home pressure
- Fair difficulty settings that alter reaction, prediction, and coordination rather than stats
