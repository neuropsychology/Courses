# Time()
```python
Time()
```

A class object to wait some time, get time, control time and such.
Its methods (functions) are:

- `reset()`
- `control()`
- `wait()`

See those for further informations.

Note that by default, there is already a Time class object called "time" (lowercase) that is initialized at neuropsydia's loading. For the sake of clarity, use this one (e.g., n.time.wait() ), especially for `wait()` and `control()` functions.

<font color="#2196F3" size="5">Parameters</font>
None

<font color="#2196F3" size="5">Returns</font>
None

<font color="#2196F3" size="5">Example</font>
```python
import neuropsydia as n
n.start()
myclock = n.Time()
time_passed_since_myclock_creation = myclock.get()
myclock.reset()
time_passed_since_reset = myclock.get()
n.close()
```

<font color="#2196F3" size="5">Authors</font>
Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>
- pygame 1.9.2
- time



------
# Time.reset()
```python
Time.reset()
```

Reset the clock of the Time object.

<font color="#2196F3" size="5">Parameters</font>
None

<font color="#2196F3" size="5">Returns</font>
None

<font color="#2196F3" size="5">Example</font>
```python
import neuropsydia as n
n.start()
time_passed_since_neuropsydia_loading = n.time.get()
n.time.reset()
time_passed_since_reset = n.time.get()
n.close()
```

<font color="#2196F3" size="5">Authors</font>
Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>
- pygame 1.9.2
- time


-------
# Time.control()
```python
Time.control(frequency=60)
```
Control time. Must be placed in a while loop and, each time the program runs through it, checks if the time passed is less than a certain amount (the frequency, by default 60, so 1/60 seconds). If true, the program stops and wait what needed before continuing, so that each loop takes at least 1/frequency seconds to be complete.

<font color="#2196F3" size="5">Parameters</font>

frequency = int, optional
The minimum frequency you want the loop to run at

<font color="#2196F3" size="5">Returns</font>

None

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
while n.time.get() < 5:
    n.time.control()
    print(n.time.get())
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- time


-------
# Time.get()
```python
Time.get(reset=True)
```
Get time since last initialisation / reset.

<font color="#2196F3" size="5">Parameters</font>

reset = bool, optional
	Should the clock be reset after returning time?

<font color="#2196F3" size="5">Returns</font>

float
	Time passed in milliseconds.

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
time_passed_since_neuropsydia_loading = n.time.get()
n.time.reset()
time_passed_since_reset = n.time.get()
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- time



-------
# Time.wait()
```python
Time.wait(time_to_wait, unit="ms", frequency=60, round_by_frame=True, skip=None)
```
Wait some time.

<font color="#2196F3" size="5">Parameters</font>

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

<font color="#2196F3" size="5">Returns</font>

float
	Actual time waited in milliseconds

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()

n.write("let's wait 500ms", round_by_frame = False)
n.refresh()
wait_time = n.time.wait(520)
n.newpage("white")
n.write("I waited for " + str(wait_time) + "ms")
n.refresh()
wait_time = n.time.wait(520, round_by_frame = True)
n.newpage("white")
n.write("I waited for " + str(wait_time) + "ms")
n.refresh()
n.time.wait(3, unit = "s")

n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- time



-------
# newpage()
```python
newpage(color_name="white", opacity=100, fade=False, fade_speed=60, fade_type="out", auto_refresh=True)
```

Fill the background with a color.

<font color="#2196F3" size="5">Parameters</font>

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

<font color="#2196F3" size="5">Returns</font>

None

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
n.newpage("blue")
n.refresh()
n.time.wait(500)
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- time



-------
# refresh()
```python
refresh()
```
Reresh / flip the screen, actually display things on screen (to use after image(), write() or newpage()).

<font color="#2196F3" size="5">Parameters</font>

None

<font color="#2196F3" size="5">Returns</font>

None

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
n.newpage("blue")
n.refresh()
n.time.wait(500)
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2



