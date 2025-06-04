# Frontend Dashboard

This module is the user interface for the AI News Dashboard.
It will be responsible for:
- Displaying news articles.
- Allowing users to filter and search for news.
- Potentially visualizing news trends.

## Technology Stack

- React (JavaScript library for building UIs)
- Tailwind CSS (utility-first CSS framework)
- React Router (for client-side routing)
- Axios or Fetch API (for making API calls to the backend)
- State Management: Context API + `useReducer` (for simple to moderate state) or Redux/Zustand (for complex state, if needed later). Start with Context API.

## Module Construction

- **Core Structure:**
    - `public/`: Static assets (index.html, favicons, etc.).
    - `src/`:
        - `App.js`: Main application component, routing setup.
        - `index.js`: Entry point, renders App.
        - `components/`: Reusable UI components (e.g., `ArticleCard`, `SearchBar`, `FilterDropdown`, `Navbar`, `Layout`).
        - `pages/`: Top-level components representing different views/pages (e.g., `HomePage`, `ArticleDetailPage`, `SettingsPage`).
        - `services/`: Functions for interacting with the backend API (e.g., `articleService.js`).
        - `hooks/`: Custom React hooks for reusable logic (e.g., `useFetchArticles`).
        - `contexts/` or `store/`: For state management (e.g., `ArticleContext`, `FilterContext`).
        - `utils/`: Helper functions (e.g., date formatting, text truncation).
- **Key Features & Components:**
    - **News Feed (`HomePage`):** Displays a list of articles (`ArticleCard` components). Supports pagination or infinite scrolling.
    - **Article Detail (`ArticleDetailPage`):** Shows the full content or summary of a selected article.
    - **Search Bar (`components/SearchBar`):** Allows users to search for articles by keywords.
    - **Filtering (`components/FilterDropdown`):** Enables filtering by source, date range, etc.
    - **Navbar/Sidebar:** For navigation and potentially settings.
- **State Management:**
    - Start with React Context API and `useReducer` for managing global state like filters, search queries, and potentially fetched articles if not too complex.
    - Evaluate need for a more robust solution like Redux or Zustand if state becomes difficult to manage.
- **API Interaction:**
    - Use `axios` (or `fetch`) in `services/` to make asynchronous requests to the backend API.
    - Handle loading states, error states, and display appropriate UI feedback.
- **Styling with Tailwind CSS:**
    - Apply utility classes directly in JSX for styling components.
    - Create custom Tailwind components or plugins if necessary for reusable styles.
- **Routing:**
    - Use React Router to define routes for different pages (e.g., `/`, `/article/:id`).

## Testing Strategy

- **Unit Tests (Jest & React Testing Library):**
    - Test individual React components in isolation (props, rendering, basic interactions).
    - Test utility functions and custom hooks.
    - Mock API calls from services.
- **Component Integration Tests (Jest & React Testing Library):**
    - Test interactions between multiple components, simulating user flows within a page (e.g., typing in search, applying filters, viewing results).
    - Mock API responses to control test data.
- **Optional: E2E Tests (Cypress or Playwright):**
    - Consider for testing critical end-to-end user flows across the entire application (frontend + backend interaction). This would be a later addition if deemed necessary.
