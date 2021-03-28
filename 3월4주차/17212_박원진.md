## 달나라 토끼를 위한 구매대금 지불 도우미

DP 문제로 점화식을 찾아 문제를 푸시면 됩니다.
먼저 7원으로 다 지불할 수 있는지 확인 후,
현재 금액에서5원,2원,1원을 뺀 값을 비교하며 최소 동전의 갯수를 갱신화 시킵니다.

최적의 값을 갱신하며 최소 동전의 개수를 찾으시면됩니다.
```C++
#include<iostream>
#include<algorithm>
using namespace std;

int dp[1000001];
int N, coin = 0;
int main() {
	cin>>N;
	dp[1] = 1; dp[2] = 1; dp[3] = 2; dp[4] = 2; dp[5] = 1; dp[6] = 2; dp[7] = 1;
	if (N % 7 == 0)
        cout<<(N / 7)<<'\n';
	else {
		for (int i = 8; i <= N; i++) {
			if (i % 7 == 0) {
				dp[i] = i / 7;
			}
			else {
				dp[i] = min(dp[i - 5], min(dp[i - 2], dp[i - 1])) + 1;
			}
		}
		cout<<dp[N]<<'\n';
	}
	return 0;
}
```
