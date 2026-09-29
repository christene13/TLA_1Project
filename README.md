# Enterprise Income Category Ledger (React JS Refactor)

**Course**: CS008.23 - Web Applications Development 1  
**Institution**: University of the Immaculate Conception  
**Assignment**: Finals TLA 1 — Income Category Ledger React Refactor  

---

## 🚀 Live Demo & Repository
- **GitHub Repository**: `https://github.com/christene13/TLA_1Project`
- **Vercel Live Deployment**: `https://vercel.com/christene13/tla-1-project`

---

## 📌 Project Overview
This application is a React JS refactor of the Midterm Vanilla DOM Income Category Ledger. It transitions imperative JavaScript DOM mutations (`document.getElementById`, `.insertAdjacentHTML`, manual element queries) into a declarative component-driven React architecture.

### Enhanced Features Beyond Baseline:
1. **Persistent Storage**: Integrated `localStorage` to retain categories across browser refreshes.
2. **Dynamic Live Search/Filter**: Filter categories in real time without additional re-renders.
3. **Delete Functional Action**: Added item removal logic per table row.
4. **Validation Feedback**: Integrated contextual dynamic error state rather than basic browser `alert()` popups.

---

## 🧠 AI Implementation & Code Defense

### 1. Features Built with AI Assistance
AI tools (Claude / ChatGPT) were utilized during the development of this refactoring project to assist with:
- **Architecture Setup**: Designing a modular component tree (`App`, `CategoryForm`, `CategoryList`).
- **State Migration Strategy**: Converting manual DOM inputs (`txtCatName`, `txtCatDesc`) into controlled React inputs driven by `useState`.
- **CSS Utility Integration**: Keeping Bootstrap markup consistent with the original design specs.

---

### 2. Deep Dive Code Defense & Architectural Breakdown

#### A. Imperative DOM vs. Declarative React State
* **Vanilla Midterm Approach**:
  The vanilla baseline selected elements manually from the RAM tree using `document.getElementById()`, read raw string properties (`.value`), and mutated the DOM tree directly using `incomeTableBody.insertAdjacentHTML("beforeend", newRowHTML)`.
* **React Refactor Approach**:
  We replaced imperative mutations with a single source of truth managed by React state (`categories` array). Whenever `setCategories` is invoked, React automatically re-evaluates the Virtual DOM diff and re-renders only the changed JSX elements.

#### B. Component Decomposition & State Hoisting
* **`App.jsx`**: Acts as the central container holding the primary `categories` array state. Passing `onAddCategory` down to `CategoryForm` and `categories` down to `CategoryList` follows unidirectional data flow.
* **`CategoryForm.jsx`**: Features controlled components. Each `<input>` element binds its `value` to local React state (`name`, `description`). Input changes trigger `onChange` events that update local state instantly.
* **`CategoryList.jsx`**: Maps over the `filteredCategories` array to declaratively render `<tr>` table rows. It uses unique key props (`key={cat.id}`) ensuring efficient Virtual DOM re-reconciliation.

#### C. React Hooks Used
* **`useState`**:
  Used in `CategoryForm` for local form values (`name`, `description`, `error`), in `CategoryList` for `searchTerm`, and in `App` for storing the master category array.
* **`useEffect`**:
  Used in `App` to synchronize state updates with `localStorage` whenever the `categories` dependency array changes (`[categories]`).

---

## 🛠️ Tech Stack
- **Framework**: React 18+ (Vite Build System)
- **Styling**: Bootstrap 5 + Custom CSS
- **Deployment**: Vercel