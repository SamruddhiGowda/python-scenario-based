given a sorted array aar of size N and a number X , you need to find the number of occurances of X in arr.
eg 1:
input: N = 7,X = 2
arr[] = {1,1,2,2,2,2,3}
output:4
explanation: 2 occurs 4 times in the given array.
eg2:
input: N= 7, X = 4
arr[]= {1,1,2,2,2,2,3}
output: 0
explanation:4 is not present in the given array
expected time complexity:0(logN) expected auxiliary space:0(1)
constraints : 1<=N<=1051<=arr[i]<=1061<=X<=106

def findFirstOccurrence(arr, X):
    low, high = 0, len(arr) - 1
    result = -1

    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == X:
            result = mid
            high = mid - 1
        elif arr[mid] < X:
            low = mid + 1
        else:
            high = mid - 1
    return result

def findLastOccurrence(arr, X):
    low, high = 0, len(arr) - 1
    result = -1

    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == X:
            result = mid
            low = mid + 1
        elif arr[mid] < X:
            low = mid + 1
        else:
            high = mid - 1
    return result

def countOccurrences(arr, X):
    first = findFirstOccurrence(arr, X)
    last = findLastOccurrence(arr, X)

    if first == -1:
        return 0
    return last - first + 1
N = int(input("Enter the size of the array (N): "))
arr = list(map(int, input("Enter the elements of the array: ").split()))
X = int(input("Enter the number to find the occurrences of (X): "))
occurrences = countOccurrences(arr, X)
print(f"Number of occurrences of {X}: {occurrences}")


addition without + or sum

a = int(input("Enter the first number: "))
b = int(input("Enter the second number: "))
sum = a-(-b)
print (sum)

division of 2 number without using mod and division
test case : 13 2 op: 6
14 -2 op:-7
-11 2 op:-5

def divide(a, b):
    if b == 0:
        raise ValueError("Division by zero is not allowed")
    negative = False
    if a < 0:
        a = -a
        negative = not negative
    if b < 0:
        b = -b
        negative = not negative
    quotient = 0
    while a >= b:
        a -= b
        quotient += 1
    if negative:
        quotient = -quotient
    return quotient, a
a = int(input("Enter the dividend (a): "))
b = int(input("Enter the divisor (b): "))
quotient, remainder = divide(a, b)
print(f"The quotient when {a} is divided by {b} is: {quotient}")
print(f"The remainder when {a} is divided by {b} is: {remainder}")

given a number N , the task is to find the largest pri
me factor of that number .
ex 1:
input : N=5
output 5
ex 2:
input :N = 24
output : 3

def lpf(N):
    if N <= 1:
        return None
    lp = None
    while N % 2 == 0:
        lp = 2
        N //= 2
    for i in range(3, int(N**0.5) + 1, 2):
        while N % i == 0:
            lp = i
            N //= i
    if N > 2:
        lp = N
    return lp
N = int(input("Enter a number (N): "))
result = lpf(N)
if result:
    print(f"The largest prime factor of {N} is: {result}")
else:
    print(f"No prime factors for the number {N}")
