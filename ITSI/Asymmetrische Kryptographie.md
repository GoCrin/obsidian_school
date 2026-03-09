Siehe geschicktes Skriptum.

## gcd / ggt

ggt(84, 30) = ggt(24,30) = ggt(24,6) = ggt(0,6) = 6
Das passiert mit a % b = a_2 (wobei a die größere Zahl ist), dieser vorgang endet wenn a_2 = 0
```python
print("a = ", end="")
input1 = int(input())

print("b = ", end="")
input2 = int(input())

a = input1
b = input2

while True:
    aTwo = max(a,b)
    bTwo = min(a,b)

    if aTwo != 0 | bTwo != 0:
        a = aTwo % bTwo
        b = bTwo
    else:
        break

solution = max(a,b)
print(f"ggt({input1},{input2}) = {solution}")
```


## erweiterte euklidescher Algorithmus

$$ggT(r_0,r_1) = sr_0 + tr_1$$
Man kann den euklidischen Algorithmus auch verwenden um s und t zu bestimmen.

ggt(973,301) = 7

973=3\*301 + 70
301=4\*70+21
70=3\*21+7
21=3\*7+0
ggt=7

Umgeformt

70=973-3\*301
21=301-4\*70
21=301-4\*(973-3\*301)
21=-4\*973+13\*301
7=70-3\*21
7=70-3\*(-4\*973+13\*301)
7=973-3\*301 - 3\*(-4\*973+13\*301)
7=973-3\*301 + 12\*973-39\*301
7=13\*973-42\*301
s = 13
t = -42

## invers mod

$12^{-1}\ \%\ 67$
ggT(12,67)=1

67 = 5.0 \* 12 + 7
12 = 1.0 \* 7 + 5
7 = 1.0 \* 5 + 2
5 = 2.0 \* 2 + 1
2 = 2.0 \* 1 + 0



