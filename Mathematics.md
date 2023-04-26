**Binary exponentiation**
```cpp
ll binpow(ll a, ll b) {
    ll result = 1;
    while (b > 0) {
        if (b & 1)
            result *= a;
        a *= a;
        a %= mod;
        b /= 2;
        result %= mod;
    }
    return result;
}// add %mod to prevent overflow
```
**Modular Inverse**
```cpp
int inv(int x) {
    return binpow(x, mod - 2); // use the inverse as normal multiplication
}
```


