- `#include <bits/stdc++>` is used for including all libraries of C++. But, this takes a little more time (noticeable).

- string s;
  cin >> s;

  The above snippet takes only the first word of the input line.

  string s;
  getline(cin, s);

  The above snippet takes all the words in the line input. The next line will not be input.

- To pass the value by reference, we need to just put '&' in the argument section. For example:- 
```
  void lol (int a[])
  {
    a[0] = 69;

    return;
  }

  int main ()
  {
    int arr[3];
    arr[0] = 14;
    arr[1] = 15;
    arr[2] = 16;

    lol(arr);

    cout << arr[0] << '\n';

    return 0;
  }
```
  This will print the following:- 

`69`

- Usually on competitive programming servers, it takes nearly 1s for 10^8 operations.

- pair <int, pair <int, char>> p = {2, {6, 'c'}};
cout << p.second.first << "\n";
cout << p.first << "\n";

pair <int, int> a[] = {{1, 3}, {2, 7}, {6, 9}};
cout << a[0].first << " " << a[2].second << "\n";

- vector <int> v;
v.push_back(1);
v.emplace_back(2);    //emplace_back is a bit more faster than push_back.

vector <pair <int, int>> v1;
v1.push_back({1, 3});
v1.emplace_back(2, 5);


vector <int> v2(5, 100);    //this will declare a vector with size 5 and initialize with the value 100, that is, {100, 100, 100, 100, 100}.

vector <int> v3(5);    //this will declare a vector with 5 elements either initialized to 0 or with garbage value (this depends on the computer).

vector <int> v4(v2);    //this will copy the vector v2 in the vector v4.

cout << v[0] << " " << v.at(0) << "\n";    //v[0] and v.at(0) are both the same.


- vector <int> :: iterator it = v.begin();

In this the variable 'it' will store the address of the first element of the vector 'v' and we can access it by the following line:- 

cout << * (it) << "\n";

For accessing the next element of the vector we will add 1 to 'it'.

it++;    //it = it + 1;
cout << * (it) << "\n";

You can also do the following:- 

it = it + 2;
cout << * (it) << "\n";

v.begin()    //{3, 6, 5, 9, 8} points at 3.
v.end()    //{3, 6, 5, 9, 8} points after 8.
v.rend()    //{3, 6, 5, 9, 8} points before 3. This is very rarelly used.
v.rbegin()    //{3, 6, 5, 9, 8} points at 8. This is very rarelly used.

- v.back() points to the end element of the array. It is not associated with iterator.

- for (vector <int> :: iterator it = v.begin(); it != v.end(); it++)
{
cout << * (it) << "\n";
}

OR

for (auto it = v.begin; it != v.end(); it++)
{
cout << it << "\n";    //look at this statement carefully (no '*');
}

OR

for (auto it : v)
{
cout << it << "\n";
}

auto s = "MOHIT";
auto n = 69;
/*Both are ok.*/

- //{7, 8, 9, 0, 6, 4}
v.erase(v.begin + 1);
//{7, 9, 0, 6, 4}
v.erase(v.begin + 2, v.begin + 4);
//{7, 9, 4}

- vector <int> v(2, 100);    //{100, 100}
v.insert(v.begin(), 300);    //{300, 100, 100}
v.insert(v.begin() + 1, 2, 10);    //{300, 10, 10, 100, 100}

vector <int> copy(2, 50);    //{50, 50}
v.insert(v.begin(), copy.begin(), copy.end());    //{50, 50, 300, 10, 10, 100, 100}

// {10, 20}
cout << v.size(); // 2
//{10, 20}
v.pop_back(); // {10}
// v1 - > {10, 20}
// v2 - > {30, 40}
v1.swap(v2); // v1 - > {30, 40}, v2 - > {10, 20}
v.clear(); // erases the entire vector
cout << v.empty(); //Gives 'true' if empty else 'false'.

- LISTS:- 

#include <bits/stdc++.h>

using namespace std;

int main ()
{
list <int> ls;
ls.push_back(2);
ls.emplace_back(4);
ls.push_front(5);
ls.emplace_front(7);
for (int i = 0; i < ls.size(); i++)
{
cout << * next(ls.begin(), i) << "\n";
}

return 0;
}

/*
output:- 
7
5
2
4
*/

[ONE IMPORTANT THING IS THAT, HERE DOUBLY LINKED LIST IS PRESENT SO THE TIME COMPLEXITY FOR ADDING ELEMENT AT THE START OF THE LIST IS VERY LESS.]

- DEQUE:- 
#include <bits/stdc++.h>

int main ()
{
deque <int> dq;
dq.push_back(8); //{8}
dq.emplace_back(9); //{8, 9}
dq.push_front(0); //{0, 8, 9}
dq.emplace_front(2); //{2, 0, 8, 9}

dq.pop_front(); //{0, 8, 9}
dq.pop_back(); //{0, 8}

cout << dq.back() << "\n"; //8
cout << dq.front() << "\n"; //0

return 0;
}

- STACK:- 
#include <bits/stdc++>

int main ()
{
stack <int> st;
st.push(5);
st.push(4);
st.emplace(6);

cout << st.top() << "\n";

st.pop();

cout << st.top() << "\n";
cout << st.empyt() << "\n";
cout << st.size() << "\n";

stacl <int> st1, st2;
s1.swap(s2);

return 0;
} 

- QUEQU:- 
#include <bits/stdc++.h>

