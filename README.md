



# Eisenhower-Matrix-Tkinter-Draft
The eisenhower matrix is a way of prioritizing your tasks into four quadrants: Important and urgent, important and not urgent, urgent and not important, and not important and not urgent 





import os
from tkinter import *
from tkinter import filedialog
from PIL import Image
import tkinter as tk
from tkinter import ttk, filedialog
import mimetypes
import random 
import string
from PIL import Image, ImageTk
from datetime import datetime

root = tk.Tk()
#root.geometry("750x500")
root.geometry("1250x860")
#root.minsize(750, 600)
#root.maxsize(750, 600)
root.config(bg = "#232323")
root.title("Eisenhower Matrix")



#each file you add will not be torn off the window root
root.option_add("*tearOff", False)


def create_file(content = "", title = "untitled"):
    text_area = tk.Text(notebook)
    text_area.config(font = ("arial", 17, "bold"))
    text_area.insert("end", content)
    #text_area.pack(fill= "both", expand = True)
    text_area.pack()
    notebook.add(text_area, text = title)
    notebook.select(text_area)
def open_file():
    pass
def save_file():
    pass
    #ask user where they wanna save it- dosent actually save have to add import os
    file_path = filedialog.asksaveasfilename()
    #now get file name from the file path
    try:
        filename = os.path.basename(file_path)
        text_widget = root.nametowidget(notebook.select())
        #first line starts at 1, 0th character, we go to end of content in widget"
        content = text_widget.get("1.0", "end-1c")
        
        with open(file_path, "w") as file:
            file.write(content)
    except(AttributeError, FileNotFoundError):
        print("Save operation cancelled")
        return
    
    notebook.tab("current", text= filename)
    
def open_file():
    file_path = filedialog.askopenfilename()
    
    try:
        filename = os.path.basename(file_path)
        with open(file_path, "r") as file:
            content = file.read()
    except (AttributeError, FileNotFoundError):
        print("Open operation cancelled")
        return
    create_file(content, filename)
    
def existing_file(content = "", title = "untitled"):
    text_area = tk.Text(notebook)
    text_area.config(font = ("arial", 17, "bold"))
    text_area.insert("end", content)
    #text_area.pack(fill= "both", expand = True)
    text_area.pack()
    notebook.add(text_area, text = title)
    notebook.select(text_area)

        
        
main = ttk.Frame(root)
main.pack(fill = "both", expand= True, padx = 1, pady = (20,0))

#right_frame = ttk.Frame(root)
#right_frame.pack(side = "right")
#listbox = tk.Listbox(right_frame)
#listbox.pack()

notebook = ttk.Notebook(main)
notebook.pack(fill = 'both', expand = True)

###create frame variable
TabControl1 = ttk.Frame(notebook)
TabControl2 = ttk.Frame(notebook)
TabControl3 = ttk.Frame(notebook)
TabControl4 = ttk.Frame(notebook)
TabControl5 = ttk.Frame(notebook)
#Notebook method: add a frame and what the tab says
#notebook.add(TabControl1, text = "All")
#notebook.add(TabControl2, text = "I + U")
#notebook.add(TabControl3, text = "I + NU")
#notebook.add(TabControl4, text = "NI + U")
#notebook.add(TabControl5, text = "NI + NU")
notebook.grid(row = 0, column = 0, sticky = "e")
frameya = tk.Frame(main, height = 30)
frameya.grid(row = 0, column = 1, sticky = "e")

def add_imp_and_urg(content = "", title = "untitled"):
    text_area = tk.Text(notebook)
    text_area.config(font = ("arial", 17, "bold"))
    text_area.insert("end", content)
    #text_area.pack(fill= "both", expand = True)
    text_area.pack()
    notebook.add(text_area, text = title)
    notebook.select(text_area)
    #TabControl2 = ttk.Frame(notebook)
    #notebook.add(TabControl2, text = "I + U")
    #notebook.grid(row = 0, column = 0, sticky = "e")
    #implab = Label(TabControl2, text = "IMPORTANT AND URGENT")
    
    ###
