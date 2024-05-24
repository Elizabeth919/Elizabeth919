# It's exactly two minutes!

from pybricks.hubs import PrimeHub
from pybricks.pupdevices import Motor, ColorSensor, UltrasonicSensor, ForceSensor
from pybricks.parameters import Button, Color, Direction, Port, Side, Stop
from pybricks.robotics import DriveBase
from pybricks.tools import wait, StopWatch, multitask, run_task



hub = PrimeHub()

L_Motor = Motor(Port.A, Direction.COUNTERCLOCKWISE)
R_Motor = Motor(Port.B, Direction.CLOCKWISE)
Axle = 110.0
Wheel_Diameter = 50
Base = DriveBase(L_Motor, R_Motor, wheel_diameter=Wheel_Diameter, axle_track=Axle)

arm = Motor(Port.D, Direction.COUNTERCLOCKWISE)
back = Motor(Port.F, Direction.COUNTERCLOCKWISE)
backarm = Motor(Port.C, Direction.COUNTERCLOCKWISE)

def hold_cable():
    back.run_angle(100,-75)
def release_cable():
    back.run_angle(100,75)
def lift_arm():
    arm.run_angle(30,60)
def lower_arm():
    arm.run_angle(30,-60)

Base.use_gyro(True)

Ultrasound = UltrasonicSensor(Port.E)
#Ultrasoundd = UltrasonicSensor(Port.F)


#Color = CS_Right.color()
Distance = Ultrasound.distance()
#Distancee = Ultrasoundd.distance() # This is the distance between the sensor and the flower.
issue = True
print(Distance)
#print(Distancee)

Ducks = [] # This list is for tracking down where the ducks are.

# Lines 42 - 73 are situations

Base.settings()
'''
def Situation_1():
    Base.straight(325)
    Base.turn(90)
    Base.straight(-90)
    arm.run_time(-100, 1000)
    arm.run_angle(30,8)
    Base.straight(160)
    Base.turn(-90)
    Base.straight(-1060)
    Base.turn(90)
    #at garden

def Situation_2():
    Base.straight(245)
    Base.turn(90)
    Base.straight(-90)
    arm.run_time(-100, 1000)
    arm.run_angle(30,8)
    Base.straight(160)
    Base.turn(-90)
    Base.straight(-975)
    Base.turn(90)

def Situation_3():
    Base.straight(160)
    Base.turn(90)
    Base.straight(-90)
    arm.run_time(-100, 1000)
    arm.run_angle(30,8)
    Base.straight(160)
    Base.turn(-90)
    Base.straight(-890)
    Base.turn(90)

def StartToGarden():
    Base.reset()
    arm.run_angle(100,-80)
    arm.run_angle(30,60,wait=False)
    Base.turn(-20)
    Base.straight(-190) #180
    Base.turn(21)
    Base.straight(-50)

# 86 - 93 will be explained if needed

    for k in range(6): # Repeat 6 times
        Base.straight(-80)
        wait(10)
        Distance = Ultrasound.distance() # Reset the variable
        print(Distance) # Check to see what the ultrasound is saying
        if Distance > 150: # If Disance is greater than 120 (Duck is spotted)
            Ducks.append(k+1) # Add the number to the list.
    
    print(Ducks) # See what ducks were spotted

# 97 - 140 is saying what happens for each of the 15 situations.

    if Ducks == [1, 2]:
        Situation_2()

    if Ducks == [1, 3]:
        Situation_2()

    if Ducks == [1, 4]:
        Situation_1()

    if Ducks == [1, 5]:
        Situation_1()

    if Ducks == [1, 6]:
        Situation_1()

    if Ducks == [2, 3]:
        Situation_3()

    if Ducks == [2, 4]:
        Situation_1()

    if Ducks == [2, 5]:
        Situation_1()

    if Ducks == [2, 6]:
        Situation_1()

    if Ducks == [3, 4]:
        Situation_1()

    if Ducks == [3, 5]:
        Situation_1()

    if Ducks == [3, 6]:
        Situation_1()

    if Ducks == [4, 5]:
        Situation_2()

    if Ducks == [4, 6]:
        Situation_2()

    if Ducks == [5, 6]:
        Situation_3()
    
    if len(Ducks) != 2:
        Situation_1()

# Older code

    #arm.run_angle(30,-80)
    #Base.straight(150)
    #arm.run_angle(30,7)
    #Base.turn(-87)
    #print(Base.angle())
    #Base.straight(-1040)
    #Base.turn(90)


def GardenToBike():
    Base.straight(-240)
    Base.straight(80)
    Base.straight(-40)
    lift_arm()
    Base.straight(245)
    Base.turn(90)
    Base.drive(150, 0)
    wait(3000)
    Base.straight(-70)
    release_cable()
    #released cable
    Base.straight(-450)
    Base.turn(-90)
    Base.straight(500)
    Base.straight(-650)
    Base.turn(90)
    # Where second run should start
    Base.straight(-400) #-400
    Base.turn(-45)
    Base.straight(-130)
    Base.turn(45)
    back.run_angle(100, -65, wait=False)
    # Catching the plants & duck
    Base.straight(-430) # was 830
    for k in range(4):
        L_Motor.run_angle(1000,-100, wait=False)
        R_Motor.run_angle(1000,-35)
        R_Motor.run_angle(1000,-100, wait=False)
        L_Motor.run_angle(1000,-35)
    Base.turn(-20)
    Base.straight(-115)
    lower_arm()
    back.run_angle(100,75)
    Base.use_gyro(False)
    Base.straight(-430)
'''

