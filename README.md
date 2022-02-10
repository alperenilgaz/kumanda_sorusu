# kumanda_sorusu
--------------------------
import random
import time


class Control():
    def __init__(self,tv_situation="close",tv_sound=0,channel_list = ["trt"],channel="trt"):
        self.tv_situation=tv_situation
        self.tv_sound=tv_sound
        self.channel_list=channel_list
        self.channel=channel

    def tv_open(self):
        if(self.tv_situation=="open"):
            print("tv  already open")
        else:
            print("tv is opening")
            time.sleep(1)
            print("tv turned on")
            self.tv_situation="on"

    def tv_close(self):
        if(self.tv_situation=="close"):
            print("tv already close")
        else:
            print("tv turns off")
            time.sleep(1)
            print("tv turned off")
            self.tv_situation="off"

    def Tv_sound(self):

        while True:
            answer=input("turn up the voice : '+'\nturn down the voice : '-'\nexit : exit")
            if(answer=="+"):
                if(self.tv_sound!=100):
                    self.tv_sound+=1
                    print("sound : ",self.tv_sound)
            elif(answer=="-"):
                if(self.tv_sound!=0):
                    self.tv_sound-=1
                    print("sound : ",self.tv_sound)
            else:
                print("the sound has been updated...",self.tv_sound)
                break

    def add_channel(self,name_channel):
        print("adding channel...")
        time.sleep(1)
        self.channel_list.append(name_channel)
        print("channel added")


    def random_channel(self):
        crandom=random.randint(len(0,self.channel_list)-1)
        self.channel=self.channel_list[crandom]
        print("current channel",self.channel_list)

    def __len__(self):
        return  len(self.channel_list)

    def __str__(self):

        return  "tv situation : {}\ntv sound : {}\nchannel list : {}\nchannel :{}\n".format(self.tv_situation,self.tv_sound,self.channel_list,self.channel)


control=Control()

print("""

tv app
------
1)turn on tv

2)turn off tv

3)sound settings

4)add channel

5)find out channel number

6)switch to random channel

7)tv information

pree to exit 'q'
""")

while True:
    operation=input("select operation")

    if(operation=="q"):
        print("program is terminated...")
        break
    elif(operation=="1"):
        control.tv_open()
    elif(operation=="2"):
        control.tv_close()
    elif(operation=="3"):
        control.Tv_sound()
    elif(operation=="4"):
        channel_name=input("Enter channel names separated by ','")
        channel_list=channel_name.split(",")
        for will_be_added in channel_list:
            control.add_channel(will_be_added)

    elif(operation=="5"):
        print("channel number : ",len(control))
    elif(operation=="6"):
        control.random_channel()
    elif(operation=="7"):
        print(control)
    else:
        print("Incorrect operation....")
