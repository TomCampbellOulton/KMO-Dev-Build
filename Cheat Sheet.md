## File Creation
*Filename*: YYYY-MM-DD-YourTitle.md

*Top of File*:
```md
title: YourTitle
description: Your description of the post
authors:
- Author 1
- Author 2 (if applicable)
- Author 3 (if applicable), etc.
date: YYYY-MM-DD HH:MM:SS +/-TTTT       #TTTT is referencing the timezone, e.g. +0800. The time isn't needed, but is supported if known.
categories [TOP_CATEGORY, SUB_CATEGORY]
tags: [YourTags]
image: The link to the tile image (image shown on the homepage for this article)
permalink: The link to the page in the URL. e.g. if permalink: /20c/20c-on-the-marsh/ the URL will be https://www.kent-maps.online/20c/20c-on-the-marsh/
published: false                        # Should be false whilst the article is a draft, change to true once finished
toc: false                              # toc meaning table of contents, default of false unless a table of contents is desired for this post
juncture: true                          # Must be enabled to allow action links, image and map viewers
```
The categories of each post are designed for two elements. The tags are designed for zero to infinitely many elements.


*Additional features for top of file*
```md
pin: true                   # Allows you to pin one or more posts to the top of the home page
```


# File Body
## Text

```md
This is  paragraph that is highlighted.
{: .highlight}
```

## Entity Popups
Takes a summary from Wikidata and displays it in a box upon being clicked.
1. Identify the Wikidata ID (Q number) for the entity
2. Link the text text in your post to that ID
For example:
```md
[Charles Darwin](Q1035)
```

