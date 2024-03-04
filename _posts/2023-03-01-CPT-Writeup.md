<table>
  <tr>
    <td>
      Program Purpose and Function
    </td>
    <td>
      The purpose of our code is to be able to create games and though with some flaws, we were able to achieve a basic design for a game, where you could texture walls, run code and change the x and y offset. 
    </td>
  </tr>
  <tr>
    <td>
      Data Abstraction:
      The best example of this is through the function menuOptions which allows for the storage and communication of the code between different functions
    </td>
    <td>
      var menuOptions = {
      "Scene Editor" : {
          "objectData" : [{
              "name": "Test Box", 
              "x": 10, 
              "y":10, 
              "width": 100, 
              "height": 150,
              "selectedLayerIndex": 0
          },
          {
              "name": "Test Box 2", 
              "x": 300, 
              "y":300, 
              "width": 100, 
              "height": 150,
              "selectedLayerIndex": 0
          }], // Holds all objects in Scene, Tile Values, Has Collision, i.e., {"x": 0, "y": 0}
          "screenData" : [], 
          "player" :{
              "speed" : 1,
              "canMove": true
          },
          "selectedObjectIndex" : 0,
      },
      "Editor Controls" : {
          "" : "" // IDK What goes here
      },
      "Tile Editor" : { // Array of color for Colors
          "tileLayers":[
              ["Background Color", []]
          ]
      },
      "Javascript API" : {
          "Code" : [""] // Array for code values, eventually to 2D Array for multiple tabs 
      }
    }
    </td>
  </tr>
  <tr>
    <td>
      A list that is used in the program in defaultObjectParamaters which creates the default texture that the rectangles are created as by the user. This could be changed potentially, through a dictionary such as: 
      var defaultObjectParameters = {
      "x": [“number, 100”] 
      }
      as a way of accessing the parameters, and then could use the Object.keys as a way of accessing which values to get from the dictionary.  
      This uses defaultObjectParamaters as a way of setting the default shape parameters for the Scene Editor to use
      The data of defaultObjectParamaters are the Display name, the one being shown to the player, the type of input, the default value and the property value, these are used to to pull the proper data when creating an object. 
    </td>
    <td>
      var defaultObjectParameters = [
    ["X:", "number", 100, "x"], 
    ["Y:", "number", 100, "y"], 
    ["Width:", "number", 100, "width"], 
    ["Height:", "number",  150, "height"], 
    ["Selected Texture Index:", "select", 0, menuOptions["Tile Editor"]["tileLayers"]]
]
    function createObjectControls(cellIteration){
        var currentAddObjectButton = document.getElementsByClassName("addObjectButton")[cellIteration]
        var addObjectPrompt = document.createElement("div")
        var objectMenu = menuOptions["Scene Editor"]["objectData"]
        var addObjectSubmitOptions = document.createElement("div")
        for(var addObjectIndex in defaultObjectParameters){
            var addObjectRow = document.createElement("div")
            var addObjectInput = document.createElement("input")
            var addObjectText = document.createElement("p")
            addObjectInput.className = "addObjectInput"
            addObjectInput.type = defaultObjectParameters[addObjectIndex][1]
            addObjectInput.value = defaultObjectParameters[addObjectIndex][2]
            addObjectText.style.fontFamily = "monospace"
            addObjectText.innerText = defaultObjectParameters[addObjectIndex][0]
            addObjectRow.style.display = "flex"
            addObjectRow.appendChild(addObjectText)
            addObjectRow.appendChild(addObjectInput)
            addObjectPrompt.appendChild(addObjectRow)
      }
    </td>
  </tr>
  <tr>
    <td>
      A function that shows procedural abstraction is selectMode, a function that takes 3 parameters, the cell the function is switching, the type it wants to switch and the active html of the cell to switch between multiple functions. These 3 parameter than allow this function to change the type of cells between them. 
    </td>
    <td>
        var defaultObjectParameters = [
    ["X:", "number", 100, "x"], 
    ["Y:", "number", 100, "y"], 
    ["Width:", "number", 100, "width"], 
    ["Height:", "number",  150, "height"], 
    ["Selected Texture Index:", "select", 0, menuOptions["Tile Editor"]["tileLayers"]]
]

function createObjectControls(cellIteration){
    var currentAddObjectButton = document.getElementsByClassName("addObjectButton")[cellIteration]
    var addObjectPrompt = document.createElement("div")
    var objectMenu = menuOptions["Scene Editor"]["objectData"]
    var addObjectSubmitOptions = document.createElement("div")

    for(var addObjectIndex in defaultObjectParameters){
        var addObjectRow = document.createElement("div")
        var addObjectInput = document.createElement("input")
        var addObjectText = document.createElement("p")
        
        addObjectInput.className = "addObjectInput"
        addObjectInput.type = defaultObjectParameters[addObjectIndex][1]
        addObjectInput.value = defaultObjectParameters[addObjectIndex][2]

        addObjectText.style.fontFamily = "monospace"
        addObjectText.innerText = defaultObjectParameters[addObjectIndex][0]

        addObjectRow.style.display = "flex"

        addObjectRow.appendChild(addObjectText)
        addObjectRow.appendChild(addObjectInput)
        addObjectPrompt.appendChild(addObjectRow)
   }
function selectMode(cellIteration, activeCell, cellType){
    var header = document.createElement("div");
    var currentCell = activeCell
    console.log("Cell Variables are", activeCell, cellIteration, cellType)

    // Does not work at all! 
    switch(cellType){
        case "Scene Editor":
            var sceneEditor = document.createElementNS("http://www.w3.org/2000/svg", "svg")
            var sceneEditorTextures = document.createElementNS("http://www.w3.org/2000/svg", "defs")

            sceneEditor.setAttribute("class", "sceneEditor")
            sceneEditorTextures.setAttribute("class", "sceneEditorTextures")
            for(var sceneEditorGroupMaker = 0; sceneEditorGroupMaker < menuOptions["Tile Editor"]["tileLayers"].length; sceneEditorGroupMaker++){

                var sceneEditorGroup = document.createElementNS("http://www.w3.org/2000/svg", "g") 
                sceneEditorGroup.setAttribute("id", menuOptions["Tile Editor"]["tileLayers"][sceneEditorGroupMaker][0])
                // Found the BUG!!!!!!
                for(var sceneEditorTexelYItterator = 0; sceneEditorTexelYItterator < (menuOptions["Scene Editor"]["objectData"][objectItterator]["height"] / gridSnaping); sceneEditorTexelYItterator++){
                    for(var sceneEditorTexelXItterator = 0; sceneEditorTexelXItterator < (
                        menuOptions["Tile Editor"]["tileLayers"][menuOptions["Scene Editor"]["objectData"][sceneEditorGroupMaker]["selectedLayerIndex"]][1][0].length); sceneEditorTexelXItterator++){
                        var sceneEditorTexel = document.createElementNS("http://www.w3.org/2000/svg", "rect")
                        console.log("Checking", menuOptions["Scene Editor"]["objectData"][sceneEditorGroupMaker]["selectedLayerIndex"], menuOptions["Tile Editor"]["tileLayers"][menuOptions["Scene Editor"]["objectData"][sceneEditorGroupMaker]["selectedLayerIndex"]][1][sceneEditorTexelYItterator][sceneEditorTexelXItterator][1])
                        sceneEditorTexel.setAttribute("fill", `rgba(
                            ${menuOptions["Tile Editor"]["tileLayers"][menuOptions["Scene Editor"]["objectData"][sceneEditorGroupMaker]["selectedLayerIndex"]][1][sceneEditorTexelYItterator][sceneEditorTexelXItterator][0]},
                            ${menuOptions["Tile Editor"]["tileLayers"][menuOptions["Scene Editor"]["objectData"][sceneEditorGroupMaker]["selectedLayerIndex"]][1][sceneEditorTexelYItterator][sceneEditorTexelXItterator][1]},
                            ${menuOptions["Tile Editor"]["tileLayers"][menuOptions["Scene Editor"]["objectData"][sceneEditorGroupMaker]["selectedLayerIndex"]][1][sceneEditorTexelYItterator][sceneEditorTexelXItterator][2]},
                            ${menuOptions["Tile Editor"]["tileLayers"][menuOptions["Scene Editor"]["objectData"][sceneEditorGroupMaker]["selectedLayerIndex"]][1][sceneEditorTexelYItterator][sceneEditorTexelXItterator][3]}
                        )`)
                        sceneEditorTexel.setAttribute("class", `The Group is ${sceneEditorGroupMaker}`)
                        sceneEditorTexel.setAttribute("width", gridSnaping)
                        sceneEditorTexel.setAttribute("height", gridSnaping)
                        sceneEditorTexel.setAttribute("x", sceneEditorTexelXItterator * gridSnaping)
                        sceneEditorTexel.setAttribute("y", sceneEditorTexelYItterator * gridSnaping)
                        sceneEditorGroup.appendChild(sceneEditorTexel)
                    }
                }
                sceneEditorTextures.appendChild(sceneEditorGroup)
                
            }
            console.log("Checking ---------------------------------")

            // Need to set scene editor to be avaliable for multiple windows
            
            menuOptions["Scene Editor"]["screenData"].push(0, 0, currentCell.clientWidth, currentCell.clientHeight)

            sceneEditor.appendChild(sceneEditorTextures)

            currentCell.appendChild(sceneEditor)
            currentCell.className += " hasSceneEditor"
            for(var objectCreator in (menuOptions["Scene Editor"]["objectData"])){
                createObjectForDisplay(objectCreator, cellIteration)
            }

            screenControlsHUD(currentCell, cellIteration)

            break

        case "Editor Controls":
            var mainEditorControls = document.createElement("nav")
            var bottomObjectBar = document.createElement("div")
            var addObjectButton = document.createElement("button")

            bottomObjectBar.className = "bottomObjectBar"
            addObjectButton.innerText = "+"
            addObjectButton.className = "addObjectButton"
            addObjectButton.onclick = () => {
                createObjectControls(cellIteration)
            }
            mainEditorControls.className = "mainEditorControls"

            console.log("Current Cell is", document.getElementsByClassName("cell"))
            bottomObjectBar.appendChild(addObjectButton)
            mainEditorControls.appendChild(bottomObjectBar)
            currentCell.appendChild(mainEditorControls)

            console.log("My current Cell is", currentCell)
            for(let editorObject in menuOptions["Scene Editor"]["objectData"]){
                addObjectControls((currentCell.getElementsByClassName("mainEditorControls")[0]), editorObject)
            }

            break
        
        case "Javascript Runner":
            var mainCodeSpace = document.createElement("div")
            var codeSpace = document.createElement("textarea")
            var codeSpaceRunButton = document.createElement("button")
            var codeSpaceIFrame = document.createElement("iframe")
            codeSpaceIFrame.className = "codeSpaceIFrame"
            codeSpaceRunButton.className = "codeSpaceRunButton"
            codeSpaceRunButton.innerText = "Run Code"
            codeSpace.className = "codeSpace"
            mainCodeSpace.style.height = "100%"
            codeSpace.addEventListener("focus", (event) => {
                menuOptions["Scene Editor"]["player"]["canMove"] = false
            })
            codeSpace.addEventListener("focusout", () => {
                menuOptions["Scene Editor"]["player"]["canMove"] = true
            })
            currentCell.getElementsByClassName("header")[0].appendChild(codeSpaceIFrame)
            mainCodeSpace.appendChild(codeSpace)
            mainCodeSpace.appendChild(codeSpaceRunButton)
            currentCell.appendChild(mainCodeSpace)
            codeSpaceRunButton.onclick = function(){runCode(document.getElementsByClassName("codeSpaceRunButton").length - 1)}
            break
            
            // Initialize CodeMirror

            var editor = CodeMirror.fromTextArea(codeSpace, {
                mode: "javascript",
                theme: "default",
                lineNumbers: true,
                autofocus: true // Optional: focus the editor when it's created
            });
            break;

            case "Tile Editor":
                var mainTileEditor = document.createElement("div")
                var tileLayerSelector = document.createElement("select")
                var mainTileLayerMenu = document.createElement("div")
                var tileEditorSceneHUD = document.createElement("div")
                var tileEditorScene = document.createElementNS("http://www.w3.org/2000/svg", "svg")
                var tileEditorItemChanger = document.createElementNS("http://www.w3.org/2000/svg", "g")
                var tileEditorZoomBarBackground = document.createElement("div")
                var tileEditorZoomBarIncrease = document.createElement("button")
                var tileEditorZoomBarNormalize = document.createElement("button")
                var tileEditorZoomBarDecrease = document.createElement("button")
    
                tileEditorSceneHUD.style.height = "100%"
                tileEditorSceneHUD.className = "tileEditorSceneHUD"
    
                tileEditorZoomBarIncrease.innerText = "+"
                tileEditorZoomBarNormalize.innerText = "0"
                tileEditorZoomBarDecrease.innerText = "-"
    
                tileEditorZoomBarIncrease.onclick = () => {
                    if(gridSizing + 1.5 < 30){
                        tileEditorZoomChanges(1.5, cellIteration)
                    }
                }
                tileEditorZoomBarNormalize.onclick = () => {
                    tileEditorZoomChanges(15 - gridSizing, cellIteration)
                }
                tileEditorZoomBarDecrease.onclick = () => {
                    if(gridSizing - 1.5 > 5){
                        tileEditorZoomChanges(-1.5, cellIteration)
                    }
                }
    
                tileEditorZoomBarIncrease.className = "tileEditorZoomBarText"
                tileEditorZoomBarNormalize.className = "tileEditorZoomBarText"
                tileEditorZoomBarDecrease.className = "tileEditorZoomBarText"
                tileEditorZoomBarBackground.className = "tileEditorZoomBarBackground"
    
                tileEditorZoomBarIncrease.style.left = `${tileEditorZoomBarBackground.clientLeft / 2 - 6.5}px`
                tileEditorZoomBarNormalize.style.left =`${tileEditorZoomBarBackground.clientLeft / 2 - 6.5}px`
                tileEditorZoomBarDecrease.style.left = `${tileEditorZoomBarBackground.clientLeft / 2 - 6.5}px`
    
                // var tileLayerAddLayer = document.createElement("button")
                
                mainTileEditor.className = "mainTileEditor"
                // tileLayerAddLayer.className = "tileLayerAddLayer"
    
                // tileLayerAddLayer.innerText = "+"
                // tileLayerAddLayer.onclick = () => {addTileLayer()}
    
                tileLayerSelector.className = "tileLayerSelector"
    
                for(var tileLayerSelectorName in menuOptions["Tile Editor"]["tileLayers"]){
                    var tileLayerSelectorLabel = document.createElement("option") 
                    tileLayerSelectorLabel.innerText = menuOptions["Tile Editor"]["tileLayers"][tileLayerSelectorName][0]
                    if(tileLayerSelectorName == menuOptions["Scene Editor"]["objectData"][menuOptions["Scene Editor"]["selectedObjectIndex"]]["selectedLayerIndex"]){
                        tileLayerSelectorLabel.selected = "true"
                    }
                    tileLayerSelector.appendChild(tileLayerSelectorLabel)
                }
                    tileEditorItemChanger.setAttribute("width", (menuOptions["Tile Editor"]["tileLayers"][tileLayerSelectorName][1][0].length) * tileXSpacing - (tileXSpacing - gridSizing))
                    tileEditorItemChanger.setAttribute("height", (menuOptions["Tile Editor"]["tileLayers"][tileLayerSelectorName][1].length * tileYSpacing - (tileYSpacing - gridSizing)))
    
                tileLayerSelector.addEventListener("input", () => {
                    var tileEditorScene = tileLayerSelector.parentElement.parentElement.getElementsByClassName("tileEditorScene")[0]
                    document.getElementsByClassName("sceneObject")[menuOptions["Scene Editor"]["selectedObjectIndex"]].setAttribute("href", `#${menuOptions["Tile Editor"]["tileLayers"][document.getElementsByClassName("tileLayerSelector")[0].selectedIndex][0]}`)
                    tileEditorScene.lastChild.remove()
                    menuOptions["Scene Editor"]["objectData"][menuOptions["Scene Editor"]["selectedObjectIndex"]]["selectedLayerIndex"] = tileLayerSelector.selectedIndex
                    var tileEditorItemChanger = document.createElementNS("http://www.w3.org/2000/svg", "g")
                    
                    tileEditorItemChanger.setAttribute("width", (menuOptions["Tile Editor"]["tileLayers"][tileLayerSelector.selectedIndex][1][0].length) * tileXSpacing - (tileXSpacing - 15))
                    tileEditorItemChanger.setAttribute("height", (menuOptions["Tile Editor"]["tileLayers"][tileLayerSelector.selectedIndex][1].length) * tileYSpacing - (tileYSpacing - 15))
                    tileEditorItemChanger.setAttribute("transform", `translate(
                        ${(parseInt(tileEditorScene.clientWidth) / 2) - (parseInt(tileEditorItemChanger.getAttribute("width")) / 2)}, 
                        ${(parseInt(tileEditorScene.clientHeight) / 2) - (parseInt(tileEditorItemChanger.getAttribute("height")) / 2)})`)
    
                    tileEditorItemChanger.onmousedown = (event) => {
                        setTileEditorClickItem(event, tileEditorItemChanger)
                        tileEditorMouseDown = true
                    }
                    tileEditorItemChanger.onmouseup = () => {
                        tileEditorMouseDown = false
                        if(document.getElementsByClassName("selectedTile").length > 0){
                            document.getElementsByClassName("selectedTile")[0].remove()
                        }
                    }
                    tileEditorItemChanger.onmouseover = (event) => {
                        if(tileEditorMouseDown == true){
                            let tileEditorSelectedX = Math.floor((event.clientX - Math.floor(tileEditorItemChanger.getBoundingClientRect().x)) / tileXSpacing)
                            let tileEditorSelectedY = Math.floor((event.clientY - Math.floor(tileEditorItemChanger.getBoundingClientRect().y)) / tileYSpacing)
                            var selectedTile = document.getElementsByClassName("selectedTile")[0]
                            selectedTile.setAttribute("x", tileEditorSelectedX * tileXSpacing)
                            selectedTile.setAttribute("y", tileEditorSelectedY * tileYSpacing)
if(document.getElementsByClassName("tileEditorColorShowcase").length == 0){
                                return
                            }
                            var currentSelectedTile = document.getElementsByClassName("tileLayerSelector")[0].selectedIndex
                            var selectedTileLayer = document.getElementsByClassName("tileEditorSlider")
                            console.log("Accessing", currentSelectedTile, tileEditorSelectedX, tileEditorSelectedY, selectedTileLayer[3].value)
                            menuOptions["Tile Editor"]["tileLayers"][menuOptions["Scene Editor"]["selectedObjectIndex"]][1][tileEditorSelectedY][tileEditorSelectedX] = [
                                selectedTileLayer[0].value, 
                                selectedTileLayer[1].value, 
                                selectedTileLayer[2].value,
                                selectedTileLayer[3].value,
                            ]                            document.getElementById(String(menuOptions["Tile Editor"]["tileLayers"][currentSelectedTile][0])).children[tileEditorSelectedY * tilesOnXAxis + tileEditorSelectedX].setAttribute("fill", `rgba(                                ${parseInt(selectedTileLayer[0].value)},
${parseInt(selectedTileLayer[1].value)},                                ${parseInt(selectedTileLayer[2].value)},
${parseFloat(selectedTileLayer[3].value)})`) document.getElementsByClassName("tileEditorPixel")[(tileEditorSelectedY * tilesOnXAxis) + tileEditorSelectedX].setAttribute("style", `fill: rgba(
                                ${selectedTileLayer[0].value}, 
                                ${selectedTileLayer[1].value}, 
                                ${selectedTileLayer[2].value},
                                ${selectedTileLayer[3].value}); 
                                user-select:none;`)
                        }
                    }                    tileEditorSceneGridSize(tileLayerSelector.selectedIndex, tileEditorItemChanger, gridSizing)
tileEditorScene.appendChild(tileEditorItemChanger)
                })
                mainTileLayerMenu.className = "mainTileLayerMenu"
                tileEditorScene.setAttribute("class", "tileEditorScene")
                tileEditorScene.setAttribute("height", currentCell.clientHeight)
                tileEditorScene.setAttribute("width", currentCell.clientWidth)
                tileEditorScene.setAttribute("x", 0)
                tileEditorScene.setAttribute("y", 0)
                tileEditorScene.setAttribute("viewbox", `0 0 ${currentCell.clientWidth} ${currentCell.clientHeight}`)
    
                tileEditorItemChanger.onmouseup = () => {
                    tileEditorMouseDown = false
if(document.getElementsByClassName("selectedTile").length > 0){     document.getElementsByClassName("selectedTile")[0].remove()
                    }
                }
                tileEditorItemChanger.onmousedown = (event) => {
                    setTileEditorClickItem(event, tileEditorItemChanger)
                    tileEditorMouseDown = true
                }
                tileEditorItemChanger.onmouseover = (event) => {
                    if(tileEditorMouseDown == true){
                        let tileEditorSelectedX = Math.floor((event.clientX - Math.floor(tileEditorItemChanger.getBoundingClientRect().x)) / tileXSpacing)
                        let tileEditorSelectedY = Math.floor((event.clientY - Math.floor(tileEditorItemChanger.getBoundingClientRect().y)) / tileYSpacing)
                        var selectedTile = document.getElementsByClassName("selectedTile")[0]
                        selectedTile.setAttribute("x", tileEditorSelectedX * tileXSpacing)
                        selectedTile.setAttribute("y", tileEditorSelectedY * tileYSpacing)
if(document.getElementsByClassName("tileEditorColorShowcase").length == 0){
                            return
                        }
                        var currentSelectedTile = document.getElementsByClassName("tileLayerSelector")[0].selectedIndex
                        var selectedTileLayer = document.getElementsByClassName("tileEditorSlider")
                        console.log("Accessing", currentSelectedTile, tileEditorSelectedX, tileEditorSelectedY, selectedTileLayer[3].value)
                        menuOptions["Tile Editor"]["tileLayers"][currentSelectedTile][1][tileEditorSelectedY][tileEditorSelectedX] = [
                            selectedTileLayer[0].value, 
                            selectedTileLayer[1].value, 
                            selectedTileLayer[2].value,
                            selectedTileLayer[3].value,
                        ]                        document.getElementById(String(menuOptions["Tile Editor"]["tileLayers"][currentSelectedTile][0])).children[tileEditorSelectedY * tilesOnXAxis + tileEditorSelectedX].setAttribute("fill", `rgba(
 ${parseInt(selectedTileLayer[0].value)},
 ${parseInt(selectedTileLayer[1].value)},
 ${parseInt(selectedTileLayer[2].value)},              ${parseFloat(selectedTileLayer[3].value)})`)        document.getElementsByClassName("tileEditorPixel")[(tileEditorSelectedY * tilesOnXAxis) + tileEditorSelectedX].setAttribute("style", `fill: rgba(
                            ${selectedTileLayer[0].value}, 
                            ${selectedTileLayer[1].value}, 
                            ${selectedTileLayer[2].value},
                            ${selectedTileLayer[3].value}); 
                            user-select:none;`)
                    }
                }
tileEditorSceneGridSize(menuOptions["Scene Editor"]["objectData"][menuOptions["Scene Editor"]["selectedObjectIndex"]]["selectedLayerIndex"], tileEditorItemChanger, gridSizing)
tileEditorZoomBarBackground.appendChild(tileEditorZoomBarIncrease) tileEditorZoomBarBackground.appendChild(tileEditorZoomBarNormalize)
                tileEditorZoomBarBackground.appendChild(tileEditorZoomBarDecrease)           tileEditorScene.appendChild(tileEditorItemChanger)                tileEditorSceneHUD.appendChild(tileEditorScene)
tileEditorSceneHUD.appendChild(tileEditorZoomBarBackground)           mainTileLayerMenu.appendChild(tileLayerSelector)
mainTileEditor.appendChild(mainTileLayerMenu)                mainTileEditor.appendChild(tileEditorSceneHUD)
currentCell.appendChild(mainTileEditor)
                console.log("Getting width of", tileEditorScene.clientWidth, tileEditorScene.clientHeight)
tileEditorItemChanger.setAttribute("transform", `translate(
                ${(tileEditorScene.clientWidth / 2) - (tileEditorItemChanger.getAttribute("width")) / 2}, 
                ${(tileEditorScene.clientHeight / 2) - (tileEditorItemChanger.getAttribute("height") / 2)})`)
                break
            case "Tile Editor Colors":
                var tileEditorMainMenu = document.createElement("div")
                var tileEditorLabels = ["Red:", "Green:", "Blue:", "Alpha:"]
                var tileEditorColorName = document.createElement("p")
                var tileEditorColorShowcase = document.createElement("div")
                var tileEditorColorRow = document.createElement("div")
                var tileEditorSetColor = [127, 127, 127, 1]
    
                tileEditorMainMenu.className = "tileEditorMainMenu"
                tileEditorColorShowcase.className = "tileEditorColorShowcase"
    
                tileEditorColorShowcase.style.width = "40px"
                tileEditorColorShowcase.style.height = "20px"
                tileEditorColorName.innerText = "Resulting Color:"
                tileEditorColorName.style.color = "white"
tileEditorColorName.style.marginBottom = "0px"
                tileEditorColorRow.style.display = "flex"      tileEditorColorRow.appendChild(tileEditorColorName)     tileEditorColorRow.appendChild(tileEditorColorShowcase)            tileEditorMainMenu.appendChild(tileEditorColorRow)
                for(let tileItterator in tileEditorLabels){
                    var tileEditorRow = document.createElement("div")
                    var tileEditorLabel = document.createElement("p")
                    var tileEditorSlider = document.createElement("input")
                    var tileEditorColorLabel = document.createElement("p")
                    tileEditorSlider.className = "tileEditorSlider"
                    tileEditorLabel.className = "tileEditorLabel"
                    tileEditorLabel.style.width = "75px"
                    tileEditorColorLabel.className = "tileEditorColorLabel tileEditorLabel"
                    tileEditorRow.style.display = "flex"
                    tileEditorRow.style.height = "20px"
                    tileEditorColorLabel.style.right = "10px"
                    tileEditorColorLabel.style.position = "absolute"
    
                    tileEditorSlider.type = "range"
                    tileEditorSlider.max = "255"
                    tileEditorSlider.value = tileEditorSetColor[tileItterator]
                    tileEditorLabel.innerText = tileEditorLabels[tileItterator]
                    tileEditorColorLabel.innerText = tileEditorSetColor[tileItterator]
                    if(tileItterator == 3){
                        tileEditorSlider.step = `${1/255}`
                        tileEditorSlider.max = "1"
                    }
           tileEditorSlider.addEventListener("input", () => {              console.log(document.getElementsByClassName("tileEditorColorLabel")[tileItterator])                document.getElementsByClassName("tileEditorColorLabel")[tileItterator].innerText = Math.floor(document.getElementsByClassName("tileEditorSlider")[tileItterator].value * 1000) / 1000
tileEditorSetColor[tileItterator] = document.getElementsByClassName("tileEditorSlider")[tileItterator].value         document.getElementsByClassName("tileEditorColorShowcase")[0].style.backgroundColor = `rgba(${tileEditorSetColor[0]}, ${tileEditorSetColor[1]}, ${tileEditorSetColor[2]}, ${tileEditorSetColor[3]})`
                    })
tileEditorRow.appendChild(tileEditorLabel)                    tileEditorRow.appendChild(tileEditorSlider)
tileEditorRow.appendChild(tileEditorColorLabel)                tileEditorMainMenu.appendChild(tileEditorRow)
                }
    currentCell.appendChild(tileEditorMainMenu)
        }
}
    </td>
  </tr>
  <tr>
    <td>
      A function that uses Algorithm Implementation is compileWindows() a function that uses iteration as a way of creating blank cells for selectMode() to use. This is first done by inputting the array layOut which is a 2D array, the outer array causing the rows to be set and the inner array causing the cells to be made. These then create divs for the cells and rows to interact, dividers, for the player to shrink and grow the cells by and each divider has an Id of the type, Vertical or horizontal and the id of the cells or rows they neighbor.
    </td>
    <td>
      function compileWindows(){
    var cellsToAppend = []
    for(let layOutOfRows in layOut){
        var startingRow = document.createElement("div")
        startingRow.className = "row"
        startingRow.style.width = `calc(${100 / layOut.length}% - 16px)`
        for(let layOutOfCells in layOut[layOutOfRows]){
            var startingCell = document.createElement("div")
            startingCell.className = "cell"
            startingCell.style.height = `calc(${100 / layOut[layOutOfRows].length}% - ${10 / layOut[layOutOfRows].length}px)`
            startingRow.appendChild(startingCell)
            cellsToAppend.push([startingCell, layOut[layOutOfRows][layOutOfCells]])
            document.getElementById("mainWindow").appendChild(startingRow)
            if(layOut[layOutOfRows].length - 1 > layOutOfCells){
                var startingVerticalDivider = document.createElement("div")
                startingVerticalDivider.id = `vertical${layOutOfRows},${layOutOfCells},${parseInt(layOutOfCells) + 1}`
                startingVerticalDivider.className = "verticalDivider"
                document.getElementsByClassName("row")[parseInt(layOutOfRows)].appendChild(startingVerticalDivider)
            }
        }
    </td>
  </tr>
  <tr>
    <td>
      function compileWindows(){
    var cellsToAppend = []
    for(let layOutOfRows in layOut){
        var startingRow = document.createElement("div")
        startingRow.className = "row"
        startingRow.style.width = `calc(${100 / layOut.length}% - 16px)`
        for(let layOutOfCells in layOut[layOutOfRows]){
            var startingCell = document.createElement("div")
            startingCell.className = "cell"
            startingCell.style.height = `calc(${100 / layOut[layOutOfRows].length}% - ${10 / layOut[layOutOfRows].length}px)`
            startingRow.appendChild(startingCell)
            cellsToAppend.push([startingCell, layOut[layOutOfRows][layOutOfCells]])
            document.getElementById("mainWindow").appendChild(startingRow)
            if(layOut[layOutOfRows].length - 1 > layOutOfCells){
                var startingVerticalDivider = document.createElement("div")
                startingVerticalDivider.id = `vertical${layOutOfRows},${layOutOfCells},${parseInt(layOutOfCells) + 1}`
                startingVerticalDivider.className = "verticalDivider"
                document.getElementsByClassName("row")[parseInt(layOutOfRows)].appendChild(startingVerticalDivider)
            }
        }
    </td>
    <td>
      function gridResizing(position){
        return Math.floor(position / gridSnaping + 0.5) * gridSnaping
      }
      function resizeSceneEditor(currentAccessedCell){
          var allCells = document.querySelectorAll(".cell")
          for(var svgShapes = 0; svgShapes < document.getElementsByClassName("sceneObject").length; svgShapes++){
              var svgShape = document.getElementsByClassName("sceneObject")[svgShapes]
              console.log(svgShape)
              console.log("X is", Math.floor((allCells[currentAccessedCell].clientWidth - menuOptions["Scene Editor"]["screenData"][2]) / 2))
              svgShape.setAttribute("x", (gridResizing((allCells[currentAccessedCell].clientWidth - menuOptions["Scene Editor"]["screenData"][2]) / 2) + parseInt(menuOptions["Scene Editor"]["objectData"][svgShapes]["x"])))
              svgShape.setAttribute("y", (gridResizing((allCells[currentAccessedCell].clientHeight - menuOptions["Scene Editor"]["screenData"][3]) / 2)  + parseInt(menuOptions["Scene Editor"]["objectData"][svgShapes]["y"])))
          }
          document.getElementById("player").setAttribute("x", gridResizing((allCells[currentAccessedCell].clientWidth / 2 - 12)))
          document.getElementById("player").setAttribute("y", gridResizing((allCells[currentAccessedCell].clientHeight / 2 - 12)))
      }
    </td>
  </tr>
</table>