# CaliVibeMap 🗺️

A collaborative interactive map of Cali, Colombia, built with **Leaflet.js** and **Vanilla JS**.

This project is designed as a hands-on exercise for teams to practice **Collaborative Development**, **Git Workflows**, and **Continuous Integration** concepts.

---

## 🚀 Collaborative Workflow Strategy

Since we are working as a team, we need a strategy to manage our code changes efficiently without stepping on each other's toes. We will explore two popular methodologies: **Trunk Based Development** and **Gitflow**.

### 1. Trunk Based Development (Recommended)

In Trunk Based Development, all developers push their changes to a single shared branch (usually `main` or `master`) very frequently.

*   **Philosophy**: "Integrate early, integrate often."
*   **Benefits**: Reduces "merge hell," faster feedback loop, and encourages smaller, manageable code updates.

#### Example Scenario in CaliVibeMap:
Imagine **Valentina** wants to add her data to the map.

1.  **Valentina** pulls the latest `main` branch.
2.  She creates a new file `data/students/valentina.json` and adds her entry to `data/index.json`.
3.  She tests it locally.
4.  She commits and pushes **directly** to `main` (or via a very short-lived Pull Request).
    ```bash
    git checkout main
    git pull origin main
    # ... makes changes ...
    git add .
    git commit -m "feat: add valentina data"
    git push origin main
    ```
5.  **Juan** pulls `main` 5 minutes later and already has Valentina's changes. He then adds his own data.

### 2. Gitflow (Alternative Approach)

Gitflow is a stricter, more structured workflow that uses multiple branches for different purposes (`develop`, `feature/*`, `release/*`, `main`).

*   **Philosophy**: "Ordered and structured development releases."
*   **Structure**:
    *   `main`: Production-ready code.
    *   `develop`: Integration branch for features.
    *   `feature/new-popup`: Individual feature branches.

#### Example Scenario:
1.  **Valentina** creates a branch `feature/add-valentina` from `develop`.
2.  She works on her branch for 2 days.
3.  She merges into `develop`.
4.  Once `develop` has everyone's changes and is stable, it is merged into `main` for a "Release".

*Note: For this specific project, since we separated the data into individual JSON files to minimize conflicts, **Trunk Based Development** is highly efficient.*

---

## 🔄 Continuous Integration (CI)

Both workflows rely heavily on **Continuous Integration (CI)**.

### What is CI?
Continuous Integration is the practice of automating the integration of code changes from multiple contributors into a single software project.

*   **How it works**: Every time you push code (to `main` in Trunk Based, or to a PR in Gitflow), an automated system (like GitHub Actions) wakes up and runs a script.
*   **The Script**: This script usually runs **Tests**, checks for **Syntax Errors**, and verifies that the build doesn't break.
*   **The Goal**: To catch bugs **immediately**. If you break the map, the CI bot will tell you right away, preventing broken code from reaching your teammates.

For *CaliVibeMap*, a simple CI pipeline could check if the `students/*.json` files are valid JSON before allowing a merge.

---

## 🛠️ Project Setup

1.  **Clone the repo**:
    ```bash
    git clone https://github.com/your-username/CaliVibeMap.git
    ```
2.  **Open in VS Code**:
    ```bash
    code CaliVibeMap
    ```
3.  **Run Locally**:
    *   Open `index.html` with **Live Server** extension (Required for `fetch` API to work properly).

## 📂 Project Structure

*   `css/`: Stylesheets.
*   `js/`: Map logic and interaction.
*   `data/`:
    *   `index.json`: Master list of student files.
    *   `students/*.json`: Individual student data files.
