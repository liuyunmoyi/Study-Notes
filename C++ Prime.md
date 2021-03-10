1. 开始  
* **while语句和for语句的优缺点**  
  在for循环中，循环控制变量的初始化和修改都放在语句头部分，形式较为简洁，适用于循环次数已知的情况。  
  在while循环中，循环控制变量的初始化一般放在while语句之前，循环控制变量的修改一般放在循环体中，形式上不如for语句简洁，但它比较适用于循环次数不易预知的情况。两种形式各有优点，但是功能上是等价的，可以相互转换。  
  例子是同一种含义分别用while和for语句表示。

```
#include <iostream>
using namespace std;
int main()
{
    int i = 10;
    while (0 <= i && i <= 10)
    {
        cout << i << "";
        i--;
    }
    cout << endl;
    return 0;
}
```  

```
#include <iostream>
using namespace std;
int main()
{
    for (int i = 10; 0 <= i; i--)
        cout << i << "";
    cout << endl;
    return 0;
}
```
* endl是和cout搭配使用的，表示输出结束，然后输出下一行。  
* 