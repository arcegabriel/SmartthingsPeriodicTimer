# SmartthingsPeriodicTimer
This solution provides timer functionality that can trigger routines in SmartThings. Currently there is not a permanent /periodic timer functionality

SmartThings allows the user to trigger routines for different reasons. A certain time of day for example. There is no trigger for "Do X every 10 minutes". This solves that
The steps:
1. Install vEdge Creator on SmartThings https://community.smartthings.com/t/st-edge-vedge-creator-a-virtual-device-generator-for-end-users/231786 (See instructions there)
2. Create a virtual Switch (See instructions there) and call it (for example "Timer 5min")
![Screenshot_20221115-203036](https://user-images.githubusercontent.com/24392647/202061458-57c14aa4-6e7c-4dcc-a7e6-9edb7bedbe6e.png)
3. Create a Routine called Reset 5min Timer
![Screenshot_20221115-203058](https://user-images.githubusercontent.com/24392647/202061559-2ec679b0-4adc-49f7-8ea1-79834d852bd2.png)
4. Create a Routine called Switch Timer 1
![Screenshot_20221115-203105](https://user-images.githubusercontent.com/24392647/202061642-232878fb-0ef9-4e5b-8add-d46e55602693.png)
5. Create a Routine called Switch Timer 2
![Screenshot_20221115-203101](https://user-images.githubusercontent.com/24392647/202061665-7e9485a7-e4c9-4544-939f-72030ae06104.png)
6. Create an account on sharptools.io and link it to your smartthings
7. Create a Rule called Timer 5min
![rule_screenshot](https://user-images.githubusercontent.com/24392647/202061920-e7d87d9f-6d33-41fd-98b4-bedea2835b4a.png)
8. Create a Rule called SmartThings 5m Timer Checkin
![rule_screenshot (1)](https://user-images.githubusercontent.com/24392647/202062123-6fed0ab0-297e-4786-976a-c30c97584abe.png)

When you trigger the switch will turn on / off every 5 minutes. There additional steps are there to account for ocassionally the trigger to stop for example a power outage or a race condition:
1. The routine Reset 5min timer will kick off once a day
2. More so sharptools has a 5 min timer on its end and will be monitoring if smartthings is updating its timer. If its not, it will restart the timer on smartthings remotely. Sharoptools on its side also has a trigger to re-start its own timmer if it stops
