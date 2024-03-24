Sure, I can create a tutorial that explains the purpose of the functions, why they were created, and how to use them. This tutorial can certainly be structured to serve as a README file for your project.

---

# Sourcing Optimization Model Tutorial

## Overview

This tutorial covers the sourcing optimization model designed to allocate resources effectively across various vendors and factories, taking into account cost, location, and specific business constraints. The model aims to optimize the distribution of items to meet factory demands while adhering to predefined target allocations and cost efficiencies.

## Functions Description

### 1. `preprocess_data(merged_df, factory_demand_df, constraints=None)`

**Purpose**: Prepares the data for the allocation process by applying predefined constraints and ensuring that the data meets the necessary criteria for the allocation to proceed.

- **Parameters**:
  - `merged_df`: The DataFrame resulting from merging items and bids, containing details like item IDs, vendor IDs, costs, and associated factories.
  - `factory_demand_df`: DataFrame detailing the demand for each factory.
  - `constraints`: A dictionary containing various constraints such as unacceptable item-factory pairings.

**Why**: This function is essential for ensuring that the allocation logic operates on data that respect business rules and constraints, such as excluding certain vendor-factory pairings.

### 2. `allocate_units_local_for_local(merged_df, target_volume_df, factory_demand_df, constraints=None)`

**Purpose**: Allocates units to factories based on vendor bids, prioritizing local vendors (where the vendor and factory are in the same country) and cost-effectiveness, while respecting target allocation percentages.

- **Parameters**:
  - `merged_df`: DataFrame with merged items and bids data, including vendor and factory information.
  - `target_volume_df`: DataFrame that specifies the target allocation percentages for each vendor.
  - `factory_demand_df`: DataFrame detailing the demand for each factory.
  - `constraints`: Optional dictionary of constraints to be applied during the allocation.

**Why**: This function is the core of the model, where the actual allocation logic is implemented. It ensures that the distribution of items to factories is optimized according to cost, locality, and specified allocation targets.

## How to Use

1. **Prepare Your Data**:
   - Load your data into DataFrames. Typically, this will involve loading data from Excel files or databases into pandas DataFrames named `merged_df`, `target_volume_df`, and `factory_demand_df`.

2. **Define Constraints** (if any):
   - Prepare a dictionary named `constraints` that includes any specific rules or pairs that should be considered during the allocation process.

3. **Run the Allocation**:
   - Call the `allocate_units_local_for_local` function with your DataFrames and constraints. This function will internally call `preprocess_data` to apply any necessary pre-processing steps.

   ```python
   allocation_results = allocate_units_local_for_local(merged_df, target_volume_df, factory_demand_df, constraints)
   ```

4. **Analyze the Results**:
   - Once you have the allocation results, you can analyze them to ensure they meet your business requirements, such as checking whether all factory demands are satisfied and whether the allocations respect the target volumes and constraints.

## Example

Assuming you have loaded your data into the appropriate DataFrames, here’s how you might call the allocation function:

```python
# Define any specific constraints
constraints = {
    'unacceptable_pairs': [(1, 'F2'), (2, 'F3')]  # Example constraints
}

# Run the allocation process
allocation_results = allocate_units_local_for_local(merged_df, target_volume_df, factory_demand_df, constraints)

# Print or analyze the allocation results
print(allocation_results)
```

## Conclusion

This sourcing optimization model provides a structured approach to resource allocation, ensuring that business rules and efficiency criteria are met. By adjusting the model to include pre-processing steps and handling specific constraints, it offers flexibility to adapt to various operational requirements and constraints.
