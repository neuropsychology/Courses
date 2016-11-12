# Time()

A class object to wait some time, get time, control time and such.
Its methods (functions) are:
	- reset()
	- control()
	- wait()
See those for further informations.

Note that by default, there is already a Time class object called "time" (lowercase) that is initialized at neuropsydia's loading. For the sake of clarity, use this one (e.g., n.time.wait() ), especially for wait() and control() functions.

Parameters
----------
None

Returns
----------
None

Example
----------
>>> import neuropsydia as n
>>> n.start()
>>> myclock = n.Time()
>>> time_passed_since_myclock_creation = myclock.get()
>>> myclock.reset()
>>> time_passed_since_reset = myclock.get()
>>> n.close()

Authors
----------
Dominique Makowski

Dependencies
----------
- pygame 1.9.2
- time



------
# Time.reset()

Reset the clock of the Time object.

Parameters
----------
None

Returns
----------
None

Example
----------
>>> import neuropsydia as n
>>> n.start()
>>> time_passed_since_neuropsydia_loading = n.time.get()
>>> n.time.reset()
>>> time_passed_since_reset = n.time.get()
>>> n.close()

Authors
----------
Dominique Makowski

Dependencies
----------
- pygame 1.9.2
- time


-------
# Time.control(frequency=60)

Control time. Must be placed in a while loop and, each time the program runs through it, checks if the time passed is less than a certain amount (the frequency, by default 60, so 1/60 seconds). If true, the program stops and wait what needed before continuing, so that each loop takes at least 1/frequency seconds to be complete.

Parameters
----------
frequency = int, optional
The minimum frequency you want the loop to run at

Returns
----------
None

Example
----------
>>> import neuropsydia as n
>>> n.start()
>>> while n.time.get() < 5:
>>>     n.time.control()
>>>     print(n.time.get())
>>> n.close()

Authors
----------
Dominique Makowski

Dependencies
----------
- pygame 1.9.2
- time


-------
# Time.get(reset=True)

Get time since last initialisation / reset.

Parameters
----------
reset = bool, optional
	Should the clock be reset after returning time?

Returns
----------
float
	Time passed in milliseconds.

Example
----------
>>> import neuropsydia as n
>>> n.start()
>>> time_passed_since_neuropsydia_loading = n.time.get()
>>> n.time.reset()
>>> time_passed_since_reset = n.time.get()
>>> n.close()

Authors
----------
Dominique Makowski

Dependencies
----------
- pygame 1.9.2
- time



-------
# Time.wait(time_to_wait, unit="ms", frequency=60, round_by_frame=True, skip=None)

Wait some time.

Parameters
----------
time_to_wait = int
	Time to wait
unit = str
	"min" for minutes, "s" for seconds, "ms" for milliseconds, or "frame" for a certain amount of frames (depending on the frequency parameter)
frequency = int
	should be a multiple of your monitor's refresh rate
round by frame = bool
	should the waiting time be rounded to match an exact number of frame / refresh cycles? (e.g., on a 60Hz monitor, 95ms will be rounded to 100, because the monitor is refreshed every 16.6667ms)
skip = str
	Shoud there be a key to skip the waiting. Default to None.

Returns
----------
float
	Actual time waited in milliseconds

Example
----------
>>> import neuropsydia as n
>>> n.start()

>>> n.write("let's wait 500ms", round_by_frame = False)
>>> n.refresh()
>>> wait_time = n.time.wait(520)
>>> n.newpage("white")
>>> n.write("I waited for " + str(wait_time) + "ms")
>>> n.refresh()
>>> wait_time = n.time.wait(520, round_by_frame = True)
>>> n.newpage("white")
>>> n.write("I waited for " + str(wait_time) + "ms")
>>> n.refresh()
>>> n.time.wait(3, unit = "s")

>>> n.close()

Authors
----------
Dominique Makowski

Dependencies
----------
- pygame 1.9.2
- time



-------
# newpage(color_name="white", opacity=100, fade=False, fade_speed=60, fade_type="out", auto_refresh=True)


Fill the background with a color.

Parameters
----------
color_name = str, tuple, optional
name of the color (see color() function), or an RGB tuple (e.g., (122,84,01))
opacity = int, optional
opacity of the color (in percents)
fade = bool, optional
do you want a fade effect?
fade_speed = int, optional
frequency (speed) of the fading
fade_type = str, optional
"out" or "in", fade out or fade in

Returns
----------
None

Example
----------
>>> import neuropsydia as n
>>> n.start()
>>> n.newpage("blue")
>>> n.refresh()
>>> n.time.wait(500)
>>> n.close()

Authors
----------
Dominique Makowski

Dependencies
----------
- pygame 1.9.2
- time



-------
# refresh()

Reresh / flip the screen, actually display things on screen (to use after image(), write() or newpage()).

Parameters
----------
None

Returns
----------
None

Example
----------
>>> import neuropsydia as n
>>> n.start()
>>> n.newpage("blue")
>>> n.refresh()
>>> n.time.wait(500)
>>> n.close()

Authors
----------
Dominique Makowski

Dependencies
----------
- pygame 1.9.2



-------
# wait_for_input(time_max=None)

Low level input checker.

Parameters
----------
time_max = int
time max in ms

Returns
----------
key
A key.
Example
----------
NA

Authors
----------
Dominique Makowski

Dependencies
----------
- pygame 1.9.2
- time



