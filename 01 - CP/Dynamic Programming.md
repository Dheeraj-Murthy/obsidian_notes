- # Digit DP
```void solve() {
	string n;
	int k;
	cin >> n >> k;
	int len = n.length();

	int dp[2][2][4];
	memset(dp, 0, sizeof(dp));

	for(int i = 0; i <= n[0] - '0'; i++) {
		bool is_tight = (i == n[0] - '0');
		int occ = (i != 0);
		dp[0][is_tight][occ]++;
	}
	for(int i = 1; i < len; i++) {
		int now = i & 1;
		int last = 1 - now;

		for(int tg = 0; tg < 2; tg++) {
			int lim = tg ? n[i] - '0' : 9;
			for(int dig = 0; dig <= lim; dig++) {
				if((i & 1) && dig == d) continue;
				for(int m = 0; m < max_m; m++) {
					int new_tg = tg && (dig == lim);
					int new_m = (m + dig) % max_m;
					if(new_occ <= k) 
						dp[now][new_tg][new_m] += dp[last][tg][m];
				}
			}
		}
		memset(dp[last], 0, sizeof(dp[last]));
	}

	cout << dp[(len - 1) & 1][0][k] + dp[(len - 1) & 1][1][k];
}
```

- # Meet in the middle technique
https://cses.fi/problemset/task/1628
https://leetcode.com/problems/partition-array-into-two-arrays-to-minimize-sum-difference/description/
