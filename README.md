```markdown
# Video to MP3

```python
from pytube import YouTube

YouTube('https://www.youtube.com/watch?v=kT_qHfoiEnQ').streams.filter(only_audio=True).first().download(filename='audio.mp3', output_path='E:/anubhav/Premiere Pro/Projects/Dad\'s Work/')
```

---

# Video to MP4

```python
from pytube import YouTube

YouTube('https://www.youtube.com/watch?v=kT_qHfoiEnQ').streams.get_highest_resolution().download(filename='video.mp4', output_path='E:/anubhav/Premiere Pro/Projects/Dad\'s Work/songs/')
```

---

# Playlist to MP3

```python
from pytube import Playlist as p, YouTube as y
from concurrent.futures import ThreadPoolExecutor as TP

P, Y = p("https://www.youtube.com/playlist?list=PLzCxunOM5WFJ7sbHi_9Zwq2xOwtkYeZlx"), y

def D(u): 
    Y(u).streams.filter(only_audio=True).first().download(output_path='E:/anubhav/Premiere Pro/Projects/Dad\'s Work/songs/')

try:
    with TP() as E: 
        E.map(D, P.video_urls)
except:
    pass
```

*This try-catch is to handle duplicate, private, or unlisted videos. Other handles are also managed by skipping those videos.*

---

# Playlist to MP4

```python
from pytube import Playlist as p, YouTube as y
from concurrent.futures import ThreadPoolExecutor as TP

P, Y = p("https://www.youtube.com/playlist?list=PLzCxunOM5WFJ7sbHi_9Zwq2xOwtkYeZlx"), y

def D(u): 
    Y(u).streams.get_highest_resolution().download(output_path='E:/anubhav/Premiere Pro/Projects/Dad\'s Work/songs/')

try:
    with TP() as E: 
        E.map(D, P.video_urls)
except:
    pass
```

*This try-catch is to handle duplicate, private, or unlisted videos. Other handles are also managed by skipping those videos.*


In Markdown, you use backslashes to escape special characters, like single quotes in file paths, to ensure they're interpreted correctly. For example, to write `Dad's Work` in a path without causing syntax issues, you write it as `Dad\'s Work`.