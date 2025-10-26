# 13
f = open("27-B (2).txt") 
s = f.readlines()
n = int(s[0])
sum = 0
dif1 = 20001
dif2 = 20001
dif3 = 20001
dif4 = 20001
count0 = 0
count1 = 0
for i in range(1, n + 1):
    x, y = map(int, s[i].split())
    if x > y:
        sum = sum + x
        if x % 2 == 0: count0 = count0 + 1
        else: count1 = count1 + 1
        if x % 2 != y % 2:
            if (x - y < dif1) and (x % 2 != 0):
                dif2 = dif1
                dif1 = x - y
            elif (x - y < dif2) and (x % 2 != 0): dif2 = x - y
            if (x - y < dif3) and (x % 2 == 0):
                dif4 = dif3
                dif3 = x - y
            elif (x - y < dif4) and (x % 2 == 0):
                dif4 = x - y
    else:
        if y % 2 == 0: count0 = count0 + 1
        else: count1 = count1 + 1
        sum = sum + y
        if x % 2 != y % 2:
            if (y - x < dif1) and (y % 2 != 0):
                dif2 = dif1
                dif1 = y - x
            elif (y - x < dif2) and (y % 2 != 0):
                dif2 = y - x
            if (y - x < dif3) and (y % 2 == 0):
                dif4 = dif3
                dif3 = y - x
            elif (y - x < dif4) and (y % 2 == 0):
                dif4 = y - x
if count1 > count0:
    if sum % 2 == 1:
        print(sum)
    elif dif3 <= dif1:
        print(sum - dif3)
    elif (count1 - count0) != 1:
        print(sum - dif1)
    elif (dif1 + dif2) < dif3:
        print(sum - dif1 - dif2)
    else: print(sum - dif3)
else:
    if sum % 2 == 0:
        print(sum)
    elif dif1 <= dif3:
        print(sum - dif1)
    elif (count0 - count1) != 1:
        print(sum - dif3)
    elif (dif3 + dif4) < dif1:
        print(sum - dif3 - dif4)
    else: print(sum - dif1)
