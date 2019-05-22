# NLP 自然語言處理與文字探勘

[講師投影片](https://drive.google.com/drive/folders/1z8xqnQZLf6GVKBEIeNYI5KK3k2Vrv43T)

[資料與投影片](https://drive.google.com/file/d/1t4nI0R0TMBPDsdbFO2q1V4X_KxF-ADgM/view)

[播放清單](https://www.youtube.com/playlist?list=PL1f_B9coMEeCpkBHXNJBPoVY5LcbDMHvk)



##  NLP Basic

Meaning Representation 



#### Knowledge-Based Representation 辭典或導師告訴你字的意思或你去查字典

Hypernyms \(is-a\) relationships of WordNet 可以想像成字

Issues:

* newly-invented words 新的字
* subjective 字和字之間的關係不確定\(每人解讀可能不一樣\)
* annotation effort 很多專家在編譯 wordNet，效率可能會不好
* difficult to compute word similarity 很難去比較之間的關聯性

根據以上問題，我們比較推薦使用Corpus-Based Representation

Corpus-Based Representation 靠Big Data 告所我們資訊，依據前後文來告訴你字的意思

#### Atomic symbols: one-hot representation

Idea: words with similar meanings often have similar neighbors 如果兩個字有相關，可以會有共同相關連的字出現

#### Neighbor-based representation

* Co-occurrence matrix constructed via neightbors
* Neighbor definition: full document vs windows



Full document:

word-document co-occurrence matrix gives general topics -&gt; "Latent Sematic Analysis"

Windows:

context window for each word -&gt; capture syntactic \(e.g. POS\) and sematic information



#### Window-Base Co-occurrence Matrix

Example

* Window lenght=1
* Left or Right context
* Corpus: 

Issues:

* matrix size increases with vocabulary
* high dimensional
* sparsity -&gt; poor robustness

Idea: low dimensional word vector



#### Low-Dimensional Dense Word Vector

Method 1：dimension reduction on the matrix

Singular Value Decomposition \(SVD\) of co-occurrence matrix X

Semantic relations

Syntacitc relations

Issue：

* computationally expensive: O\(mn2\) when n&lt;m matrix
* difficult to add new words

Idea: directly learn low-dimensional word vectors 直接在空間上是哪一個位置



Method2：directly learn low-dimensional word vectors

Recent and most popular models: word2vec\(Mikolov et al. 2013\) and Glove\(Pennington et al., 2014\) and As known as "Word Embeddings"





2. 文字探勘

3. 文字探勘 - 實作 

4. 文字特徵工程

