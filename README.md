# Sourcing Optimization Model

This model is designed to optimize the sourcing process by selecting the best suppliers based on cost, location, and predefined constraints, then allocating units to factories accordingly.

## Overview

The model processes data through several stages:

1. **Preprocessing** to apply hard constraints and prepare the data.
2. **Winning Supplier Selection** to choose the best supplier for each item based on cost and local-for-local preference.
3. **Factory Allocation** to distribute units to factories based on the selected suppliers and target volumes.

## Requirements

- Python 3.x
- Pandas
- NumPy

## Data Preparation

The model expects the following datasets:

- `merged_df`: Contains item and vendor information, including costs and countries.
- `factory_demand_df`: Lists each factory's demand and location.
- `target_volume_df`: Specifies target volumes and acceptable ranges for each vendor.

Optional constraints (such as unacceptable item-factory pairs) can be defined and applied during preprocessing.

## Functions

### Preprocessing Function

Removes unacceptable item-factory pairs from `merged_df` based on the provided constraints.

```python
def preprocess_data(merged_df, constraints=None):
    # Function implementation
```

### Winning Supplier Selection Function

Selects the best supplier for each item, prioritizing local vendors and lower costs.

```python
def select_winning_supplier(merged_df, factory_demand_df):
    # Function implementation
```

### Factory Allocation Function

Allocates units to factories based on the selected suppliers, adhering to target volumes.

```python
def allocate_to_factories(selected_suppliers, target_volume_df, factory_demand_df):
    # Function implementation
```

## Execution Workflow

1. Load and prepare the data.
2. Run the preprocessing function to apply constraints.
3. Execute the supplier selection function to determine the best suppliers.
4. Allocate units to factories using the allocation function.
5. Explore and analyze the results to assess the optimization outcomes.

## Analysis of Results

After running the allocation process, perform an analysis to understand:

- How units are distributed among factories.
- Which vendors are selected as suppliers and their cost implications.
- Adherence to local-for-local preferences and other business rules.

---