def HomeToHouse():
    Base.settings(turn_rate=100)
    Base.reset()
    Base.use_gyro(True)
    Base.straight(250)
    Base.turn(85)
    Base.straight(40)
    Base.straight(-450)
    #turning to hook onto the green starters
    Base.turn(96)
    backarm.run_angle(50,-30, wait=False)
    back.run_angle(50, -85)
    back.run_angle(50, 30)
    Base.drive(100, 0)
    wait(1200)
    Base.stop()
    back.run_angle(50, 60)
    backarm.run_angle(50, 25)
    #Hooked onto the green starters
    Base.straight(-150)
    Base.turn(30)
    Base.straight(-500)
    Base.turn(60)
    Base.straight(130)
    hold_cable()
    Base.settings(turn_rate=60)
    Base.straight(-35)
    Base.turn(15)
    back.run_angle(50, 15)
    Base.straight(47)
    Base.settings(turn_rate=100)
    back.run_angle(50,50)
    Base.turn(10)
    Base.straight(20)
    
    '''
    #released first green starter
    Base.straight(-150)
    Base.turn(40)
    Base.straight(60)
    backarm.run_angle(50, -35)
    Base.settings(turn_rate=60)
    Base.straight(40)
    Base.straight(-100)
    backarm.run_angle(50, -20)
    Base.straight(80)
    Base.straight(-100)
    backarm.run_angle(50, 20)
    Base.turn(45)
    #Base.turn(10)
    #Base.straight(-70)
    #backarm.run_angle(50, 40)
    #Base.turn(45)
    #backarm.run_angle(50, -40)
    #Base.turn(-65)
    Base.settings(turn_rate=100)
    Base.straight(60)
    Base.turn(-70)
    Base.straight(-200)
    Base.turn(45)
    Base.straight(240)
    hold_cable()
    Base.straight(-200)
    release_cable()
    Base.turn(40)
    Base.straight(620)
    Base.turn(70)
    Base.straight(-540)
    Base.turn(45)
    Base.straight(-240)
    Base.straight(80)
    Base.straight(-40)
    lift_arm()


    #Base.straight(-200)
    #Base.turn(-90)
    #Base.straight(-500)
    #Base.straight(195)
    #Base.turn(92)
    #Base.straight(-700)
    #Base.turn(-90)
    #Base.straight(-200)
    #Base.straight(80)
    #Base.straight(-40)
    #lift_arm()
    #Base.straight(120)
    #Base.turn(92)
    #Base.straight(1200)




    `
'''
#StartToGarden()
#GardenToBike()
HomeToHouse()
