# Car-Game

from random import *

print("Game started")

pumps = [randint(1,30)]
sorts = [randint(1,30)]
dirs = [choice(["F","B"])]
movs = [randint(5,10)]
pits = [randint(1,40)]

init_petrol = 30
i = 0
for x in range(4):
    pumps.append(randint(pumps[i],100))
    sorts.append(randint(sorts[i],100))
    dirs.append(choice(["F","B"]))
    movs.append(randint(5,10))
    if x<2:
        pits.append(randint(pits[i],100))
    i = i+1

print("Petrol pumps generated at:", pumps)
print ("Shortcuts generated at:", sorts)
print("sortcuts directions:", dirs)
print("moves in sortcut:", movs)
print ("Pits generated at:", pits)

def my_fun(init_petrol,step):
    mv = 0
    ran = 0
    remain_petrol = init_petrol
    while True:
        if mv in sorts:
            print("takes sortcut")
            ind = sorts.index(mv)
            print("moves",dirs[ind])
            remain_petrol = remain_petrol - movs[ind]
            if remain_petrol == 0:
                print("step=",step,"move=",movs[ind], "car at=",mv,"petrol remains =",remain_petrol)
                print("game over : no petrol")
                break
            elif remain_petrol < 0:
                print("game over: no petrol")
                break
            
            step = step + 1
            if dirs[ind] == "B":
                mv = mv - movs[ind]
                if mv in pits:
                    print("step=",step,"move=",movs[ind], "car at=",mv,"petrol remains =",remain_petrol)
                    print("game over : pit comes")
                    break
                elif mv >= 100:
                    print("step=",step,"move=",mov[ind], "car at=",mv,"petrol remains =",remain_petrol)
                    print("reached : 100km")
                    break
                print("step=",step,"move=",movs[ind], "car at=",mv,"petrol remains =",remain_petrol)

            else:
                mv = mv + movs[ind]
                if mv in pits:
                    print("step=",step,"move=",movs[ind], "car at=",mv,"petrol remains =",remain_petrol)
                    print("game over : pit comes")
                    break
                elif mv >= 100:
                    print("step=",step,"move=",movs[ind], "car at=",mv,"petrol remains =",remain_petrol)
                    print("reached : 100km")
                    break
                print("step=",step,"move=",movs[ind], "car at=",mv,"petrol remains =",remain_petrol)
               
            init_petrol = remain_petrol
            

        else:
            remain_petrol = init_petrol
            if mv in pits:
                
                print("game over : pit comes")
                break
            elif mv >= 100:
                
                print("reached : 100km")
                break
            elif remain_petrol == 0:
                
                print("game over : no petrol")
                break
            elif remain_petrol < 0:
                print("game over: no petrol")
                break
            else:
                if mv in pumps:
                    print("petrol pump : petrol added")
                    remain_petrol = remain_petrol + 20
                    step = step + 1
                    ran = randint(0, 6)
                    mv = mv + ran
                    remain_petrol = remain_petrol - ran

                    print("step=", step, "move=", ran, "car at=", mv, "petrol remains =", remain_petrol)
                else:
                    step = step+1
                    ran = randint(0,6)
                    mv = mv + ran
                    remain_petrol = remain_petrol - ran
                    print("step=",step,"move=",ran, "car at=",mv,"petrol remains =",remain_petrol)
            init_petrol = remain_petrol
            
            """
             dirr = choice("F","B")
            mov = randint(5,10)
            ran1 = mov
            """


my_fun(30,0)
