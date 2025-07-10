# AnkoScripts

A collection of automation scripts for the browser game OGame, written in Anko scripting language. These scripts help automate various game activities such as colonization, farming, ship building, and resource management.

## 📋 Table of Contents

- [Overview](#overview)
- [Scripts Description](#scripts-description)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Features](#features)
- [Disclaimer](#disclaimer)
- [Contributing](#contributing)

## 🎮 Overview

AnkoScripts is a comprehensive automation toolkit for OGame players who want to optimize their gameplay experience. The scripts are designed to handle repetitive tasks, allowing players to focus on strategic decisions rather than manual operations.

## 📜 Scripts Description

### Core Automation Scripts

- **`autoColonization.ank`** - Automated planet colonization system
  - Automatically sends colony ships to random locations
  - Abandons colonies with less than 290 fields
  - Includes safety delays and Telegram notifications
  - Requires planets to be sorted by colonization date

- **`farmBot.ank`** - Farming automation with realistic work patterns
  - Simulates human-like work schedules
  - Includes work cycles, breaks, and lunch periods
  - Automatically pauses/resumes farming activities
  - Sends Telegram notifications for status updates

- **`buildShips.ank`** - Automated ship production
  - Maintains a desired number of ships across all planets
  - Automatically builds ships when below threshold
  - Configurable ship types and quantities
  - Continuous monitoring with configurable intervals

### Utility Scripts

- **`bidAuction.ank`** - Automated auction bidding
- **`buildDef.ank`** - Automated defense building
- **`deployRecall.ank`** - Fleet deployment and recall automation
- **`expeditionDebris.ank`** - Expedition debris collection
- **`fleetSaveOnColonize.ank`** - Fleet protection during colonization
- **`jumpGate.ank`** - Jump gate automation
- **`loginLogout.ank`** - Session management
- **`missiles.ank`** - Missile system automation
- **`moonsToPlanets.ank`** - Moon to planet transfers
- **`planetsToMoons.ank`** - Planet to moon transfers
- **`repatriateNow.ank`** - Resource repatriation
- **`setFarmerSession.ank`** - Farming session configuration
- **`transferShips.ank`** - Ship transfer automation

## ⚙️ Prerequisites

- OGame account
- Anko browser extension or compatible script runner
- Telegram bot (for notifications - optional)
- Basic understanding of OGame mechanics

## 🚀 Installation

1. Clone or download this repository
2. Install the Ninja Bot


## 📖 Usage

### Basic Setup

1. **Configure Telegram Notifications** (Optional)
   ```javascript
   // Add your Telegram chat ID to scripts that use notifications
   TELEGRAM_CHAT_ID = "your_chat_id_here"
   ```

2. **Run Individual Scripts**
   - Load the desired `.ank` file in your script runner
   - Configure any required parameters
   - Execute the script

### Example Configuration

For `autoColonization.ank`:
```javascript
// Configure colonization parameters
destinationGalaxy = 3
minSystem = 240
maxSystem = 260
minPosition = 7
maxPosition = 9
```

For `buildShips.ank`:
```javascript
// Configure ship building parameters
shipsDesired = 500
checkInterval = 10  // minutes
```

## ⚙️ Configuration

### Global Variables

Most scripts use these common variables:
- `UserName` - Player name from game
- `UniverseName` - Current universe name
- `Language` - Game language setting
- `TELEGRAM_CHAT_ID` - Telegram notification target

### Safety Features

- **Delays**: Scripts include built-in delays to avoid detection
- **Randomization**: Random intervals and values to simulate human behavior
- **Error Handling**: Graceful error handling with retry mechanisms
- **Notifications**: Telegram integration for status updates

## ✨ Features

- **Automated Colonization**: Smart planet colonization with field validation
- **Farming Automation**: Human-like farming patterns with work schedules
- **Ship Management**: Automated ship building and maintenance
- **Resource Management**: Automated resource transfers and collection
- **Fleet Operations**: Automated fleet movements and protection
- **Real-time Notifications**: Telegram integration for status updates
- **Safety Mechanisms**: Built-in delays and error handling
- **Configurable Parameters**: Easy customization for different play styles

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

- Add clear comments and documentation
- Include error handling
- Test scripts thoroughly before submitting
- Follow the existing code style
- Add appropriate safety mechanisms

## 📝 License

This project is provided as-is for educational purposes. Use responsibly and in accordance with OGame's Terms of Service.

## 🔗 Related Links

- [OGame Official Website](https://ogame.org)
- [Anko Scripting Documentation](https://github.com/anko/anko)
- [OGame Wiki](https://ogame.fandom.com)

---

**Happy Gaming! 🚀** 