int main ()
{
queqe <int> q;
q.push(1); //{1}
q.emplace(9); //{1, 9}

q.back() += 5;  //{1, 14}

cout << q.back() << "\n"; //14

cout << a.front() << "\n"; //1

q.pop(); //{14}

cout << q.front() << "\n"; //14

return 0;
}

[HERE ALL THE OPERATIONS ARE HAPPENING IN CONSTANT TIME.]

- PRIORITY QUEQE:- 
#include <bits/stdc++.h>

int main ()
{
//maximum priority
priority_queqe <int> pq;

pq.push(5); //{5}
pq.push(2); //{5, 2}
pq.push(8); //{8, 5, 2}
pq.emplace(10); //{10, 8, 5, 2}

cout << pq.top(); //10

pq.pop(); //{8, 5, 2}

cout << pq.top(); //8

//minimum priority
priority_queqe <int, vector <int>, greater <int>> pq;
pq.push(5); //{5}
pq.push(2); //{2, 5}
pq.push(8); //{2, 5, 8}
pq.emplace(10); //{2, 5, 8, 10}

cout << pq.top() << "\n"; //2

rerturn 0;
}
[FOR STRINGS IT WILL ARRAGE LEXICOGRAPHYCALLY]
[THE POP FUNCTION WILL WORK WITH LOG(N) TIME COMPLEXITY]

- SET:- 
It is sorted and unique. Inserting and erasing will happen in logarithmic time.

#include <bits/stdc++>

int main ()

{
set <int> s;
s.insert(1); //{1}
s.insert(2); //{1, 2}
s.insert(2); //{1, 2}
s.insert(4); //{1, 2, 4}
s.emplace(3); //{1, 2, 3, 4}

//{1, 2, 3, 4, 5}
auto it = s.find(3); //it will point to 3
//{1, 2, 3, 5, 6}
auto it = s.find(4); //it will point at s.end()
//{1, 4, 5}
s.erase(4); //{1, 5}

int cnt = s.count(1); //returns 1 or 0 (in this case)

auto it = s.find(3);
s.erase(it); //it takes constannt time
// {1, 2, 3, 4, 5}
suto it1 = s.find(3);
suto it2 = s.find(5);
s.erase(it1, it2); //{1, 2, 5}
//just for syntax (below)
auto it = s.lower_bound(2);
auto it = s.upper_bound(3);

return 0;
}

- MULTISET:- 
#include <bits/stdc++>

int main ()
{
multiset <int> ms;
ms.insert(1); //{1}
ms.insert(1); //{1, 1}
ms.insert(1); //{1, 1, 1}

ms.erase(1); //erases all 1

int cnt = ms.count(1); //3

ms.erase(ms.find(1)); //erases only one 1

ms.erase(ms.find(1), ms.find(1) + 2);

return 0;
}

[THIS IS ORDERED BUT CAN STORE MULTIPLE ITEMS.]

- UNORDERED SET:- 
#include <bits/stdc++>

int main ()
{
unordered_set <int> st;
//Everything is same in here except few things.
//As the name suggests, the set is unordered, but unique.
//It does not even store as per the inputed order, it is completely random.
//Almost all the operations are of the time complexity of O(1).
//There is no upper_bound and lower_bound function.
//In very rare (and I mean, very rare) cases the time complexity reaches O(n).
}

- MAP:- 
Types of declaration:- 
- map <int, int> m; //1
- map <int, pair <int, int>> m; //2
- map <pair <int, int>, int> m; //3

Ways to give values:- 
m[1] = 2; //for 1
m.emplace({3, 2}); //for 1
m.insert({3, 4}); //for 1
m[{9, 0}] = 10; //for 3

Map stores the keys in unique and sorted order.

for (auto it: m)
{
cout << it.first << " " << it.second << endl;
}

auto it = m.find(2);
cout << * (it).first << ", " << * (it).second << endl;

If the key is not present and still you try to find it then it will retrun m.end().

auto it = m.lower_bound(2);

auto it = m.upper_bound(3);

The default value for a key that is not there in the map is 0. The storing and fetching in map takes log(n) time.

- MULTIMAP:- 
Here you can store duplicate keys but, it will be storted.

- UNORDEREDMAP:- 
Here there is no duplicate keys but the keys will not be sorted. The fetching and searching the time complexity is (best and average) is O(1) and (worst) is O(n). In ordered map the key can be any data type but in unordered type the key is limited to few (like int, char, etc. no pair).

- int n = 7;
int c = __builtin_popcount(n); //this will give the number of 1's in the binary representation of the number n

long long n = 78349273487;
int c = __builtin_popcountll(n);

- string s = "abc";
do
{
cout << s << endl;
} while(next_permutaion(s.begin(), s.end()));

This will print all the permutaion of the string s.
The printing order will be as per the dictionary.
If we want all the permutations then the string should be in the sorted order or else it will print only till the decending order permutation of the string.

- int a[n] = {1, 4, 7, 3, 0};
int min = * min_element(a, a + n);
int max = * max_element(a, a + n);

- Euclidian algorithm:- 
gcd(a, b) = gcd(a- b, b)
therefor,
gcd(a, b) = gcd(a % b, b)

- We cannot declare an array of more than 10^6 in main(). Declaring for more than 10^6 elements will through a segmentation fault. But, if the array is declared outside (that is, globally) then it can declared for more than 10^7.

- If we something in a function then it is given a garbage value inititally, but if it is declared globally then it is initialised to 0 everytime.
