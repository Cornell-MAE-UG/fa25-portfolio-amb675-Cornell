---
layout: project
title: Mechantronics Robot
description: Robot for classwide robot competition
image: /assets/images/HT_Problem_set_3.png
---
Our Final Project in Mechantronics was to built a bot to compete in a robotics competition at the end of the semester! The Goal was to collect as many 1 inch cubes in your robots perimeter as possible within a minute. 


## 1. Robot Design and Strategy Overview.

We aimed to be simple in our design and strategy. Our strategy was to open ourselves up to being as wide as possible with a 3D printed claw, then to quickly collect in a simple path from one side of the middle to the other. At the start of the match, we wrote our code to open our claw, move forward until the left black border was detected, turn until the opposite color was detected, and then turn again. This allowed our robot to follow a path between the intersection of the blue and yellow section, until the black border was detected, where we would then turn right to go back to our original color section. 
For our robot, we primarily designed an L-shaped claw that would open us to the maximum legal dimensions upon start. Our claw was composed of two arms and symmetric on either side, with one long thin arm being mounted on one positional servo placed in front of our wheels. We utilized the color sensor to detect blue and yellow and two QTI sensors to detect black at the left or right side of our robot. We bought and utilized the bigger wheels from the lab to increase our speed.


## 2. Design Process Reflection. 

Our team decided to design our robot following the specification with the milestones. We tended to procrastinate in our design process, such as starting a milestone the week it was due. Oftentimes, we would run into issues with our code not working, which would then delay progress and led to us completing the milestones near or on the day it was due. We think we should have CADed sooner and spent more time iterating our mechanical design and code. Many of our problems stemmed from rushed or a lack of testing (questionable color detection, a very simple code strategy, and very very flimsy claws). This led to us making last minute changes, such as taping cardboard onto our claws to strengthen them, which limited our time to test fully. 

## 3. Competition Analysis. 

We did not do that well during competition and lost all our matches. Our strategy was very common which meant oftentimes our robot would interact with another robot in the block collection section. Our claws were very flimsy and would get frequently caught on the opposing team’s bots. This would lead to us losing the blocks we managed to collect, since they were either pushed away or ended up in the other robot’s perimeter. Because our design was flimsy and our bot was light we also frequently got pushed off the mat or our claw folded back to an unusable position. 
A strength was our wide claw, which collect many blocks at a single time, but in contrast the flimsy structure of it was also our primary weakness. Other weaknesses was our color detection and turning, since sometimes the blue floor would be mistaken as black or the rotation to turn 90 degrees would veer to wide, and therefore minimizing our time in the block collection section. 

## 4. Conclusions. 

Overall, our team enjoyed this experience of being able to design a robot from start to finish. We enjoyed being able to brainstorm and strategize together to create our robot design, and were able to accomplish all aspects of the milestones and project together since we collaborated for all mechanical, electrical, and software aspects. While we wish our robot could have performed better, we also recognize that as a team of 2 it was difficult to allocate time specifically to testing and iteration since our primary focuses throughout the week was to accomplish the milestones.
If we could do the project over again, we would recommend starting early with CAD and writing the code for your strategy. We only began CAD for milestone 4, which was too late in our opinion since the turn around from obtaining the RPL parts and implementing our claws into our CAD was very slim. Had we started earlier, we would have had more time to potentially redesign our claws and improve our code. In addition, we advise future students to not procrastinate and start the milestones as early as possible. We often got stressed when our code or claw were not working the day the milestone was due, and saw a lot of other teams in a similar dilemma. Avoiding these situations would help mitigate stress and also ensure a fun time during the robot project!



## Bill of Materials

| Component | Type | Quantity | Cost |
|---|---|---|---|
| Large Wheels | Purchased | 2 | $4.00 |
| Positional Servo | Purchased | 1 | $3.00 |
| Servo Mounts | 3D Printed | 2 | $3.32 |
| Claws | 3D Printed | 2 | $7.20 |
| **Total** |  |  | **$17.52** |



<div style="text-align:center; margin:20px 0;">
  <img src="{{ '/assets/images/HT_Problem_set_3.png' | relative_url }}"
       style="max-width: 600px; width: 100%; display:block; margin:auto;" />
</div> 


<a href="{{ '/assets/Files/HeatTransfer-Problem_set_3.pdf' | relative_url }}"
style="
display:inline-block;
padding:10px 18px;
background:#b31b1b;
color:white;
text-decoration:none;
border-radius:6px;
font-weight:600;
margin-top:10px;">
Download Homework PDF
</a>
