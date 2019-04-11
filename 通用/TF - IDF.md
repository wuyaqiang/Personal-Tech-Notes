TF-IDF的主要思想： 

如果词 w 在一篇文档 d 中出现的频率高，并且在其他文档中很少出现，则认为词 w 具有很好的区分能力，适合用来把文章 d 和其他文章区分开来。

词 w 在文档 d 中的词频 tf (Term Frequency)，即词 w 在文档 d 中出现次数 count (w, d) 和文档 d 中总词数 size (d) 的比值：

tf(w,d) = count(w, d) / size(d) 

词 w 在整个文档集合中的逆向文档频率 idf (Inverse Document Frequency)，即文档总数 n 与词 w 所出现文件数 docs (w, D) 比值的对数:

idf = log(n / docs(w, D)) 
