import subprocess
import winshell
import pyttsx3 #pip intstall pyttsx3
import datetime
import speech_recognition as sr #pip install speechRecognition
import wikipedia #pip install wikipedia
import smtplib
import webbrowser as wb
import psutil #pip install psutil
import pyjokes #pip install pyjokes
import os
import pyautogui #pip install pyautogui
import random
import json
import requests
from pprint import pprint
import wolframalpha #pip install wolframalpha
from urllib.request import urlopen
import time
import PySimpleGUI as sg
engine=pyttsx3.init()
wolframalpha_app_id = '8QH35T-86YXH34EW4'
voice_id = "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Speech\Voices\Tokens\TTS_MS_EN-US_ZIRA_11.0"
engine.setProperty('voice', voice_id) 
#engine. setProperty("rate", 178)
def speak(audio):

    engine.say(audio)
    engine.runAndWait()

def time_():
    Time=datetime.datetime.now().strftime("%I:%M:%S")# for 12 hours
    speak("the current time is: ")
    print(Time)
    speak(Time)

def date_():
    Year=datetime.datetime.now().year
    Month=datetime.datetime.now().month
    Day=datetime.datetime.now().day
    speak("the current date is:")
    print(Day)
    print(Month)
    print(Year) 
    speak(Day)
    speak(Month)
    speak(Year)  

def wishme(): # this is for greetings
    speak("Welcome back Prathyusha !")
    Hour=datetime.datetime.now().hour
    if(Hour>=6 and Hour<=12):
        speak("Good morning Madam! Have a nice day")
    elif(Hour>12 and Hour<=18):
        speak("Good afternoon Madam!")
    elif(Hour>18 and Hour<=24):
        speak("Good Evening Madam!")
    else:
        speak("Good Night Madam! Have a Good sleep")
    speak("How can I help you..!")

def weather_data(query):
	res=requests.get('http://api.openweathermap.org/data/2.5/weather?'+query+'&APPID=b35975e18dc93725acb092f7272cc6b8&units=metric');
	return res.json();
def print_weather(result,city):
	print("{}'s temperature: {}°C ".format(city,result['main']['temp']))
	print("Wind speed: {} m/s".format(result['wind']['speed']))
	print("Description: {}".format(result['weather'][0]['description']))
	print("Weather: {}".format(result['weather'][0]['main']))
def weather():
	city=input('Enter the city:')
	print()
	try:
	  query='q='+city;
	  w_data=weather_data(query);
	  print_weather(w_data, city)
	  print()
	except:
	  print('City name not found...')

def sendEmail(to,content):
    server=smtplib.SMTP('smtp.gmail.com',587)
    server.ehlo()
    server.starttls()
    # for this function you must use the low secured gmail account
    server.login('onlyforprojects2020@gmail.com','Projects@123')
    server.sendmail('onlyforprojects2020@gmail.com',to,content)
    server.close()

def joke():
    speak(pyjokes.get_joke())
    print(pyjokes.get_joke())

def screenshot():
    img=pyautogui.screenshot()
    img.save('ss.png')

def TakeCommand(): # taking command from the user
    r=sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening....")
        r.pause_threshold = 1
        audio = r.listen(source)
    
    try:
        print("Recognizing....")
        query=r.recognize_google(audio,language="en-US")
        print(query)

    except Exception as e:
        print(e)
        print("Say that again Plzz.....")
        return "None"
    return query

def cpu():
    usage = str(psutil.cpu_percent())
    speak('CPU is at'+usage)
    print(usage)
    battery = psutil.sensors_battery()
    speak('Battery is at')
    speak(battery.percent)
    print("Battery is in:",battery.percent)

