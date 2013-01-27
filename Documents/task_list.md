#研发任务清单

##代码定位
在android系统源码中定位用于处理activity和application切换的代码。

主要的类：

* `ActivityManagerService`:

    * startActivity
    
    (通过Binder驱动程序以参数START_ACTIVITY_TRANSACTION进入)
    
    * activityPaused
    
    (调用ActivityStack.activityPaused)
    
    * startProcessLocked
    
    (Process.start("android.app.ActivityThread",...))

* `ActivityStack`:

    * startActivityMayWait
    
    (由ActivityManagerService成员mMainStack调用，会获得PackageName和ActivityName)
    
    * startActivityLocked
    
    * startActivityUncheckedLocked
    
    (考察LaunchMode, NotTop，确定是否需要new TaskRecord，新建的TaskRecord会保存到ActivityRecord的task属性里)
    
    * startActivityLocked
    
    (这里会处理切换Task操作)
    
    * resumeTopActivity
    
    把当前处于Resumed状态的Activity推入Paused状态(然后才可以启动新的Activity)
    
    * startPausingLocked
    
    * activityPaused
    
    * completePauseLocked
    
    * resumeTopActivityLocked
    
    准备启动目标Activity
    
    * startSpecificActivityLocked

* `ActivityThread`:

    * handleMessage

    * handlePauseActivity

次要的类：

* `ActivityManagerProxy`
* `ApplicationThreadProxy`

##研究处理流程
1.  研究各模块之间的依赖、调用关系
2.  研究并描绘出完整的处理流程
3.  寻找合适的植入点

##植入功能
1.  编写记录日志功能并进行植入
2.  编写服务器交互功能

##服务器部分
架设基于ror的rest api服务，用于接收android系统发送过来的信息并做相应处理

