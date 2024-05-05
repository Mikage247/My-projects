def factorial(number):
    if number == 1:
        return number
    else:
        return number * factorial(number - 1)
b=2%11
for x in range(138,200):
    if (factorial(x) // factorial(138)%11)==2:
        print(x)
