---
title: "First Thread Train"
date: 2020-08-17T00:53:09+08:00
draft: true
---

# 初探线程

### Java线程具有五种基本状态
1. 新建状态：当线程对象创建后，处于新建状态，如：Thread thread = new MyThread();
2. 就绪状态(Runnable)：当调用的线程对象的start()方法，线程及进入就绪状态。即cpu空闲即可调度执行；
3. 运行状态(Running)：CPU开始调度线程；
4. 阻塞状态(Blocked)：由于某些行为，使得线程放弃CPU使用权;
   * wait()
   * sleep()
   * join()
   * synchronized()
5. 死亡状态(Dead)：线程执行完了或者因异常退出了run()方法，该线程结束生命周期。