-------
# response(allow=None, enable_escape=True, time_max=None, get_RT=True)

Get a (keyboard, for now) response.

Parameters
----------
allow = str or list
keys to allow
enable_escape = bool
enable escape to exit
time_max = int
maximum time to wait for a response (ms)
get_RT = bool
return response time

Returns
----------
str or (str, int)
returns a tuple when get_RT is set to True
Example
----------
NA

Authors
----------
Dominique Makowski

Dependencies
----------
- pygame 1.9.2
- time



-------
# Coordinates()

A class object to go from pygame corrdinates system to neuropsydia's and vice versa.

Its methods (functions) are:
- to_pygame()
- from_pygame()

Parameters
----------
None

Returns
----------
None

Example
----------
None

Authors
----------
Dominique Makowski

Dependencies
----------
- pygame 1.9.2




-------
# Coordinates.to_pygame(x=None, y=None, distance_x=None, distance_y=None)

Convert coordinates from neuropsydia (-10:10) to pygame's system (in pixels).

Parameters
----------
x = float
	[-10:10]
y = float
	[-10:10]
distance_x = convert a horizontal distance
	[-10:10]
distance_y = convert a horizontal distance
	[-10:10]
Returns
----------
NA

Example
----------
NA

Authors
----------
Dominique Makowski

Dependencies
----------
- pygame 1.9.2




-------
# Coordinates.from_pygame(x=None, y=None)

Help incomplete, sorry.

Parameters
----------
NA

Returns
----------
NA

Example
----------
NA

Authors
----------
Dominique Makowski

Dependencies
----------
- pygame 1.9.2


-------
# colors list

|Type|Colours|
|----|-------|
|Primary|![](https://img.shields.io/badge/white-255--255--255-green.svg?colorB=FFFFFF) ![](https://img.shields.io/badge/black-0--0--0-green.svg?colorB=000000) ![](https://img.shields.io/badge/grey-128--128--128-green.svg?colorB=808080) ![](https://img.shields.io/badge/raw__red-255--0--0-green.svg?colorB=ff0000) ![](https://img.shields.io/badge/raw__green-0--255--0-green.svg?colorB=00ff00)![](https://img.shields.io/badge/raw__blue-0--0--255-green.svg?colorB=0000ff)|
|Design|![](https://img.shields.io/badge/red-244--67--54-green.svg?colorB=f44336) ![](https://img.shields.io/badge/pink-233--30--99-green.svg?colorB=E91E63) ![](https://img.shields.io/badge/purple-156--39--176-green.svg?colorB=9C27B0) ![](https://img.shields.io/badge/deeppurple-103--58--183-green.svg?colorB=673AB7) ![](https://img.shields.io/badge/indigo-63--81--181-green.svg?colorB=3F51B5) ![](https://img.shields.io/badge/blue-33--150--243-green.svg?colorB=2196F3) ![](https://img.shields.io/badge/lightblue-33--150--243-green.svg?colorB=03A9F4) ![](https://img.shields.io/badge/cyan-0--188--212-green.svg?colorB=00BCD4) ![](https://img.shields.io/badge/teal-0--150--136-green.svg?colorB=009688) ![](https://img.shields.io/badge/green-76--175--80-green.svg?colorB=4CAF50) ![](https://img.shields.io/badge/lightgreen-139--195--74-green.svg?colorB=8BC34A) ![](https://img.shields.io/badge/green-76--175--80-green.svg?colorB=4CAF50) ![](https://img.shields.io/badge/lightgreen-139--195--74-green.svg?colorB=8BC34A) ![](https://img.shields.io/badge/lime-20--220--57-green.svg?colorB=CDDC39) ![](https://img.shields.io/badge/yellow-255--235--59-green.svg?colorB=FFEB3B) ![](https://img.shields.io/badge/amber-255--193--7-green.svg?colorB=FFC107) ![](https://img.shields.io/badge/orange-255--152--0-green.svg?colorB=FF9800) ![](https://img.shields.io/badge/deeporange-255--87--34-green.svg?colorB=FF5722) ![](https://img.shields.io/badge/brown-121--85--72-green.svg?colorB=795548) ![](https://img.shields.io/badge/lightgrey-220--220--220-green.svg?colorB=BDBDBD) ![](https://img.shields.io/badge/darkgrey-105--105--105-green.svg?colorB=424242) ![](https://img.shields.io/badge/bluegrey-96--125--139-green.svg?colorB=607D8B)|
|Pale|add `"pale_"` prefix|





-------
# color(color)

Returns an RGB color tuple (or list) from its name.

Parameters
----------
color = str
one from the color_list list

Returns
----------
tuple or list

Example
----------
>>> import neuropsydia as n
>>> n.start()
>>> print(n.color_list)
>>> print(n.color("blue"))
>>> n.close()

Authors
----------
Dominique Makowski

Dependencies
----------
None



-------
# cursor(visible=True)

Set the mouse cursor to visible or invisible.

Parameters
----------
visible = bool
True for visible, False for invisible.

Returns
----------
None

Example
----------
>>> import neuropsydia as n
>>> n.start()
>>> n.cursor(True)
>>> n.time.wait(2000)
>>> n.close()

Authors
----------
The pygame team

Dependencies
----------
- pygame 1.9.2



-------
# Time.control()



-------
# Time.control()



-------
# Time.control()



-------
# Time.control()



-------
# Time.control()



-------
# Time.control()



