"# weather-app" 
<<<<<<< HEAD
"# Login-System" 
=======
from tkinter import *
import tkinter as tk
from geopy.geocoders import Nominatim
from tkinter import ttk,messagebox
from timezonefinder import TimezoneFinder
from datetime import datetime
import requests
import pytz

root=Tk()
root.title("Weather App")
root.geometry("900x500+300+200")
root.resizable(False,False)

def getWeather():
    try:
        city=textfield.get()

        geolocator=Nominatim(user_agent="OpenWeather")
        location=geolocator.geocode(city)
        obj=TimezoneFinder()
        result=obj.timezone_at(lng=location.longitude,lat=location.latitude)

        home=pytz.timezone(result)
        local_time=datetime.now(home)
        current_time=local_time.strftime("%I:%M %p")
        clock.config(text=current_time)
        name.config(text="CURRENT WEATHER")
        name1.config(text="CURRENT TIME")


        api="http://api.openweathermap.org/data/2.5/weather?q="+city+"&appid=18568f1aaa237b96e6973f271357fd11"
        json_data=requests.get(api).json()
        condition=json_data['weather'][0]['main']
        description=json_data['weather'][0]['description']
        temp=int(json_data['main']['temp']-273.15)
        pressure=json_data['main']['pressure']
        humidity=json_data['main']['humidity']
        wind=json_data['wind']['speed']


        t.config(text=(temp,"°"))
        c.config(text=(condition,"|","FEELS","LIKE",temp,"°"))

        w.config(text=wind)
        h.config(text=humidity)
        d.config(text=description)
        p.config(text=pressure)
    
    except Exception as e:
        messagebox.showerror("Weather App","Invalid Entry!!")




Search_image=PhotoImage(file="C:/Users/anshad c v/Desktop/weatherapp/search.png")
myimage=Label(image=Search_image)
myimage.place(x=20,y=20)

textfield=tk.Entry(root,justify='center',width=17,font=("poppins",25,"bold"),bg="#404040",border=0,fg="white")
textfield.place(x=50,y=40)
textfield.focus()

Search_icon=PhotoImage(file="C:/Users/anshad c v/Desktop/weatherapp/Copy of search_icon.png")
myimage_icon=Button(image=Search_icon,borderwidth=0,cursor='hand2',bg="#404040",command=getWeather)
myimage_icon.place(x=400,y=34)


Logo_image=PhotoImage(file="C:/Users/anshad c v/Desktop/weatherapp/Copy of logo.png")
logo=Label(image=Logo_image)
logo.place(x=150,y=100)


Frame_image=PhotoImage(file="C:/Users/anshad c v/Desktop/weatherapp/Copy of box.png")
frame=Label(image=Frame_image)
frame.pack(padx=5,pady=5,side=BOTTOM)

name=Label(root,font=("arial",15,"bold"))
name.place(x=380,y=120)
name1=Label(root,font=("arial",15,"bold"))
name1.place(x=10,y=175)
clock=Label(root,font=("Helvetica",20))
clock.place(x=10,y=200)







label1=Label(root,text="WIND",font=("Helvetica",15,'bold'),fg="white",bg="#1ab5ef")
label1.place(x=120,y=400)
label1=Label(root,text="HUMIDITY",font=("Helvetica",15,'bold'),fg="white",bg="#1ab5ef")
label1.place(x=250,y=400)
label1=Label(root,text="DESCRIPTION",font=("Helvetica",15,'bold'),fg="white",bg="#1ab5ef")
label1.place(x=430,y=400)
label1=Label(root,text="PRESSURE",font=("Helvetica",15,'bold'),fg="white",bg="#1ab5ef")
label1.place(x=650,y=400)

t=Label(font=("arial",70,"bold"),fg="#ee666d")
t.place(x=400,y=150)
c=Label(font=("arial",15,'bold'))
c.place(x=400,y=250)


w=Label(text="...",font=("arial",20,"bold"),bg="#1ab5ef")
w.place(x=120,y=430)
h=Label(text="...",font=("arial",20,"bold"),bg="#1ab5ef")
h.place(x=280,y=430)
d=Label(text="...",font=("arial",20,"bold"),bg="#1ab5ef")
d.place(x=450,y=430)
p=Label(text="...",font=("arial",20,"bold"),bg="#1ab5ef")
p.place(x=670,y=430)








root.mainloop()


>>>>>>> ffd543246fe907050dd68c5c93658f4c017cc81a
"# Login-System" 