-------
# wait_for_input()
```python
wait_for_input(time_max=None)
```
Low level input checker.

<font color="#2196F3" size="5">Parameters</font>

time_max = int
time max in ms

<font color="#2196F3" size="5">Returns</font>

key
A key.
<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- time



-------
# response()
```python
response(allow=None, enable_escape=True, time_max=None, get_RT=True)
```
Get a (keyboard, for now) response.

<font color="#2196F3" size="5">Parameters</font>

allow = str or list
keys to allow
enable_escape = bool
enable escape to exit
time_max = int
maximum time to wait for a response (ms)
get_RT = bool
return response time

<font color="#2196F3" size="5">Returns</font>

str or (str, int)
<font color="#2196F3" size="5">Returns</font> a tuple when get_RT is set to True
<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- time



-------
# Coordinates()
```python
Coordinates()
```
A class object to go from pygame corrdinates system to neuropsydia's and vice versa.

Its methods (functions) are:
- to_pygame()
- from_pygame()

<font color="#2196F3" size="5">Parameters</font>

None

<font color="#2196F3" size="5">Returns</font>

None

<font color="#2196F3" size="5">Example</font>

None

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2




-------
# Coordinates.to_pygame()
```python
Coordinates.to_pygame(x=None, y=None, distance_x=None, distance_y=None)
```
Convert coordinates from neuropsydia (-10:10) to pygame's system (in pixels).

<font color="#2196F3" size="5">Parameters</font>

x = float
	[-10:10]
y = float
	[-10:10]
distance_x = convert a horizontal distance
	[-10:10]
distance_y = convert a horizontal distance
	[-10:10]
<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2




-------
# Coordinates.from_pygame()
```python
Coordinates.from_pygame(x=None, y=None)
```
Help incomplete, sorry.

<font color="#2196F3" size="5">Parameters</font>

NA

<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2


-------
# colors list

