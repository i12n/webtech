# cavas 性能优化

1. 避免全局重绘，使用 clip 绘制更改区域
2. 分层 canvas，避免静态背景重绘
2. 离屏 canvas 使用，避免 canvas 每一帧大量调用 API
3. requestAnimationFrame 替代 setTimeout、setInterval
4. 计算使用 webworker
5. 避免频繁的绘制操作



[https://www.cnblogs.com/mopagunda/p/5622911.html](https://www.cnblogs.com/mopagunda/p/5622911.html)

[https://blog.csdn.net/DeepLies/article/details/82799854](https://blog.csdn.net/DeepLies/article/details/82799854)