## Images
*Adding Images*:
```md
Your Paragraph About The Image
{% include embed/image.html src="YourImageSource" caption="YourImageCaption" %}
```
This makes the paragraph(s) about the image appear to the left and the image be centred with the image on the right hand side of your screen. (YourImageSource is the URL to the image, or the path to the image if it's hosted on the github page)

Alternative for if the image is from Wikimedia Commons:
```md
Your Paragraph About The Image
{% include embed/image.html src="wc:FileName.jpg" caption="YourImageCaption" %}
```

Image with Manifest (IIIF)
```md
{% include embed/image.html manfiest="URLToManifest" %}
```
E.g. URLToManifest could be "https://iiif.harvardartmuseums.org/manifests/object/299843" which would make:
{% include embed/image.html manifest="https://iiif.harvardartmuseums.org/manifests/object/299843" %}


### Before and After Images
```md
{%  include embed/image.html 
    before="BeforeImageName.jpg"
    after ="AfterImageName.jpg"
    caption = "Your Caption Goes Here"
    position = "50"
%}
The position argument is a % of how far from the left to the right the slider should start, with 50% being in the middle of the image


A more complex example, with scaling of the images to line them up more precisely
{%  include embed/image.html&bx=-2&by=-6*bs=1.31 
    before="BeforeImageName.jpg"
    after ="AfterImageName.jpg"
    caption = "Your Caption Goes Here"
    position = "50"
%}

The extension on the url means the following:
- &bx=-2 means the image has been shifted left by 2%    (limits between -50 and +50, negative meaning left and positive meaning right)
- &by=-6 means the image has been shifted up by 6%      (limits between -50 and +50, negative meaning up and positive meaning down)
- &bs=1.31 means the image has been zoomed in 31%       (limits between 0.5 and 3) - (scales from the centre of the image)


These images can be easily adjusted using the alignment adjustment tool (available in the expanded viewer)
To open the tool:
1. Click the viewer in your article to open the expanded version
2. Double-click anywhere on the image comparison. The alignment panel sliders should appear below the viewer.
3. If you want to reset the sliders, press Reset all and all 6 sliders (3 sliders for before and 3 sliders for after image) should be set back to 1x
4. Double-click again or click the x button in the panel header to close the tool.
```


*Additional features for Images*:
```md
Adding Zooming Functionality
The id tag assigned is the used in the zoomto action underneath.
{% include embed/image.html id="ImageIDTag" src="YourImageSource" caption="YourImageCaption" %}
[zoomto example](ImageIDTag/zoomto/pct:X, Y, Width, Height){: label="YourCustomLabel"}
X and Y are the positioning of the image. E.g. X=15.15 means the image begins from 15.15% along the image from the left. Y=12.19 means the image begins 12.19% down from the top of the image.
Width and height are similarly percentages, referring to the width and height of the image.


Additional Features
- cover="true"              # Fills the space, similar to cover photos
- aspect="width/height"     # Allows you to manually set the aspect ratio, with width/height being the Ratio of width to height, not the actual dimensions
- region="pct:x,y,w,h"      # Allows you to start the viewer zoomed into a specific area, with the top left corner of the zoomed image being at position x% in from the left, y% down and the width and height being w% and h% of the total dimensions of the image respectively. (x,y,w,h can be decimal numbers, e.g. x=12.34 is supported)
- rotate="X"                # Allows you to rotate the images by X degrees clockwise


Links to Specific Parts of an Image:
{% include embed/image.html id="ImageIDTag" src="YourImageSource" caption="YourImageCaption" %}
[Clickable Caption For Zooming Into Image](image/zoomto/pct:x,y,w,h)    # With x,y,w,h being the same as above. This should zoom into that region and highlight the selected area of text
```

## Maps
Simple code
```md
{%  include embed/map.html
    center="longitudeCoordinate, lattitudeCoordinate"
%}
```
If you want to add a marker (a label):
```md
{%  include embed/map.html
    center="longitudeCoordinate, lattitudeCoordinate"
    markers="longitudeCoordinateOrMarker, lattitudeCoordinateOfMarker~The Name of Your Marker"
%}
```
Example:
```md
{%  include embed/map.html
    center="37.01056, -110.2425"
    caption="Monument Valley, UT USA"
    markers="37.01056, -110.2425~Monument Valley"
%}
```
Example with Multiple Markers:
```md
{%  include embed/map.html
    center="37.01056, -110.2425"
    caption="Monument Valley, UT USA"
    markers="37.01056, -110.2425~Monument Valley | 37.01055, -110.2425~My 2nd Marker"
%}
```
You must provide the center attribute to the map tag, but this doesn't have to be the longitude and lattitude coordinates! It could also be a Wikidata ID!
You could also specify a caption like with the images, or the zoom. Zoom is at a default value of 8

```md
{%  include embed/map.html
    center="37.01056, -110.2425"
    caption="Monument Valley, UT USA"
    markers="37.01056, -110.2425~Monument Valley | 37.01055, -110.2425~My 2nd Marker"
    zoom="12"
%}
```

## Audio Files
1. Add to the top of the post: "media_subpath: /assets/posts/YourPostsName"
2. Add the audio file (mp3, m4a or wav) to the following folder: "assets/posts/YourPostsName/YourAudioFilesName.mp3" (.mp3 to be replaced with your audio files file type, e.g. .m4a or .wav)
3. In your post where you want the audio to appear, add the following: {% include audio.html src="YourAudioFilesName.mp3" %}


*Technical Adding Media*
```md
{% include embed/{Platform}.html id='{ID}' %}
With Platform being the lowercase of the platform name and ID being the video ID.
This allows for youtube, twitch, bilibili and spotify.
```

*Technical Embedding Video (Not Youtube, but an MP4)*
```md
{% include embed/video.html src='{URL}' %}
Where URL is replaced by the path to your sample mp4
Additional features you could add:
- poster='pathToYourPoster' # Poster image for a video that's shown while the video is downloading
- title=VideoTitle          # Title for the video, appearing below the video much like the images
- autoplay=True             # Enables autoplay between videos
- loop=true                 # Defaults the video to loop (video seeks back to start upon reaching end to allow endless play)
- muted=true                # Defaults the video to be on mute, until unmuted by the user
- tpyes                     # Specify the extensions of additional video formats in same directory as primary video file. Extensions must be seperated by |
```




# Editing Process
1. Edit in GitHub
2. Click*Commit changes*
3. Wait ~ 5 seconds
4. Click*Reload*in the preview
Repeat as required



