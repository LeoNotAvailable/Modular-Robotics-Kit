# Modular-Robotics-Kit
This is a long-term project that aims to become a complete kit of different modules. Ones will just be sensors, others actuators, and others will manage logic. And the user will program them through an app without code. They are for IoT and automation, as well as for learning event-based conditionals. It is really educational and visual because every module executes a very defined and limited function, so each one has its role, without depending on a central programming.

The project has this elements:


## - Modules:
They will be programmed in a ESP32, possibly the ESP32 SuperMini (C3). They will communitcate between them through WiFi or ESP-NOW (I have to make some tests). They'll be programmed in Arduino, first I've got to learn how to code with it...


## -App:
In first term, should be free. I'll develop it first with Python (tkinter) as it is what I control, but later I'll implement it possibly with TypeScrit, trying to create a web version as well.

As you can see, I only code with Python for now, so there's still a long way until I can achieve this objective. I'll probably be posting the progress of my search in X and Reddit under my same username.


## This is my plan to acomplish this:
- Design the whole environment, how the modules will communicate between them and with the app, how they'll manage their conditions and how to make them easy and intuitive to understand and edit for non especialized users, the structuration of every communication, internal states, logs... (mostly done)
- Write a code in Python that sims to be the module, with the specific functions per module empty (as there's no hardware-related code yet), as well as BLE and WiFi code. The objective is to find a structure that allows to copy-paste to every module, so their behaviour only changes with what they've got in their memories (module type, conditions...), and make it so modular and scalable that I'm able to add any new module without touching most of it. (mostly done)
- "Pass" the Python code to Arduino, filling the communication functions as well as those that define the behaviour of basic modules (this will be a major problem, as I've just found how complicated C++ can be, and will take much longer than I thought, my most complicated project with robotics was made with micro Python... I'll have to test basic functions and learn the language before I'm able to acomplish this).
- Develop the App with all its functions, but with Python, and test if it works well (it's able to connect to every module, make changes in their memories...). Test is first with a normal ESP32, later with the tiny one (there must be soldering) simulating a actuator.
- Design an MVP; the two logic modules, some simple actuators (as a LED string and a sound emmiter) and sensors (movement, light), and pass them the code (here I'll start to learn how to 3D print, so the progress will be slow as well, and decide what every module will have (some leds to indicate states to the user, how the module will be powered...), as well as designing a general base for all the modules, and how to adapt it to every one).
- Only once the Python app works effortlessly, and every module works properly as I want them to, start learning how to program with Typescript and figure out the best way of approaching to the final app I want.
- Develop the whole app. It will change its aspect depending on the characteristics of the module it's connected to, so I need a code enough general to manage every possible interaction, without having to rewrite it for every module. So in the end, I just have to design the UI for every module. This will be another big step, as I need to learn how to interact with the bluetooth functions of the mobile, how to develop professionaly an app, how to commercialize it...
- And, if I manage to get to this point, slowly design all of the modules that I ideated, creating its 3D design, the specific code for every one, as well as the UI for the app... if the previous work is good enough, this procedure should not take much effort.

As you can see, this is an ambitious project. My honest objective, is to build the MVP I want with no more than 5 modules, and the app in Python, at which point I'll be really happy. If then I go on, and manage to build the whole app professionaly, create more modules, and even sell this, then better for me, but I don't expect to do that.


## General functioning of the project:

As I said, this project consist in create a environment where we can add or take modules without braking the funcitioning of the rest. It will be an event-based model, as the sensor modules will emit events "to the air" depending on what they observe, and the actuator and logic modules will receive them, decide if ignoring them depending on internal conditions (this is what the app will configure), and executing especific functions (emiting as well events).

As you can see, the idea is to have an environment that doesn't depend to any central logic, as all the conditions are managed and configure inside of every module, making the project more scalable and modular, as well as much more intuitive and visual when learning with it. A central brain would admit to configure the whole system through one elemnt, but that would make the system much more difficult to understand and configure (as you would have to assign not just the conditions that trigger an action, but the module the action will be executed in, and every module has specific actions. Also, it would overload one moudle, limiting the extension of the environment). The actual model allows to create simple conditions and responses without depending on any element, one of the objectives, but also leaves space to add more complexity to the system with the logic moudles, always keeping it intuitive. In this format, allows its use from really simple usage, from understanding simple conditions and responses (if it happens this --> execute this) to really complex conditions (if you receive X times this event in this temporary frame, send this event every minute until this happens), depending always on the user and the use it wants to give to the modules. Also, allows the system to be extremely resilient (if you take a module, the system holds on) and "infinitely" scalable, as you can add modules without overloading a central one, without them having to be near to a central node, and even permiting the use of logic modules as extenders of the system, repeating events just like a WiFi repeater and allowing long-distance communication, while the other mode is extremely limited in range.

As every module needs configuration, this will be done through the app. One of the main objectives it's to end up with an app so intuitive that can be used for children with the modules, but allows to create those complex conditionals with the logic modules. If it's hard to combine those functionalities in the same app, it will be separated in a "educational mode" and "technical mode" or something like that.
One example of how that would be is that in the first one, the user will only be able to set something like "if light is received, do this", and the second one will allow "if light is received from de module (id) between the values M and N, do this".
