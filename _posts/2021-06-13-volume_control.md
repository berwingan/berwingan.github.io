---
layout: post
title: "Volume Control with CV2 and Mediapipe"
author: "Berwin Gan "
categories: projects
tags: [projects]
image: volume_control.png
---

The apple touch bar is great. It lets me slide my fingers to adjust the brightness and volumne and stuff. But the thing is, sometimes its a little too far, especially if I use an external ergonomic keyboard because my wrist is important. Hence, I would like another way of changing the settings on my computer. 

Turning to the internet, I soon realize that these very basic processing such as face recognition and hand tracking are already neatly packed into libraries such as mediapipe. So instead of going through the trouble of making an entire pytorch model, I yoinked the library and just used it directly. In combination with cv2 and osascript, the program would track my hand and more specifically the distance between my thumb and pointer finger and change the volume of my computer's sound accordingly. 

One of the things I learn is that not every frame is important. It is computationally expensive/slow when running the change volume part of the code through the osascript library. Instead, I choose to only check and update the volume every 20 or so frames which made the program run much faster and did not even seem noticable given that on average 30 frames per second was being recorded. 

The one thing I could imporve on is perhaps to include a start and end gesture. As it stands, if I were to run this continuously, the volume would change everytime my hand shows up in the view of the camera. It would be better, if I could make the program wait for a particular uncommon gesture which would signal that I would like to make changes to the volume or brightness. Thats for a future iteration I guess. 

The code can be found [here](https://github.com/berwingan/cv_projects/tree/main/handtracking)
