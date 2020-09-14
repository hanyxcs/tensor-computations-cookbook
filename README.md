# 面向交通数据的张量计算技术

  - 作者：何兆成（中山大学）
  
  > 评述：我们的手册实际上是要提出一种面向交通数据分析与计算的范式，架构包括数据组织-特征计算-分析应用三个层次。第一部分数据组织讲清楚交通数据的多维性、随机性、稀疏性、物理性的特点，通过数据例子呈现这些特性，引出张量结构的优势以及要解决的问题；第二部分是特征计算，这一部分要承前启后，引入满足交通数据特性下的特征计算的各类方法；第三部分是应用分析，给出交通数据分析应用的标准问题：修复问题、聚类问题、预测问题（以后结合图谱还有推理问题），这部分结合案例进行介绍。
  
## 第一章 总论

第一节  交通数据本质特性

第二节  张量简介

第三节  张量与交通数据

## 第二章 张量计算的数学基础

第一节  认识张量

- 张量与张量计算

- 符号与术语规定

第二节  内积与范数

第三节  Kronecker积的计算

- Kronecker积

- Hadamard积与Khatri-Rao积

- 向量化与重构

第四节  张量的展开

- 模态展开与一般性展开

- 外积与秩-1张量

- 模态积

第五节  张量分解

- 高阶奇异值分解

- Tucker逼近与CP逼近

第六节  实例分析：STD分解

## 第三章 概率张量分解

第一节  引例：从确定性分解到不确定性分解

- 两种等价性证明

- 对比L1正则项与L2正则项

- 贝叶斯张量分解的优势

第二节  概率模型的表达：贝叶斯网络

- 贝叶斯网络的分解特性

- 贝叶斯网络的条件独立性

第三节 精确推断方法

- 变量消除法

- 信念传播法

第四节 变分推断

第五节 马尔可夫蒙特卡罗采样

- 拒绝采样

- 重要性采样

- Metropolis采样

- Metropolis-Hastings采样

- Gibbs采样

第六节  实例分析(1)：贝叶斯张量分解

第七节  实例分析(2)：增强贝叶斯张量分解



Contents
--------

