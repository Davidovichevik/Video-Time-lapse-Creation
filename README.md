# Video-Time-lapse-Creation
Create a time-lapse video from a series of frames.
import cv2
import os

images_folder = 'frames'
video_name = 'timelapse.avi'

images = [img for img in os.listdir(images_folder) if img.endswith('.png')]
frame = cv2.imread(os.path.join(images_folder, images[0]))
height, width, layers = frame.shape

video = cv2.VideoWriter(video_name, cv2.VideoWriter_fourcc(*'DIVX'), 1, (width, height))

for image in images:
    video.write(cv2.imread(os.path.join(images_folder, image)))

cv2.destroyAllWindows()
video.release()
