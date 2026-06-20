---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
---
# Modifications

Use this page when you want to change the way the loading screen plays media.

## Play Image + Audio

Use this setup when you want one static background image with one audio track.

What to update:
- replace the background image file used by the loading screen
- replace the audio file with your own `.mp3`
- keep the image path and audio path in the loading screen files matched to the new files

## Play Slides + Audio

Use this setup when you want multiple images to rotate like a slideshow while one audio track plays in the background.

What to update:
- replace the slide images with your own images
- keep the slide file names or update the file list where the slides are loaded
- replace the background audio file if needed

## Play Video + Audio

Use this setup when you want a video background instead of static images.

What to update:
- replace the current video file with your own video
- make sure the video format and file name match what the loading screen expects
- replace the audio file only if your setup uses a separate background track

## Final Check

After any modification:
- restart the resource
- reconnect to the server and test the loading screen fully
- confirm that the media files were uploaded in the correct folder structure
