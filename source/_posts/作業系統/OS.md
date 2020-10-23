---
title: 作業系統 Operating System
date: 2020-09-16 18:02:33
tags:
 - OS
---
# 作業系統:多程序與多執行緒的觀念與實作控制,在Linux與Windows
## 基本觀念
多程序與多執行緒是什麼? 這些概念了解之前, 必須要建立一些作業系統OS的背景知識!
?

## Process v.s. Thread
<!-- more -->
1. Process 表示 Program 正在執行，而 Thread 表示 Process 的一部分。
2. Process 不是輕量級的，Thread 是輕量級的。
3. Process 要花費許多的時間來終止，Thread花費比較少的時間來終止。
4. Process 要花費更多的時間來創建，Thread花費的時間比較少。
5. Process 要花費比較多的時間進行context switching，而Thread Thread花費的時間比較少。
6. Process 通常是孤立的(isolated)，而Thread共享記憶體資源(share memory)。
7. Process 不共享資料，Thread彼此間會共享資料。

## 執行緒安全與同步處理
?

## 在Linux 撰寫簡單 Process/Thread 程式
Linux process/thread特點:
* 可直接執行sleep()等系統呼叫，而不會影響其他threads
* threads其實是共用記憶體空間等資源的processes，因此可以使用kill命令，送訊號或殺掉thread
* clone()為Linux特有, 不相容於其他Unix系統
* Linux沒有另外定義thread: Linux的threads (例如: POSIX threads)，其實是利用clone()產生的child processes
* sleep()系統呼叫: 會使得該process睡覺，所有thread因此全部睡覺。若只是要讓某一thread睡覺，必須設計另一系統呼叫，例如: pthread_delay()

## 在Windows 撰寫簡單 Process/Thread 程式
--[參考自Microsoft MSDN](https://msdn.microsoft.com/en-us/library/3c8c4cxa.aspx)--

執行緒(thread)基本上是一個經由程式的執行路徑。 它也是 Win32 排程執行的最小單位。 執行緒由堆疊、CPU 暫存器的狀態和系統排程器之執行清單裡的項目所組成。 每個執行緒共用所有處理序的資源。

處理序(process)由一或多個執行緒和程式碼、資料以及程式在記憶體中的其他資源所組成。 一般的程式資源是開啟檔案、號誌 (Semaphore) 和動態配置的記憶體。 當系統排程器給與一個執行緒執行控制權，程式就會執行。 排程器決定哪些執行緒要執行以及何時執行。 當較高優先權執行緒在完成工作時，優先權較低的執行緒可能必須等待。 在多處理器的電腦上，排程器可以將各個執行緒移到不同的處理器上來平衡 CPU 的負載。

在處理序(process)中每一個執行緒都獨立作業。 除非您讓它們彼此看得見對方，否則執行緒是個別執行而且不知道處理序 (Process) 裡有其他執行緒存在。 然而，共用通用資源的執行緒必須藉著使用號誌(Semaphore)或其他處理序之間的通訊方法來協調。
