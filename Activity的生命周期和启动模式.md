# Activity的生命周期和启动模式

包括生命周期和启动模式以及IntentFilter的匹配规则分析

## Activity的生命周期全面分析

### 1、典型情况下的生命周期分析

- **onCreate:** 表示Activity正在被创建，Activity生命周期的第一个方法，可做初始化工作。
- **onRestart:** 表示Activity正在重新启动， Activity从不可见重新变为可见onRestart被调用。
- **onStart:**  表示Acticity正在被启动，即将开始，Activity已经可见，单位出现在前台。
- **onResume:** 表示Activity已经可见，并出现在前台
- **onPause:** 表示Activity正在停止，可做存储数据、停止动画等工作，但不能太耗时
- **onStop:**表示Activity即将停止，可做稍重量级的回收工作
- **onDestroy:**表示Activity即将被销毁，这是Activity生命周期中的最后一个周期

<img src="C:\Users\qixiaojun\AppData\Roaming\Typora\typora-user-images\image-20220824124455842.png" alt="image-20220824124455842" style="zoom: 50%;" />

**onStart和onResume、onPause和onStop有什么区别？**

onStart和onStop是从Activity是否可见的角度来回调的，而onResume和onPause是从Activity是否位于前台这个角度来回调的，除了这种区别，在实际使用过程中没有其他明显区别。

**Activity的跳转，是旧Activity先执行onPause还是新Activity先执行onResume?**

先执行onPause再执行onResume.

### 2、异常情况下的生命周期分析

**情景1、资源相关的系统配置发生改变导致Activity被杀死并重新创建**

<img src="C:\Users\qixiaojun\AppData\Roaming\Typora\typora-user-images\image-20220824131016251.png" alt="image-20220824131016251" style="zoom:50%;" />

旧Activity生命周期：(onPause、onSaveInstanceState)而这没有时序关系 $\rightarrow$ onStop $\rightarrow$ onDestroy.

新Activity生命周期: onCreate$\rightarrow$ onStart $\rightarrow$ onRestoreInstanceState.



 
$$

$$
