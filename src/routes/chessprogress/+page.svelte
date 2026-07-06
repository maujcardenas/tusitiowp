<script>
    // Constants defining grid dimensions
    const WEEKS = 24;

    // Task definitions and distributions per row
    const TASK_TYPES = [
        { id: "CRP", count: 2, color: "#ef476f" },
        { id: "LTP", count: 3, color: "#f78c6b" },
        { id: "UEG", count: 4, color: "#ffd166" },
        { id: "SPA", count: 4, color: "#06d6a0" },
        { id: "SCB", count: 2, color: "#118ab2" },
    ];

    // Programmatically generate column schema
    const columns = [];
    TASK_TYPES.forEach((task) => {
        for (let i = 0; i < task.count; i++) {
            columns.push({
                type: task.id,
                color: task.color,
                // The last cell of a task type sequence forms a boundary
                isBoundary: i === task.count - 1,
            });
        }
    });

    // Initialize the 24x15 grid state (false = empty/white)
    let grid = Array(WEEKS)
        .fill()
        .map(() => Array(columns.length).fill(false));

    // State mutation handler
    function toggleCell(row, col) {
        grid[row][col] = !grid[row][col];
        grid = grid; // Reassign to trigger Svelte reactivity
    }

    // Reactive analytics computation
    $: stats = TASK_TYPES.map((task) => {
        // Identify which column indices belong to the current task type
        const typeColIndices = columns
            .map((c, index) => (c.type === task.id ? index : -1))
            .filter((index) => index !== -1);

        let completed = 0;
        const total = task.count * WEEKS;

        // Count completions across all weeks for these specific columns
        grid.forEach((row) => {
            typeColIndices.forEach((colIndex) => {
                if (row[colIndex]) completed++;
            });
        });

        return {
            id: task.id,
            completed,
            total,
            percentage: total > 0 ? ((completed / total) * 100).toFixed(2) : 0,
        };
    });
</script>

<div class="tracker">
    <div class="stats-container">
        {#each stats as stat}
            <div class="stat-card">
                <div class="stat-title">{stat.id}</div>
                <div class="stat-data">{stat.completed} / {stat.total}</div>
                <div class="stat-data">{stat.percentage}%</div>
            </div>
        {/each}
    </div>

    <div class="grid-container">
        <div class="grid">
            {#each grid as row, rIndex}
                {#each row as isDone, cIndex}
                    <div
                        class="cell {columns[cIndex].isBoundary
                            ? 'boundary'
                            : ''}"
                        style="background-color: {isDone
                            ? columns[cIndex].color
                            : '#ffffff'};"
                        on:click={() => toggleCell(rIndex, cIndex)}
                        role="switch"
                        aria-checked={isDone}
                        title="Week {rIndex + 1} - {columns[cIndex].type}"
                    ></div>
                {/each}
            {/each}
        </div>
    </div>
</div>

<style>
    .tracker {
        font-family:
            system-ui,
            -apple-system,
            sans-serif;
        display: flex;
        flex-direction: column;
        gap: 24px;
        padding: 20px;
    }

    /* Grid Layout */
    .grid-container {
        overflow-x: auto;
    }

    .grid {
        display: grid;
        /* 15 columns of equal width */
        grid-template-columns: repeat(15, 32px);
        width: fit-content;

        /* Outer bounds of the entire grid */
        border-top: 2px solid #1a1a1a;
        border-left: 2px solid #1a1a1a;
        border-bottom: 2px solid #1a1a1a;
        background-color: #ffffff;
    }

    .cell {
        height: 32px;
        width: 32px;
        box-sizing: border-box;
        cursor: pointer;
        transition: background-color 0.15s ease-in-out;

        /* Default borders: 1px dotted */
        border-right: 1px dotted #a0a0a0;
        border-bottom: 1px dotted #a0a0a0;
    }

    /* Structural division between task types */
    .cell.boundary {
        border-right: 2px solid #1a1a1a;
    }

    /* Analytics Styling */
    .stats-container {
        display: flex;
        gap: 16px;
        flex-wrap: wrap;
    }

    .stat-card {
        border: 1px solid #e2e8f0;
        border-radius: 6px;
        padding: 12px 20px;
        background: #f8fafc;
        min-width: 100px;
        text-align: center;
    }

    .stat-title {
        font-weight: 700;
        color: #334155;
        margin-bottom: 8px;
        font-size: 1.1rem;
    }

    .stat-data {
        font-size: 0.95rem;
        color: #475569;
        line-height: 1.4;
    }
</style>
