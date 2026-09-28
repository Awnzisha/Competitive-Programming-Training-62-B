## 3. Vector

A `vector` is a dynamic array. Unlike standard arrays (e.g., `int arr[100];`), vectors can grow and shrink in size automatically.

**Example 1: Input and Storing Numbers**

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    
    vector<int> v;
    for(int i = 0; i < n; i++) {
        int x;
        cin >> x;
        v.push_back(x); // Adds x to the back of the vector
    }
    for (int i=0;i < n;i++)
    {
			    cout << v[i] << endl;
    }
    
    return 0;
}

```

**Example 2: Reversing a Vector using a for-loop**

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v = {10, 20, 30, 40, 50};
    int n = v.size();
    
    // Swap elements from the outside going inwards using two pointers
    for(int i = 0; i < n / 2; i++) {
        int temp = v[i];
        v[i] = v[n - 1 - i];
        v[n - 1 - i] = temp;
        // Tip: You can also just use the built-in swap(v[i], v[n - 1 - i]);
    }
		 for (int i=0;i < n;i++)
    {
			    cout << v[i] << endl;
    }
    
    // It is now reversed!
    return 0;
}

```

**Example 3: Traversing with a For-Each Loop**

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v = {1, 2, 3, 4, 5};
    
    // "For each integer 'x' inside vector 'v'..."
    for(int x : v) {
        cout << x << " ";
    }
    cout << "\n";
    
    return 0;
}

```

### Leveling Up with Vectors: 5 More Examples

**Level 1: Initialization with Default Values**

```cpp
// Creates a vector of size 5, where every element is initially 10
vector<int> v(5, 10); 

```

**Level 2: The `front()` and `back()` functions**

```cpp
vector<int> v = {5, 9, 15, 22};
cout << v.front() << "\n"; // Prints 5 (first element)
cout << v.back() << "\n";  // Prints 22 (last element)

```

**Level 3: Removing elements with `pop_back()**`

```cpp
vector<int> v = {1, 2, 3};
v.pop_back(); // Removes the last element (3). Size is now 2.

```

**Level 4: Copying vectors directly**

```cpp
vector<int> v1 = {10, 20, 30};
vector<int> v2;
v2 = v1; // In C++, you can copy an entire vector with the = operator!

```

**Level 5: Vector of Pairs (Very common in CP)**

```cpp
vector<pair<int, int>> points;
points.push_back({1, 5});
points.push_back({3, 7});

for(auto p : points) {
    cout << "X: " << p.first << ", Y: " << p.second << "\n";
}

```

---

## 4. Handling Test Cases (Codeforces Style)

In CP, your program usually doesn't run just once. The platform will give you an integer $t$ (the number of test cases), followed by $t$ distinct problems to solve in a single run.

### Problem A: Even-Odd Battle

**Problem Statement:**
You are given $t$ test cases. In each test case, you are given an integer $n$, followed by an array of $n$ integers. Print "EVEN" if the sum of all even numbers in the array is strictly greater than the sum of all odd numbers. Otherwise, print "ODD".

**Solution Code:**

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int n;
    cin >> n;
    
    vector<int> v(n);
    long long even_sum = 0;
    long long odd_sum = 0;
    
    for(int i = 0; i < n; i++) {
        cin >> v[i]; // Reading directly into the sized vector
        if(v[i] % 2 == 0) {
            even_sum += v[i];
        } else {
            odd_sum += v[i];
        }
    }
    
    if(even_sum > odd_sum) {
        cout << "EVEN\n";
    } else {
        cout << "ODD\n";
    }
}

int main() {
    // Fast I/O
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int t;
    cin >> t; // Read number of test cases
    while(t--) {
        solve(); // Process each test case individually
    }
    return 0;
}

```

### Problem B: Hide and Seek Words

**Problem Statement:**
You are given $t$ test cases. In each testcase, you are given an integer $n$, followed by $n$ strings. Your task is to output the longest string in the list. If multiple strings share the maximum length, print the one that appeared *first*.

**Solution Code (Using Vector of Strings):**

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int n;
    cin >> n;
    
    vector<string> words(n);
    for(int i = 0; i < n; i++) {
        cin >> words[i];
    }
    
    string longest_word = "";
    int max_len = -1;
    
    // Traversing the vector of strings using a for-each loop
    for(string s : words) {
        if(s.size() > max_len) {
            max_len = s.size();
            longest_word = s;
        }
    }
    
    cout << longest_word << "\n";
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int t;
    cin >> t;
    while(t--) {
        solve();
    }
    return 0;
}

```



# STL SORT

## Example 1: Basic Ascending Sort (Smallest to Largest)

By default, the `sort()` function arranges elements in ascending order.

  

C++

```
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v;
    v.push_back(50);
    v.push_back(20);
    v.push_back(40);
    v.push_back(10);
    v.push_back(30);
    
    cout << "Before sorting: ";
    for(int i = 0; i < v.size(); i++) {
        cout << v[i] << " ";
    }
    cout << endl;
    
    // Sorts the vector from the beginning to the end
    sort(v.begin(), v.end());
    
    cout << "After sorting: ";
    for(int i = 0; i < v.size(); i++) {
        cout << v[i] << " ";
    }
    cout << endl;
    
    return 0;
}

```

## Example 2: Descending Sort (Largest to Smallest)

If you want to sort in reverse order, you have two options. You can use reverse iterators (`rbegin()` and `rend()`), or you can pass `greater<int>()` as a third parameter.

  

C++

```
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<int> v;
    v.push_back(50);
    v.push_back(20);
    v.push_back(40);
    v.push_back(10);
    v.push_back(30);
    
    // Method 1: Using reverse iterators
    sort(v.rbegin(), v.rend());
    
    /* 
    // Method 2: Using the greater comparator
    sort(v.begin(), v.end(), greater<int>()); 
    */
    
    cout << "Descending order: ";
    for(int i = 0; i < v.size(); i++) {
        cout << v[i] << " ";
    }
    cout << endl;
    
    return 0;
}

```

## Example 3: Sorting a String (Alphabetical Order)

A `string` in C++ acts very much like a vector of characters. You can use the exact same `sort()` function to alphabetize the letters in a word.

  

C++

```
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s = "programming";
    
    cout << "Original string: " << s << endl;
    
    // Sorts characters based on their ASCII values
    sort(s.begin(), s.end());
    
    cout << "Sorted string: " << s << endl;
    
    return 0;
}

```

## Example 4: Sorting a Vector of Pairs

When you sort a vector of pairs, C++ automatically sorts them by the `first` element. If two pairs have the exact same `first` element, it will break the tie by sorting them by the `second` element!

  

C++

```
#include <bits/stdc++.h>
using namespace std;

int main() {
    // Note: older compilers might need a space between > > 
    vector<pair<int, int> > v; 
    
    // Use make_pair() when {} is not supported
    v.push_back(make_pair(2, 50));
    v.push_back(make_pair(1, 90));
    v.push_back(make_pair(2, 30)); // Has same first element as (2, 50)
    v.push_back(make_pair(1, 40));
    
    sort(v.begin(), v.end());
    
    cout << "Sorted pairs:" << endl;
    for(int i = 0; i < v.size(); i++) {
        cout << "{" << v[i].first << ", " << v[i].second << "}" << endl;
    }
    
    /* Output will be:
       {1, 40}
       {1, 90}
       {2, 30}
       {2, 50}
    */
    
    return 0;
}

```
