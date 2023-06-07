import matplotlib.pyplot as plt
import math
import csv

# B = benign(not cancerous)
# M = malignant(cancerous)

x = [] #radius B    
y = [] #texture B

x2 = [] #radius M
y2 = [] #texture M

#loading data
with open('training.csv','r') as csv_file:
    csv_reader = csv.DictReader(csv_file)
    for line in csv_reader:
        if(line["diagnosis"] == "B"):
            x.append(float(line['radius_mean']))
            y.append(float(line["texture_mean"]))
        else:
            x2.append(float(line['radius_mean']))
            y2.append(float(line["texture_mean"]))
plt.scatter(x,y,label = "benign",color = "blue")
plt.scatter(x2,y2,label = "malignant",color = "red")

# these below are the radius and texture of a tumor we are trying to pridict
targetx = 20.92
targety = 25.09
plt.scatter(targetx,targety,label = "testcase",color = "black")

#distance[] is storing distances of all the scater points from the target
distance = []

for i in range(len(x)):
    test = (math.sqrt((targetx - x[i])**2 + (targety - y[i])**2)),"benign"
    distance.append(test)
for i in range(len(x2)):
    test = (math.sqrt((targetx - x2[i])**2 + (targety - y2[i])**2)),"malignant"
    distance.append(test)


# getting k nearest point from the target OR one can say TRAINING THE MODEL
k = 7
final_voting = []
while k > 0:
    minimum = 101
    last_index = 0
    for i in range(len(distance)):
        if(distance[i][0] < minimum):
            minimum = distance[i][0]
            last_index = i
    k = k-1
    final_voting.append(distance[last_index][1])
    print(minimum,distance[last_index][1])
    del distance[last_index]

#chossing the majority 
class_1 = 0
class_2 = 0

for i in final_voting:
    if(i == "benign"):
        class_1+=1
    else:
        class_2+=1

if(class_1 > class_2):
    print("Result : BENIGN")

else:
    print("Result : MALIGNANT")

#for ploting purposes
plt.xlabel("tumor_radius_mean")
plt.ylabel("tumor_texture_mean")
plt.legend()
plt.title("Cancer Detection")
plt.show()



