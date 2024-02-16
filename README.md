# Speech-recognition
This project is used to convert the speech (voice) and gives us output like a text . for that we need to install some modules in cmd like pip install pipwin,pip install pyaudio,pip install speechrecognition
import speech_recognition as sr
def main():
    r=sr.Recognizer()

    #listen  
    with sr.Microphone() as source:
        r.adjust_for_ambient_noise(source)
        print("Please say something")
        audio=r.listen(source)
        print("Recognizing now")

        #recognize with google
        try:
            print("You have said \n"+r.recognize_google(audio))
            print("successfully recognized")
        except Exception as e:
            print("Error: "+str(e))
        
        #write
        with open("recorded.wav","wb") as f:
            f.write(audio.get_wav_data())

if __name__=="__main__":
    main()
