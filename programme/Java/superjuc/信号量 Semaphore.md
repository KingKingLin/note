# 信号量 Semaphore

```java
package cn.itcast.jvm;

import java.util.concurrent.Semaphore;

public class TestSemaphore {
    public static void main(String[] args) {
        // 1. 创建 semaphore 对象
        Semaphore semaphore = new Semaphore(3); // permits: 许可上限3个线程；fair 公平，非公平

        // 2. 10个线程同时运行
        for (int i = 0; i < 10; i++) {
            new Thread(()->{
                // 获得许可
                try {
                    semaphore.acquire();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                try {
                    String name = Thread.currentThread().getName();
                    System.out.println(name+" running...");
                    try {
                        Thread.sleep(1000);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    System.out.println(name+" end...");
                } finally {
                    // 释放许可
                    semaphore.release();
                }
            }).start();
        }
    }
}
```

# Semaphore 应用

- 使用 Semaphore 限流，在访问高峰期时，让请求线程阻塞，高峰期过去再释放许可，当然它只适合限制单机线程数量，并且仅是限制线程数，而不是限制资源数（例如连接数，请对比 Tomcat LimitLatch 的实现）
- 用 Semaphore 实现简单连接池，对比【享元模式】下的实现（用 wait notify），性能和可读性显然更好，注意下面的实现中线程数和数据库连接数是相等的