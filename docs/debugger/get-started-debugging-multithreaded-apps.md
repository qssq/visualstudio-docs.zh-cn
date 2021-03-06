---
title: 了解如何调试多线程应用程序
description: 使用 Visual Studio 中的并行堆栈和并行监视窗口进行调试
ms.custom: H1HackMay2017
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11cb05ea81f086cf8c26e3058850968a909b84e3
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468678"
---
# <a name="get-started-debugging-multithreaded-applications-in-visual-studio"></a>开始调试 Visual Studio 中的多线程应用程序
Visual Studio 提供多种工具和用户界面元素，以帮助您调试多线程应用程序。 本教程演示如何使用线程标记**并行堆栈**窗口中，**并行监视**窗口中，条件断点，并筛选器断点。 本教程中，只需要几分钟，但完成它将使您熟悉用于调试多线程应用程序的功能。

|         |         |
|---------|---------|
|  ![视频的摄像机图标](../install/media/video-icon.png "观看视频")  |    [观看视频](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171)上显示了类似的步骤的多线程调试。 |

其他主题提供有关使用其他多线程调试工具的其他信息：

- 有关演示如何使用的类似主题**调试位置**工具栏和**线程**窗口中，请参阅[演练： 调试多线程应用程序](../debugger/how-to-use-the-threads-window.md)。

- 与使用的示例类似主题<xref:System.Threading.Tasks.Task>（托管代码） 和并发运行时 （c + +），请参阅[演练： 调试并行应用程序](../debugger/walkthrough-debugging-a-parallel-application.md)。 有关适用于最多线程应用程序类型的常规调试技巧，阅读本主题和链接的主题。
  
若要开始学习本教程，需要一个多线程应用程序项目。 请按照下面列出的步骤创建该项目。  
  
#### <a name="to-create-the-multithreaded-app-project"></a>若要创建多线程应用程序项目  
  
1.  上**文件**菜单中，选择**新建**，然后单击**项目**。  
  
     此时将出现 “新建项目” 对话框。  
  
2.  单击所选的语言： **Visual C#**， **Visual c + +**，或**Visual Basic**。  
  
3.  下**Windows 桌面**，选择**控制台应用**。  
  
4.  在中**名称**框中，键入名称 MyThreadWalkthroughApp。  
  
5.  单击 **“确定”**。  
  
     新的控制台项目随即显示。 创建该项目后，将显示源文件。 根据您选择的语言，源文件可能 Program.cs、 MyThreadWalkthroughApp.cpp 或 Module1.vb 调用。  
  
6.  删除出现在源代码文件中的代码并将替换此处显示的示例代码。

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    using namespace;

    int count = 0;

    void doSomeWork() {

        cout << "The doSomeWork function is running on another thread." << endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        this_thread::sleep_for(chrono::seconds(3));
        cout << "The function called by the worker thread has ended." << endl;
    }

    int main() {
        vector<thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(thread(doSomeWork));
            cout << "The Main() thread calls this after starting the new thread" << endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```
  
7.  上**文件**菜单上，单击**全部保存**。  
  
#### <a name="to-begin-the-tutorial"></a>若要开始学习教程  
  
-   在源代码编辑器中，查找以下代码： 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3));
    cout << "The function called by the worker thread has ended." << endl; 
    ```  

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>开始调试  
  
1.  左侧滚动条槽中单击`Thread.Sleep`或`this_thread::sleep_for`语句将新断点。  
  
     在源代码编辑器左侧的滚动条槽，将显示一个红色圆圈。 这表示现在已在该位置设置了一个断点。 
  
2.  上**调试**菜单上，单击**开始调试**(**F5**)。  
  
     Visual Studio 生成该解决方案、 应用程序开始运行附带，调试器，然后应用程序停止在断点处。  
  
    > [!NOTE]
    > 如果焦点切换到控制台窗口中，单击在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]窗口，以使焦点返回到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
4.  在源代码编辑器中，找到包含该断点的行：  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3)); 
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>若要发现线程标记  

