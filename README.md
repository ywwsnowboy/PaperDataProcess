# PaperDataProcess
针对不同的问题执行不同的代码
---------------------------------------------
**问题一**: 

由于 Citespace 去重是根据 DOI 进行去重，并不能够有效去除所有重复率。由于 Web of Science 数据库和 Scopus 数据库检索数据导出的数据
存在差异，通过 Citespace 转换 Scopus 数据库的数据保存为`txt`数据，需要将缩略词`DE`改为`ID`，然后通过 Citespace 进行去重，然而两个数据库中仍
然存在大量数据重复，比如标题大小写或者某个数据库 DOI 信息缺失等等，因此此脚本通过`标题`进行检索去重。

**前提条件**：首先需要通过 Citespace 将文献数据分割成年份的形式，也就是 Citespace 去重处理后的效果，如下所示：

![image-20230708151126322](https://vip2.loli.io/2023/07/08/CNm56wEfH4d9AxG.png)

**实现功能一**：RemoveDuplicate

* 对上述每个`txt`文档中的数据进行去重，由于 Citespace 对年份进行区分，为了避免某些论文标题重复，每个年份做一次去重，即每个`txt`文件做一次去重。
* 由于 Web of Science 的数据更加完整（前提数据来自核心合集数据库），因此，如果存在两条数据重复的情况下，默认选择 Web of Science 的数据库数据，判断方式是`UT`缩略词对应的字符串中含有`WOS`

**操作步骤**：

* 将需要处理的数据存放在`input`文件夹中，运行`main.py`可以得到去重后的`txt`文本数据，文本数据存放在`output`文件夹中。

---------------------------------------------

**问题二**:

需要进行统计分析所有的期刊内容, 分析每个期刊的发文量有多少, 这里将所有的 `SO` 对应的内容进行提取并输出。

**前提条件**：首先需要通过 Citespace 将文献数据分割成年份的形式，也就是 Citespace 去重处理后的效果，如下所示：

![image-20230708151126322](https://vip2.loli.io/2023/07/08/CNm56wEfH4d9AxG.png)

**实现功能二**：ExtractFieldTags

将每篇文献的信息分离出来，然后再在每篇文献的信息中提取 `SO` 对应的内容，提取的内容存放在`output.csv`文件中。

**操作步骤**：

* 将需要处理的数据存放在`input`文件夹中，运行`main.py`可以得到提取的内容存放在`output.csv`文件中。
