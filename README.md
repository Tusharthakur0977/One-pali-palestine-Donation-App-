# OnePali 🕊️
OnePali is a beautifully crafted mobile application designed to seamlessly facilitate donations, build community identity, and track philanthropic impact. Built with an emphasis on premium user experience, the app features highly interactive micro-animations, real-time number reservation logic, and a gamified badge system to keep supporters engaged.

### 📱 Download the App
- [**iOS App Store**](https://apps.apple.com/in/app/onepali-%241-for-palestine/id6758080916)
- [**Google Play Store**](https://play.google.com/store/apps/details?id=com.onepali&pcampaignid=web_share)

## 🚀 Tech Stack
- **Core Framework:** React Native (v0.83.1) with TypeScript for type-safe, cross-platform mobile development.
- **State Management:** Redux Toolkit (`@reduxjs/toolkit`) for predictable, centralized application state.
- **Routing:** React Navigation v7 (`@react-navigation/native`, `native-stack`, `bottom-tabs`).
- **Backend & Cloud Services:** Firebase (Auth, App, Analytics, Messaging) and Axios for robust API communication.
- **Payments & Subscriptions:** Stripe React Native (`@stripe/stripe-react-native`) and React Native IAP (`react-native-iap`) for handling global donations.
- **Animations & UI Engine:** React Native Reanimated (v3), Lottie React Native, and Animated API for highly fluid 60FPS UI interactions.
- **Analytics & Marketing:** Klaviyo SDK and Firebase Analytics for detailed user journey tracking.

## ⭐ Spotlight Feature: The "Slot Machine" Number Reveal & Reservation Engine
One of the most technically demanding aspects of the app is the **Identity Number Reservation System**, specifically the `SlotMachineNumber` and `ClaimSpot` components. This feature allows users to claim a unique, randomized "Supporter Number" between 1 and 1,000,000, complete with a highly polished slot-machine reveal effect.

### Why it was technically challenging:
- **Complex Animation Orchestration:** The `SlotMachineNumber` component required sequencing multiple independent animations simultaneously. It uses staggered `setInterval` timers (spinning at ~50ms intervals) paired with React Native's `Animated` API to independently lock each digit of a 6-digit string from left to right.
- **Haptic Feedback Synchronization:** To make the interaction feel tactile and premium, `react-native-haptic-feedback` is synchronized down to the millisecond with the animation loops. The app triggers a *Light* impact when scrambling starts, a *Medium* impact as individual digits lock, and a *Heavy* impact when the final digit settles.
- **Dynamic Masking & Layout Shifts:** The logic involves dynamic string manipulation to automatically hide leading zeros (e.g., displaying `#123` instead of `#000123`). This required calculating precise bounding boxes and interpolating color opacities concurrently without dropping frames.
- **Concurrency & State Control:** On the backend/API side (`ClaimSpot`), the app handles debounced API polling to verify number availability in real-time. If a number is generated (via a shake-dice animation), a server-validated reservation token and an active expiry countdown timer are initialized using Redux, preventing race conditions if multiple users attempt to claim the same spot.

## 🛠 Key Features
- **Gamified Badge System:** A robust achievement engine (Growth, Community, and Impact badges) with locked/unlocked states and interactive modal breakdowns to encourage continuous support.
- **Stripe Donation Flow:** Secure, seamless integration with Stripe for processing recurring and one-time global donations.
- **Progress Tracking & Analytics:** Real-time dashboards visualizing both personal milestones and a global $1M community goal.
- **Push Notifications & Event Tracking:** Fully integrated Klaviyo and Firebase event tracking to trigger personalized notifications based on app usage and subscription milestones.
- **Dynamic Deep Linking & App Review:** Built-in routing for native App Store / Play Store reviews (`react-native-in-app-review`) triggered programmatically after meaningful user interactions.

## 💡 Why This Project Stands Out
OnePali proves my ability to go beyond basic CRUD applications and deliver a consumer-grade product that feels alive. By heavily utilizing the `Animated` API alongside synchronized haptics, I engineered a tactile user interface that feels premium and responsive. Furthermore, architecting a real-time reservation system with token expiration demonstrates my capability to handle complex asynchronous state management, debounced network requests, and edge-case error handling. This application is a testament to my focus on high-performance mobile engineering and pixel-perfect UI execution.
