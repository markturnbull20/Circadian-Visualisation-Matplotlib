# 📈 Circadian Time-Series Data Visualisation in Python


![Python](https://img.shields.io/badge/Python-3.11-blue)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.11-orange)
![Jupyter](https://img.shields.io/badge/Jupyter-orange)

## Overview

As a circadian scientist interested in human behaviour, I work with time-series data that capture changes across daily cycles, often over periods of 12–24 hours. These datasets contain complex patterns that are closely linked to the timing of biological rhythms. For example, daily rhythms in alertness and cognitive performance follow similar patterns to core body temperature ([Dijk, et al., 1992](https://doi.org/10.1111/j.1365-2869.1992.tb00021.x)).

It is important to visualise data in a way that reflects the influence of the body's internal clock rather than relying only on standard clock time. In this repository, I show figures that were created during my PhD to visualise subjective sleepiness, cognitive performance, and neurophysiological data relative to DLMO (dim light melatonin onset). 

## Project

In this example dataset, participants remain awake under controlled laboratory conditions for 24-hours. Subjective sleepiness ratings are recorded every two hours, along with saliva samples to measure melatonin levels. The data are aligned relative to DLMO. 

This visualisation illustrates how sleepiness and alertness change across the sleep-wake cycle relative to a biological marker of circadian timing. The plot uses dual x and y axes to display time relative to DLMO alongside the corresponding clock time and sleepiness and melatonin levels. 

### Example Data

The example dataset can be found here: [Example Dataset](Example_Data.csv)

** Data Privacy Note** 

The datasets included here are examples created to demonstrate the plots. They do not contain real participant information or represent actual study results.

### Using matplotlib to create a visualisation of the example sleepiness data 

Import the appropriate libraries 

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline
```

Load the dataset as a pandas DataFrame 

```python
df = pd.read_csv("Example_Data.csv)
```

Create a plot that has four axes 

```python
fig, ax1 = plt.subplots()
ax2 = ax1.twinx()
ax3 = ax1.twiny()
```

Plot the data from sleepiness data, with time from DLMO on the x axis and sleepiness scores and melatonin levels on the y axes 

```python
ax2.fill_between(df["Circadian_Time"], df["Melatonin_Value"], color="#56B4E9", alpha=0.2, label="Melatonin Levels")
ax1.plot(df["Circadian_Time"], df["Sleepiness_Z_Score"], color="#E66808", marker="s", markerfacecolor = "#8F9190", 
         markeredgecolor= "#000000", markersize=10, linewidth=3, label="Sleepiness Scores (95% CI)")
```
