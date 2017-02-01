# raffle-js
Control to play a raffle based on a list of string values

It uses pure JavaScript and CSS Animations to run.

##Browser compatibility
Any modern browser should support this control. I even tested in IE10, which is the first IE version to support CSS Animations, and it worked fine.
The audio is in both OGG and MP4 format for browsers support.

##Notes
The `audioPlayer` control is used for the demo only. It's not actually part of the Raffle controller, and can be replaced with any other audio controller. Anyway, you can use this `audioPlayer` for any purpose ;)

I used [http://listofrandomnames.com/](http://listofrandomnames.com/) to obtain a random list of names, but only for the demo. They can be retrieved in any form, and just added to the Raffle configuration.

##Usage
First, you have to initialize the controller:
```Javascript
raffle.config({
  names: names_array,
  container: document.getElementById('raffle-container'),
  duration: 5.2,
  itemDuration: .2,
  removeSelected: true
});
```
####`config` function parameters
|Property|Description|
|-------------|-------------|
|`names`|`String Array` with the names to sort.|
|`container`|`HTMLElement` that will display the names. The class `raffle-container` is required for the styles and animation.|
|`duration`|`Number` with the total duration in seconds (can include decimals). It's default value is `5.2` to match the demo audio's duration. _Optional_.|
|`itemDuration`|`Number` with the time (in seconds) each name will be visible. It must match the animation duration. Default value of `0.2`. _Optional_.|
|`removeSelected`|`Boolean` that indicates if the selected element at the end of the raffle will be removed for the next round. Default value of `true`. _Optional_.|


Once the raffle is configured, the `play` function can be executed at any moment to run the animation.
```Javascript
raffle.play({
  start: function () {
    console.log('Raffle started.');
  },
  end: function () {
    console.log('Raffle ended.');
  }
});
```
####`play` function parameters
|Property|Description|
|-------------|-------------|
|`start`|`Function` to run once the raffle is ready to play. _Optional_.|
|`end`|`Function` to run once the animation is over and the resulting item is displayed. _Optional_.|

