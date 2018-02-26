 1. 为什么fst的结果要优于trie
 > fst为最大片段匹配,前缀后缀无关,trie要求从头匹配.
 > fst解析时间耗时短,当rule很大时,trie读取耗时长.
 
 2. 在nmt中为什么短句的预测结果要优于长句的预测结果?
 > 可通过使用attention mechanism改善长句的预测结果.