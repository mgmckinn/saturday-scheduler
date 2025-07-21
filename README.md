<!-- @format -->

# Saturday Schedule App

A web-based application for automatically generating fair and balanced Saturday work schedules for teams. The app ensures equitable workload distribution by tracking each team member's shift history and prioritizing those who have worked fewer shifts.

## Features

### 🗓️ Smart Schedule Generation

- **Date-based staffing**: Automatically adjusts staffing levels based on the date
  - Days 1-3 of the month: 5 people (1 MOD + 4 Fillers)
  - Days 4-31 of the month: 4 people (1 MOD + 3 Fillers)
- **Fair rotation**: Prioritizes team members with the lowest shift counts
- **Role-specific assignment**: Separate pools for Managers on Duty (MODs) and Fillers

### 📊 Workload Tracking

- Real-time tracking of each team member's shift count
- Visual workload comparison across the team
- Reset functionality for new scheduling periods

### 📝 Schedule History

- Complete history of all generated schedules
- Chronologically sorted with full schedule details
- Bulk history clearing option

### 🔧 Technical Features

- **Responsive Design**: Works on desktop, tablet, and mobile devices
- **Local Mode**: Functions without Firebase for testing and development
- **Cloud Sync**: Full Firebase integration for data persistence (when configured)
- **Real-time Updates**: Live data synchronization across devices

## Getting Started

### Quick Start (Local Mode)

1. Clone or download the repository
2. Open `mainpage.html` in your web browser
3. The app will run in local mode without data persistence

### Full Setup with Firebase

#### Prerequisites

- A Firebase project with Firestore and Authentication enabled

#### Setup Steps

1. Create a Firebase project at [Firebase Console](https://console.firebase.google.com/)
2. Enable Firestore Database and Authentication (Anonymous sign-in)
3. Get your Firebase configuration object
4. Update the `firebaseConfig` object in `mainpage.html`:

```javascript
const firebaseConfig = {
  apiKey: "your-api-key",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "123456789",
  appId: "your-app-id",
};
```

## File Structure

```
saturday-scheduler/
├── mainpage.html                    # Main schedule generation page
├── workload-tracker.html           # Team workload tracking
├── saturdayschedulehistory.html    # Schedule history viewer
└── README.md                       # This file
```

## Team Configuration

### Current Team Setup

**Fillers:**

- Cody
- Jacob
- Veronica
- Vicky
- Mikayla
- Rita
- Karen

**Managers on Duty (MODs):**

- Mitch
- Amy
- Nick
- Shawan

### Customizing Team Members

To modify team members, edit the arrays in `mainpage.html`:

```javascript
const teamMembers = [
  "Cody",
  "Jacob",
  "Veronica",
  "Vicky",
  "Mikayla",
  "Rita",
  "Karen",
];
const mods = ["Mitch", "Amy", "Nick", "Shawan"];
```

**Note**: Remember to update the same arrays in `workload-tracker.html` to keep the workload tracking synchronized.

## How It Works

### Schedule Generation Algorithm

1. **Date Analysis**: Determines required staffing based on the day of the month
2. **Workload Retrieval**: Fetches current shift counts for all team members
3. **Fair Selection**:
   - Sorts MODs by shift count (ascending) and selects the least-worked MOD
   - Sorts remaining team members by shift count and selects the required number of fillers
   - Excludes the selected MOD from the filler pool

### Data Storage

- **Local Mode**: Data exists only during the browser session
- **Firebase Mode**: Data persists across devices and sessions
  - User sessions are managed via Firebase Anonymous Authentication
  - Schedule history stored in Firestore collections
  - Workload tracking maintained in real-time

## Usage Guide

### Generating a Schedule

1. Navigate to the Main Page
2. Select a date using the date picker
3. Click "Generate Schedule"
4. Review the generated schedule
5. Click "Submit Schedule" to save (updates workload tracking and history)

### Viewing Workload

1. Navigate to "Workload Tracker"
2. View current shift counts for all team members
3. Use "Reset Tracker" to start fresh (use cautiously!)

### Checking History

1. Navigate to "Schedule History"
2. Browse past schedules in chronological order
3. Use "Clear History" to remove all records (use cautiously!)

## Browser Compatibility

- ✅ Chrome 80+
- ✅ Firefox 75+
- ✅ Safari 13+
- ✅ Edge 80+

## Development

### Technologies Used

- **Frontend**: HTML5, CSS3 (Tailwind CSS), Vanilla JavaScript
- **Backend**: Firebase Firestore, Firebase Authentication
- **Deployment**: Static hosting compatible

### Local Development

1. Serve the files through a local web server (required for module imports)
2. Use Python: `python -m http.server 8000`
3. Or use Node.js: `npx serve`
4. Access via `http://localhost:8000/mainpage.html`

## Troubleshooting

### Common Issues

**Schedule not generating:**

- Check browser console for JavaScript errors
- Ensure a date is selected before clicking "Generate Schedule"
- Verify Firebase configuration if using cloud mode

**Data not persisting:**

- App may be running in local mode
- Check Firebase configuration and project setup
- Verify Firestore rules allow read/write access

**Navigation broken:**

- Ensure all HTML files are in the same directory
- Check that file names match the navigation links

## Security Notes

- Firebase security rules should be configured appropriately for production use
- Anonymous authentication is used by default - consider implementing proper authentication for sensitive environments
- Local mode stores no persistent data

## Contributing

1. Fork the repository
2. Create a feature branch
3. Test your changes thoroughly
4. Submit a pull request with a clear description

## License

This project is open source and available under the MIT License.

## Support

For issues, questions, or feature requests, please create an issue in the repository or contact the development team.

---

_Last updated: July 2025_
