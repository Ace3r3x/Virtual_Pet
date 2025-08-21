# Virtual Pet Game 🐕

A real-time virtual pet simulation game built with p5.js and Firebase. Take care of your virtual dog by feeding, playing, and watching it go through realistic daily activities based on real-world time.

## Features ✨

- **Real-Time Pet Behavior**: Pet activities change based on actual time since last feeding
- **Firebase Integration**: Persistent data storage for food stock, feeding times, and game state
- **Multiple Environments**: Dynamic backgrounds including bedroom, garden, and washroom
- **Interactive Pet Care**: Feed your pet, manage food stock, and monitor pet happiness
- **Time-Based States**: Pet automatically transitions through different activities
- **Persistent Game State**: Your pet continues its routine even when you're away

## Tech Stack 🛠️

- **p5.js** - Creative coding library for graphics and interaction
- **p5.play.js** - Sprite management and game mechanics
- **Firebase Realtime Database** - Cloud data storage and synchronization
- **HTML5 Canvas** - Rendering and animation
- **JavaScript ES6** - Game logic and real-time mechanics

## Game Mechanics 🎮

### Pet States
Your virtual dog cycles through different states based on real-world time:

1. **Hungry** (Default): Pet needs feeding and stays in the main room
2. **Playing** (1 hour after feeding): Pet moves to the garden for exercise
3. **Sleeping** (2 hours after feeding): Pet rests in the bedroom
4. **Bathing** (2-4 hours after feeding): Pet cleans up in the washroom

### How to Play
1. **Feed Your Pet**: Click "Feed the Dog" button when pet is hungry
2. **Manage Food Stock**: Use "Add Food" button to replenish food supply
3. **Monitor Status**: Check last feeding time and remaining food
4. **Watch Activities**: Pet automatically moves between rooms based on schedule

### Food System
- Each feeding consumes 1 food unit from your stock
- Food stock is persistently stored in Firebase
- Pet happiness depends on regular feeding schedule
- Food can be added anytime to maintain adequate supply

## Project Structure 📁

\`\`\`
Virtual_Pet/
├── sketch.js              # Main game logic and Firebase integration
├── food.js               # Food class for inventory management
├── index.html            # HTML entry point with Firebase config
├── style.css             # Basic styling
├── p5.play.js           # p5.play library for sprites
├── assets/              # Game sprites and backgrounds
│   ├── Dog.png          # Default dog sprite
│   ├── happydog.png     # Happy dog after feeding
│   ├── deadDog.png      # Sad/neglected dog state
│   ├── running.png      # Dog running animation
│   ├── runningLeft.png  # Dog running left animation
│   ├── Bed Room.png     # Bedroom background
│   ├── Garden.png       # Garden background
│   ├── Living Room.png  # Living room background
│   ├── Wash Room.png    # Washroom background
│   ├── Milk.png         # Food/milk icon
│   ├── Food Stock.png   # Food inventory icon
│   ├── Injection.png    # Vaccination item
│   └── dogVaccination.png # Vaccinated dog sprite
└── README.md            # This file
\`\`\`

## Installation & Setup 🚀

### Prerequisites
- Modern web browser with HTML5 Canvas support
- Firebase account for database functionality
- Local web server (recommended for development)

### Quick Start

1. **Clone the repository**
   \`\`\`bash
   git clone https://github.com/Ace3r3x/Virtual_Pet.git
   cd Virtual_Pet
   \`\`\`

2. **Firebase Setup**
   - Create a new Firebase project at [Firebase Console](https://console.firebase.google.com/)
   - Enable Realtime Database
   - Copy your Firebase configuration
   - Update the Firebase config in `index.html`

3. **Run locally**
   \`\`\`bash
   # Using Python 3
   python -m http.server 8000
   
   # Using Node.js (if you have http-server installed)
   npx http-server
   \`\`\`

4. **Play the game**
   - Navigate to `http://localhost:8000`
   - Start taking care of your virtual pet!

## Code Structure 🏗️

### Main Components

**sketch.js** - Core game logic:
- Firebase database integration
- Real-time state management
- Pet behavior and animation
- User interface controls

**food.js** - Food management system:
- Food inventory display
- Stock management
- Feeding mechanics
- Room background rendering

### Key Functions

- `setup()`: Initializes game, Firebase connection, and UI elements
- `draw()`: Main game loop with state management and rendering
- `feedDog()`: Handles pet feeding and database updates
- `addFoods()`: Manages food stock replenishment
- `update()`: Updates game state in Firebase database

## Real-Time System ⏰

The game uses JavaScript's `hour()` function to create realistic pet behavior:

\`\`\`javascript
currentTime = hour();
if(currentTime == (lastFed + 1)) {
    update("Playing");     // Garden time
} else if(currentTime == (lastFed + 2)) {
    update("Sleeping");    // Bedroom time
} else if(currentTime > (lastFed + 2) && currentTime < (lastFed + 4)) {
    update("Bathing");     // Washroom time
} else {
    update("Hungry");      // Back to main room
}
\`\`\`

## Firebase Integration 🔥

### Database Structure
\`\`\`json
{
  "Food": 20,
  "FeedTime": 14,
  "gameState": "Playing"
}
\`\`\`

### Security Note ⚠️
The current implementation exposes Firebase configuration in the client-side code. For production use:
- Implement Firebase Security Rules
- Use environment variables for sensitive configuration
- Add user authentication for personalized pets

## Future Enhancements 🔮

- **Multiple Pet Types**: Cats, birds, and other virtual pets
- **Health System**: Vaccination schedules and health monitoring
- **Mini-Games**: Interactive activities in each room
- **Social Features**: Visit friends' pets and share achievements
- **Mobile App**: React Native version for mobile devices
- **Advanced AI**: More complex pet personality and behavior patterns
- **Customization**: Pet accessories, room decorations, and themes

## Known Issues 🐛

- Firebase configuration exposed in client code (security risk)
- Limited error handling for database connectivity
- Pet state transitions could be more gradual
- No offline mode when Firebase is unavailable

## Contributing 🤝

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Repository Information 📋

- **Repository**: [Ace3r3x/Virtual_Pet](https://github.com/Ace3r3x/Virtual_Pet)
- **Created**: December 5, 2020
- **Language**: 98.6% JavaScript
- **Game Type**: Real-time virtual pet simulation

## License 📄

This project is open source and available under the MIT License.

---

**Happy Pet Caring! 🐕💕**
