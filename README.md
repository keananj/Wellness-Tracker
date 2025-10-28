Perfect 👍 Here’s a **professional, clean, and beginner-friendly README.md** file description based on everything you’ve built for your **Wellness Tracker website** so far — including features like the dashboard, counseling, mood tracker, gratitude log, and calming music toggle.

---

# Emergency Call – Wellness Tracker

**Emergency Call** is a simple, calming wellness tracker web application built using **Vue.js**. It helps users check in with themselves, track their mood and gratitude, schedule counseling sessions, and find daily motivation—all in one gentle, supportive dashboard.

## Overview

The goal of this website is to promote emotional well-being and mindfulness. The interface is clean, minimal, and designed to create a sense of calm, allowing users to focus on self-reflection rather than complexity.

Upon visiting the page, users are greeted with a time-based welcome message (e.g., “Good morning, take a deep breath 🌤️”) followed by a dashboard of personal wellness tools.

---

## Features

### *Dashboard Overview**

* A clean and welcoming dashboard showing personalized greetings based on the user’s time of day.
* Motivational quotes that change dynamically to encourage positivity and reflection.
* A visually organized grid layout containing all main features in one scrollable view.

### 💬 **Counseling Section**

* Displays upcoming and past counseling sessions with counselor names and session types.
* Allows users to **add**, **edit**, or **remove** counseling schedules.
* Includes date and time selection for future counseling appointments.
* Shows summaries like *total sessions*, *average duration*, and *sessions this month*.

### **Mood Tracker**

* A static **Weekly Mood Report** displaying the user’s emotional pattern over the week.
* Moods represented with emojis, labels, or bar charts for easy understanding.
* Ends with a motivational reflection line to promote self-awareness.

### **Gratitude Log**

* A text field for users to write daily gratitude entries.
* Encourages mindfulness by prompting users with *“What are you thankful for today?”*
* Helps users reflect on positive moments regularly.

### **Music Toggle**

* A floating button that allows users to play or pause calm background music.
* Adds a comforting atmosphere to enhance focus and relaxation.

### **Daily Motivation**

* Displays a randomly selected motivational quote when the app loads.
* Refreshes automatically each day for a sense of inspiration and renewal.

---

## **Tech Stack**

* **Frontend:** Vue 3 (Composition API + `<script setup>`)
* **Styling:** CSS3 with responsive grid layout and theme variables
* **Build Tool:** Vite
* **Icons & Fonts:** Custom emojis and Google Fonts

---

## **Folder Structure**

```
src/
│
├── assets/               # App images and icons (e.g., favicon)
├── components/           # Reusable components (Header, Counseling, MoodTracker, etc.)
├── App.vue               # Main app layout and structure
├── main.js               # Vue app entry point
└── index.html            # Root HTML file
```

---

## **Design Concept**

The design is centered around **warm neutral tones** (light beige, cream white, and soft red highlights). The purpose is to make users feel calm, safe, and emotionally supported — similar to a digital safe space.

---

## **How to Run**

1. Clone the repository

   ```bash
   git clone https://github.com/yourusername/wellness-tracker.git
   ```
2. Navigate to the folder

   ```bash
   cd wellness-tracker
   ```
3. Install dependencies

   ```bash
   npm install
   ```
4. Run the development server

   ```bash
   npm run dev
   ```
5. Open your browser at

   ```
   http://localhost:5173
   ```
