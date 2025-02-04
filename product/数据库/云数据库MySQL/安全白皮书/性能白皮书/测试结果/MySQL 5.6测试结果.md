本文为您介绍云数据库 MySQL 5.6 通用型实例的性能测试结果。

## 场景一：全缓存
全缓存指只有全部数据可以放到缓存里，查询过程中不需要读写磁盘更新缓存。
![](https://qcloudimg.tencent-cloud.cn/raw/5f2b10c004b7e723b6d983850a3481ed.png)

| CPU<br>（core） | 内存<br>（MB） | 并发度 | 单表数据量 | 表总数 | SysBench TPS | SysBench QPS | avg_lat |
|---------|---------|---------|---------|---------|---------|---------|---------|
| 1 | 1000 | 8 | 25000 | 150 | 577.97 | 11559.4 | 13.84 |
| 1 | 2000 | 8 | 25000 | 150 | 550.21 | 11004.3 | 14.54 |
| 2 | 4000 | 16 | 25000 | 150 | 1190.41 | 23808.1 | 13.44 |
| 4 | 8000 | 32 | 25000 | 150 | 2307.1 | 46142 | 13.87 |
| 4 | 16000 | 32 | 25000 | 150 | 2229.8 | 44596.1 | 14.35 |
| 8 | 16000 | 64 | 25000 | 150 | 3771.25 | 75425 | 16.97 |
| 8 | 32000 | 64 | 25000 | 150 | 3909.36 | 78187.1 | 16.37|
| 16 | 32000 | 128 | 25000 | 150 | 6102.35 | 122047 | 20.97 |
| 16 | 64000 | 128 | 25000 | 150 | 6788.83 | 135777 | 18.85 |
| 16 | 96000 | 128 | 25000 | 150 | 6771.81 | 135436 | 18.9 |
| 16 | 128000 | 128 | 25000 | 150 | 7039.65 | 140793 | 18.18 |
| 24 | 244000 | 192 | 25000 | 150 | 8031.1 | 160622 | 23.9 |


## 场景二：磁盘 IO 型
磁盘 IO 型场景指只有部分数据可以放到缓存里，查询过程中需要读写磁盘更新缓存。
![](https://qcloudimg.tencent-cloud.cn/raw/ae85e6564e34a164a839864b9484f7b0.png)

| CPU<br>（core） | 内存<br>（MB） | 并发度 | 单表数据量 | 表总数 | SysBench TPS | SysBench QPS | avg_lat |
|---------|---------|---------|---------|---------|---------|---------|---------|
| 1 | 1000 | 8 | 800000 | 6 | 530.36 | 10607.3 | 15.08 |
| 1 | 2000 | 8 | 800000 | 12 | 543.86 | 10877.2 | 14.71 |
| 2 | 4000 | 16 | 800000 | 24 | 1120.47 | 22409.4 | 14.28 |
| 4 | 8000 | 32 | 800000 | 48 | 2189.87 | 43797.4 | 14.61|
| 4 | 16000 | 32 | 6000000 | 13 | 2138.75 | 42775.1 | 14.96 |
| 8 | 16000 | 64 | 6000000 | 13 | 3589.44 | 71788.8 | 17.83 |
| 8 | 32000 | 64 | 6000000 | 25 | 3535.54 | 70710.8 | 18.1 |
| 16 | 32000 | 128 | 6000000 | 25 | 5550.31 | 111006 | 23.06 |
| 16 | 64000 | 128 | 6000000 | 49 | 6414.39 | 128288 | 19.95 |
| 16 | 96000 | 128 | 6000000 | 74 | 5874.64 | 117493 | 21.78 |
| 16 | 128000 | 128 | 6000000 | 98 | 5611.06 | 112221 | 22.81 |
| 24 | 244000 | 192 | 6000000 | 187 | 7586.35 | 151727 | 25.3 |

