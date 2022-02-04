# Required Module
## PyTube Module :
Python pytube module consist of various methods and classes by using which we can download YouTube video or fetch the Video metadata.

The PyTube mode is not a Built-in module, so we need to install it separately , using Python-pip command
-pip install pytube


### Befor downloading the Youtube Viideo, let's first fetch the Video META DATA, like, video title, video length, total views on videos etc.


```python
from pytube import Youtube
#Function takes Youtube Object as Argument 
def video_Info(yt):
    print("Title:",yt.title)
    print("Total Length : ",yt.length,"Seconds")
    print("Total Views :", yt.views)
    print("Is Age Restricted :"yt.age_restricted)
    print("Video Rating", round(yt.rating))
    print("Thumbnail URL :" , yt.thumbnail_url)

link ="Youtube Video Url"
yt = Youtube(link) #Create Youtube object
#call the function
video_Info(yt)
```

## Download Youtube Video in mp4 Format:
#### To download Youtube video in MP4 streams and then use that itag value of a specific stream to download the video


```python
from pytube import Youtube

def download_Video(yt):
    #fiilter mp4 steams from object
    my_streams =yt.streams.filter(file_extension='mp4',only_video=True)
    for streams in my_streams:
        #print itag resoluction and codec format of MP4 streams
        print(f"Video itag:{streams.itag}Resolution:{streams.resolution}")
    #enter the itag value of resolution on which you want to download the video
    input_itag =input("Enter itag Value:")
    
    #finally dowload the Youtube Video...
    video.download()
    print("Video is Downloading as ",yt.title+".mp4")

link = "Enter Your Link Here"
#Create Youtube Object
yt = Youtube(link)
#call the Function
download_video(yt)
    
    
    
```

## Download Youtube Video in Audio Format


```python
from pytube import Youtube
# Define Function..

def download _Audio(yt):
    #Filter all the audio files
    my_streams = yt.streams.filter(only_audio=True)
    for streams in my_streams:
        #print audio quality/itag/codec
        print(f"Audio itag :{streams.itag}Quality :{streams.abr}")
        
    input_itag=input("Enter itag Value : ")
    audio = yt.streams.get_by_itag(input_itag)
    
    audio.download() #download the VIdeo in audio format..
    #audio.download(r"New path where you want to save the fike)
    print("Audio is Downloading as ",yt.title+".mp3")
    
link = "Your Link"
yt = Youtube(link) # create Object
download_Audio(yt) #call the function
    
    
```

## Download complete Youtube Playlist
### to download a complete Youtube playlist we need to creat a Playlist class Object of Pytube modelu


```python
from pytube import Playlist

def download_Playlist(p):
    #print Playlist title
    print(p.title)
    #get video of playlist
    for video in p.videos:
        try:
            #download all videos in best resolution
            video.streams.first().download(video.title)
        except Exception as e:
            print(e,type(e))
            
    print("Playlist is Downloaded")
    
link ="Youtube Playlist URL"
p=Playlist(link) #create Playlist object
download_playlist(p)




```
