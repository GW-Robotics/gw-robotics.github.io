+++
title = "Software Meeting 11/5/16 Notes"
date = "2016-11-05T15:39:28"
tags = ["meeting"]
category = ["control-systems"]
+++
Today's meeting, we basically just wrote some pseudocode for the drivetrain and for a generic sensor. These will be expanded on once more features are needed or when a physical part is given to us. As of right now they are as follows:

drivetrain.txt:
```
ultrasonic [8]
encoder [6]
gyro&acceleratometer
motor [6]

drive (forward_speed, rotation, strafe_speed):
    left motors = forward_speed
    right motors = forward_speed
    
    strafe motors = strafe_speed
    
    if rotation < 0
        clockwise 
        left motors = forward_speed
        right motors = - forward_speed
    else if rotation > 0
        anticlockwise
            right = forward_speed
            left = -forward_speed
            
get ultrasonic in array:
    return value of ultrasonic sensor at index

get encoder in array:
    return value of encoder at index

get gyro rotation:
    return value of gyro at index

get acceleration on axis:
    if x axis:
        TODO: Stuff
    if y axis:
        TODO: Stuff
    if z axis:
        TODO: Stuff
        
        
limit:
    while true
        if absolute value speed < limit
            speed *= limit/speed
        else if abs(speed) > limit
	    speed *= limit/speed
```

sensor.txt:
```
pin_value [2]

# y = mx + b
m
b

get:
return m * voltage + b
```

We also are planning on using Cloud9 for collaborative coding in real-time, however, it seems that you need to input credit card information to use a free service. This is inconvenient for those without a credit card, so an alternative will be looked into.
