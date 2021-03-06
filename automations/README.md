# Automations

## Publishers and subscribers

<div align="center">
    <figure>
        <div>
            <img src="https://media.giphy.com/media/CmFMWpEa4IFtS/giphy.gif" alt="Ticket clerk hidden inside a turnstile">
        </div>
        <figcaption>
            <p><strong>Pub/sub!</strong></p>
        </figcaption>
    </figure>
</div>

To prevent [spaghetti code](https://www.youtube.com/watch?v=vZA6h7djGmc) in automations as this project grows, I employ a [publish–subscribe pattern](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) (kind of a lightweight [mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) where some automations will trigger changes on [`/misc/input_booleans.yaml`](../misc/input_booleans.yaml) and [`/misc/variables.yaml`](../misc/variables.yaml) while others listen to those changes.

For example, one push of a button will lead to enabling the **night mode** by setting the relevant boolean to _true_. Every room has an automation that listens to changes on that **night mode** boolean, and is responsible for turning devices on and off accordingly. This makes every room reactive to one central direction, without having to maintain a monolithic `/scripts/go_to_sleep.yaml` that lists all the devices that must be acted upon.

It's a bit like a boss giving orders to managers, and letting them figure out how to best accomplish these goals based on what they know about their respective teams. Less micromanagement = smarter teams.

To help clarify and document this pattern in the files' comments, automations annotated with **@publish** are the ones that issue orders, and those annotated with **@subscribe** are listening for such orders. Some automations will be both **publishers** and **subscribers** of different orders.

<div align="center">
    <figure>
        <div>
            <a href="https://www.youtube.com/watch?v=vZA6h7djGmc" title="Understanding spaghetti code"><img src="https://media.giphy.com/media/IVoBdwlksSq7m/giphy.gif" alt="Someone adding a meatball to an already overflowing spaghetti takeaway container"></a>
        </div>
        <figcaption>
            <p><strong><a href="https://www.youtube.com/watch?v=vZA6h7djGmc" title="Understanding spaghetti code">Understanding spaghetti code.</a></strong></p>
        </figcaption>
    </figure>
</div>


## Folders

### [`📂 ./areas/`](areas)

Contains automations related to smart areas.


### [`📂 ./devices/`](devices)

For automations related to individual smart devices.


### [`📂 ./modes/`](modes)

For all automations related to modes.


## Files

### [`💡️ ./cct_lifx.yaml`](cct_lifx.yaml)

Adjust LIFX bulbs colour temperature (CCT) based on cyrcadian rythm.


### [`💡️ ./cct_limitlessled.yaml`](cct_limitlessled.yaml)

Adjust LimitlessLED/MiLight colour temperature (CCT) based on cyrcadian rythm.


### [`🗣️️ ./daily_greeting.yaml`](daily_greeting.yaml)

Greet the day with a daily briefing.


### [`🚪 ./doors_notify.yaml`](doors_notify.yaml)

Warn someone if a door was left open for too long.


### [`🚪️ ./doors_verify.yaml`](doors_verify.yaml)

Verify the state of all external doors.


### [`🚪️ ./front_door_notify.yaml`](front_door_notify.yaml)

Warn whenever the front door is opening or closing.


### [`⚗️️ ./humidity_notify.yaml`](humidity_notify.yaml)

Check if humidity is too high or too low.


### [`🔆️ ./scene_daylight.yaml`](scene_daylight.yaml)

Toggle the daylight scene.


### [`👾 ./scene_gaming.yaml`](scene_gaming.yaml)

Toggle the gaming scene.


### [`💏️ ./scene_romantic.yaml`](scene_romantic.yaml)

Toggle the romantic scene.


### [`🔘️️ ./scene_select.yaml`](scene_select.yaml)

Manually select a global scene.


### [`🖐 ./tamper_notify.yaml`](tamper_notify.yaml)

Warn someone if the tamper flag has changed.


### [`🌈️ ./theme_auto.yaml`](theme_auto.yaml)

Set theme to "normal" during daytime and "dark" during night mode.


### [`🆕️ ./update_notify.yaml`](update_notify.yaml)

Notify when a new version of Home Assistant is available.


### [`⏰️ ./wake_up.yaml`](wake_up.yaml)

Wake up all devices.


## Customization

The bulk of the customization is done in [`/customize.yaml`](../customize.yaml) and [`/customize_glob.yaml`](../customize_glob.yaml).

The looks of many state cards depend on Custom UI and other templates in [`/www/custom_ui/`](../www/custom_ui).
