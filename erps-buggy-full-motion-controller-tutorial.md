### @activities true
### @explicitHints true

# ERPS STEM WEEK :: Motorised Buggy - Full Radio

## Introduction
### Introduction Step @unplugged
Let's extend our simple buggy project which just moves it forwards and backwards, and get some
left and right turns happening!

If you haven't already, create the code for the forwards-and-backwards only controller: [Simple controller](https://makecode.microbit.org/#tutorial:github:niaxotim/erps-buggy-simple-radio-controlled-sender/erps-buggy-radio-controlled-simple-sender-tutorial)

Let's use our radio skills to *remote control* our buggy with the game controller, but with some more directions this time!

![Motorised Buggy](https://raw.githubusercontent.com/niaxotim/erps-buggy-full-motion-controller/master/assets/buggy_controller.png)

## Putting our buggy together!
### Assembling the pieces @unplugged
Before we start, make sure your buggy has been assembled. There are lots of sensors we *can* connect, but for now, just make
sure that the tyres are on the wheels, and that the wheels are connected to the motors.  
    
Oh, and don't forget some AA batteries too!

![Buggy Key Features](https://raw.githubusercontent.com/niaxotim/erps-buggy-full-motion-controller/master/assets/features.png)


## Setting up our radio
### Step 1
Following on from using our existing code, make sure that your radio channel is set correctly, using a ``||radio:radio set group||`` block - make sure you set it to the channel assigned to you!  

#### ~ tutorialhint
```blocks
radio.setGroup(255)
```

## Setting our speed
### Step 2
In our original code, we sent the speed for our buggy with each transmission on the radio, but had to repeat ourselves
in our code each time.  

This time, we're going to replace doing that with a *variable* instead. Create a new variable called *speed*, and underneath
our radio channel block, use a variable block to set it to "50".

#### ~ tutorialhint
```blocks
radio.setGroup(255)
let speed = 50
```

### Step 3
Taking our existing code for sending the radio transmissions, let's replace everywhere that we've
'hard coded' our speed with our new variable block.  

Take out the "50" from each part of our if-statement, and replace it with the 'speed' variable block.

#### ~ tutorialhint
```blocks
basic.forever(function () {
    if (Kitronik_Game_Controller.buttonIsPressed(Kitronik_Game_Controller.ControllerButtonPins.Fire1)) {
        radio.sendValue("forwards", speed)
    } else if (Kitronik_Game_Controller.buttonIsPressed(Kitronik_Game_Controller.ControllerButtonPins.Fire2)) {
        radio.sendValue("back", speed)
    } else {
        radio.sendValue("stop", 0)
    }
})
```

## New directions
### Step 4
Now to move left or right, we'll need to use some more buttons on our controller. That means some more parts to
our if-statement!  

Click on the '+' to create 2 more *else-if* statements in our block. Then drag a 
``||Kitronik_Game_Controller:button Joypad Left (P12) is pressed||`` block in to the first new section.  

In the second new section, drag a ``||Kitronik_Game_Controller:button Joypad Right (P13) is pressed||`` block.

#### ~ tutorialhint
```blocks
basic.forever(function () {
    if (Kitronik_Game_Controller.buttonIsPressed(Kitronik_Game_Controller.ControllerButtonPins.Fire1)) {
        radio.sendValue("forwards", speed)
    } else if (Kitronik_Game_Controller.buttonIsPressed(Kitronik_Game_Controller.ControllerButtonPins.Fire2)) {
        radio.sendValue("back", speed)
    } else if (Kitronik_Game_Controller.buttonIsPressed(Kitronik_Game_Controller.ControllerButtonPins.Left)) {
    } else if (Kitronik_Game_Controller.buttonIsPressed(Kitronik_Game_Controller.ControllerButtonPins.Right)) {
    } else {
        radio.sendValue("stop", 0)
    }
})
```

### Step 5
Now we need to send the commands for 'left' and 'right' to the buggy.  

Duplicate one of your 'forwards' or 'back' transmission blocks twice, move one in to each of your new
left and right statements, and change the 'key' command to 'left' and 'right'.  

#### ~ tutorialhint
```blocks
basic.forever(function () {
    if (Kitronik_Game_Controller.buttonIsPressed(Kitronik_Game_Controller.ControllerButtonPins.Fire1)) {
        radio.sendValue("forwards", speed)
    } else if (Kitronik_Game_Controller.buttonIsPressed(Kitronik_Game_Controller.ControllerButtonPins.Fire2)) {
        radio.sendValue("back", speed)
    } else if (Kitronik_Game_Controller.buttonIsPressed(Kitronik_Game_Controller.ControllerButtonPins.Left)) {
        radio.sendValue("left", speed)
    } else if (Kitronik_Game_Controller.buttonIsPressed(Kitronik_Game_Controller.ControllerButtonPins.Right)) {
        radio.sendValue("right", speed)
    } else {
        radio.sendValue("stop", 0)
    }
})
```

### Step 6
That's it! You're ready to go!  

If you want to, perhaps think about some of the spare buttons you have, and check out the other blocks available for your buggy.  

Hint: the buggy as a 'buzzer' to act as a car horn, and even lights!

### Step 7
Connect your BBC micro:bit and click ``|Download|`` to transfer your code.  

Put your micro:bit in to your game controller, making sure it faces forwards. Also put some AA batteries in the back!  

The next thing we need to do is write and update to the code to receive the signals from our controller...

### Buggy Full Motion Controller Tutorial Complete @unplugged
Great work! You should now have a working radio controller for your buggy with a few more commands. But you'll need to complete
the matching tutorial to code the receiver to do something with them!

![Great job](https://raw.githubusercontent.com/niaxotim/erps-buggy-full-motion-controller/master/assets/great_job.png)
