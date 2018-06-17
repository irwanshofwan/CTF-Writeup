### Binpeg  
```110 Solved
Author: abdilahrf  
Point: 50   Difficulties:

Black(0,0,0) is represent 1 and White(255,255,255) is represent 0 get the message as binary and get the flag!
Source code attached
```

File attachment berupa gambar berformat .jpg dengan ukuran 8 x 4689 yang berupa warna hitam dan putih pada tiap pixelnya, karena clue pada soal ini sudah jelas adalah membaca tiap pixelnya menjadi dalam bentuk biner dan metranslasikannya ke dalam bentuk ascii, untuk mengerjakan soal ini digunakan python dan library Pillow http://pillow.readthedocs.io/en/4.0.x/index.html
Berikut kode yang saya gunakan 

```python
from PIL import Image
import binascii

im 		= Image.open("binpeg.jpg")
im_rgb 	= im.convert("RGB")
x, y 	= im.size
msg 	= ""

for vline in range(y):
  for hline in range(x):
    if im_rgb.getpixel((hline,vline)) == (255, 255, 255):
      msg += "0"
    else:
      msg += "1"
			
n = int('0b'+msg, 2)
print(binascii.unhexlify('%x' % n))


```

output dari program

```bash
irwanshofwan@x:~/Desktop/workspace$ python solve_binpeg.py
 Introduction My son Nat is autistic. He likes to look at pictures of familiar places, things, and people. We bought a digital camera so we could take as many pictures of as many ordinary things as we wanted, without having to worry about the cost and bother of film and development. Nat's tastes are difficult to predict, so we might take pictures of a subject certain to please him, only to find that he has no interest in them at all. We wanted to be able to cast a wide net while taking pictures, to be certain to capture the images that would interest him. Once we had the camera, we took hundreds of pictures, and showed Nat how to look through them on the computer using an off-the-shelf image viewer called ThumbsPlus. Watching Nat flip through pictures, though, I noticed something: once he became familiar with the sequence of the pictures, he was clicking on the pictures as if it mattered where he clicked. The image viewer didn't care: any click on the picture would show the next picture. But if Nat knew that the next picture was of a thing off to the left of the current picture, he would click on the left of the image. If he knew the next picture was through a door at the right of the picture, he would click on the door. He's played a number of kid's adventure games, such as Pajama Sam, and knew about this style of navigation. Even in a program that didn't use that navigation style, he had begun using it as if it did. So I thought, why not make an image viewer that worked his way? Why not write a program that lets me build picture environments from our life, and lets Nat navigate through them in the style he wanted? Natworld Screen Shot One of over 1500 images in Natsworld. The user interface is simply a set of directional cursors (near center) Zoom in Choosing Python I had used Python for small scripting projects before, and liked its quick-off-the-blocks feel. It would provide me with a malleable environment in which to experiment with features, to see what Nat would find interesting. Although this was an at-home project to be used only by my son, it shared issues with larger, supposedly more serious projects: unclear requirements, unpredictable customers, and limited developer resources. The most important concern to me in choosing the development tools was my productivity. Since this was after-hours work, my time and attention would be stretched thin, and I wanted to be able to focus on the user experience, not build environments, memory management, and the like. I looked for existing software, and found lots of interesting examples at pygame (www.pygame.org). Pygame provided all the functions I'd need for image manipulation and display management, and there were a few existing projects there that provided useful examples. Pyzzle almost provided what I needed the flag is ctfs{YoU_n33d_Rob0t_To_r3ad} in all uppercase, but wasn't as well-organized internally as I would have liked to be able to quickly experiment with new features. Implementation Using the existing examples to help guide my pygame use, I created a new framework for my program. My program, which I named simply Nats World, would provide a virtual world for exploration. It would work the way Nat expected it to, providing a simple exploration environment similar to games like Myst; clicking on the left of the screen would turn you left, clicking center would move you forward, and so forth. At its simplest, the entire environment was simply a set of nodes, each of which had an image to display, and a list of other connected nodes to navigate to. One physical location in the world is represented by a number of nodes, one for each direction to face. These nodes together are called a spot. Over time, this model was extended to add features to the environment, but this simple model got me off the ground. Python gave me a clean object-oriented basis for building my Node class, and pygame provided the primitives for displaying images, creating cursors, and collecting input. One of the biggest challenges was deciding among ways to organize the description of the world. On the one hand, I could have created a descriptive language for the structure of the world, and written an interpreter to read the description and build the in-memory structures on which the game would run. This would have been a fairly large effort, and would have required me to formalize all of the structures that could have appeared in a world. It also would have meant a longer delay before I had something that Nat could actually use. On the other hand, I could have simply used Python statements to construct the structures directly. This would have been tedious and error-prone.
```
karena ouput dari program berupa teks, untuk memudahkan pencarian digunakan grep | "ctfs", *pada soal ini semua flag berupa uppercase 