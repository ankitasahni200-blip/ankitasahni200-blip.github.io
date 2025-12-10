---
layout: page
title: IS 445 – Homework 5
permalink: /hw5/
---

## Homework 5 – Building Inventory Visualizations

### Links

## Homework 5 – Building Inventory Visualizations

### Links

- **The Data:** [building_inventory.csv](https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv)  
- **The Analysis (Jupyter Notebook):** [hw5_building_inventory.ipynb](https://github.com/ankitasahni200-blip/ankitasahni200-blip.github.io/blob/main/python_notebooks/hw5_building_inventory.ipynb)

---

## Plot 1 – Top 15 Illinois Counties by Number of State Buildings

For my first visualization, I wanted a clear, honest picture of which parts of Illinois dominate the state building inventory. Each bar represents one county, and its length shows how many state-owned 
buildings from that county appear in the dataset, so the chart directly answers the question, “Which counties contribute the most state buildings here?” I chose a horizontal bar chart so the county names 
sit comfortably on the y-axis and viewers can compare bar lengths at a glance. The x-axis encodes the count of buildings, the y-axis encodes county names, and I use a categorical color scheme on County so
each bar is visually distinct. I hide the legend on purpose, because the labels already tell you who is who and an extra legend would just repeat the same information. In my notebook, I used value_counts() 
on the County column, selected the top 15 counties with nlargest(15), and then filtered the dataframe to only those rows. This transformation keeps the story focused on the counties with the highest concentration
of state buildings and avoids a long tail of tiny bars that would clutter the view and distract from the main pattern.

---

## Plot 2 – Year Built vs. Square Footage with County Breakdown

For my second visualization, I wanted to see how building size and construction year relate to each other across Illinois. In the top panel, each point represents a single building, with Year Constructed on the x-axis
and Square Footage on the y-axis, so I can quickly scan how building sizes are distributed over time. I color the points by County using a categorical color scheme to show which counties contribute buildings in different
regions of the plot, while keeping the axes focused on the main quantitative story (year and size). In the notebook, I first cleaned the data by dropping rows where Year Constructed, Square Footage, or County were missing.
I then filtered to buildings constructed in 1950 or later and limited Square Footage to 200,000 or less. These transformations remove incomplete records and extreme outliers that would stretch the axis and compress most 
of the other points at the bottom of the chart. For the bottom panel, I aggregate the brushed subset of buildings by County, compute a count for each one, and then use a window transform to keep only the top 15 counties. 
That summary is shown as a horizontal bar chart with the number of buildings in the current selection on the x-axis and County on the y-axis, which makes it easy to compare which counties dominate within whatever slice
of the scatterplot I am focusing on.

---

## Interactivity Discussion

Most of the interactivity is concentrated in the second visualization. I use an interval brush on the scatterplot so I can drag over any range of years and square footages and instantly see a linked breakdown of the top 15 
counties for just that selection in the bar chart below. I also include a hover interaction that enlarges and darkens the point under the cursor and shows a detailed tooltip with building name, agency, city, county, year built,
and square footage, which helps connect individual buildings back to the broader pattern. Finally, by clicking on a bar in the lower chart it selects a specific county and highlights its buildings in the scatterplot. Together, the 
brush, hover, and click interactions let me move back and forth between the big picture and county-level detailed in a way that a static plot could not.

