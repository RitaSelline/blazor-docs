---
layout: post
title: Accessibility in Blazor Charts Component | Syncfusion
description: Checkout and learn here all about Accessibility using Keyboard navigation in Syncfusion Blazor Charts component and more.
platform: Blazor
control: Chart
documentation: ug
---

# Accessibility in Blazor Chart Component

Accessibility is achieved in the Chart component through WAI-ARIA standard and keyboard navigation. The chart features can be effectively accessed through assistive technologies such as screen readers.

## WAI-ARIA

WAI-ARIA(Accessibility Initiative - Accessible Rich Internet Applications) defines a way to increase the accessibility of web pages, dynamic content, and user interface components developed with AJAX, HTML, Javascript, and related technologies. ARIA provides additional semantics to describe the role, state, and functionality of web components.

The following ARIA attributes are used in the chart:

Element |Default description
-----|-----
Datalabel |Reads the Point y value.
Legend |Click to show or hide the series.
Axis Title |Reads the axis title.
Chart Title |Reads the chart title.
Series Points |Reads the Point x: Point y value.

## Keyboard navigation

Chart functionalities can be interactive with keyboard shortcuts.

The following keyboard shortcuts are supported by Chart.

Interaction Keys |Description
-----|-----
<kbd>Tab</kbd> |Moves the focus to the next element in the chart.
<kbd>Shift + Tab</kbd> |Moves the focus to the previous element in the chart.
<kbd>DownArrow</kbd> |Moves the focus to the data point right side from the selected point.
<kbd>UpArrow</kbd> |Moves the focus to the data point right side from the selected point.
<kbd>Left Arrow</kbd> |Moves the focus to the next series in our Chart component.
<kbd>Right Arrow</kbd> |Moves the focus to the previous series in our Chart component.
<kbd>ESC</kbd> |Cancel the tooltip for the data point.
<kbd>Enter/Space</kbd> |Selects the data point in the series
<kbd>Down/Left Arrow</kbd> |Moves the focus to the legend left side from the selected legend.
<kbd>Up/Right Arrow</kbd> | Moves the focus to the legend right side from the selected legend.
<kbd>Enter/Space</kbd> |Toggles the visibility of the corresponding series.
<kbd>Ctrl + +</kbd> |Zoom in the chart.
<kbd>Ctrl + -</kbd> |Zoom out the chart.
<kbd>Down/Up Arrow</kbd> |Pans the chart vertically.
<kbd>Left/Right Arrow</kbd> |Pans the chart horizontally.
<kbd>R</kbd> |Reset the zoomed chart.
<kbd>Ctrl + P</kbd> |Prints the Chart.