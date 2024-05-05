Example
k = 0
for s in open("d2.csv"):
    a = [int(x) for x in s.split(";")]
    a2 = [x for x in a if a.count(x)==4]
    a1 = [x for x in a if a.count(x) == 1]
    if len(a1) == 3 and len(a2) == 4 and  sum(a1)/3 < sum(a2)/4:
        print(a1,a2)
        k+=1
print(k)