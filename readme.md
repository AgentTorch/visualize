# Visualizing AgentTorch Simulations

This module provides a Python API that works seamlessly with AgentTorch
to visualize a simulation using the trajectory of its state.

The various supported types of visualizations are described below. To
request/add a new visualization, please open a pull request or an issue.

## GeoPlot

This visualization renders a 3-D plot of the data given the state
trajectory of a simulation, and the path of the property to render.

It generates an HTML file that contains code to render the plot using
Cesium Ion, and the GeoJSON file of data provided to the plot.

An example of its usage is as follows:

```py
from agent_torch.visualize import GeoPlot

# create a simulation
# ...

# create a visualizer
geoplot = GeoPlot(config, cesium_token)

# visualize in the runner-loop
for i in range(0, num_episodes):
  runner.step(num_steps_per_episode)

  geoplot.visualize(
    name = f"consumer-money-spent-{i}",
    state_trajectory = runner.state_trajectory,
    entity_position = "consumers/coordinates",
    entity_property = "consumers/money_spent",
  )
```
