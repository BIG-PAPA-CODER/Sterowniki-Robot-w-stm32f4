# STM32 Maze Tilt Game

This project is a tilt-controlled maze game implemented on the [STM32F429I Discovery Board](https://www.st.com/en/evaluation-tools/32f429idiscovery.html). It uses the built-in LCD screen and MEMS gyroscope to allow players to guide a virtual ball through a maze by physically tilting the board.

## Features

- Tilt-controlled ball movement via gyroscope
- Real-time physics integration using angular velocity
- Collision detection against walls and hazards
- Visual maze rendered on the LCD display
- Restart mechanism upon hitting obstacles
- Arrows and boundaries rendered with clear color-coded visuals
- Game-over screen with reset delay

## Hardware Requirements

- STM32F429I Discovery Board
- USB Debug/Power cable
- STM32CubeIDE or Keil uVision (for flashing/debugging)
- Optionally: ST-LINK debugger

## Software Components

- STM32 HAL Drivers
- Gyroscope driver (`stm32f429i_discovery_gyroscope.h`)
- BSP LCD API for graphical rendering
- Math library for trigonometric functions
- Custom modules: `color2.h`, `save.h`, `maze_1.h`

## How It Works

- The gyroscope measures angular velocity in X and Y axes.
- Angular velocity is integrated over time to calculate orientation angles.
- Ball position is updated based on these angles and drawn on the LCD.
- A bitmap and hardcoded line paths define walls and obstacles.
- If the ball hits a "hole", a **YOU LOST!** message is displayed and the game resets after a delay.

## Game Logic

- Ball position is updated every loop cycle based on tilt.
- `check_hole()` checks if the ball has hit a losing area.
- `collision()` prevents the ball from passing through walls.
- `draw_all()` resets the game screen, redrawing maze and holes.
- Visual cues like arrows indicate movement directions.
