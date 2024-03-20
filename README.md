THIS LLM MODEL HELPS YOU TO GET ANSWER OF THE QUESTION THAT YOU ASK FROM IT ABOUT THE CONTENTS COVERED IN YOU TUBE VEDIOS WITHOUT ACTUALLY WATCHING YOU TUBE VEDIOS.



..........................LIBRARIES USED ARE........................................
openai: For interaction with OpenAI's GPT-3.5 model.
langchain
pytube
pydub
SpeechRecognition
....................................................................................


Simply paste the link of you tube vedios in "vedio_link":-

For example in my case................video_link="https://youtu.be/imNlJohlLPk?si=6ofqc2jLa7UJ7vbf"

Then specify the destination where you want to store every files wheather audio,vedio and python files in "destination":-

For example in my case................destination=r"C:\Users\Dell\3D Objects\LLM"
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Step 1

A)Run this part of code first in youtubellm_1 file and it will download your vedio directly in your destination path.

from pytube import YouTube
import os
destination=r"C:\Users\Dell\3D Objects\LLM"
video_link="https://youtu.be/imNlJohlLPk?si=6ofqc2jLa7UJ7vbf"
try:
    video=YouTube(video_link)
    audio=video.streams.filter(only_audio=False,file_extension='mp4').first()
    audio.download(destination)
    #audioreal = VideoFileClip("exampl")
    #video.audio.write_audiofile("example.mp3")
    print("download completed!")
except:
    print("download is not yet completed")





B)Then rename your downloaded vedio as per your comfort. In my case it is "tutorial2.mp4".



C)After renaming run this part of code in youtubellm_1, otherwise if you do not rename and run this part of code then it will give you error.

from moviepy.editor import *


video = VideoFileClip("tutorial2.mp4")

video.audio.write_audiofile("tutorialnew.wav")




It will extract audio in .wav format.

My extracted audio name is "tutorialnew.wav"...............you can provide your own name but keep .wav format................or you can try any other format
also because whisper model is comfort with any extensions.





/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Step 2



Run youtubellm_2 file. It will process audio chunk wise(try to keep chunk size small in my case it is 2 minutes.Dont increase otherwise it will give bytes error).
It will process each chunk and convert to text using wishper-1 model provided by OpenAI and simultaneously write it to text file(.txt format). In my case text file name is aditya1.txt
You can provide your own name.

You will see that text file has been created.
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
Step 3


The code loads a text document and splits it into smaller chunks.
It generates embeddings for each chunk using OpenAI's GPT-3.5 model.
These embeddings are used to create a vector store for efficient retrieval of relevant chunks based on user queries.
The query_document function retrieves relevant chunks based on user questions and launches a chat session using OpenAI's model.
Finally, the code prints out the response generated by the chat model.


