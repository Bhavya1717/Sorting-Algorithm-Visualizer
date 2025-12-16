# 6-Algorithm Sorting Visualizer

An interactive web application built with HTML, Tailwind CSS, and pure JavaScript to simultaneously visualize and compare the performance and operational patterns of six fundamental sorting algorithms.

## 🌟 Features

* **Concurrent Visualization:** Watch Bubble Sort, Insertion Sort, Quick Sort, Selection Sort, Heap Sort, and Merge Sort run side-by-side on the same initial randomized array.
* **Clear Animations:** Uses distinct color coding to highlight key operations:
    * **Yellow:** Comparison
    * **Red:** Swap Operation
    * **Violet:** Pivot/Key Element
    * **Green:** Permanently Sorted Element
* **Speed Control:** Adjust the visualization speed from Slow (400ms delay per step) to Turbo (10ms delay per step).
* **Code Reference:** Each visualizer includes the corresponding pseudocode for the algorithm being executed.
* **Pure JavaScript:** No heavy frameworks required, making the source code easy to follow for educational purposes.

## 🚀 Getting Started

### Prerequisites

You only need a modern web browser to run this application.

### Installation & Execution

1.  **Save the file:** Save the entire code block provided as an HTML file (e.g., `index.html`).
2.  **Open in Browser:** Double-click the saved `index.html` file to open it in your web browser (Chrome, Firefox, Edge, etc.).
3.  **Start:** Click the **"Start Visualization"** button to begin the sorting process.

## 🛠️ Implementation Details

The core of the application relies on an **action-recording pattern** to decouple the sorting logic from the animation:

1.  **Action Generation:** Each sorting function (`getBubbleSortActions`, `getQuickSortActions`, etc.) takes the initial array and *simulates* the sorting, recording every significant step (compare, swap, pivot placement) into an array of objects.
2.  **Visualization Execution:** The `startAllVisualizations` function runs all recorded action arrays in parallel.
3.  **DOM Manipulation:** The `Visualizer` class reads the next action, applies the corresponding color and position changes using CSS transitions (`style.order` and `className`), and uses `setTimeout`/`delay` to wait for the configured `ANIMATION_SPEED_MS` before processing the next action.

### Key Data Attributes for Tracking

To ensure the visual bars correspond correctly to the logical array indices even after multiple swaps, the following data attributes are used:

* `data-index`: The current logical index (position in the array) for the bar. This is swapped during a visual swap.
* `data-value`: The original value of the bar, which remains constant.

## ⚙️ Configuration

You can easily adjust the visualization parameters within the `<script>` tag:

| Variable | Description | Default Value |
| :--- | :--- | :--- |
| `ARRAY_SIZE` | The number of bars to display. | `15` |
| `MAX_VALUE` | The maximum height (percentage) of any bar. | `90` |
| `ANIMATION_SPEED_MS` | Initial delay between steps in milliseconds. | `150` |
