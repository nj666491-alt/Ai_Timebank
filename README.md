
AI Time Bank
A mobile app that helps free-tier AI platform users manage their daily usage time smartly. Track how long you spend on each AI platform, borrow extra minutes from tomorrow's allowance when you need more time today, and review your full usage history — all on-device with no account needed.

Screenshots
Run the app and scan the QR code with Expo Go to see it on your device.

Features
Usage Timer — Start and stop a live session timer for any AI platform (ChatGPT, Claude, Gemini, Perplexity, and more)
Time Ring — A circular progress ring shows how much of your daily limit you have left
Borrow Time — Extend today's limit by borrowing minutes from tomorrow's allowance (up to 50% of the daily limit)
Tomorrow Alert — A clear warning on the home screen showing exactly how many minutes will be cut from tomorrow
Usage History — A dated log of every session and every borrow, so nothing is hidden
Platform Settings — Toggle platforms on/off and edit each platform's daily limit inline
Feedback Form — Submit star ratings, categories (Suggestion, Bug, Review, UI, Other), and written feedback stored locally
Dark Mode — Full dark/light mode support based on device setting
Tech Stack
Layer	Technology
Framework	Expo (SDK 54) + Expo Router
Language	TypeScript
UI	React Native
Navigation	Expo Router file-based tabs
State	React Context + AsyncStorage
Icons	@expo/vector-icons (Feather)
Charts	react-native-svg (custom TimeRing component)
Fonts	Inter (via @expo-google-fonts/inter)
Haptics	expo-haptics
Storage	@react-native-async-storage/async-storage
Package manager	pnpm (workspace monorepo)
Project Structure
ai-time-bank/
├── app.json                        # Expo app config
├── package.json
├── tsconfig.json
├── babel.config.js
├── metro.config.js
│
├── app/                            # Expo Router screens
│   ├── _layout.tsx                 # Root layout (providers)
│   ├── +not-found.tsx
│   └── (tabs)/
│       ├── _layout.tsx             # Tab bar (5 tabs)
│       ├── index.tsx               # Home — overview ring + quick stats
│       ├── platforms.tsx           # Per-platform cards + timers
│       ├── history.tsx             # Full usage & borrow log
│       ├── settings.tsx            # Platform toggles + limit editor
│       └── feedback.tsx            # Star rating + review form
│
├── components/
│   ├── TimeRing.tsx                # SVG circular progress ring
│   ├── PlatformCard.tsx            # Per-platform timer card
│   ├── BorrowModal.tsx             # Bottom sheet to borrow time
│   ├── ErrorBoundary.tsx
│   ├── ErrorFallback.tsx
│   └── KeyboardAwareScrollViewCompat.tsx
│
├── context/
│   ├── AppContext.tsx              # Platforms, usage, borrowing logic
│   └── FeedbackContext.tsx         # Feedback form state + storage
│
├── constants/
│   └── colors.ts                   # Design tokens (light + dark)
│
├── hooks/
│   └── useColors.ts                # Returns correct palette for scheme
│
└── assets/
    └── images/
        └── icon.png

Getting Started
Prerequisites
Node.js 18+
pnpm — npm install -g pnpm
Expo Go app on your phone (iOS or Android)
1. Clone the repo
git clone https://github.com/YOUR_USERNAME/ai-time-bank.git
cd ai-time-bank

2. Install dependencies
pnpm install

3. Start the dev server
pnpm --filter @workspace/mobile run dev

4. Open on your phone
Scan the QR code that appears in the terminal using:

iOS → Camera app
Android → Expo Go app
Or press w in the terminal to open the web version.

How Borrowing Works
Free-tier AI platforms give you a fixed daily usage window. This app lets you:

Use your normal daily allowance for a platform (e.g. 40 min for ChatGPT)
If you need more time today, tap Borrow and pick how many extra minutes (5 / 10 / 15 / 20 / 30)
You get a notification-style alert confirming the borrow and the tomorrow deduction
The Home screen shows a "Tomorrow's cut" banner so you always know what's owed
The limit is 50% of the daily quota — you can't borrow more than that
This doesn't bypass any platform limits. It's a personal time-tracking and self-management tool.
