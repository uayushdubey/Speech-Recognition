# Speech-Recognition
It's all about Speech Recognition without pyAudio
import speech_recognition as sr
import sounddevice as sd
import wavio
import os

fps = 44100
duration = 5
print("Recog.....")

recording = sd.rec(duration*fps,samplerate=fps,channels=2)
sd.wait()
print("Done")

wavio.write('output.wav',recording,fps,sampwidth=2)
rec = sr.Recognizer()
audioF = 'output.wav'
with sr.AudioFile(audioF) as sourceF:
    audio = rec.record(sourceF)
    print("File is READING")
print("file text is : ")
try :
    text = rec.recognize_google(audio)
    print(text)

except Exception as e:
    print(e)

os.remove('output.wav')
print("..................................")
