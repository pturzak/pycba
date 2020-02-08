# pycba
A Python module for cost-benefit analysis of infrastructure projects


This module provides a consistent way to evaluate economic efficiency
of a road project with well-defined inputs and parameters.
It offers a significantly wider options for analysis of alternatives
than Excel.


## Dependencies
Numpy, Pandas


## Inputs
Required project inputs:
* capital expenditures (CAPEX) with pre-defined items
* parameters of old and new road sections (length, width, number of lanes etc)
* intensities in variant 0 and 1 (without and with the project)
* velocities in variant 0 and 1

Options to load project inputs:
* separately as Pandas dataframes
* from an Excel file with sheet names:
  `road_params, capex, intensities_0, intensities_1, velocities_0, velocities_1`


## Outputs
* Dataframe of costs and benefits
* Economic indicators:
  - net present value (ENPV)
  - internal rate of return (ERR)
  - benefit to cost ratio (BCR)


## Example

```python
from pycba import RoadCBA
from pycba.sample_projects import load_sample_bypass

byp = load_sample_bypass()

rcba = RoadCBA(2020, 2020, "svk")
rcba.load_parameters(source="default")
rcba.economic_analysis()
```

Output (values might differ):
```
ENPV: -41.24M
ERR : -7.07 %
BCR : 0.09
```



