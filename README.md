# recurse
Recursion is a powerful programming tool, but it requires a different way of thinking about a problem.  You need to write a function that will call itself and eventually come up with a case that can be answered easily.  For this learning activity, we will be writing a function to compute the length of a string.  You could easily do this with iteration and a while loop.
```c++
#include <iostream>
using namespace std;

int itersize(string str)
{
    int strsize = 0;
    while (str != "") {
        strsize++;
        str = str.substr(1);
    }
    return(strsize);
}

int main()
{
    cout << "iteration "<<itersize("byurules")<<endl;
}
```
In the iterative version, we count the number of times we have to remove a character before we have an empty string.  Now lets look at how we would do this recursively.  First, we need a base case.  We know that the empty string has size zero.
```c++
#include <iostream>
using namespace std;

int recursesize(string str)
{
    if (str == "") {
        cout << "Base Case"<<endl;
        return 0;
    } 
}

int main()
{
    cout << "recursion "<<recursesize("byurules")<<endl;
}
```
Now we need a way of passing a smaller problem to the same function.  In this case, we will pass a substring that has everything except for the first character. The substr(1) function returns a string starting at position 1 in the original string
```c++
#include <iostream>
using namespace std;

int recursesize(string str)
{
    if (str == "") {
        cout << "Base Case"<<endl;
        return 0;
    } else {
        int subsize = recursesize(str.substr(1));
        cout << "recurse "<< str << " subsize "<< subsize << endl;
        return 1 + subsize;
    }
}

int main()
{
    cout << "recursion "<<recursesize("byurules")<<endl;
}
```
