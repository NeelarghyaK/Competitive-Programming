# AM > GM > HM INEQUALITY
https://en.wikipedia.org/wiki/HM-GM-AM-QM_inequalities

# CAUCHY SCHWARZ INEQUALITY
https://mathworld.wolfram.com/CauchysInequality.html

# CHEBYSHEF INEQUALITY
https://brilliant.org/wiki/chebyshev-inequality/

# TITU'S LEMMA 
https://brilliant.org/wiki/titus-lemma/

# Binary exponentiation
```cpp
int power(int a , int b){
int result=1;
while(b>0)
{
if(b&1){
result*=a;
}
a*=a;
b/=2;
}
return result;
}
```

