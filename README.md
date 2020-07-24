# PhothBooth_App
The Inspiration for this project came from my working knowledge of Mathematica's image processing capabilities and my gained understanding of the dynamic function. Thus the goal of this project is to make an interactive Photo Booth, one that is unique from what we currently have on our phones and other devices.

This App is a dynamic photo booth! Users are able to name the image, change the filter color and opacity as well as save the image to their computer as a png. (YAY IT ACTUALLY WORKS)

This is the finial photo booth note this verison does not include my custom functions but should give a genral idea of mathematica code 

CreatePalette[( * creates a new tab seperate from mathematica 's \notebook view *){
    inputname = InputString["Enter file name for picture"],
    Style["Photo Booth by Marin!!", FontSize - > 20,
      FontColor - > Magenta],

    Mouseover["Hover for Instructions",
      "click on the color slider to change color of the filter and use \
    the regular slider to change the opacity of the colored filter,to \
    take a photo Press the button!"],

    ColorSlider[Dynamic[y]],

    Slider[Dynamic[opacity], {
      0,
      1
    }, Appearance - > "Labeled"],

    ManyFilters / @ Normalfilter / @ dy, ( *
      creates different colored filters * )

    Style[ToString[inputname] < > ".png"
      ": file name"], ( *
      the to string
      function changes the users input into a string which\ then can be combined to anther string using the < > function*)

    Button["Take The Picture!",

      CreatePalette[{
        a = ManyFilters @Normalfilter @CurrentImage[], (* ManyFilters is the color changing effect, normal filter is a image relection *)
        Button[
          "Save image as .png ", {
            Export[
              ToString[inputname] < > ( * adds two strings togther * )
              "photoboothpicture.png", a],
            Beep[]( *
              the sound should notify users something has happened * )
          }]
      }]]
  }, \

  WindowTitle - > "Project 3", Background - > LightMagenta]
