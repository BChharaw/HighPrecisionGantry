# Keyboard Typing Gantry Code

This code controls a high-precision 2-axis gantry system three classmates and I designed for typing on a physical keyboard. It utilizes an array of sensors to interact with its environment and perform various tasks, including typing messages and sending SMS texts using the TextNow desktop interface. Check it out at: [Check it out at: https://bchharaw.github.io/#/projects/2axisgantry](https://bchharaw.github.io/#/projects/2axisgantry)

## Features

- **Auto Calibration and Origin Detection**: The gantry system is equipped with auto calibration to establish a precise coordinate system and origin, ensuring accurate positioning and typing accuracy.
- **High Precision and Speed**: The gantry system can perform high-speed and high-precision movements, accurately actuating any desired key on the keyboard with a precision of +/- 5mm.
- **Sensor Interaction**: The system uses touch sensors, a color sensor, an ultrasonic sensor, and a sound sensor to interact with its environment. This enables it to respond to changes in the environment and perform tasks accordingly.
- **Text Typing**: The gantry system can type out text messages on a physical keyboard by navigating the keyboard and typing out the desired text using key indexes.
- **SMS Sending**: The system can send SMS texts using the TextNow desktop interface. It navigates the interface and sends messages once the text has been typed out.
- **Easter Eggs**: The code includes an "easter egg" feature that can be triggered by holding the enter and top brick buttons simultaneously. This feature demonstrates a looping message about contacting the user for their car's extended warranty.

## Functions

- `press_key(int speed)`: Actuates the keypress mechanism at a given speed, considering the system's inertia model for precise positioning.
- `setDatum(int speed)`: Used for the initial calibration of the gantry system. Moves the system to the bottommost corner of the plane and sets that point as the origin (0,0). It also calculates offsets for fine-tuning calibration.
- `driveToKey(int index, int* coordinateX, int* coordinateY, int speed, char* keysArray, int delayKey, int xoffset, int yoffset)`: Drives the gantry to a specific key on the keyboard, considering its relative position. Utilizes multiple checks for different movement scenarios.
- `manualOverride(int speed)`: Provides manual control over the gantry system's movements. Can be used by holding the top and bottom brick buttons while controlling the system's axes using the directional buttons.
- `typeString(int* keysToType, int datumOffsetX, int datumOffsetY, int sizeOfArray)`: Types out a sequence of keys by driving the gantry to each key's position, using the `driveToKey` function.
- `configureAllSensors()`: Configures the various sensors used by the gantry system, including touch sensors, a color sensor, an ultrasonic sensor, and a sound sensor.
- `environmentChecking(int xoffset, int yoffset)`: Checks the environment using the array of sensors and performs specific actions based on the detected conditions, such as typing responses or triggering easter eggs.
- `checkIfAboveAndToLeft`, `checkIfBelowAndToLeft`, `checkIfAboveAndToRight`, `checkIfBelowAndToRight`: These functions are used within the `driveToKey` function to determine the appropriate movement direction based on the key's relative position.
- `easterEgg(int xoffset, int yoffset)`: Executes an easter egg feature if the enter and top brick buttons are held down simultaneously. It demonstrates a looping message about 'contacting the user for their car's extended warranty'.

## Usage

1. **Calibration**: Before using the gantry system, calibrate it using the `setDatum` function. This establishes the coordinate system and origin.

2. **Typing Messages**: To type messages on the keyboard, use the `typeString` function with the desired array of key indexes to type out the text.

3. **SMS Sending**: The system's capabilities for sending SMS texts using the TextNow desktop interface are integrated with the typing process. Once the text is typed using the `typeString` function, the system can navigate the interface and send the message.

4. **Environment Interaction**: The `environmentChecking` function allows the gantry system to interact with its environment using the configured sensors. It can detect conditions such as touch, ambient noise, lighting changes, and obstructions to perform corresponding actions.
