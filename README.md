# <p style="color:blue;"> Wooden Sticks </p>
<ul>
  <li> Trc hết xem xét bài Chia dãy, một cách tóm tắt nhất, bài này hỏi: Số lis mà mảng A ban đầu tách ra được <b> ít nhất </b> là bao nhiêu? Vấn đề này sẽ giải quyết bằng cách tìm <i> dãy con giảm dài nhất </i> của mảng A ( do mỗi phần tử trong dãy giảm này ko thể ghép với phần tử nào có chỉ số thấp hơn cùng trong dãy này, để tạo thành 1 lis nào đó, như vậy mỗi phần tử trg <i> dãy con giảm dài nhất </i> phải nằm trong các lis khác nhau) </li>
  <li> Quay trở lại với bài này, bài hỏi tương tự với bài Chia dãy, nhưng các phần tử trong lis phải lớn hơn phần tử trc nó theo cả 2 chiều ( chiều <i> .first() </i> và chiều <i> .second() </i> Như vậy, ta chỉ cần sort chiều <i> .first() </i> cho dãy ban đầu, và tìm <i> dãy con giảm dài nhất </i> theo chiều <i> .second() </i> tương tự bài Chia dãy</li>
</ul>

# Code mẫu nè:
```cpp
#include <bits/stdc++.h>
#define int long long
#define st first
#define nd second
#define pb push_back
#define lb lower_bound
#define pii pair<int,int>
#define for1(i,a,b) for(int i=a; i<=b; i++)
#define for2(i,a,b) for(int i=a; i>=b; i--)
#define endl '\n'
using namespace std;
const int mod = 1e9 + 7;
const int maxn = 5007;

int n,f[maxn],a[maxn];
pii p[maxn];

void program(){
    cin >> n;
    for1(i,1,n){
        cin >> p[i].st >> p[i].nd;
        f[i] = 0;
    }
    sort(p + 1, p + 1 + n);
    for1(i,1,n) a[i] = p[i].nd;
    
    int res = 1;
    a[0] = mod;
    f[1] = 1;
    for1(i,2,n){
        int l = 0, r = res, sav = -1;
        while(l<=r){
            int mid = (l + r)/2;
            if(a[f[mid]]>a[i]){
                sav = mid;
                l = mid + 1;
            }
            else r = mid - 1;
        }
        if(sav==res) f[++res] = i;
        else{
            sav++;
            if(a[f[sav]]<a[i]) f[sav] = i;
        }
    }
    cout << res << endl;
    
}
signed main(){
    ios_base::sync_with_stdio(false);cin.tie(0);
    int query = 1;
    cin >> query;
    while(query--) program();
}
```

# <p style="color:blue;"> Card Sorting </p>

<ul>
  <li> Đề dễ nên tự đọc nhé :))</li>
  <li> Với bài này, ta chỉ cần <b>sinh hoán vị thứ tự</b> của các màu (do chỉ có tối đa 4 màu nên đpt hoán vị tối đa là 4!=24), sau đó với mỗi thứ tự các màu, ta tìm độ ưu tiên của các lá bài, lá nào sẽ xếp lên đầu,... Như vậy với mỗi trường hợp sinh ra, ta chỉ cần tìm <i>lis</i> của <i>n*c</i> lá bài đó, thì số lần chuyển lá bài sẽ là <i> n - lis </i>. Tìm ans là min của các trường hợp thôi :3 
</ul>

# Code mẫu nè
```cpp
#include <bits/stdc++.h>
#define int long long
#define st first
#define nd second
#define pb push_back
#define lb lower_bound
#define pii pair<int,int>
#define for1(i,a,b) for(int i=a; i<=b; i++)
#define for2(i,a,b) for(int i=a; i>=b; i--)
#define endl '\n'
using namespace std;
const int mod = 1e9 + 7;
const int maxn = 1007;

int n,c,x[5],ans,f[maxn],a[maxn];
pii p[maxn];

void solve(){
    // x : 3 1 2 4 : x[1] = 3 -> color 1 xep thu 3
    
    for1(i,1,n) a[i] = p[i].nd + n/c*(x[p[i].st] - 1);
    
    int res = 1;
    f[1] = 1;
    
    for1(i,2,n){
        int l = 0, r = res, sav = -1;
        while(l<=r){
            int mid = (l + r)/2;
            if(a[f[mid]]<a[i]){
                sav = mid;
                l = mid + 1;
            }
            else r = mid - 1;
        }
        if(sav==res) f[++res] = i;
        else{
            sav++;
            if(a[f[sav]]>a[i]) f[sav] = i;
        }
        
    }
    ans = max(ans,res);
    
}
void program(){
    cin >> c >> n;
    n*=c;
    for1(i,1,n){
        cin >> p[i].st >> p[i].nd;
    }
    
    int turn = 1;
    for1(i,1,c){
        turn*=i;
        x[i] = i;
    }
    
    while(turn--){
        next_permutation(x + 1, x + 1 + c);
        solve();
    }
    cout << n - ans;
    
}
signed main(){
    //freopen(".INP","r",stdin);
    //freopen(".OUT","w",stdout);
    ios_base::sync_with_stdio(false);cin.tie(0);
    int query = 1;
    //cin >> query;
    while(query--) program();
}
```
