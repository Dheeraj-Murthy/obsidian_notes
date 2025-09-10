- ## Enumerating Submasks
  Calculating submasks of all masks in O(3^n) 
  https://cp-algorithms.com/algebra/all-submasks.html
  very relevent to DP in which we have to divide a n members in groups 
  https://atcoder.jp/contests/dp/tasks/dp_u
  
  idea is 
```
  for(int i = 0; i < (1 << n); i++) {
	  for(int s = i; ; s = (i&(s - 1))) {
		---whatever
		if(s == 0) break;
	  }
  }
```

- if one number is submask of other number 
  a - b = (a)^(b)

1111
1000
1100
1110

i = 1001
1001
1000
0001



- ## __builtin functions
  __builtin_popcount() -> Counts the number of `1` bits in a 32-bit unsigned integer.
  __builtin_clz -> returns the number of leading `0` bits before the first `1`.
  __builtin_ctz -> returns the number of zeros following the least significant `1`.
  __builtin_parity() -> Returns 1 if the number of 1-bits is odd, else 0.
  