## File Creation
**Filename**: YYYY-MM-DD-YourTitle.md

**Top of File**: ```md
title: YourTitle
description: Your description of the post
date: YYYY-MM-DD HH:MM:SS +/-TTTT       #TTTT is referencing the timezone, e.g. +0800. The time isn't needed, but is supported if known.
categories [TOP_CATEGORY, SUB_CATEGORY]
tags: [YourTags]
image: The link to the tile image (image shown on the homepage for this article)
permalink: The link to the page in the URL. e.g. if permalink: /20c/20c-on-the-marsh/ the URL will be https://www.kent-maps.online/20c/20c-on-the-marsh/
toc: false                              # toc meaning table of contents, default of false unless a table of contents is desired for this post
```
The categories of each post are designed for two elements. The tags are designed for zero to infinitely many elements.


** Additional features for top of file **
```md
pin: true                   # Allows you to pin one or more posts to the top of the home page
```


## File Body

** Adding Images**:```md
Your Paragraph About The Image
{% include embed/image.html src="YourImageSource" caption="YourImageCaption" %}
```
This makes the paragraph(s) about the image appear to the left and the image be centred with the image on the right hand side of your screen


** Additional features for Images**:
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




** Technical Adding Media **
```md
{% include embed/{Platform}.html id='{ID}' %}
With Platform being the lowercase of the platform name and ID being the video ID.
This allows for youtube, twitch, bilibili and spotify.
```

** Technical Embedding Video (Not Youtube, but an MP4) **
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















## Questions for Ron
Is "permalink: theLink" automatic / can it be made automatic or will / should it rely upon the author.
Same for description

Why aren't we using the author id tags functionality?

For the images, why not use the default Chirpy: 
![img-description](/path/to/image)
_Image Caption_
![Desktop View](/assets/img/sample/mockup.png){: .left }    # Float to the left
![Desktop View](/assets/img/sample/mockup.png){: .right }   # Float to the right

Do we plan on adding a dark / light mode theme?
