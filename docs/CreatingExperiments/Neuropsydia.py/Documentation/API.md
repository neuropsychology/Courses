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