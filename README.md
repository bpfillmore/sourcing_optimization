# Sourcing Optimization Model

This model is designed to optimize the sourcing process by selecting the best suppliers based on cost, location, and predefined constraints, then allocating units to factories accordingly.

## Background

The use case here is developing a product that simplifies the project of optimizing resource allocation for a vendor. This particular vendor runs pricing for input raw materials twice per year, negotiating on raw materials in several distinct categories across hundreds of external suppliers. This process is typically a self-contained RFQ - with external suppliers submitting their prices for raw materials, allowing the primary vendor to compare pricing options. 

Once this information is collected and aggregated, the vendor has to go through the process of deciding what volume to allocate to different factories, and from which external suppliers. This is a balancing act, primarily between cost of materials from suppliers, and regionality (local-for-local). It's quite common for suppliers with less competitive prices to still be awarded business just because of their proximity to preferred factories, allowing a local-for-local pairing.   The function takes into consideration target volume (internal vendor figures indicating preferred suppliers), factory demand (volume the factories are capable of producing) and prices. 

Using this, and considering imputed hard constraints, the model is able to generate a best-case, optimized allocation of items between suppliers and factories.

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

## Detailed Function Logic

Preprocess Data: Filters out any data not meeting the specified constraints.
Select Winning Supplier: Determines the most cost-effective supplier for each item, preferring local suppliers to align with the local-for-local strategy.
Allocate to Factories: Distributes the items to factories based on the selected suppliers and the factories' demand, respecting the target volume constraints.

## Data Structure

Vendors: Contains vendor IDs and their corresponding countries.
Items: Lists items with their IDs and associated types.
Factories: Includes factory IDs, countries, and demand volumes.
Constraints: Specifies pairs of items and factories that are unacceptable for allocation.

## Notes

Ensure all data is correctly loaded and preprocessed before running the allocation functions.
The model can be adjusted to accommodate additional constraints and preferences as needed.
---
