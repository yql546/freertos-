


1. FreeRTOS
其他功能
1.1列举
任务创建，删除，挂起和恢复
软件定时器
事件标志组
临界区

1.2 任务创建，删除，挂起和恢复
•任务创建和删除常用于重启，如通信异常时重启通信
•任务挂起和恢复常用于暂停，如按下暂停键时机械手动作暂停


1.3软件定时器
•软件定时器是由操作系统内核提供的一种虛拟定时器，它不依赖硬件定时器，完全通过软件方式实现定时功能
• 软件定时器可以设定一个时间，时间到了，系统就会自动调用预先定义好的回调函数


• 1.4 事件标志组
• 事件标志组是一个可以存储多个二进制标志位的数据结构，可以理解为一个“状态面板”
•每个位（bit）代表一个“事件”或“状态”（如bito为“按键按下”，bit1为“数据接收完成”)
•任务可以设置被单个或多个bit 唤醒;




•1.5临界区

•临界区本质上是一段不允许被打断的代码片段，一旦任务进入这个区间，就不允许高优先级任务抢占，也不允许中断（或部分中断）打断，直到代码执行完，退出临界区为止
•任务级临界区：通过vTaskSuspendAlIl 暂停任务调度器，此时即使有高优先级任务就绪，也不会切换，直到调用×TaskResumeAlI()恢复调度;
•中断级临界区：通过 taskENTER_CRITICAL() 关闭中断（本质是修改CPU的BASEPRI或PRIMASK 寄存器），taskEXIT_CRITICAL()恢复中断，期间所有可屏蔽中断都被屏蔽。


2.文件结构
2.1总览
Middlewares/FreeRTOScroutine.cevent_groups.clist.c
queue.c
stream_buffer.ctasks.ctimers.ccmsis_os2.c

heap_4.cport.c

其功能，后续自己可以了解。up视频里有总结




3.CMSIS
CMSIS：ARM Cortex-M系列微控制器软件接口标准（Cortex Microcontrollr Software Interface Standard），是ARM 为简化 MCU软件开发推出的通用接口，覆盖内核访问、外设驱动、RTOS接口等：



FreeRTOS CMSIS V2：是CMSIS 标准中针对FreeRTOS 的第二版标准化接口层（CMSIS-RTOS V2 for FreeRTOS），本质是对FreeRTOS 原生API的封装——它没有改变FreeRTOS 的内核逻辑，只是提供了一套符合CMSIS 标准的统一API，让开发者可以用相同的接口调用 FreeRTOS 的功能，也方便在不同 RTOS（如 FreeRTOS、RTX）之间切换。




4.结语
FreeRTOS理论部分完成，ɪ后续会在项目中使用

·多思考，多实践

一定要自己敲代码，多操作，多实验

·活用工具，AI很强大
