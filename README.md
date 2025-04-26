# Zutil-Utility-Library
Utility library, some tools including Löve2D.

## Download
Press the green "Code" button and hit "Download .ZIP". Copy the zutil.lua file into your game's files, in the same directory as the rest of your code.
Then, write the following at the very top line of your main.lua file:

`local zutil = require "zutil.lua"`

All done! Enjoy.

## Tools

###### All random-based functions below function off of Lua's built-in `math.random()` function. If you're getting identical or similar results between each running instance of your code, make sure you're setting the random seed beforehand with `math.randomseed(seed)` or with `zutil.alwaysrandom()`.

##### `zutil.jitter(amplitude)`
Supply an amplitude. Returns a random value between `amplitude * -1` and `amplitude`.

##### `zutil.clamp(x, min, max)`
Supply x, a minimum, and maximum. Returns x "restrained" between the minimum and maximum. In other words, returns min if `x < min`, returns max if `x > max`, and otherwise returns `x`.

##### `zutil.touching(x1, y1, w1, h1, x2, y2, w2, h2)`
Supply x, y, width, and height values for two objects. Returns boolean: whether or not the objects are colliding.

##### `zutil.pythag(a, b)`
Returns `math.sqrt(a^2 + b^2)`; applies the Pythagorean theorem `a^2 + b^2 = c^2` and returns `c`.

##### `zutil.lerp(a, b, t)`
Supply a maximum `a`, a minimum `b`, and a float `t`, where `0 ≤ t ≤ 1`. Returns `a + (b - a) * t`.

##### `zutil.reverselerp(a, b, x)`
Supply a maximum `a`, a minimum `b`, and a value `x`. Returns `(x - a) / (b - a)`. This function is a rearranged form of `x = zutil.lerp(a,b,t)`, here as `t = zutil.reverselerp(a,b,x)`.

##### `zutil.midpoint(x1, y1, x2, y2)`
Supply two pairs of coordinates. Returns the coordinates of the midpoint between the two.

##### `zutil.distance(x1, y1, x2, y2)`
Supply two pairs of coordinates. Returns the distance between the two.

##### `zutil.varDisplay(...)`
Displays data about supplied variables. Requires Love2D. Supply any non-function variables you wish. Returns a string containing one data point about each variable, split over multiple lines.

##### `zutil.anglebetween(x1, y1, x2, y2)`
Supply a pair of coordinates. Returns the angle between them in radians.

##### `zutil.shuffle(t)`
Supply a table `t`. Returns `t` with the order of its elements randomized.

##### `zutil.overlay(color)`
Requires Löve2D. Renders a rectangle of the specified color and alpha over the entirety of the screen (be wary of graphics transformations you may have applied). Supply a table `color`, containing the RGB and alpha values of the overlay.

##### `zutil.stdinit(windowWidth, windowHeight, gameName)`
Requires Löve2D. Initialises global variables WINDOW.WIDTH, WINDOW.HEIGHT, WINDOW.CENTER_X, and WINDOW.CENTER_Y, sets file identity, sets window title, turns on highdpi setting, and sets window dimensions.

##### `zutil.split(str, separator)`
Supply a string and a separator (single character). Returns a table containing the substrings of the string split by the separator (all substrings excluding the separator).

##### `zutil.loadsfx(directory, sfxTable, fileType)`
Requires Löve2D. Loads SFX with fle type `fileType` (suffix, like ".wav" or ".ogg") from the desired directory into the supplied `sfxTable`. Returns `sfxTable`.

##### `zutil.playsfx(sfx, volume, pitch)`
Requires Löve2D. Plays an audio source. Returns whether the audio source had to be stopped.

##### `zutil.wrap(x, a, b)`
Supply a value `x`, `a`, and `b`. Returns `x` wrapped between `a` and `b`.

##### `zutil.abbreviatelove2dgraphics()`
Requires Löve2D. Initialises a global variable `graphics = love.graphics`.

##### `zutil.floor(x, placeValue)`
Supply a value `x` and an integer `placeValue` (1). Returns x truncated to the `placeValue` supplied. For example: `zutil.floor(5.6, 1) = 5`, `zutil.floor(91, 2) = 90`, `zutil.floor(220, 3) = 200`.

##### `zutil.ceiling(x, placeValue)`
Supply a value `x` and an integer `placeValue` (1). Returns x rounded up to the `placeValue` supplied. For example: `zutil.ceiling(5.6, 1) = 6`, `zutil.ceiling(91, 2) = 100`, `zutil.ceiling(220, 3) = 300`.

##### `zutil.updatetimer(timer, completeFunction, speed, dt)`
Supply a timer table `timer`, a function `completeFunction`, a number `speed` to increment by, and the delta-time `dt`. `timer` must have fields `current: number` and `max: number`. This function returns the `current` field of the timer incremented by `dt * speed`.

##### `zutil.remove(t, v)`
Supply a table `t` and a value `v` to remove from the table. Returns the value removed and the index it was removed at. Returns `nil` if the value was not found.

##### `zutil.search(t, v)`
Supply a table `t` and a value `v` to search for in the table. Returns the the index the value was found at. Returns `nil` if the value was not found.

##### `zutil.count(t)`
Returns the number of elements in table `t`, ignoring elements with a field `disabled = true`.

##### `zutil.thanks()`
Returns "You're welcome!"

##### `zutil.sprinkle(t, tSprinkle)`
Returns `t` with the elements of `tSprinkle` randomly placed within.

##### `zutil.clone(t)`
Returns a clone of table `t`, not sharing a memory adress with `t`.

##### `zutil.nilcheck(x, v, nilv)`
Returns `nilv` if `x` is nil, otherwise returns `v`.

##### `zutil.letters()`
Returns a table containing all English letters (without diacratics) in lowercase.

##### `zutil.relu(x)`
Returns `x` if `x > 0`, otherwise returns `0`.

##### `zutil.weighted(t)`
Returns a random value from table `t`, where the values of `t` are fields equal to their weight. For example, with `zutil.weighted({ lion = 2, bear = 1 })`, this function is two times more likely to return `"lion"` than `"bear"`.

### `zutil.weightedbool(trueWeight)`
Supply a percentage `trueWeight` where `0 ≤ trueWeight ≤ 100`. Returns `true` `trueWeight`% of the time.

### `zutil.randomchoice(t)`
Returns a random element from table `t`.

### `zutil.alwaysrandom()`
Sets the random seed to `os.time()`: `math.randomseed(os.time())`. Returns the seed used.
