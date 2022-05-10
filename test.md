# Educational Codeforces Round 126 (Rated for Div. 2)

## A - Array Balancing
```c=
#include <iostream>
#include <string.h>
#include <algorithm>
#define MAXN 200005
#define INF 0x3f3f3f3f3f3f3f
#define int long long
using namespace std;
 
int t, n;
int a[MAXN], b[MAXN];
 
int32_t main(void){
    cin >> t;
    while(t--){
        cin >> n;
        for (int i = 1; i <= n; i++)
            cin >> a[i];
        for (int i = 1; i <= n; i++)
            cin >> b[i];
        for (int i = 2; i <= n; i++){
            int sum1 = abs(a[i-1] - a[i]) + abs(b[i-1] - b[i]);
            int sum2 = abs(b[i-1] - a[i]) + abs(a[i-1] - b[i]);
            if(sum1>sum2){
                int temp = a[i];
                a[i] = b[i];
                b[i] = temp;
            }
        }
        int ans = 0;
        for (int i = 1; i < n; i++){
            ans += abs(a[i] - a[i + 1]);
            ans += abs(b[i] - b[i + 1]);
        }
        cout << ans << '\n';
    }
}
```

## B - Getting Zero
注意：有些時候還是需要聰明的暴力解
```c=
#include <iostream>
#include <string.h>
#include <algorithm>
#define MAXN 200005
#define INF 0x3f3f3f3f3f3f3f
#define int long long
using namespace std;
 
pair<int,int> toPow(int a){
    int temp = 1;
    int cnt = 0;
    while(temp<=a){
        cnt++;
        temp *= 2;
    }
    cnt--;
    temp /= 2;
    return {cnt, temp};
}
 
int n;
 
int32_t main(void){
    cin >> n;
    int a;
    while(n--){
        cin >> a;
        int ans = INF;
        for (int i = 0; i <= 15; i++){
            int temp = i;
            int cur = a + i;
            while(cur%32768!=0){
                cur *= 2;
                temp++;
            }
            ans = min(ans, temp);
        }
        cout << ans << '\n';
    }
}
```