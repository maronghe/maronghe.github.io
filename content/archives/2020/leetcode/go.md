Go 调度器



1. 线程池的缺陷

   G -> Create -> Pool -> G(Block) -> Pool !增大! -> Thread ! -> CPU竞争 ->消费能力有上限 或 下降

2. Go中为了大量线程进行CPU竞争从而自己实现调度

   1. G是调度单位
   2. 将准备好的G分配给线程进行排队调度。
   3. PMG 模型
      1. P有本地LRQ
      2. M持有P才能运行G
      3. P默认与CPU核数相同
      4. M一般 >= P

3. 