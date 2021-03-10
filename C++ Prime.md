1. 开始  
* UTF-8 编码的 cpp 文件在 Windows 环境下使用 Visual Studio 进行编译时会出现 Error: C4819（仅在包含中文注释的情况下），将编码设置成 UTF-8 with BOM （UTF-8 带签名）即可解决编译报错问题。
* return 0 一般约定表示为程序无错误，如果 main 函数 return 其他数值则表示出现错误。
* **while 语句和 for 语句的优缺点**  
  在 for 循环中，循环控制变量的初始化和修改都放在语句头部分，形式较为简洁，适用于循环次数已知的情况。  
  在 while 循环中，循环控制变量的初始化一般放在 while 语句之前，循环控制变量的修改一般放在循环体中，形式上不如 for 语句简洁，但它比较适用于循环次数不易预知的情况。两种形式各有优点，但是功能上是等价的，可以相互转换。  
  例子是同一种含义分别用 while 和 for 语句表示。

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
* endl 是和 cout 搭配使用的，表示输出结束，然后输出下一行。endl会刷新输出流缓存，但是在以下情况下，缓冲区都会被刷新：  
  1. 程序运行正常结束，返回 main 时会清空所有输出缓冲区。  
  2. 当缓冲区满了的情况下，会在写下一个值之前刷新。  
  3. 使用 endl（行结束符）或者 fflush（C 标准库中用于刷新输出缓冲区的函数）会显式地刷新缓冲区。  
  4. 在每次输出操作执行完后，用 unitbuf 操作符设置流的内部状态，从而清空缓冲区。  
  5. 可将输出流与输入流关联（tie）起来。在这种情况下，在读输入流的时将刷新其关联的输出缓冲区。  
  * endl 会不停地刷新输出流，频繁的操作会降低程序的运行效率，这也是 C++ 标准库对流的输入/输出操作使用缓冲区的原因。没有必要刷新输出流的时候应尽量使用 \n，比如对于无缓冲的流 cerr，就可以直接使用 \n。
* 关于 Microsoft Visual Studio 2019 编译器相关：  
  1. 编译时需要使用 Developer Command Prompt 而不是 CMD 或者 PowerShell  
  2. 此选项指定编译器使用的异常处理模型：  
       * 使用 /EHs 指定同步异常处理模型（没有结构化异常处理异常的 C++ 异常处理）。如果使用 /EHs，不要依靠编译器捕捉异步异常。  
       * 使用 /EHa 指定异步异常处理模型（带结构化异常处理异常的 C++ 异常处理）。  
       * /EHc 选项要求指定 /EHs、/EHa 或 /GX。它通知编译器假定 extern C 函数从不引发异常。  
       * 推荐使用 /EHsc 参数