def stopwatch():
    sg.theme('DarkBrown1')

    layout = [ [sg.Text('Stopwatch', size=(20, 2), justification='center')],
            [sg.Text(size=(10, 2), font=('Helvetica', 20), justification='center', key='-OUTPUT-')],
            [sg.T(' ' * 5), sg.Button('Start/Stop', focus=True), sg.Quit()]]  
    timer_running, counter = True, 0
    window = sg.Window('Stopwatch Timer', layout)
    while True:                                 
        event, values = window.read(timeout=10) 
        if event in (sg.WIN_CLOSED, 'Quit'):             
            break
        elif event == 'Start/Stop':
            timer_running = not timer_running
        if timer_running:
            window['-OUTPUT-'].update('{:02d}:{:02d}.{:02d}'.format((counter // 100) // 60, (counter // 100) % 60, counter % 100))
            counter += 1
    window.close()

if __name__ == "__main__":
    while True:
        commander = TakeCommand().lower()
        if 'honey' in commander:
            clear = lambda: os.system('cls') 
            clear()
            wishme()       
            while(True):
                query = TakeCommand().lower()

                if 'time' in query:
                    time_()

                elif 'date' in query:
                    date_()
                
                elif 'how are you' in query: 
                    speak("I am fine, Thank you") 
                    speak("How are you, Madam")                     

                elif 'are you there' in query: 
                    speak("Sorry Madam,I am there!") 

                elif 'fine' in query: 
                    speak("It's good to know that your fine")

                elif "what's your name" in query or "What is your name" in query: 
                    speak("I am Honey")

                elif "who made you" in query or "who created you" in query:  
                    speak("I have been created by Prathyusha. she is an extra-ordinary person ,"
                    "She is very co-operative ,"
                    "If you are facing any problem regarding the 'Honey', She will be glad to help you ")
  
                elif "who i am" in query: 
                    speak("If you talk then definately your human.") 
  
                elif "why you came to world" in query: 
                    speak("Thanks to Prathyusha. further It's a secret") 

                elif 'what is love' in query: 
                    speak("It is 7th sense that destroy all other senses") 
  
                elif "who are you" in query: 
                    speak("I am your virtual assistant created by Pratyusha") 
                
                elif "good morning" in query: 
                    speak("A warm good morning!") 
                    speak("How are you Ms.Prathyusha") 
  
                    # most asked question from google Assistant 
                elif "will you be my gf" in query or "will you be my bf" in query:    
                    speak("I'm not sure about, may be you should give me some time") 
  
                elif "i love you" in query: 
                    speak("I Love You Too")

                elif 'stopwatch' in query or 'stop watch' in query:
                    stopwatch()

                elif 'wikipedia' in query or 'wiki' in query:
                    speak("Searching.....")
                    query=query.replace('wikipedia','')
                    result=wikipedia.summary(query,sentences=3)
                    speak("According to the wikipedia...")
                    print(result)
                    speak(result)

                elif 'send email' in query:
                    try:
                        speak("what should I say?")
                        content = TakeCommand()
                        speak("Who is the reciever.?")
                        reciever=input("Enter the Reciever's Email Id:")                
                        to=(reciever)
                        sendEmail(to,content)
                        speak(content)
                        speak("Email has been sent..")
                        print("Email has been sent..")
                    except Exception as e:
                        print("unable to send email")
                        speak("Unable to send mail")

                elif 'weather report' in query:
                    weather()

                elif 'search in chrome' in query:
                    speak("What should I search ?")
                    chromepath = 'C:/Program Files (x86)/Google/Chrome/Application/chrome.exe %s'
                    search = TakeCommand().lower()
                    wb.get(chromepath).open_new_tab(search+'.com')

                elif 'open stack overflow' in query: 
                    speak("Here you go to Stack Over flow.Happy coding") 
                    wb.open("stackoverflow.com")

                elif 'youtube' in query:
                    speak("What should I search?")
                    search_term=TakeCommand().lower()
                    speak("Here we go to YOUTUBE!")
                    wb.open('http://www.youtube.com/results?search_query='+search_term)
        
                elif 'google' in query:
                    speak("What should I search?")
                    search_term=TakeCommand().lower()
                    speak("Searching....")
                    wb.open('http://www.google.com/search?q='+search_term)

                elif 'empty recycle bin' in query: 
                    winshell.recycle_bin().empty(confirm = False, show_progress = False, sound = True) 
                    speak("Recycle Bin Recycled") 
                    print("Empty Recycle Bin process done! ")

                elif 'cpu' in query:
                    cpu()

                elif 'joke' in query:
                    joke()

                elif 'ms word' in query:
                    speak("Opening MS word...")
                    ms_word = 'winword'
                    os.startfile(ms_word)

                elif 'powerpoint' in query:
                    speak("Opening MS Power Point...")
                    ms_ppt = 'powerpnt'
                    os.startfile(ms_ppt)
                
                elif 'excel' in query:
                    speak("Opening MS Excel...")
                    ms_excel = 'excel'
                    os.startfile(ms_excel)

                elif 'ms access' in query:
                    speak("Opening MS Access...")
                    ms_access = 'msaccess'
                    os.startfile(ms_access)

                elif 'vlc' in query:
                    speak("Opening VLC media player...")
                    vlc = 'vlc'
                    os.startfile(vlc)
                
                elif 'cmd' in query or 'command prompt' in query or 'terminal' in query:
                    speak("Opening Command Prompt...")
                    cp = 'cmd'
                    os.startfile(cp)
                

                elif "hibernate" in query or "sleep" in query: 
                    speak("Hibernating") 
                    os.system("rundll32.exe powrprof.dll,SetSuspendState 0,1,0")

                elif 'write a note' in query:
                    speak("What should I write! Madam?") 
                    notes = TakeCommand()
                    file = open('notes.txt','w')
                    speak('Madam! Should I include Date and Time?')
                    ans=TakeCommand()
                    if 'yes' in ans or 'sure' in ans:
                        strTime=datetime.datetime.now().strftime("%H:%M:%S")
                        file.write(strTime)
                        file.write(':-')
                        file.write(notes)
                        speak('Done Taking notes..!')
                        print('Done Taking notes..!')
                    else:
                        file.write(notes)
                        print('Done Taking notes..!')
                        speak('Done Taking notes..!')
                
                elif 'show notes' in query:
                    speak("showing notes")
                    file = open('notes.txt','r')
                    print(file.read())
                    speak(file.read())

                elif 'screenshot' in query:
                    screenshot()
                    speak("Screenshot Done!")


                elif 'remember' in query:
                    speak("What should I remember Madam?") 
                    memory = TakeCommand()
                    remember = open('memory.txt','w')
                    remember.write(memory)
                    remember.close()
                
                elif 'do you remember anything' in query:
                    remember = open('memory.txt','w')
                    speak('You asked me to remember that'+remember.read())

                elif 'news' in query:
                    try:
                        jsonObj = urlopen('http://newsapi.org/v2/everything?q=tesla&from=2021-01-06&sortBy=publishedAt&apiKey=8520c971a15b4521af444d3182b638a8')
                        data = json.load(jsonObj)
                        i=1
                        speak('Here are some top headlines fromm Entertainment')
                        print("============TOP HEADLINES=============")
                        for items in data['articles']:
                            print(str(i)+'. '+items['title']+'\n')
                            print(items['description']+'\n')
                            speak(items['title'])
                            i+=1
                    except Exception as e:
                        print(str(e))

                elif 'where is' in query:
                    query = query.replace('where is','')
                    location=query
                    speak('You asked to locate'+location)
                    wb.open_new_tab('https://www.google.com/maps/place'+location)

                elif 'calculate' in query:
                    client = wolframalpha.Client(wolframalpha_app_id)
                    indx = query.lower().split().index('calculate')
                    query = query.split()[indx +1: ]
                    res = client.query(''.join(query))
                    answer = next(res.results).text
                    print('The Answer is'+answer)
                    speak('The Answer is'+answer)

                elif 'what is' in query or 'who is' in query:
                    client = wolframalpha.Client(wolframalpha_app_id)
                    res = client.query(query)
                    try:
                        print(next(res.results).text)
                        speak(next(res.results).text)
                    except StopIteration:
                        print('No results...')

                elif 'stop listening' in query or 'dont listening' in query:
                    speak('For how many seconds you want me to stop listening to your commands?')
                    ans = int(TakeCommand())
                    time.sleep(ans)
                    print(ans)

                elif 'restart' in  query:
                    os.system('system /r /t 1')

                elif 'shutdown' in  query:
                    os.system('system /s /t 1')
   
                elif 'thank you' in query or 'bye honey' in query:
                    speak("Your Welcome Madam.. Honey is Signing off")
                    exit()