-   [第一章    总论](#第一章-总论)
-   [第二章    张量计算的数学基础](#第二章-张量计算的数学基础)
-   [第三章    统计学习基础](#第三章-统计学习基础)
-   [第四章    矩阵分解](#第四章-矩阵分解)
-   [第五章    主成分分析与压缩感知](#第五章-主成分分析与压缩感知)
-   [第六章    张量分解](#第六章-张量分解)
-   [第七章    低秩张量复原](#第七章-低秩张量复原)
-   [第八章    贝叶斯张量分解](#第八章-贝叶斯张量分解)
-   [第九章    深度张量分解](#第九章-深度张量分解)
-   [第十章    张量与交通数据修复](#第十章-张量与交通数据修复)
-   [第十一章  张量分解与交通预测](#第十一章-张量分解与交通预测)
  
## 第一章 总论

第一节  交通数据特性

- 高维度、随机性、稀疏性以及检测器带来的不完备性

- 列举交通数据实例

第二节  张量简介

- 张量定义

- 张量表达数据的优势

- 张量分解概述

第三节  张量与交通数据

- 张量对于交通数据处理的优势

- 概述张量在交通数据分析领域的研究进展

第四节  本书的组织结构

第五节  本章参考文献

- Tamara G. Kolda, Brett W. Bader, 2009. [*Tensor Decompositions and Applications*](https://www.sandia.gov/~tgkolda/pubs/pubfiles/TensorReview.pdf). SIAM REVIEW Vol. 51, No. 3. pp. 455-500.

- Cichocki, A., Lee, N., Oseledets, I., Phan, A. H., Zhao, Q., & Mandic, D. P., 2016. [*Tensor networks for dimensionality reduction and large-scale optimization: Part 1 low-rank tensor decompositions*](https://www.nowpublishers.com/article/DownloadSummary/MAL-059). Foundations and Trends® in Machine Learning, 9(4-5), 249-429.

- Cichocki, A., Phan, A. H., Zhao, Q., Lee, N., Oseledets, I., Sugiyama, M., & Mandic, D. P., 2017. [*Tensor networks for dimensionality reduction and large-scale optimization: Part 2 applications and future perspectives*](https://www.nowpublishers.com/article/DownloadSummary/MAL-067). Foundations and Trends® in Machine Learning, 9(6), 431-673.

- CICHOCKI, Andrzej, et al., 2009. [*Nonnegative matrix and tensor factorizations: applications to exploratory multi-way data analysis and blind source separation*](https://sci.hub.ac.cn/scholar?hl=zh-TW&as_sdt=0%2C5&q=Nonnegative+Matrix+and+Tensor+Factorizations&btnG=). John Wiley & Sons.


## 第二章 张量计算的数学基础

第一节  张量的代数结构

- 张量符号表示

- 张量纤、切片

第二节  范数

- 张量的范数和迹范数

第三节  内积与外积

- 内积与范数关系

- 外积与秩一张量

第四节  矩阵的Kronecker积、Khatri-Rao积和Hadamard积

- 三种矩阵积运算公式

- 互相之间变换公式

第五节  张量与矩阵的n-模积

- 运算公式

- 运算结果

第六节  张量的矩阵化和向量化

- 不同维度矩阵化运算

第七节  本章参考文献

- Tamara G. Kolda, Brett W. Bader, 2009. [*Tensor Decompositions and Applications*](https://www.sandia.gov/~tgkolda/pubs/pubfiles/TensorReview.pdf). SIAM REVIEW Vol. 51, No. 3. pp. 455-500.

- Sidiropoulos, N. D., De Lathauwer, L., Fu, X., Huang, K., Papalexakis, E. E., & Faloutsos, C., 2017. [*Tensor decomposition for signal processing and machine learning*](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7891546). IEEE Transactions on Signal Processing, 65(13), 3551-3582.


## 第三章 统计学习基础

第一节  最大似然估计

第二节  最大后验估计

第三节  共轭分布

第四节  随机过程

- 介绍高斯过程、中餐馆过程等

第五节  MCMC算法

第六节  变分推断

第七节  案例：贝叶斯线性回归

第八节  本章参考文献

- Gelman, A., Stern, H. S., Carlin, J. B., Dunson, D. B., Vehtari, A., & Rubin, D. B., 2013. [*Bayesian data analysis*](https://xs.glgoo.top/scholar?hl=zh-CN&as_sdt=0%2C5&q=Bayesian+Data+Analysis&btnG=). Chapman and Hall/CRC.

- Blei, D. M., Kucukelbir, A., & McAuliffe, J. D., 2017. [*Variational inference: A review for statisticians*](https://www.tandfonline.com/doi/pdf/10.1080/01621459.2017.1285773?needAccess=true). Journal of the American Statistical Association, 112(518), 859-877.

- Gershman, S. J., & Blei, D. M., 2012. [*A tutorial on Bayesian nonparametric models*](https://ac.els-cdn.com/S002224961100071X/1-s2.0-S002224961100071X-main.pdf?_tid=6da6d060-9b18-4c24-a0f9-ee1877378a7f&acdnat=1547348438_c822cbd92c4f9465557bbfa22bb3dc99). Journal of Mathematical Psychology, 56(1), 1-12.

- Hoffman, M. D., Blei, D. M., Wang, C., & Paisley, J., 2013. [*Stochastic variational inference*](http://www.jmlr.org/papers/volume14/hoffman13a/hoffman13a.pdf). The Journal of Machine Learning Research, 14(1), 1303-1347.

- ANDRIEU, Christophe, et al., 2003. [*An introduction to MCMC for machine learning*](https://link.springer.com/content/pdf/10.1023%2FA%3A1020281327116.pdf). Machine learning, 50(1-2), 5-43.

## 第四章 矩阵分解

第一节  特征值分解

第二节  奇异值分解

第三节  UV分解

第四节  概率矩阵分解

第五节  贝叶斯矩阵分解

第六节  本章参考文献

- Golub, G. H., & Van Loan, C. F., 2012. [*Matrix computations*](https://sci-hub.org.cn/scholar?hl=zh-CN&as_sdt=0%2C5&q=Matrix+computions&btnG=&oq=Qibin+)(Vol. 3). JHU Press.

- Salakhutdinov, R., & Mnih, A., 2008. [*Bayesian probabilistic matrix factorization using Markov chain Monte Carlo*](http://delivery.acm.org/10.1145/1400000/1390267/p880-salahutdinov.pdf?ip=120.236.174.155&id=1390267&acc=ACTIVE%20SERVICE&key=BF85BBA5741FDC6E%2E3D07CFA6C3F555EA%2E4D4702B0C3E38B35%2E4D4702B0C3E38B35&__acm__=1547381467_6d56beef989a8ce01131507553552fa1). In Proceedings of the 25th international conference on Machine learning (pp. 880-887). ACM.

- Shahnaz, F., Berry, M. W., Pauca, V. P., & Plemmons, R. J., 2006. [*Document clustering using nonnegative matrix factorization*](https://ac.els-cdn.com/S0306457304001542/1-s2.0-S0306457304001542-main.pdf?_tid=abdf3829-8ebc-4afc-b7f4-86d2c2d32446&acdnat=1547382759_8bb285c19eddbd86fc94312bef66a489). Information Processing & Management, 42(2), 373-386.

- Kim, J., & Park, H., 2008. [*Sparse nonnegative matrix factorization for clustering*](https://smartech.gatech.edu/bitstream/handle/1853/20058/GT-CSE-08-01.pdf?sequence=1&isAllowed=y). Georgia Institute of Technology.

- Petersen, K. B., & Pedersen, M. S., 2008. [*The matrix cookbook*](http://www.cim.mcgill.ca/~dudek/417/Papers/matrixOperations.pdf). Technical University of Denmark, 7(15), 510.


## 第五章 主成分分析与压缩感知

第一节  主成分分析

第二节  概率主成分分析

第三节  贝叶斯主成分分析

第四节  压缩感知

第五节  低秩矩阵复原

第六节  本章参考文献

- Tipping, M. E., & Bishop, C. M., 1999. [*Probabilistic principal component analysis*](https://rss.onlinelibrary.wiley.com/doi/pdf/10.1111/1467-9868.00196). Journal of the Royal Statistical Society: Series B (Statistical Methodology), 61(3), 611-622.

- Bishop, C. M., 1999. [*Bayesian pca*](http://papers.nips.cc/paper/1549-bayesian-pca.pdf). In Advances in neural information processing systems (pp. 382-388).

- Schölkopf, B., Smola, A., & Müller, K. R., 1997. [*Kernel principal component analysis*](https://link.springer.com/content/pdf/10.1007%2FBFb0020217.pdf). In International Conference on Artificial Neural Networks (pp. 583-588). Springer, Berlin, Heidelberg.

- Candes, E. J., & Plan, Y., 2010. [*Matrix completion with noise*](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=5454406). Proceedings of the IEEE, 98(6), 925-936.

- Keshavan, R. H., Montanari, A., & Oh, S., 2010. [*Matrix completion from a few entries*](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=5466511). IEEE transactions on information theory, 56(6), 2980-2998.

- Shen, H., & Huang, J. Z., 2008. [*Sparse principal component analysis via regularized low rank matrix approximation*](https://core.ac.uk/download/pdf/82392248.pdf). Journal of multivariate analysis, 99(6), 1015-1034.


## 第六章 张量分解

第一节  Tucker分解

第二节  CP分解

第三节  本章参考文献

- Tamara G. Kolda, Brett W. Bader, 2009. [*Tensor Decompositions and Applications*](https://www.sandia.gov/~tgkolda/pubs/pubfiles/TensorReview.pdf). SIAM REVIEW Vol. 51, No. 3. pp. 455-500.

- Oseledets, I. V., 2011. [*Tensor-train decomposition*](https://epubs.siam.org/doi/pdf/10.1137/090752286). SIAM Journal on Scientific Computing, 33(5), 2295-2317.

- Yuan, L., Li, C., 2018. [*Tensor Ring Decomposition with Rank Minimization on Latent Space: An Efficient Approach for Tensor Completion*](https://arxiv.org/pdf/1809.02288.pdf). arXiv.

- Nickel, M., Tresp, V., & Kriegel, H. P., 2011. [*A Three-Way Model for Collective Learning on Multi-Relational Data*](http://www.cip.ifi.lmu.de/~nickel/data/slides-icml2011.pdf). In ICML (Vol. 11, pp. 809-816).


## 第七章 低秩张量复原

第一节  核范数最小化

第二节  增强拉格朗日算子

第三节  本章参考文献

- Liu, J., Musialski, P., Wonka, P., & Ye, J, 2013. [*Tensor completion for estimating missing values in visual data*](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6138863). IEEE transactions on pattern analysis and machine intelligence, 35(1), 208-220.

- Chen, Y. L., Hsu, C. T., & Liao, H. Y. M., 2014. [*Simultaneous tensor decomposition and completion using factor priors*](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6587455). IEEE transactions on pattern analysis and machine intelligence, 36(3), 577-591.


## 第八章 贝叶斯张量分解

第一节  高斯张量分解

第二节  贝叶斯高斯张量分解

第三节  泊松张量分解

第四节  贝叶斯时序张量分解

第五节  本章参考文献

- Zhao, Q., Zhang, L., & Cichocki, A., 2015. [*Bayesian CP factorization of incomplete tensors with automatic rank determination*](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7010937). IEEE transactions on pattern analysis and machine intelligence, 37(9), 1751-1763.

- Zhao, Q., Zhang, L., & Cichocki, A., 2015. [*Bayesian sparse Tucker models for dimension reduction and tensor completion*](https://arxiv.org/pdf/1505.02343.pdf). arXiv.

- Schein, A., Paisley, J., Blei, D. M., & Wallach, H., 2015. [*Bayesian poisson tensor factorization for inferring multilateral relations from sparse dyadic event counts*](http://delivery.acm.org/10.1145/2790000/2783414/p1045-schein.pdf?ip=120.236.174.155&id=2783414&acc=ACTIVE%20SERVICE&key=BF85BBA5741FDC6E%2E3D07CFA6C3F555EA%2E4D4702B0C3E38B35%2E4D4702B0C3E38B35&__acm__=1547300174_2e6550300f22e21c87b1e98afc85d9b8). In Proceedings of the 21th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining (pp. 1045-1054). ACM.

- Schein, A., Zhou, M., Blei, D. M., & Wallach, H., 2016. [*Bayesian poisson tucker decomposition for learning the structure of international relations*](http://proceedings.mlr.press/v48/schein16.pdf). arXiv.

- Gopalan, P., Hofman, J. M., & Blei, D. M., 2013. [*Scalable recommendation with poisson factorization*](https://arxiv.org/pdf/1311.1704.pdf). arXiv.

- Gopalan, P., Hofman, J. M., & Blei, D. M., 2015. [*Scalable Recommendation with Hierarchical Poisson Factorization*](http://www.cs.columbia.edu/~blei/papers/GopalanHofmanBlei2015.pdf). In UAI (pp. 326-335).

- Rai, P., Hu, C., Harding, M., & Carin, L., 2015. [*Scalable Probabilistic Tensor Factorization for Binary and Count Data*](https://ccc.glgoo.top/scholar?hl=zh-CN&as_sdt=0%2C5&q=Scalable+Probabilistic+Tensor+Factorization+for+Binary+and+Count+Data&btnG=). In IJCAI (pp. 3770-3776).

- Rai, P., Wang, Y., Guo, S., Chen, G., Dunson, D., & Carin, L., 2014. [*Scalable Bayesian low-rank decomposition of incomplete multiway tensors*](http://proceedings.mlr.press/v32/rai14.pdf). In International Conference on Machine Learning (pp. 1800-1808).

- JOHNDROW, James E.; BHATTACHARYA, Anirban; DUNSON, David B., 2017. [*Tensor decompositions and sparse log-linear models*](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5764221/pdf/nihms855931.pdf). Annals of statistics, 2017, 45.1: 1.

- HU, Changwei. 2017. [*Scalable Bayesian Matrix and Tensor Factorization for Discrete Data*](https://sci.hub.ac.cn/scholar?hl=zh-TW&as_sdt=0%2C5&q=Scalable+Bayesian+Matrix+and+Tensor+Factorization+for+Discrete+Data&btnG=). PhD Thesis.


## 第九章 深度张量分解

第一节  贝叶斯神经网络

- 基本的神经网络

  - 介绍标准的神经网络，并指出现有模型的弊端。

- 用贝叶斯推断求解神经网络

  - 主要介绍变分推断在神经网络中的应用。

第二节  案例：非线性回归

- 具体介绍如何实现贝叶斯神经网络。

第三节  将逼近问题转换为回归问题

- 讨论现有的深度张量分解模型，论述交替条件更新的可行性，探究贝叶斯深度张量分解模型的结构。
  
第四节  本章参考文献

## 第十章 张量与交通数据修复

第一节  缺失交通数据修复

- 城市路网车速数据集

- 矩阵计算技术

- 张量计算技术

第二节  交通模式挖掘

- 隐性特征发现

- 显性特征提取
  
第三节  本章参考文献

- Chen, X., He, Z., & Sun, L., 2019. [*A Bayesian tensor decomposition approach for spatiotemporal traffic data imputation*](https://ac.els-cdn.com/S0968090X1830799X/1-s2.0-S0968090X1830799X-main.pdf?_tid=aacbc3b8-83c5-410d-942b-b3e211878a53&acdnat=1547299868_fdfd4bd4e940c400b3bd95d368f620d6). Transportation Research Part C: Emerging Technologies, 98, 73-84.

- Sun, L., & Axhausen, K. W., 2016. [*Understanding urban mobility patterns with a probabilistic tensor factorization framework*](https://ac.els-cdn.com/S0191261516300261/1-s2.0-S0191261516300261-main.pdf?_tid=5b860e08-f50e-43e7-88fd-67e8a546c8a5&acdnat=1547300718_a39626f45b72887d0897b9c5dcc996d1). Transportation Research Part B: Methodological, 91, 511-524.

- Chen, X., He, Z., & Wang, J., 2018. [*Spatial-temporal traffic speed patterns discovery and incomplete data recovery via SVD-combined tensor decomposition*](https://ac.els-cdn.com/S0968090X17302966/1-s2.0-S0968090X17302966-main.pdf?_tid=b5aa0326-405f-4efb-a725-3e18e0879e53&acdnat=1547301047_76cc7a91a77b051162899536e31c3320). Transportation Research Part C: Emerging Technologies, 86, 59-77.

- Fanaee-T, H., & Gama, J., 2016. [*Event detection from traffic tensors: A hybrid model*](https://ac.els-cdn.com/S0925231216302235/1-s2.0-S0925231216302235-main.pdf?_tid=b05da122-d3e7-4890-bc49-c2435d148c81&acdnat=1547339421_7bdca0bae18a2a9fd1b6a97638969bf7). Neurocomputing, 203, 22-33.

- Asif, M. T., Mitrovic, N., Dauwels, J., & Jaillet, P., 2016. [*Matrix and tensor based methods for missing data estimation in large traffic networks*](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7384738). IEEE Transactions on Intelligent Transportation Systems, 17(7), 1816-1825.

- Ran, B., Tan, H., Wu, Y., & Jin, P. J., 2016. [*Tensor based missing traffic data completion with spatial–temporal correlation*](https://ac.els-cdn.com/S0378437115008870/1-s2.0-S0378437115008870-main.pdf?_tid=b0968db8-de96-4a12-a27b-274d929d4d64&acdnat=1547381638_c29e502169a405b204acdedaa2e7f78b). Physica A: Statistical Mechanics and its Applications, 446, 54-63.


## 第十一章 张量分解与交通预测

第一节  以相似性为基础的交通预测模型

第二节  以时序特征为基础的交通预测模型

第三节  案例：个体出行预测

- 协同群体的出行模式

- 个体出行重构
  
第四节  本章参考文献

- Yu, R., Zheng, S., Anandkumar, A., & Yue, Y., 2017. [*Long-term forecasting using tensor-train RNNs*](https://arxiv.org/pdf/1711.00073.pdf). arXiv.

- Han, Y., & Moutarde, F., 2012. [*Analysis of large-scale traffic dynamics using non-negative tensor factorization*](https://arxiv.org/ftp/arxiv/papers/1212/1212.4675.pdf). arXiv.

- Tan, H., Wu, Y., Shen, B., Jin, P. J., & Ran, B., 2016. [*Short-term traffic prediction based on dynamic tensor completion*](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=7407622). IEEE Transactions on Intelligent Transportation Systems, 17(8), 2123-2133.

- Tan, H., 2014. [*Weighted Tensor Completion-Based Traffic State Estimation Model*](http://or.nsfc.gov.cn/bitstream/00001903-5/417341/1/1000014132925.pdf). (Doctoral dissertation, Department of Transportation Engineering, Beijing Institute of Technology, Beijing).

- Tang, K., Chen, S., Liu, Z., & Khattak, A. J., 2018. [*A tensor-based Bayesian probabilistic model for citywide personalized travel time estimation*](https://ac.els-cdn.com/S0968090X18303103/1-s2.0-S0968090X18303103-main.pdf?_tid=e7c78810-161a-4ab0-a607-415f4284667c&acdnat=1547346249_ac0108cc9c82e65f4fa8f677058a4e92). Transportation Research Part C: Emerging Technologies, 90, 260-280.
