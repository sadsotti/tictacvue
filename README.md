# 🕹️ tictacvue

A fun, responsive, and intuitive web-based **Tic Tac Toe game**, built with **Vue.js** and optimized for a seamless experience on any device. Created as the **first project** of two for the Vue.js course in the "Full Stack Development and AI" Master by start2impact.

---

## 🔗 Try It Live!

Click the link below:

👉 [**tictacvue**](https://tictacvue-fixed.netlify.app/) 👈

---

## 🎯 Project Goal

The main goal of this project was to develop a **single-page application (SPA)** implementing the classic Tic Tac Toe game.

The core development focused on leveraging **Vue** reactive state management, game logic implementation, and dynamic UI updates. Emphasis was placed on creating a **responsive and engaging user interface**, ensuring clear game status feedback (current player, winner/draw), and providing a smooth reset functionality.

Attention was also paid to creating a **responsive layout** and allowing users to toggle between dark and light themes for a personalized experience.

---

## ✨ Implemented Features

* **Classic Tic Tac Toe Logic:** Fully functional game rules for X and O players.
* **Dynamic Turn Display:** Clearly indicates the current player.
* **Win/Draw Detection:** Accurately identifies game outcomes.
* **Winning Line Highlight:** Visually emphasizes the cells that led to a win.
* **Game Reset Functionality:** Allows users to easily start a new game.
* **Theme Toggle (Dark/Light Mode):** Switches between two distinct visual themes.
* **Responsive Design:** Fully optimized for desktop, tablet, and mobile viewing.
* **Modern Styling:** Clean interface using CSS variables, gradients, and subtle animations.
* **Vue Composition API:** Efficient state management using `ref` for reactive data.
* **DynaPuff Font:** Utilizes a playful and modern font for headings and game elements.

---

## 🛠️ Technologies Used

* **Vue.js** with **Vue Composition API**
* **Vite** as the fast build tool and development server.
* **CSS3 & Variables** for responsive styling and theme management
* **Google Fonts:** `DynaPuff` for a unique and playful aesthetic

---

## 🚀 How to Run the Project Locally

Follow these steps to clone the repository and run the project:

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/sadsotti/tictacvue.git
    ```

2.  **Navigate to the project directory:**

    ```bash
    cd tictacvue
    ```

3.  **Install dependencies:**

    Make sure you have [Node.js and npm](https://nodejs.org/en/download/) installed. Then run:

    ```bash
    npm install
    ```

4.  **Start the development server (using Vite):**

    This command leverages **Vite** to start a local development server, compile your code instantly, and automatically enable **Hot Module Replacement (HMR)** for live updates in the browser.

    ```bash
    npm run dev
    ```

    You will see the local access URL (e.g., `http://localhost:5173/`) in the console.

5.  **(Optional) Create the production build (using Vite):**

    To generate optimized files for production (bundle, compiled CSS, assets), run:

    ```bash
    npm run build
    ```

    Compiled files will be saved in the `dist/` directory, ready for deployment.

---

## 📂 Project Structure

The project follows a standard Vite/Vue structure for better maintainability:

* `dist/`: Output folder for the optimized production build.
* `public/`: Static assets (favicon).
* `src/`: Vue source code.
    * `components/`: Reusable UI components (e.g., `Game.vue` for the main game logic/layout).
    * `assets/`: Global CSS (`style.css`), images, and other static assets.
* `index.html`: The entry point for Vite.
* `vite.config.js`: **Vite** configuration file (defines plugins, build options, etc.).
* `package.json`: Defines the project dependencies and scripts.
* `README.md`: This project description file.

---

### ✨ Implemented Solution (Component Hierarchy)

The original monolithic component (`Game.vue`) was refactored into a clear component hierarchy to ensure **Separation of Concerns**:

1.  **`Game.vue` (Parent):** Holds the **central reactive state** and all **business logic** (`makeMove`, `checkWin`, `resetGame`).
2.  **`Board.vue` (Child):** Responsible for the **structural rendering** of the 3x3 grid. It receives data (like the board state) via **Props** and forwards user interaction events.
3.  **`Cell.vue` (Grandchild):** Handles the **single cell's presentation** and direct user interaction. It receives its specific details via **Props** and notifies the `Board` component of a click using **Custom Events** (`$emit`).

This reorganization results in code that is significantly more **modular, reusable, and maintainable**.

---

## 🔗 Useful Links

* [start2impact](https://www.start2impact.it/)
* [My LinkedIn](https://linkedin.com/in/lorenzo-sottile)