|Type|Colours|
|----|-------|
|Primary|![](https://img.shields.io/badge/white-255--255--255-green.svg?colorB=FFFFFF) ![](https://img.shields.io/badge/black-0--0--0-green.svg?colorB=000000) ![](https://img.shields.io/badge/grey-128--128--128-green.svg?colorB=808080) ![](https://img.shields.io/badge/raw__red-255--0--0-green.svg?colorB=ff0000) ![](https://img.shields.io/badge/raw__green-0--255--0-green.svg?colorB=00ff00)![](https://img.shields.io/badge/raw__blue-0--0--255-green.svg?colorB=0000ff)|
|Design|![](https://img.shields.io/badge/red-244--67--54-green.svg?colorB=f44336) ![](https://img.shields.io/badge/pink-233--30--99-green.svg?colorB=E91E63) ![](https://img.shields.io/badge/purple-156--39--176-green.svg?colorB=9C27B0) ![](https://img.shields.io/badge/deeppurple-103--58--183-green.svg?colorB=673AB7) ![](https://img.shields.io/badge/indigo-63--81--181-green.svg?colorB=3F51B5) ![](https://img.shields.io/badge/blue-33--150--243-green.svg?colorB=2196F3) ![](https://img.shields.io/badge/lightblue-33--150--243-green.svg?colorB=03A9F4) ![](https://img.shields.io/badge/cyan-0--188--212-green.svg?colorB=00BCD4) ![](https://img.shields.io/badge/teal-0--150--136-green.svg?colorB=009688) ![](https://img.shields.io/badge/green-76--175--80-green.svg?colorB=4CAF50) ![](https://img.shields.io/badge/lightgreen-139--195--74-green.svg?colorB=8BC34A) ![](https://img.shields.io/badge/lime-20--220--57-green.svg?colorB=CDDC39) ![](https://img.shields.io/badge/yellow-255--235--59-green.svg?colorB=FFEB3B) ![](https://img.shields.io/badge/amber-255--193--7-green.svg?colorB=FFC107) ![](https://img.shields.io/badge/orange-255--152--0-green.svg?colorB=FF9800) ![](https://img.shields.io/badge/deeporange-255--87--34-green.svg?colorB=FF5722) ![](https://img.shields.io/badge/brown-121--85--72-green.svg?colorB=795548) ![](https://img.shields.io/badge/lightgrey-220--220--220-green.svg?colorB=BDBDBD) ![](https://img.shields.io/badge/darkgrey-105--105--105-green.svg?colorB=424242) ![](https://img.shields.io/badge/bluegrey-96--125--139-green.svg?colorB=607D8B)|
|Pale|add `"pale_"` prefix|





-------
# color()
```python
color(color)
```
<font color="#2196F3" size="5">Returns</font> an RGB color tuple (or list) from its name.

<font color="#2196F3" size="5">Parameters</font>

color = str
one from the color_list list

<font color="#2196F3" size="5">Returns</font>

tuple or list

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
print(n.color_list)
print(n.color("blue"))
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

None



-------
# cursor()
```python
cursor(visible=True)
```
Set the mouse cursor to visible or invisible.

<font color="#2196F3" size="5">Parameters</font>

visible = bool
True for visible, False for invisible.

<font color="#2196F3" size="5">Returns</font>

None

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
n.cursor(True)
n.time.wait(2000)
n.close()

<font color="#2196F3" size="5">Authors</font>

The pygame team

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2



-------
# Trigger()
```python
Trigger(TTL=True, photosensor=None, photosensor_position="bottomleft", stimtracker=False, stimtracker_duration=5)
```
A class object to send trigger via TTL, ethernet or stimtracker.

<font color="#2196F3" size="5">Parameters</font>

TTL = bool, optional
	Send trigger through the parallel port.
photosensor = str, optional
	"white" or "black" for the color of the rectangle.
photosensor_position = str, optional
	"bottomleft", "bottomright", "topleft" or "topright" for its position.
stimtracker = bool, optional
	Send trigger through a stimtracker.
stimtracker_duration = float, optional
	Time for the stimtracker trigger to last (in seconds).

<font color="#2196F3" size="5">Returns</font>

None

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
trigger = n.Trigger()
trigger.start()
trigger.stop()
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- ctypes
- pyxid


-------
# Trigger.start()
```python
Trigger.start(trigger=1, port=0x378, lines=1)
```
Send the trigger.

<font color="#2196F3" size="5">Parameters</font>

trigger = int, optional
	What trigger to send (TTL).
port = binary, optional
	Port address (TTL).
lines = int, optional
	Lines to activate (stimtracker).

<font color="#2196F3" size="5">Returns</font>

None

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
trigger = n.Trigger()
trigger.start()
trigger.stop()
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- ctypes
- pyxid


-------
# Trigger.stop()
```python
Trigger.stop(trigger=0, port=0x378)
```
Return to baseline (for TTL only).

<font color="#2196F3" size="5">Parameters</font>

trigger = int, optional
	What trigger to send (TTL).
port = binary, optional
	Port address (TTL).

<font color="#2196F3" size="5">Returns</font>

None

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
trigger = n.Trigger()
trigger.start()
trigger.stop()
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- ctypes
- pyxid


-------
# instructions()
```python
instructions(text, background='white', color="black", size=1.0, title=None, replace_title=False, end_text="Appuyez sur ENTRER pour commencer.")
```
Help incomplete, sorry.

<font color="#2196F3" size="5">Parameters</font>

NA

<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- time


-------
# questionnaire()
```python
questionnaire(questions_dictionary, questions_list_key_name='Item', background='white', size=1, show_page_number=True,  randomize=False, reverse=False, results_save=False, results_type="csv", results_name="questionnaire_results", results_path="", dimensions_mean=False, dimensions_key_name='Dimension', style='red', x=0, y=-3.3, anchors=None, anchors_space=2, anchors_size=0.7, edges=[0,100], validation=True, analog=True, step=1, labels="numeric", labels_size=0.8, labels_rotation=0, labels_space=-1, labels_x=0, line_thickness=4, line_length=8, line_color="black", title=None, title_style="body", title_size=1, title_space=2, point_center=False, point_edges=True, force_separation=False, separation_labels=None, separation_labels_size=1, separation_labels_rotate=0, separation_labels_space=-1, show_result=False, show_result_shape="circle", show_result_shape_fill_color="white", show_result_shape_line_color="red", show_result_shape_size=0.8, show_result_space=1.2, show_result_size=0.5, show_result_color="black", instructions_text=None):
```
A wrapper function for easily creating questionnaires. You can go back or foth using the LEFT and RIGHT keyboard arrows.

<font color="#2196F3" size="5">Parameters</font>

questions_dictionary = dict
	needs an object of the following stucture:

	questions_dictionary = {
	    "Item": {
	        1: "Is Neuropsydia great?",
	        2: "Is Neuropsydia not great?",
	        3: "Is Python great?",
	        4: "Is Python not great?"
	        }
	}

<font color="#2196F3" size="5">Returns</font>

A pandas dataframe containing the data. See http://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe for details.

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
questions_dictionary = {
    "Item": {
        1: "Is Neuropsydia great?",
        2: "Is Neuropsydia not great?",
        3: "Is Python great?",
        4: "Is Python not great?"
    },
    "Reverse": {
        1: False,
        2: True,
        3: False,
        4: True
    },
    "Dimension": {
        1: "Neuropsydia",
        2: "Neuropsydia",
        3: "Python",
        4: "Python"
    }
}
n.start()
n.questionnaire(questions_dictionary, anchors=["No", "Yes"], results_save=True, dimensions_mean=True)
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- pandas 18.0
- time




-------
# get_creation_date()
```python
get_creation_date(path_to_file)
```
Try to get the date that a file was created, falling back to when it was
last modified if that isn't possible.
See http://stackoverflow.com/a/39501288/1709587 for explanation.

<font color="#2196F3" size="5">Parameters</font>

file =  BIOPAC's AcqKnowledge file
	a file read by bioread.read()

<font color="#2196F3" size="5">Returns</font>

creation_date

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start(False)
date = n.get_creation_date(path)

<font color="#2196F3" size="5">Authors</font>

Mark Amery

<font color="#2196F3" size="5">Dependencies</font>

- os
- platform



-------
# line()
```python
line(left_x=-5, left_y=0, right_x=5, right_y=0, line_color="black", thickness=1)
```
Help incomplete, sorry.

<font color="#2196F3" size="5">Parameters</font>

NA

<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- pygame.gfxfraw


-------
# rectangle()
```python
rectangle(x=0, y=0, width=10, height=10, line_color="black", thickness=1, fill_color=None, opacity=225)
```
Help incomplete, sorry.

<font color="#2196F3" size="5">Parameters</font>

NA

<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- pygame.gfxfraw

-------
# circle()
```python
circle(x=0, y=0, size=10, line_color="black", thickness=0, fill_color="white", opacity=225)
```
Help incomplete, sorry.

<font color="#2196F3" size="5">Parameters</font>

NA

<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- pygame.gfxfraw


-------
# countdown()
```python
countdown(style="circle", duration=3000, width=5, reverse=False, background="white", write_seconds=True, write_color="white", write_outline="black", color_fade=False, color_start="red", color_end="green", sound=False, melody=[1000, 1500])
```
Help incomplete, sorry.

<font color="#2196F3" size="5">Parameters</font>

NA

<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- pygame.gfxfraw
- time
- winsound


-------
# scale_styles()
```python
scale_styles()
```
<font color="#2196F3" size="5">Returns</font> available scale styles.

<font color="#2196F3" size="5">Parameters</font>

None

<font color="#2196F3" size="5">Returns</font>

None

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
print(n.scale_styles())
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

None


-------
# scale()
```python
scale(style='red', x=0, y=-3.3, anchors=None, anchors_space=2, anchors_size=0.7, edges=[0, 100], validation=True, analog=True, step=1, labels="numeric", labels_size=0.8, labels_rotation=0, labels_space=-1, labels_x=0, line_thickness=4, line_length=8, line_color="black", background="white", title=None, title_style="body", title_size=1, title_space=1.75, point_center=False, point_edges=True, reverse=False, force_separation=False, separation_labels=None, separation_labels_size=1, separation_labels_rotate=0, separation_labels_space=-1, show_result=False, show_result_shape="circle", show_result_shape_fill_color="white", show_result_shape_line_color="red", show_result_shape_size=0.8, show_result_space=1.25, show_result_size=0.5, show_result_color="black", show_result_decimals=1):
```
Draw a scale.
HELP INCOMPLETE.

<font color="#2196F3" size="5">Parameters</font>

style = str, optional
	style, check scale_styles() function to see what's available
x = float, optional
	position on x axis (from -10 (left) to 10 (right))
y = float, optional
	position on y axis (from -10 (down) to 10 (up))
anchors = list of two str, optional
	a list of two propositions to be displayed on the sides of the scale (e.g., [not at all, very much])
anchors_space = float, optional
	spacing betweeen the edge and the anchors
anchors_size = float, optional
	size of the anchors' font
edges = list of two floats
	the underlying numerical edges of the scale
validation = bool, optional
	confirm the response with a second left click or withdraw with a right click
analog = bool, optional
	continuous (discrete) scale
step = int, optional
	if analog is True, what are the step to go between the edges (determine the number of points on the scale)
labels = str or list of str, optional
	"num", "numeric" or "numbers" or list of actual text labels (e.g., ["not at all", "a bit", "very much"])

<font color="#2196F3" size="5">Returns</font>

response

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
n.scale()
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2



-------
# start()
```python
start(open_window=True)
```
Initialize all the components of Neuropsydia. Always at the beginning of a neuropsydia script.

<font color="#2196F3" size="5">Parameters</font>

open_window = bool
	should it open the pygame's window or close it immediatly (useful when using neuropsydia for something else than experiments, e.g., statistics)

<font color="#2196F3" size="5">Returns</font>

None

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2


-------
# close()
```python
close()
```
A clean closing of all the components of Neuropsydia. Always at the end of a neuropsydia script.

<font color="#2196F3" size="5">Parameters</font>

None

<font color="#2196F3" size="5">Returns</font>

None

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2


-------
# write()
```python
write(text="Write something here", style="body", x=0, y=0, size=1.0, rotate=0, color="black", background=None, outline=False, outline_size=0.1, outline_color="black", allow=None, wait=None, long_text=False, fast=False)
```
Display some text on screen.

<font color="#2196F3" size="5">Parameters</font>

text = str, optional
	The text to display
style = str, optional
	"body", "psychometry", "psychometry_bold", "light", "bold", "title", "subtitle" or "end". Can overwrite other <font color="#2196F3" size="5">Parameters</font> such as position, size or allow. You can also insert the name of a system font, or a path to a specific font you want to use
x = float, optional
	position on x axis (from -10 (left) to 10 (right))
y = float, optional
	position on y axis (from -10 (down) to 10 (up))
size = float, optional
	text size
rotate = int, optional
	angle (0 to 360) by which rotate the text
color = str or tuple, optional
	color of the text. See color() function.
background = str or tuple, optional
	color of the background. See color() function. Default to None
outline = bool, optional [this parameter needs your help]
	outline the text (not perfect for now, the outline is larger for horizontal than for vertical lines)
outline_size = float, optional
	the size of the outlining
outline_color = str or tuple
	color of  the outlining. See color() function
allow = str, optional
	wait until a specific key is pressed (e.g., "ENTER", or "any" for any). Default to None
long_text = bool, optional [this parameter needs your help]
	set to True if you want to write a longer text on multiple lines. Then, the x and y <font color="#2196F3" size="5">Parameters</font> are not working, but you can jump lines using  "\n" in your text (e.g., "\n\n\n here's my long text\n do you like it?"). Some other <font color="#2196F3" size="5">Parameters</font> are not compatible.
fast = some <font color="#2196F3" size="5">Parameters</font> are toggled off, but faster.

<font color="#2196F3" size="5">Returns</font>

None

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
n.write("here's my  title", style = "title")
n.write("here's my  text", font_color = "red")
n.write("press ENTER to quit", style = "end")
n.close()

<font color="#2196F3" size="5">Authors</font>

Léo Dutriaux, Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- time


-------
# ask()
```python
ask(text="Write something here:", style='light', x=-8, y=0, order=None, size=1.0, color="black", background="white", hide=False, detach_question=False, question_style="light", question_x=0, question_y=0, question_size=1, question_color="black", question_long_text=False, allow=None, allow_length=None, allow_type=None, allow_max=None):
```
Display a question and get the subject's answer.

<font color="#2196F3" size="5">Parameters</font>

text = str, optional
	the question to be displayed
style = str, optional
	"body", "light" or "bold"
order = int, optional
	for series of questions, sometimes it's easier to just specify the order (1, 2 , 3, ...) and the quetsions will appear one under the other
x = float, optional
	position on x axis (from -10 (left) to 10 (right))
y = float, optional
	position on y axis (from -10 (down) to 10 (up))
size = float, optional
	text size
color = str or tuple, optional
	color of the text. See color() function.
background = str or tuple, optional
	color of the background. See color() function. Default to None
hide = bool, optional
	display "****" (stars) instead of the actual answer
detach_question = bool, optional
	if set to true, then the question can be manipulated separately using the <font color="#2196F3" size="5">Parameters</font> below
- question_style = see style arg in write()
- question_x = see x arg in write()
- question_y = see y arg in write()
- question_size = see size arg in write()
- question_color = see color arg in write()
- question_long_text = see long_text arg in write()
allow = list, optional
	only allow specific answers (e.g., "yes" or "no")
allow_length = int, optional
	allow only a specific answer length
allow_type = str, optional
	"str", "int" or "float", allow only this specific type
allow_max = int, optional
	when numeric answer, set a maximum

<font color="#2196F3" size="5">Returns</font>

str
	answer

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start()
response = n.ask("Hey, you're good?")
print(response)
n.close()

<font color="#2196F3" size="5">Authors</font>

Léo Dutriaux, Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- time



-------
# choice()
```python
choice(choices=["Yes","No"], write_choices=True, overwrite_choices_display=None, choices_size=1.0, choices_color="black", y=0, height=-5, boxes_space=0.5, boxes_background='white', boxes_edge_color="black", boxes_edge_size=3, confirm_edge_color="orange", confirm_edge_size=3, help_list=None, help_background="lightgrey", title=None, title_position="default", title_x=-7.5, title_space=0.75, pictures=None, pictures_size=0.5):
```
Help incomplete, sorry.

<font color="#2196F3" size="5">Parameters</font>

NA

<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- time


-------
# preload()
```python
preload(file, x=0, y=0, cache=None, path='', extension='', size=1.0, fullscreen=False, rotate=0, scramble=False, compress=False, compression=0, opacity=100, key=None):
```
Preload images.

<font color="#2196F3" size="5">Parameters</font>

NA

<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- PIL



-------
# image()
```python
image(file, x=0, y=0, cache=None, path='', extension='', size = 1.0, fullscreen=False, rotate=0, scramble=False, background=None, compress=False, compression=0, allow=None, wait=None, opacity=100)
```
Help incomplete, sorry.

<font color="#2196F3" size="5">Parameters</font>

NA

<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski, Léo Dutriaux

<font color="#2196F3" size="5">Dependencies</font>

- pygame 1.9.2
- PIL
- time

-------
# read_data()
```python
read_data(filename, path="", localization="US")
```
Load the datafile into a pandas' dataframe.

<font color="#2196F3" size="5">Parameters</font>

NA

<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pandas


-------
# select_variables()
```python
select_variables(df, dtype="numeric")
```
Keep a specific type subset of your pandas dataframe.

<font color="#2196F3" size="5">Parameters</font>

df = pandas.DataFrame object
	a pandas dataframe
dtype = str, optional
	"numeric" or "factor". Note that right now, entering something else than "numeric" will just result in a dataframe with all non-numeric variables.

<font color="#2196F3" size="5">Returns</font>

subset = pandas.DataFrame object
	the subsetted dataframe

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pandas



-------
# t_test()
```python
t_test(var1, var2, data=None, var1_name="VARIABLE-1", var2_name="VARIABLE-2", independent=False, output=True, plot=True, bayesian=False, bootstrapped=True, N_resamples=1000, significance_treshold=0.05)
```
Performs a t-test.

<font color="#2196F3" size="5">Parameters</font>

var1 = list/array
	a numeric variable
var2 = list/array
	either a numeric variable or a factor (with 2 levels)
var1_name = str
	name of the first variable
var2_name = str
	name of the second variable
independent = bool
	pairwise or two-sample. Is adjusted automatically depending on the type of var2.
output = bool
	if True, print the summary using APA6 style
plot = bool
	if True, open a html window with a distribution plot
bayesian = bool
	feature not implemented yet
bootstrapped = bool
	if False, do a "traditional" t-test (and assumes the usual stuff about normal distrubtion of the data). If True, do a boostrapped t-test (tries to get closer of the true distribution of the data)
N_resamples = int
	the number of resamples in case of a bootstrapped t-test
significance_treshold = float
	under what treshold should the difference be considered as significant

<font color="#2196F3" size="5">Returns</font>

dic
	a result dictionnary containing the different computed values.

<font color="#2196F3" size="5">Example</font>
```python
import numpy as np
import neuropsydia as n
n.start(False)

# generate variables
variable1 = np.random.normal(3, 1, 1000)  # get a normal distribution of size = 1000
variable2 = np.random.normal(2.5, 0.1.2, 1000)  # get a second normal distribution of size = 1000
factor = ["a","a","b","b"] * 250  # get a factor with a and b levels of size = 1000

# paired-samples t-test
n.t_test(var1, var2)

# independent t-test
n.t_test(var1, factor)
```

<font color="#2196F3" size="5">Authors</font>
Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>
- pandas
- numpy
- plotly
- scipy
- pymc3



-------
# dprime()
```python
dprime(n_Hit=None, n_Miss=None, n_FA=None, n_CR=None)
```
Calculates d', beta, c & ad'.

see http://lindeloev.net/?p=29

<font color="#2196F3" size="5">Parameters</font>

NA

<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- scipy



-------
# identify_outliers()
```python
identify_outliers(serie, treshold=3)
```
Identify outliers.

<font color="#2196F3" size="5">Parameters</font>

NA

<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- scipy

-------
# z_score()
```python
z_score(raw_score)
```
Transform an numeric pandas' array or list into Z scores (scaled and centered scores).

<font color="#2196F3" size="5">Parameters</font>

NA

<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- scipy

-------
# bayesian_model()
```python
bayesian_model(y, x, data=None, correlation=False, family="Normal", robust = True, samples = 1000, plot_posterior=True, plot_regression=True, plot_samples = "default", print_summary=True, alpha = 0.05):
```
Performs a Bayesian regression.

<font color="#2196F3" size="5">Parameters</font>

NA

<font color="#2196F3" size="5">Returns</font>

NA

<font color="#2196F3" size="5">Example</font>

NA

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pandas
- numpy
- plotly
- scipy
- pymc3


-------
# acq_to_df()
```python
acq_to_df(file, samples=1, unit="ms", method="mean")
```
Format a BIOPAC's AcqKnowledge file into a pandas' dataframe.

<font color="#2196F3" size="5">Parameters</font>

file =  str
	the path of a BIOPAC's AcqKnowledge file
samples = int
	the final frequency (samples/unit)
unit = str
	"ms" or "s", the final frequency
method = str
	"mean" or "pad", resampling method

<font color="#2196F3" size="5">Returns</font>

df = pandas.DataFrame()
	the dataframe


<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start(False)
>>>
df = acq_to_df('file.acq')

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- pandas
- bioread
- datetime



-------
# process_EDA()
```python
process_EDA(EDA_raw, frequency, tau0=2., tau1=0.7, delta_knot=10., alpha=0.4, gamma=1e-2, solver=None, options={'reltol':1e-9})
```
A convex optimization approach to electrodermal activity processing (CVXEDA)

This function implements the cvxEDA algorithm described in "cvxEDA: a
Convex Optimization Approach to Electrodermal Activity Processing" (Greco et al., 2015).

<font color="#2196F3" size="5">Parameters</font>

   EDA_raw
	   observed EDA signal (we recommend normalizing it: EDA_raw = zscore(EDA_raw))
   frequency
	   sampling interval (in seconds) of EDA_raw
   tau0
	   slow time constant of the Bateman function
   tau1
	   fast time constant of the Bateman function
   delta_knot
	   time between knots of the tonic spline function
   alpha
	   penalization for the sparse SMNA driver
   gamma
	   penalization for the tonic spline coefficients
   solver
	   sparse QP solver to be used, see cvxopt.solvers.qp
   options
	   solver options, see http://cvxopt.org/userguide/coneprog.html#algorithm-<font color="#2196F3" size="5">Parameters</font>

<font color="#2196F3" size="5">Returns</font>

   phasic
	   phasic component
   tonic
	   tonic component
   p
	   sparse SMNA driver of phasic component
   l
	   coefficients of tonic spline
   d
	   offset and slope of the linear drift term
   e
	   model residuals
   obj
	   value of objective function being minimized (eq 15 of paper)

<font color="#2196F3" size="5">Authors</font>

Luca Citi (lciti@ieee.org), Alberto Greco

Citation

A Greco, G Valenza, A Lanata, EP Scilingo, and L Citi
"cvxEDA: a Convex Optimization Approach to Electrodermal Activity Processing"
IEEE Transactions on Biomedical Engineering, 2015
DOI: 10.1109/TBME.2015.2474131

<font color="#2196F3" size="5">Dependencies</font>

- cvxopt
- numpy


-------
# extract_peak()
```python
extract_peak(channel_data, value="max", size=0)
```
Exctract the peak (max or min) of one or several channels.

<font color="#2196F3" size="5">Parameters</font>

channel_data = pandas.DataFrame
	Use the `to_data_frame()` method for evoked nme data.
value = str
	"max" or "min".
size = int
	Return an averaged peak from how many points before and after.

<font color="#2196F3" size="5">Returns</font>

tuple
	(peak, time_peak)

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start(False)
>>>
channel_data = evoked.pick_channels(["C1", "C2"]).to_data_frame()
peak, time_peak = extract_peak(channel_data, size=2)
>>>
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- mne > 0.13.0
- numpy
- pandas



-------
# triggers_from_photodiode()
```python
triggers_from_photodiode(photo_channel, names=None, treshold=0.04)
```
Create MNE compatible triggers based on a photodiode channel.

<font color="#2196F3" size="5">Parameters</font>

photo_channel = MNE channel
	The photodiode channel.
names = list
	A list of event names.
treshold = float
	The treshold to select the triggers.

<font color="#2196F3" size="5">Returns</font>

tuple
	(events, event_id)

<font color="#2196F3" size="5">Example</font>

import neuropsydia as n
n.start(False)
>>>
raw = mne.io.read_raw("eeg_file")
photo_channel = raw.copy().pick_channels(['PHOTO'])
events, event_id = triggers_from_photodiode(photo_channel)
raw.add_events(events, stim_channel="STI 014")
>>>
n.close()

<font color="#2196F3" size="5">Authors</font>

Dominique Makowski

<font color="#2196F3" size="5">Dependencies</font>

- mne > 0.13.0
- numpy