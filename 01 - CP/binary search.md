```int st = 0, end = x;
while (st < end) {
    int mid = (st + end) / 2;
    if ((i64)mid * mid < x)
        st = mid + 1;
    else
        end = mid;
}
return end;

```
this approach finds smallest r which is bigger than x, r * r >= x;
how -> let suppose end approach a number then st gets mid + 1 and mid is our ans only then end never comes to mid again

```
int st = 0, end = x;
while (st <= end) {
    int mid = (st + end) / 2;
    if ((i64)mid * mid <= x)
        st = mid + 1;
    else
        end = mid - 1;
}
return end;

```
this will correctly return floor(sqrt(x))