1.  在调试工具栏中，单击**源中显示线程**按钮![在源中显示线程](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")。

2. 按**F11**一次以前进的调试器一个代码行。
  
3.  查看窗口左侧的滚动条槽。 在此行中，你会看到*线程标记*图标![线程标记](../debugger/media/dbg-thread-marker.png "ThreadMarker") ，类似于两根细线。 线程标记指示线程在此位置停止。

    请注意，可能会通过断点部分隐藏线程标记。 
  
4.  将指针悬停在线程标记上。 屏幕上显示数据提示。 数据提示将告诉您每个已停止线程的名称和线程 ID 号。 在这种情况下，名称可能是`<noname>`。 
  
5.  右键单击要查看的快捷菜单上的可用选项的线程标记。
    
## <a name="ParallelStacks"></a>查看线程的位置

在中**并行堆栈**窗口中，您可以切换线程视图之间和 （适用于基于任务的编程） 任务视图，您可以查看每个线程的调用堆栈信息。 在此应用中，我们可以使用线程视图。

1. 打开**并行堆栈**通过选择窗口**调试 > Windows > 并行堆栈**。 您应看到类似于以下内容 （的确切信息将当前的位置每个线程，您的硬件，以及您的编程语言而异）。

    ![并行堆栈窗口](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    在此示例中，从左到右将托管代码的此信息：
    
    - 主线程 （左侧） 上已停止`Thread.Start`(由线程标记图标指示停止点![线程标记](../debugger/media/dbg-thread-marker.png "ThreadMarker"))。
    - 输入的两个线程`ServerClass.InstanceMethod`，其中之一是当前线程 （黄色箭头），而另一个线程已停止在`Thread.Sleep`。
    - 此外启动新线程 （右侧） (上停止`ThreadHelper.ThreadStart`)。

2.  右键单击中的条目**并行堆栈**窗口来查看快捷菜单上的可用选项。

    您可以执行各种操作从这些右键单击菜单中，但对于本教程中我们将显示多个中的这些详细信息**并行监视**窗口 （下一节）。

    > [!NOTE]
    > 如果您更感兴趣查看的每个线程上的信息，请使用列表**线程**窗口相反。 请参阅[演练： 调试多线程应用程序](../debugger/how-to-use-the-threads-window.md)。

## <a name="set-a-watch-on-a-variable"></a>对变量设置监视

1. 打开**并行监视**通过选择窗口**调试 > Windows > 并行监视 > 并行监视 1**。

2. 单击将出现的单元格`<Add Watch>`文本 （或中的第 4 列的空标头单元格），类型`data`，然后按 Enter。

    在窗口中显示每个线程的数据变量的值。

3. 再次单击将出现的单元格`<Add Watch>`文本 （或第五个列中的空标头单元格），类型`count`，然后按 Enter。

    在窗口中显示为每个线程计数变量的值。 （如果看不到这么多的信息，请尝试按 F11 几次以继续在调试器中线程的执行。）

    ![并行监视窗口](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. 右键单击某个窗口以查看可用选项中的行。

## <a name="flagging-and-unflagging-threads"></a>标记线程和取消标记线程  
可以标记要格外关注的线程。 标记线程是一个好的方法来跟踪重要线程并忽略您不关心的线程。  
  
#### <a name="to-flag-threads"></a>标记线程  

1. 在中**并行监视**窗口中，按住 SHIFT 键并选择多个行。

2. 右键单击并选择**标志**。

    现在，将标记所有所选的线程。 现在，您可以筛选为仅显示已标记的线程。
  
3.  在中**并行监视**窗口中，找到**仅显示标记的线程**按钮![显示已标记线程](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")。  
  
4.  单击**仅显示标记的线程**按钮。  
  
    现在只有标记的线程显示在该列表中。

    > [!TIP]
    > 当你具有标记的一些线程时，可以右键单击代码编辑器中的代码行，然后选择**运行到光标处的已标记线程**（请确保选择所有标记的线程的代码将访问）。 这将中止线程，从而使代码更容易控制的执行顺序的选定行上[冻结和解冻线程](#bkmk_freeze)。

5.  单击**仅显示标记的线程**按钮可以切换回**显示所有线程**模式。
    
#### <a name="to-unflag-threads"></a>取消标记线程

若要取消标记线程，可以右键单击一个或多个标记的线程中**并行监视**窗口，然后选择**取消标记**。

## <a name="bkmk_freeze"></a> 冻结和解冻线程执行 

> [!TIP]
> 您可以冻结和解冻 （暂停和恢复） 线程来控制线程在其中执行工作的顺序。 这可以帮助你解决并发问题，例如死锁和争用条件。
  
#### <a name="to-freeze-and-unfreeze-threads"></a>冻结和解冻线程  
  
1.  在中**并行监视**窗口中，与所有选定的行，右键单击并选择**冻结**。

    在第二个专栏中，暂停图标现在显示每个行。 暂停图标指示该线程已冻结。

2.  通过单击只有一行，取消选中行。

3.  右键单击某一行，然后选择**解冻**。

    暂停图标指示线程已不再被冻结此行上会消失。

4.  切换到代码编辑器中，单击**F11**。 仅在未冻结的线程运行。

    应用还实例化某些新线程。 请注意，任何新线程未标记，未被冻结。

## <a name="bkmk_follow_a_thread"></a> 通过使用条件断点执行单线程

有时，可能很有帮助，以按照在调试器中单线程的执行。 你可以这么一种方法是通过冻结线程，您不感兴趣，但在某些情况下，可能想要操作一个线程，并且不冻结其他线程 （与特定错误，例如重现）。 若要执行一个线程不冻结其他线程的情况下，必须避免中断到除你感兴趣的线程上的代码。 您可以执行此操作通过设置[条件断点](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)。

可以在不同的条件，例如，线程名称或线程 ID 上设置断点 可能会有所帮助的另一种方法是将条件设置您知道将是唯一的每个线程的数据。 这是常见的调试方案中，你会更感兴趣比任何特定的线程中的一些特定的数据值。

#### <a name="to-follow-a-single-thread"></a>若要按照单个线程

1. 右键单击以前创建的断点，然后选择**条件**。

2. 在中**断点设置**窗口中，键入`data == 5`为条件表达式。

    ![条件断点](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > 如果要更感兴趣的特定线程，然后使用线程名称或线程 ID，条件。 若要执行此操作**断点设置**窗口中，选择**筛选器**而不是**条件表达式**，并按照筛选器提示。 您可能想要名称您在应用代码中的线程 （因为线程 Id 更改时重新启动调试器）。

3. 关闭**断点设置**窗口。

4. 单击重启![重新启动应用程序](../debugger/media/dbg-tour-restart.png "RestartApp")按钮以重新启动调试会话。

    将分解为其数据变量为 5 的线程上的代码。 黄色箭头 （当前调试器上下文） 中查找**并行监视**窗口，验证是否。

5. 现在，可以单步执行代码 (F10) 和单步执行代码 (F11) 并遵循单一线程的执行。

    只要断点条件是唯一的线程，并且调试器不会命中 （可能需要禁用它们） 的其他线程上的任何其他断点，可以单步执行代码并单步执行代码而无需切换到其他线程。

    > [!NOTE]
    > 当您推进调试器进度时，将运行所有线程。 但是，调试器不会中断到其他线程上的代码中，除非其中一个其他线程遇到断点。 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>有关多线程调试窗口的详细信息 

#### <a name="to-switch-to-another-thread"></a>若要切换到另一个线程 

- 若要切换到另一个线程，请参阅[如何： 切换到另一个线程时调试](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>若要了解有关并行堆栈和并行监视窗口的详细信息  
  
- 请参阅[如何： 使用并行堆栈窗口](../debugger/using-the-parallel-stacks-window.md) 

- 请参阅[如何： 使用并行监视窗口](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>请参阅  
 [调试多线程应用程序](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何：在调试时切换到另一个线程](../debugger/how-to-switch-to-another-thread-while-debugging.md)
