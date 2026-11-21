# AnkoScripts

A collection of automation scripts for the browser game OGame, written in the [Anko](https://github.com/mattn/anko) scripting language and run inside the Ninja Bot. They automate colonization, farming schedules, ship and defense building, fleet movements, fleetsaves, expeditions, debris harvesting and reporting.

## 📜 Scripts

Every script is standalone. Open it, adjust the `SETTINGS` block at the top and run it in the bot.

### 🪐 Colonization

- **`autoColonization.ank`** - Sends colony ships to random spots in a range and keeps the first colony with enough fields
  - Abandons the new colony if it has fewer than `minFields` (290 by default)
  - Only ever touches the planet at the colony ship's destination, never an older colony
  - Stops after `maxFailedSends` failed sends in a row

### 🛡️ Fleetsave and protection

- **`attackGuard.ank`** - Watches incoming attacks, fleetsaves the target shortly before impact and recalls the fleet afterwards
- **`fleetsaveToMoons.ank`** - Parks all ships (and resources) from every planet/moon on random own moons 1-2 galaxies away (galaxies are circular) at 10%, with human-like timing
  - `useRecall = true` cancels each fleet halfway so it flies home on its own; one return time is picked in the `returnFromHour`-`returnToHour` window and every fleet lands within `returnSpread` minutes of it
- **`nightFleetsave.ank`** - Sends one fleetsave and recalls it halfway so the fleet is back the next morning; refuses to send if the flight is too short to recall in time
- **`fleetsaveColonize.ank`** - Fleetsaves every moon with the Colonize mission (moons without a colony ship are skipped)

### 🚚 Fleet and resource transfers

- **`homeworldToPlanets.ank`** - Sends a fixed number of Large Cargos from the homeworld to every planet
- **`planetsToHomeworld.ank`** - Brings the Large Cargos from every planet back to the homeworld with all the resources they can carry
- **`moonsToHomeworld.ank`** - Parks the extra Large/Small Cargos from every moon on the homeworld, keeping a set amount on each moon
- **`moonsToPlanetsLC.ank`** - Sends the Large Cargos from every moon down to its planet
- **`planetsToMoons.ank`** - Sends all ships and resources from every planet up to its moon (planets without a moon are skipped)
- **`repatriateNow.ank`** - Runs `moonsToPlanetsLC` and `planetsToMoons` in order, waits for the fleets to land, then calls the bot's repatriate
- **`resourceCollector.ank`** - Periodically transports resources from planets above a threshold to the homeworld
- **`fleetBalancer.ank`** - Moves surplus ships so every planet reaches a target amount per ship type
- **`jumpGate.ank`** - Moves ships between moons through jump gates in pairs, leftovers to the home moon, every 30-45 min

### 🏗️ Building

- **`buildLargeCargos.ank`** - Keeps a target number of Large Cargos on every planet
- **`buildDef.ank`** - Keeps a target amount of each defense on every planet, scaled by a per-planet factor (0 = no defense)
- **`fullProduction.ank`** - Sets the metal, crystal and deuterium mines to 100% on every planet (energy settings untouched), with random delays between planets
- **`ipmAttack.ank`** - Builds and launches interplanetary missiles at a target a set number of times

### 🌾 Farming, expeditions and auctions

- **`farmSchedule.ank`** - Pauses and resumes the bot's farming on a human-like daily schedule (work cycles, breaks, lunch, night)
- **`createFarmSessions.ank`** - Every day, replaces its farm sessions with new ones: each moon gets the systems closest to it (circular galaxy, no overlap), with borders moved a little and split into random-sized sessions
- **`expeditionManager.ank`** - Keeps expedition slots busy, rotating origins and always leaving some fleet slots free
- **`debrisHarvester.ank`** - Scans galaxies for expedition debris and sends pathfinders from the nearest planet/moon
- **`scanExpeditionDebris.ank`** - Scans one galaxy and reports large expedition debris fields (no fleets sent)
- **`bidAuction.ank`** - Bids on the auctioneer up to a maximum, never against your own alliance

### 📊 Reporting and session

- **`dailyReport.ank`** - Daily Telegram report: points/rank change, resources per planet, fleet totals, slots
- **`loginLogout.ank`** - Logs out for a random 4-6 hours and logs back in

### 🧩 Template

- **`_template.ank`** - Starting point for new scripts with the SETTINGS / COMMON / MAIN layout

## ⚙️ Prerequisites

- OGame account
- Ninja Bot with scripting enabled
- Telegram and/or a Discord webhook configured in the bot (optional, for notifications; Discord uses the bot-provided `DISCORD_WEBHOOK`)

## 📖 Usage

1. Clone or download this repository
2. Load the `.ank` file in the bot's script section
3. Adjust the `SETTINGS` block at the top of the script
4. Run it

Settings you must fill in before the first run:

- `nightFleetsave.ank`: `sendTo` (the script refuses to run without it)
- `timezoneOffsetHours` (server time minus UTC) in `nightFleetsave`, `farmSchedule`, `dailyReport` and `fleetsaveToMoons`
- `resourceCollector.ank`: `lcCapacity` for your Hyperspace Technology level
- `buildDef.ank`: one entry in `factors` per planet, in the in-game order
- Coordinates and origins in `ipmAttack` and `expeditionManager`

## 🧱 Script structure and logging

Every script has the same layout:

1. **SETTINGS** - everything you are expected to change
2. **COMMON** - identical in every script: `UserName`, `UniverseName` and `Notify(level, msg)`
3. **MAIN** - the script logic

`Notify` levels:

| Level | Bot log | Telegram + Discord |
|---|---|---|
| `info` | ✅ | - |
| `report` | ✅ | ✅ |
| `warn` | ✅ | ✅ |
| `error` | ✅ | ✅ |

Per-item events (each fleet sent, each jump) are `info`, so Telegram and Discord only get start/end summaries, warnings and errors.

Human-like behavior is built in: random delays between actions, occasional longer pauses, random order and random times. Keep it when editing.

## ⚠️ Disclaimer

**Important**: These scripts are for educational and personal use only. Please be aware that:

- Using automation scripts may violate OGame's Terms of Service
- Use at your own risk - account bans are possible
- Scripts should be used responsibly and not excessively
- The authors are not responsible for any consequences of using these scripts

**Recommendations**:
- Use scripts moderately to avoid detection
- Monitor your account regularly
- Respect other players and game balance
- Consider the impact on your gaming experience

## 🤝 Contributing

Contributions are welcome! Please feel free to:

1. Fork the repository
2. Create a feature branch
3. Add new scripts or improve existing ones
4. Submit a pull request

### Guidelines for Contributions

- Start new scripts from `_template.ank` (SETTINGS, COMMON and MAIN blocks)
- Log with `Notify(level, msg)` instead of raw `SendTelegram`/`Print`
- Handle errors (`if err != nil`) and keep human-like random delays
- Test scripts in the bot before submitting

## 📝 License

This project is provided as-is for educational purposes. Use responsibly and in accordance with OGame's Terms of Service.

## 🔗 Related Links

- [OGame Official Website](https://ogame.org)
- [Anko Scripting Documentation](https://github.com/mattn/anko)
- [OGame Wiki](https://ogame.fandom.com)

---

**Happy Gaming! 🚀** 