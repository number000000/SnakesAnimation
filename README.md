# Snake Animation Generator
*A VIS142 Project* \
![snake demo](/misc/snake-multiturn-inScreen-demo.gif)
## File Description
### snake.py
The snake generated by this file can only take one turn at the time. He/she has to finish the current turn before deciding to make a new turn. He/she also may go out of scope and most likely you will never see him/her again unless you give him/her enough time until he/she decides to come back to the screen by chance. We value free-will here so don't force your snake friend to come back to the screen. He/she will be mad :/
### snake_multiturn.py
The snake generated by this file can take multiple turns at the time. He/she doesn't have to wait for the current turn to finish before making the next turn. So you will often see snakes in zig-zag shape. The snake from this file may also go out of scope.
### snake_multiturn_inScreen.py
The ULTIMATE version of snakes! The snake generated by this file can take multiple turns. He/she also loves to stay in the screen and shows off his/her beautiful wavy body. So when he/she reaches the edge, he/she will not keep going out of the screen.

## Preparation before running
### Install pygame
Run this line in terminal
```
python3 -m pip install -U pygame --user
```
Check this page if you meet any issues with installation: https://www.pygame.org/wiki/GettingStarted \
Check pygame documentation for more information: https://www.pygame.org/docs/
### Install ffmpeg (if want to get a video)
[Download here](https://ffmpeg.org/download.html)

## How to get the video
First move inside the `frames` folder. \
Since the program generates frames (images ends in .png) in the folder `frames` (You will have to have this folder for the program to run), you will have to run the following command to merge the frames into a video:
```
ffmpeg -r 60 -start_number 1000000 -s 4096x2160 -i %d.png -vcodec libx264 -crf 31 -pix_fmt yuv420p final.mp4
```
1000000 should be replaced with your `start_sequence_num`

## Customize your own snake frames and video
### Frame/video Size
Change `width` and `height` parameters at the start of the file
### Change name and title
Change `name` and `title` parameters
### Change output frames' name
Change `start_sequence_num`
### Change snake's body data
Look for `self.size` `self.length` `self.color` in class Snake
### Change the length of the video
```python
for i in range(0, 20*60): # Change Here
    screen.fill((0,0,0))
    for thing in snakes:
        thing.move()
    pygame.image.save(screen, "./frames/" + str(frame_num) + ".png")
    frame_num = frame_num + 1
    pygame.display.update()
    clock.tick(60)
```
The for loop generates 60 frames for one second. Change 20 to any other length of time. eg. 30*60 generates 30 seconds of 60-frame video. \
**Note** There will always be 3 seconds of title and 1 second of black screen before the snake videos.

### Change the number of snakes in a video
```python
snakes = []
for i in range (0, 35): #Change Here
    snakes.append(Snake())
```
Change the range to modify how many snakes you want in a video. \
eg. `for i in range (0, 40)` will give you 40 snakes in a video.
