FlowMap
=======

Javascript code for the spiral flow map

To use this code, please follow the steps below:

Step 1. Create the spiral tree object and specify the SVG panel
For example:

this.myFlow = new SpiralTree(this.svgMap);

Step 2. You need to set up a projection function 
which can convert the latitutde and longitude to the screen space pixel coordinate.
For example:

//using the google map api

parameterProjection = function (LngLatArray) {
        var tempP = new google.maps.LatLng(LngLatArray[1], LngLatArray[0]);
        tempP = projection.fromLatLngToContainerPixel(tempP);
        return [tempP.x, tempP.y];
    }
this.myFlow.setProjection(parameterProjection);

Step 3. Specify the options for the spiral tree: node color, line width etc.
For example:

this.myFlow.setColor('spiralSegment', lineColor);
this.myFlow.setColor('center', centerColor);
this.myFlow.setColor('terminal', centerColor);
this.myFlow.setWidth(lineWidth);
this.myFlow.setAlpha(spiralAngle);
this.myFlow.setThreshold(map.getZoom());
this.myFlow.setInfoFields(["lat", "lng"]);

Step 4. Call the preprocess function for the data which needs two parameters: 
1. an array of the spiral terminals (ie, the nodes) 
2. the origin of the flow map

For example:

this.myFlow.preprocess(fitInTerminals, fitInCenter);

Step 5. Finally, call the draw function
For example:

this.myFlow.drawTree();
