# Mark@jervelund.com

##----------------------------------------------------------------------------------
##Configures turtle world
##----------------------------------------------------------------------------------
from swampy.TurtleWorld import *
#import time
#import random
w = TurtleWorld()
t = Turtle()
t.set_delay(0.00001)
##----------------------------------------------------------------------------------
#moves to the start location
##----------------------------------------------------------------------------------
i = 3
pu(t)
fd(t,0000)
rt(t,90)
fd(t,300)
pd(t)
lt(t,90)
##colorlist = ["red", "blue", "green", "yellow", "Violet", "orange"]
##set_pen_color(t,colorlist[0])

##----------------------------------------------------------------------------------
#opens the file and prints the content from the file
##----------------------------------------------------------------------------------
fdlfile = open('tree.fdl')
#prints the file content 
print open('tree.fdl').read()

##----------------------------------------------------------------------------------
#gets commands, and rules from the file
##----------------------------------------------------------------------------------
#def get_rules(fdlfile)
rules = {}
cmd = {}
for line in fdlfile:
    #reads that start value from the file
    if line[0:5] == "start":
        start = (line[6:].rstrip('\n')).split()
    #reads the rules from the file and adds them to a list
    elif line[0:4] == "rule":
        rulesholder = []
        rules[line[5]]=((line[9:]).rstrip('\n')).split()
    #reads the lengt from the file
    elif line[0:6] == "length":
        length = line[7:].rstrip('\n')
        length = float(length)
    # reads the depth from the file
    elif line[0:5] == "depth":
        depth = line[6:].rstrip('\n')
        depth = int(depth)
        #depth = 3
    #reads the commands from the file and adds them to a list
    elif line[0:3] == "cmd":
        cmdholder = []
        ##handling of forewards and backwards commands
        if line[6:8] == "fd" or line[6:8] == "bk":
            cmd[line[4]]= line[6:8]+"(t,length)"
            print cmd
        ##handling of scale command 
        elif line[6:9] == "sca":
            cmd[line[4]]= "length = length *"+((line[11:].rstrip('\n')))
            print cmd
        elif line[6:9] == "nop":
            pass
        ##handling of turning commands
        else:
            ags = (line[9:]).rstrip('\n')
            cmd[line[4]]= line[6:8]+"(t,"+ags+")"
##            print cmd
    else:
        print "unknown command ", line
##----------------------------------------------------------------------------------
#Applies the rules to the start list and add them to the commands list.
##----------------------------------------------------------------------------------
#def applyrules(start,rules,depth)
commands = start
    
while depth > 0:
    depth -= 1
    print depth," Done"
    newcommands = []
    
    for item in commands:
        if item in rules:
            for i in rules[item]:
                newcommands.append(i)
        else:
            newcommands.append(item)
    commands = newcommands
      
#debugging to see if it converts the commands as it should           
#print commands

##----------------------------------------------------------------------------------
#Applies the commands from and the commands list.
##----------------------------------------------------------------------------------    
for item in commands:
    if item in cmd:
        exec(cmd[item])
        
      
wait_for_user()