def add_imp_and_not_urgent():
    TabControl3 = ttk.Frame(notebook)
    notebook.add(TabControl3, text = "I + NU")
    notebook.grid(row = 0, column = 0, sticky = "e")
def add_not_import_and_urg():
    TabControl4 = ttk.Frame(notebook)
    notebook.add(TabControl4, text = "NI + U")
    notebook.grid(row = 0, column = 0, sticky = "e")
def add_not_both():
    TabControl5 = ttk.Frame(notebook)
    notebook.add(TabControl5, text = "NI + NU")
    notebook.grid(row = 0, column = 0, sticky = "e")
#linn = tk.PhotoImage("C:\\Users\\judeh\\Downloads\\png2jpg\\runcouple.")
#maya = tk.PhotoImage(frameya,file = "C:\\Users\\judeh\\Family\\runcouple.png")
#button_maya = ttk.Button(frameya, image = linn)
#button_maya.pack()


#add notebook
content = ""
title = "All"
yay = "-\n"
text_area = tk.Text(notebook)
text_area.config(font = ("arial", 17, "bold"))
text_area.insert("end", content)
#text_area.pack(fill= "both", expand = True)
text_area.pack()
notebook.add(text_area, text = title)
notebook.select(text_area)
for i in range(15):
    text_area.insert("end", yay)
    
def dad_imp_and_not_urg(content = "", title = "untitled"):
    text_area = tk.Text(notebook)
    text_area.config(font = ("arial", 17, "bold"))
    text_area.insert("end", content)
    #text_area.pack(fill= "both", expand = True)
    text_area.pack()
    notebook.add(text_area, text = title)
    notebook.select(text_area)

#add actual notebook
#def existing_file(frame_name, title):
#    frame_name = ttk.Frame(notebook)
#    new_text_area = tk.Text(frame_name)
#    title = Label(new_text_area, font = ("arial", 17, "bold"))
#    notebook.add(frame_name)
    #content = 

#existing_file(TabControl1, title = "")


menubar = tk.Menu()
root.config(menu = menubar)

#dropdown
file_menu= tk.Menu(menubar)
menubar.add_cascade(menu = file_menu, label = "File")

file_menu.add_command(label = "New", command = create_file, accelerator = "Ctrl+N")
file_menu.add_command(label = "Open...", command = open_file, accelerator = "Ctrl+O")
file_menu.add_command(label = "Save", command = save_file, accelerator = "Ctrl+S")
#####shortcuts when you don't have the menu clicked
#as long as this window is open (root) it will take effect
#not executing create file, that only happens when lambda gets executed which happens when ctrln clicked

root.bind("<Control-n>", lambda event: create_file())
root.bind("<Control-o>", lambda event: open_file())
root.bind("<Control-s>", lambda event: open_file())
#create_file()
#create_file()
 



b = Button(root, text = "Imp + Urgent", relief = GROOVE, bg = "#232323", fg = "white", command = add_imp_and_urg("","Important and Urgent"))
b.pack(side = "left", padx = 20, pady = 24)
b.config(width = 16, height= 6)

b = Button(root, text = "Imp + Non-Urgent", relief = GROOVE, bg = "#232323", fg = "white", command = dad_imp_and_not_urg("", "Important + Non-Urgent"))
b.pack(side = "left", padx = 20, pady = 24)
b.config(width = 16, height= 6)

b = Button(root, text = "Not Imp + Urgent", relief = GROOVE, bg = "#232323", fg = "white")
b.pack(side = "left", padx = 20, pady = 24)
b.config(width = 16, height= 6)

b = Button(root, text = "Non-Imp + Non-Urg", relief = GROOVE, bg = "#232323", fg = "white")
b.pack(side = "left", padx =20, pady = 24)
b.config(width = 16, height= 6)

###lb = Button(root, text = "", relief = GROOVE, bg = "#232323", fg = "white")
#lb.pack(side = "left", padx = 20)
#lb.config(width = 16, height= 6)

progressbar = ttk.Progressbar(root, orient = HORIZONTAL, length = 500)
#length = 600
progressbar.pack(side = "left", padx = 70)
b.config(width = 16, height= 6)



root.mainloop()
