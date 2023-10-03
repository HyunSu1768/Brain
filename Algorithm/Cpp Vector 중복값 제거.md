# Cpp Vector 중복값 제거

```
#include <bits/stdc++.h>
using namespace std;

int main(){
    vector<int> vec;
    vec.push_back(1);
    vec.push_back(2);
    vec.push_back(3);
    vec.push_back(1);
    vec.push_back(2);
    vec.push_back(3);

    cout << "지우기 전 결과입니다." << "\n";
    for(int i : vec){
        cout << i << " ";
    }
    cout << "\n";
    sort(vec.begin(), vec.end());
    vec.erase(unique(vec.begin(), vec.end()), vec.end());
    cout << "지우고 난 뒤 결과입니다." << "\n";
    for(int i : vec){
        cout << i << " ";
    }
    cout << "\n";
}
``` 

vector의 erase 와 unique 함수를 사용해서 제거합니다.