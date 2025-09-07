## Sample Frontend File Structure

```
/learn.it
├── /public/
│   ├── index.html                  # Main HTML file for your React app
│   └── /assets/                    # Public assets like images, fonts, and maybe your Figma prototype image
├── /src/
│   ├── /components/                # Reusable UI components used across different pages
│   │   ├── /Auth/
│   │   │   ├── LoginForm.jsx       # Login form component
│   │   │   └── RegisterForm.jsx    # Registration form component
│   │   ├── /Common/
│   │   │   ├── Header.jsx          # Navigation bar
│   │   │   ├── Footer.jsx
│   │   │   └── Modal.jsx           # Reusable modal for pop-ups
│   │   ├── /Gamification/
│   │   │   ├── Leaderboard.jsx     # Displays the leaderboard
│   │   │   └── MissionCard.jsx     # A card for a daily mission
│   │   ├── /Resources/
│   │   │   ├── ResourceCard.jsx    # A card for a single resource file
│   │   │   └── UploadForm.jsx      # Form for uploading files
│   │   ├── /StudyRoom/
│   │   │   ├── StudyRoomCard.jsx   # The card for a study room in the lobby
│   │   │   ├── PomodoroTimer.jsx   # The timer component
│   │   │   └── VideoStream.jsx     # The video component using WebRTC
│   │   └── /Mentor/
│   │       ├── MentorCard.jsx      # A card to display mentor info
│   │       └── MeetingForm.jsx     # Form to create a mentor meeting
│   ├── /pages/                     # Top-level components that represent full pages/routes
│   │   ├── Dashboard.jsx           # Main dashboard for all user types
│   │   ├── StudyRoomsLobby.jsx     # The lobby page with a list of rooms
│   │   ├── StudyRoom.jsx           # The page for an active study room
│   │   ├── ResourcesHub.jsx        # The main page for resources
│   │   └── Profile.jsx             # User profile page
│   ├── /services/                  # Functions to interact with external services (Firebase, etc.)
│   │   ├── firebase.js             # Firebase initialization and authentication functions
│   │   ├── resourceService.js      # Logic for handling resource uploads/downloads
│   │   └── aiService.js            # Logic for calling the OpenAI API
│   ├── /styles/                    # Global stylesheets or themed components
│   │   └── main.css
│   ├── App.js                      # Main application component with routing logic
│   └── index.js                    # Entry point of the React application
├── .gitignore                      # Specifies files and folders to be ignored by Git
└── package.json                    # Manages project dependencies and scripts

```

## Sample Firebase Database Structure

Backend is handled by Firebase, which uses a NoSQL, JSON-like structure.

```
/firestore-db
├── users/                          # Top-level collection for all user profiles
│   ├── [userID]/
│   │   ├── role: "student" | "mentor"
│   │   ├── username: "..."
│   │   ├── points: 120
│   │   ├── profileData: {...}
│   │   └── missions: [...]          # Daily missions and completion status
├── studyRooms/                     # Collection for all active and past study rooms
│   ├── [roomID]/
│   │   ├── name: "Math Study Session"
│   │   ├── hostID: "..."
│   │   ├── isPublic: true
│   │   ├── participants: ["..."]
│   │   └── invitedMentorID: "..."   # ID of the invited mentor or AI mentor
├── resources/                      # Collection for shared learning materials
│   ├── [resourceID]/
│   │   ├── title: "..."
│   │   ├── fileURL: "..."          # Link to the file in Firebase Storage
│   │   ├── uploaderID: "..."
│   │   └── type: "PDF" | "video"
├── meetings/                       # Collection for mentor-led sessions
│   ├── [meetingID]/
│   │   ├── mentorID: "..."
│   │   ├── scheduledTime: "..."
│   │   └── topic: "..."
└── leaderboard/                    # A simpler collection for gamification
    ├── [entryID]/
    │   ├── userID: "..."
    │   └── totalPoints: 120

```