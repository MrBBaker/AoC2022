import copy

readfrom, gap, piles = ["input.txt", 9, 9]
#readfrom, gap, piles = ["test.txt", 4, 3]

#Splitting file into two parts
with open(readfrom) as f:
  lines1 = [line[:-1] for line in f.readlines()[:gap]]

with open(readfrom) as f:
  lines2 = [line[:-1].split(" ") for line in f.readlines()[gap+1:]]
  
#Clean stack data into lists
stacks = [[] for i in range(piles)]
for line in lines1[:-1]:
  for index, value in enumerate(line):
    if index % 4 != 1 or value == " ":
      continue
    stacks[int((index - 1) / 4)].append(value)

#Ensure stacks are bottom to top, and one set per puzzle
for stack in stacks:
  stack.reverse()
stacks1 = copy.deepcopy(stacks)
stacks2 = copy.deepcopy(stacks)
  
#Move boxes
for line in lines2:
  
  #Clean inputs
  take = int(line[3]) - 1
  put = int(line[5]) - 1
  num = int(line[1])

  #Grab boxes one at a time
  for i in range(num):
    stacks1[put].append(stacks1[take].pop())
  
  #Grab all boxes and place in order
  move = stacks2[take][-num:]
  for i in move:
    stacks2[put].append(i)
  del stacks2[take][-num:]
  
#Print top boxes
tops1 = ""
tops2 = ""
for i in stacks1:
  tops1 += i[-1]
for i in stacks2:
  tops2 += i[-1]
print(tops1)
print(tops2)

