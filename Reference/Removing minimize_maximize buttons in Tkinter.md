---
_Source URL: [](https://stackoverflow.com/questions/2969870/removing-minimize-maximize-buttons-in-tkinter)._

tags: 
- '#python #tkinter'

---

# Removing minimize/maximize buttons in Tkinter


 7  [favorite](https://stackoverflow.com/questions/2969870/removing-minimize-maximize-buttons-in-tkinter#)
**1**

I have a python program which opens a new windows to display some 'about' information. This window has its own close button, and I have made it non-resizeable. However, the buttons to maximize and minimize it are still there, and I want them gone.

I am using Tkinter, wrapping all the info to display in the Tk class.

The code so far is given below. I know its not pretty, and I plan on expanding the info making it into a class, but I want to get this problem sorted before moving along.

Anyone know how I can govern which of the default buttons are shown by the windows manager?

    def showAbout(self):
    
    
        if self.aboutOpen==0:
            self.about=Tk()
            self.about.title("About "+ self.programName)
    
            Label(self.about,text="%s: Version 1.0" % self.programName ,foreground='blue').pack()
            Label(self.about,text="By Vidar").pack()
            self.contact=Label(self.about,text="Contact: adress@gmail.com",font=("Helvetica", 10))
            self.contact.pack()
            self.closeButton=Button(self.about, text="Close", command = lambda: self.showAbout())
            self.closeButton.pack()
            self.about.geometry("%dx%d+%d+%d" % (175,\
                                            95,\
                                            self.myParent.winfo_rootx()+self.myParent.winfo_width()/2-75,\
                                            self.myParent.winfo_rooty()+self.myParent.winfo_height()/2-35))
    
            self.about.resizable(0,0)
            self.aboutOpen=1
            self.about.protocol("WM_DELETE_WINDOW", lambda: self.showAbout())
            self.closeButton.focus_force()
    
    
            self.contact.bind('<Leave>', self.contactMouseOver)
            self.contact.bind('<Enter>', self.contactMouseOver)
            self.contact.bind('<Button-1>', self.mailAuthor)
        else:
            self.about.destroy()
            self.aboutOpen=0
    
    def contactMouseOver(self,event):
    
        if event.type==str(7):
            self.contact.config(font=("Helvetica", 10, 'underline'))
        elif event.type==str(8):
            self.contact.config(font=("Helvetica", 10))
    
    def mailAuthor(self,event):
        import webbrowser
        webbrowser.open('mailto:adress@gmail.com',new=1)

[python](https://stackoverflow.com/questions/tagged/python) [windows](https://stackoverflow.com/questions/tagged/windows) [tkinter](https://stackoverflow.com/questions/tagged/tkinter)

|     |     |     |
| --- | --- | --- |
| [share](https://stackoverflow.com/q/2969870)\|[improve this question](https://stackoverflow.com/posts/2969870/edit) | [edited Jul 12 '17 at 15:34](https://stackoverflow.com/posts/2969870/revisions)<br>[![[2d8cb0eaa4de7f781e42328ec7544ca3.jpg]]](https://stackoverflow.com/users/1000551/vadim-kotov)<br>[Vadim Kotov](https://stackoverflow.com/users/1000551/vadim-kotov)<br>**3,304**52743 | asked Jun 3 '10 at 21:20<br>[![[0RTYG.png]]](https://stackoverflow.com/users/346645/vidar)<br>[Vidar](https://stackoverflow.com/users/346645/vidar)<br>**2,894**41628 |

## 1 Answer

[active](https://stackoverflow.com/questions/2969870/removing-minimize-maximize-buttons-in-tkinter?answertab=active#tab-top) [oldest](https://stackoverflow.com/questions/2969870/removing-minimize-maximize-buttons-in-tkinter?answertab=oldest#tab-top) [votes](https://stackoverflow.com/questions/2969870/removing-minimize-maximize-buttons-in-tkinter?answertab=votes#tab-top)

 22  accepted

In general, what decorations the WM (window manager) decides to display can not be easily dictated by a toolkit like Tkinter. So let me summarize what I know plus what I found:

    import Tkinter as tk
    
    root= tk.Tk()
    
    root.title("wm min/max")
    
    # this removes the maximize button
    root.resizable(0,0)
    
    # # if on MS Windows, this might do the trick,
    # # but I wouldn't know:
    # root.attributes(toolwindow=1)
    
    # # for no window manager decorations at all:
    # root.overrideredirect(1)
    # # useful for something like a splash screen
    
    root.mainloop()

There is also the possibility that, for a `Toplevel` window other than the root one, you can do:

    toplevel.transient(1)

and this will remove the min/max buttons, but it also depends on the window manager. From what I read, the MS Windows WM does remove them.

|     |     |
| --- | --- |
| [share](https://stackoverflow.com/a/2970757)\|[improve this answer](https://stackoverflow.com/posts/2970757/edit) | answered Jun 4 '10 at 0:30<br>[![[132aeb33251a1eddee3efc87633c0af1.jpg]]](https://stackoverflow.com/users/6899/tzot)<br>[tzot](https://stackoverflow.com/users/6899/tzot)<br>**56.2k**2092166 |

|     |     |
| --- | --- |
| 2   |     |

Thanks. I ended up using the overrideredirect - approach and added a ridge to the the bottom frame. Looks decent enough. – [Vidar](https://stackoverflow.com/users/346645/vidar) [Jun 5 '10 at 11:11](https://stackoverflow.com/questions/2969870/removing-minimize-maximize-buttons-in-tkinter#comment3041123_2970757)

|     |     |
| --- | --- |
| 1   |     |

root.resizable(0,0) worked for me in Ubuntu, 'm using tkinter – [RahulArackal](https://stackoverflow.com/users/1642148/rahularackal) [Mar 21 '14 at 6:12](https://stackoverflow.com/questions/2969870/removing-minimize-maximize-buttons-in-tkinter#comment34322530_2970757)

|     |     |
| --- | --- |
| 1   |     |

@tzot root.overrideredirect(1) would hide the outer frame altogether. There will be no options for close, min or max. If a code containing this line was executed, then the window will stuck to the screen forever unless the IDLE is restarded or the OS is switched off. – [Mohammed](https://stackoverflow.com/users/2228380/mohammed) [Jan 9 '15 at 20:03](https://stackoverflow.com/questions/2969870/removing-minimize-maximize-buttons-in-tkinter#comment44139056_2970757)

|     |     |
| --- | --- |
| 2   |     |

root.attributes(toolwindow=1) This command does not work in Windows. The correct command is root.attributes("-toolwindow",1). Thanks! – [Mohammed](https://stackoverflow.com/users/2228380/mohammed) [Jan 9 '15 at 20:08](https://stackoverflow.com/questions/2969870/removing-minimize-maximize-buttons-in-tkinter#comment44139220_2970757)

|     |     |
| --- | --- |
|     |     |

For anyone, who seeks more flexible windows solution, [this](https://stackoverflow.com/a/47867275/6634373) might be useful! – [CommonSense](https://stackoverflow.com/users/6634373/commonsense) [Dec 18 '17 at 13:15](https://stackoverflow.com/questions/2969870/removing-minimize-maximize-buttons-in-tkinter#comment82703590_2970757)

## Your Answer

### Sign up or [log in](https://stackoverflow.com/users/login?ssrc=question_page&returnurl=https%3a%2f%2fstackoverflow.com%2fquestions%2f2969870%2fremoving-minimize-maximize-buttons-in-tkinter%23new-answer)

Sign up using Google
Sign up using Facebook
Sign up using Email and Password

### Post as a guest

**Name**
**Email**

By posting your answer, you agree to the [privacy policy](https://stackexchange.com/legal/privacy-policy) and [terms of service](https://stackexchange.com/legal/terms-of-service).

## Not the answer you're looking for? Browse other questions tagged [python](https://stackoverflow.com/questions/tagged/python) [windows](https://stackoverflow.com/questions/tagged/windows) [tkinter](https://stackoverflow.com/questions/tagged/tkinter) or [ask your own question](https://stackoverflow.com/questions/ask).

