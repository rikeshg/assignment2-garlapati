# Rikesh garlapati
  I am rikesh garlapati.I am from India,Andhra pradesh state.My hobbies are watching movies, playing cricket.<br>I completed my graduation from Kallam harinatha reddy institute of technology.I had a experience as a software engineer for 3 years in CES technoligies and solutins.I quit my job for my masters degree to gain extra knowledge in my field.<br><br>

![my picture](/rikesh.jpeg?raw=true)

---

# Food/Drinks

following table illustrates the beverages cost and locations where we can get.

| Food/Drinks | location | amount |
|-------------|----------|--------|
|    burger   |    Mcd   | 1.5usd |
|    coke     |    Mcd   | 2.5usd |
| french fries|  tachos  | 3.0usd |
|   sprite    |    Mcd   | 2.5usd |


>The purpose of our lives is to be happy. — *Dalai Lama*

>Life is what happens when you’re busy making other plans. — *John Lennon*

---

# String Processing 
> Dynamic programming is both a mathematical optimization method and a computer programming method. The method was developed by Richard Bellman in the 1950s and has found applications in numerous fields, from aerospace engineering to economics.<br><br>

In both contexts it refers to simplifying a complicated problem by breaking it down into simpler sub-problems in a recursive manner. While some decision problems cannot be taken apart this way, decisions that span several points in time do often break apart recursively. Likewise, in computer science, if a problem can be solved optimally by breaking it into sub-problems and then recursively finding the optimal solutions to the sub-problems, then it is said to have optimal substructure.<br><br>

If sub-problems can be nested recursively inside larger problems, so that dynamic programming methods are applicable, then there is a relation between the value of the larger problem and the values of the sub-problems.[1] In the optimization literature this relationship is called the Bellman equation. 

[Source](https://en.wikipedia.org/wiki/Dynamic_programming)

```
int m, n;
vector<long long> dp_before(n), dp_cur(n);

long long C(int i, int j);

// compute dp_cur[l], ... dp_cur[r] (inclusive)
void compute(int l, int r, int optl, int optr) {
    if (l > r)
        return;

    int mid = (l + r) >> 1;
    pair<long long, int> best = {LLONG_MAX, -1};

    for (int k = optl; k <= min(mid, optr); k++) {
        best = min(best, {(k ? dp_before[k - 1] : 0) + C(k, mid), k});
    }

    dp_cur[mid] = best.first;
    int opt = best.second;

    compute(l, mid - 1, optl, opt);
    compute(mid + 1, r, opt, optr);
}

int solve() {
    for (int i = 0; i < n; i++)
        dp_before[i] = C(0, i);

    for (int i = 1; i < m; i++) {
        compute(0, n - 1, 0, n - 1);
        dp_before = dp_cur;
    }

    return dp_before[n - 1];
}
```
[Source](https://cp-algorithms.com/dynamic_programming/divide-and-conquer-dp.html)