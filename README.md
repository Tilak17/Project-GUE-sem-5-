__author__ = 'TILAK_PUROHIT'
from tkinter import*
import csv
import tkinter.scrolledtext

root = Tk()
root.wm_title("Name Database")
top_options=[5, 10, 15, 20, 25, 30, 40, 45, 50, 60, 70, 80, 90, 100]
########################################### Widgets Used ###############################################################

year = Label(root, text='Year of Birth:', bg='grey', fg='black')
year.configure(font=('Bold',20))
top_label = Label(root, text='Display Top:', bg='grey', fg='black')
top_label.configure(font=('Bold', 20))
Search_Button = Button(text='Fetch', bg='grey', fg='black', width=20)
def settozero():
list_display.delete(0,END)
print ("done")
Reset_Button = Button(text='Reset log', bg='grey', fg='black', width=20, command=settozero)

list_display = tkinter.scrolledtext.ScrolledText(root, bg="Black", fg="Green", relief=GROOVE, height=25, width=80, state=DISABLED)
list_display.configure(font=('Italics',15))
############################################# Option_Menu ##############################################################
choice_top = StringVar(root)
top_menu = OptionMenu(root, choice_top, *top_options)
top_menu.pack()
############################################ RadioButton ###############################################################
gender = IntVar()
girl = Radiobutton(root, text='GIRL', bg='grey', fg='black', variable=gender, value=1)
boy = Radiobutton(root, text='BOY', bg='grey', fg='black', variable=gender, value=2)
both = Radiobutton(root, text='UNISEX', bg='grey', fg='black', variable=gender, value=3)

girl.configure(font=('Bold', 20))
boy.configure(font=('Bold', 20))
both.configure(font=('Bold', 20))
########################################### Entry for year #############################################################

year_entry = Entry(root, state=NORMAL, bg='white', fg='black', relief=GROOVE,  width=10)

################################################### Widgets Placements #################################################

year.grid(row=4, sticky=W, padx=20, pady=30)
year_entry.grid(row=4, sticky=W, padx=160)

top_label.grid(row=4, sticky=W, column=2, padx=80)
top_menu.grid(row=4, sticky=E ,column=2, padx=5)
top_menu.configure(width=6)

list_display.grid( padx=20, pady=10, sticky=N ,columnspan=1, rowspan=5)
list_display.configure(state=NORMAL)
list_display.insert(END,'NAMES:' )
#list_display.configure(state=DISABLED)

girl.grid(column=2,  row=6, sticky=W, columnspan=1, rowspan=1, padx=35)
boy.grid(column=2, row=7, sticky=W,  columnspan=1, rowspan=1, padx=35)
both.grid(column=2, row=8,  sticky=W, columnspan=1, rowspan=1, padx=35)


Search_Button.grid(column=2, row=9, sticky=N)
Reset_Button.grid(column=2, row=10, sticky=N,)


root.configure(background='grey')
root.maxsize(1450, 850)
root.resizable(width=FALSE, height=FALSE)


#######################################################################################################################
year='1995'
sex='male'
with open('/Users/TILAK_PUROHIT/PycharmProjects/baby_database/Data_Base/%s_cy%s_top.csv'% (sex,year)) as csvfile:
reader=csv.DictReader(csvfile)
for row in reader:
name=row['Given Name']
amount=row['Amount']
position=row['Position']
position=str(position).replace('=','')
if(int(str(position)) <= 80):
list_display.configure(state=NORMAL)
list_display.insert(END, '\n\n'+'\t\t\t\t'+name)
print("going on...")
list_display.configure(state=DISABLED)



root.mainloop()

########################################################################################################################
