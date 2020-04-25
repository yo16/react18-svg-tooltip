# React Path Tooltop
A simple yet beautiful react tooltip component for SVG-Paths.
The component detects the SVG and Path locations/sizes. The component also detects the display text width of the tooltip. Based on that information a calculation is done so that the rendering of the tooltip will be optimized and correctly oriented.  

**Note:** When generating SVG with multiple paths, make sure to add the tooltips at the bottom of the SVG element, after all the paths are already displays. 

## Install 

In order to install, run the following command:
~~~
$ npm install react-path-tooltip --save
~~~


## Usage 
A very simple `App.tsx' example: 

```tsx
import React from "react"
import "./App.css"
import { PathTooltip } from "ReactPathTooltip" // import the package

function App() {

  const svgRef = React.createRef<SVGSVGElement>()
  const pathRef = React.createRef<SVGCircleElement>()

  return (
    < div className="App" >
      < div className="Main">
        <svg width="400" height="400" ref={svgRef}>
          <circle cx={50} cy={50} r={50} fill="red" ref={pathRef} />
          <PathTooltip svgRef={svgRef} pathRef={pathRef} tip="Hello World!" />
        </svg>
      </div>
    </div>
  )
}

export default App
```

## Customization
The following parameters are passed to the tooltip component:

| Prop       | Type   | Description |
| ---------- | ------ | ----------- |
| tip        | string | Mandatory. The text to be displayed inside the tooltip |
| svgRef     | React.RefObject<SVGElement> | Mandatory. A React reference object to the SVG element |
| pathRef    | React.RefObject<SVGSVGElement> | Mandatory. A React reference object to the path element bounded to the tooltip |
| bgColor    | string | Optional. Background color. Default: "black" |
| textColor  | string | Optional. Text color. Default: "white" |
| fontFamily | string | Optional. The font family. Default: san-serif |
| fontSize   | number | Optional. The font size. Default 12| 

**Notes:**

* `tip` must include simple text. No new lines, or html decoration. 
* `pathRef` must be a valid reference to a path element. There are a number of such types such as SVGRectElement, SVGCircleElement, etc. 
* The SVG rendering should be such that all the tooltip elelments are at the bottom of the SVG definition, and specifically, after the path elements. Otherwise, there is a risk of paths overlaping tooltips. 


## License
MIT

