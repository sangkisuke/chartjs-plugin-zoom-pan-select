# Chart control functions enhancement for ChartJS
A [chartjs](https://www.chartjs.org/) plugin for **zooming**, **panning** and **selecting** data in a chartjs instance.

See the [example](https://jjppof.github.io/chartjs-plugin-zoom-pan-select/example/index).

### Install:

```
npm install @jjppof/chartjs-plugin-zoom-pan-select
```

### Usage:

```javascript
import ChartJSEnhancements from '@jjppof/chartjs-plugin-zoom-pan-select';

let enhancer = new ChartJSEnhancements(chartjs_object);
enhancer.initialize(mouse_buttons);
/* 
mouse_buttons is an optional object with the mouse button number for each chart action (pan, zoom or select).
More info about the numbers: https://developer.mozilla.org/en-US/docs/Web/API/MouseEvent/buttons#Return_value

Example:
mouse_buttons = {
    zoom: zoom_button_value, //optional
    select: select_button_value, //optional
    pan: pan_button_value //optional
};
*/
```

### Default behavior

 - Click, hold and drag on the plot area to create a select region;
 - Double click on canvas to reset zoom and pan;
 - Use the mouse wheel to zoom;
 - Hold shift and drag the chart to pan.

### Methods:

```javascript
ChartJSEnhancements(chartjs_object, change_point_radius); //change_point_radius: default true, when selecting points, if this is set to true, the radius of the bullets changes
initialize(mouse_buttons, background_color); // mouse_buttons explained on Usage section. background_color if the background color of your chart. Default: white
setAction(action); //sets the mode of the chart if no mouse button is defined. The arg is a string that can be "zoom", "pan" or "select"
setAfterSelectHandler(callable); //callable that receives the selected points array as arg
setAfterUnselectHandler(callable);
setZoomXFactor(factor); //factor is a number
setZoomYFactor(factor);
setBackgroundColor(color); //updates the background color of the chart
setMinMax(); //updates the ticks.max and ticks.min chart properties without updating the chart
unselectPoints(update); //boolean that says if the chart is going to update or not
resetZoom(update, update_options); //boolean that says if the chart is going to update or not. update_options is the update options from chartjs update() function
removeEventListeners(); //removes all event listeners added by this plugin
destroy(); //remove all external references
```

### Limitations

 - For now, this plugin only works for linear x axis type.
