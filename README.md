# Asymptotic-Theory-of-PCA
## Introduction
主成分分析は，$10$次元や$50$次元，$100$次元といった多くの次元を持つ多次元データを$2$次元や$3$次元といった次元に圧縮し，データ構造を視覚的に把握する手法であり，元のデータの線形結合として合成された新たな変数の持つ意味を見いだすことによって，有益な情報抽出が可能となる．理論上は元々ある次元の数だけ主成分といういくつかの条件を持ったそれぞれのデータの線形結合を構成できるが，その線形結合が圧縮された小次元データ，つまりは計測されたデータの意味のある組み替えとなり，元の多次元データの代わりに主成分を分析することができる．具体的な応用としては，文字画像の圧縮と復元（LeCun \textit{et al.}$\cite{bib:cun}$，Bishop\cite{bib:bishop}）が挙げられる．

多次元データに内在する情報はデータのまとまりと散らばり，つまり分散で捉えられ，主成分の構成では分散をできる限り保存するように新しい変数を定義していくことになる．主成分の構成方法の背景として，データの共分散行列の固有値や固有ベクトルが鍵になる．具体的には，以下のように主成分は構成される．$\slp$次元のデータを$\bX$とする．さらに，このデータに基づいた共分散行列の固有値を$\lambda_1\geq\cdots \geq\lambda_\slp\geq 0$として，各固有値に対応する正規化した固有ベクトルを$\bbeta^1,...,\bbeta^{\slp}$とすると，この$\bbeta^1,...,\bbeta^{\slp}$が主成分となる．データに対して主成分分析を適用することは，主成分$\bbeta^1,...,\bbeta^{\slp}$から主成分$\bbeta^1,...,\bbeta^{q}$（$q\leq\slp$）を選択することであり，元の観測された$\slp$次元データ$\bX$を$q$次元データ$(\bbeta^{1'}\bX,...,\bbeta^{q'}\bX)'$へと縮小できる．この主成分の構成より，得られた標本から主成分の構成を行うためには母集団の共分散行列またはその固有値と固有ベクトルの推定が必要となることがわかる．

本[記事]([https://github.com/ShoShohh/T.W.Anderson-2003-_Hypo/blob/main/Anderson(2003)_Hypo.pdf](https://github.com/ShoShohh/Asymptotic-Theory-of-PCA/blob/main/Asymptotic%20Theory%20of%20PCA.pdf))は，母共分散行列の固有値・固有ベクトルの推定と検定を標本共分散行列の固有値・固有ベクトルを用いて行うことを目的としている．そこで，Anderson\cite{bib:anderson}を参考にし，確率変数の中心極限定理から確率変数ベクトルの中心極限定理と確率変数行列の中心極限定理を示し，標本の共分散行列の固有値・固有ベクトルを並べた確率変数行列の漸近分布から母共分散行列の固有値・固有ベクトルの推測を行う．また本レポートでは，主成分の構成としてデータの線形結合の分散の最大化を共分散行列の固有値・固有ベクトルの問題へ帰着できる様子を確認している．本レポートの構成は以下のとおりである．$\cref{chap1}$では，確率論の基本概念を導入し，確率変数の中心極限定理から確率変数ベクトルと確率変数行列の中心極限定理を示している．$\cref{chapshu}$では，主成分の構成を共分散行列の固有値・固有ベクトル問題へ帰着できることを示す定理について述べている．$\cref{zenkin}$では，確率変数行列の中心極限定理を用いて，標本共分散行列の固有値・固有ベクトルの漸近分布を示している．$\cref{kenteitoukeiryou}$では，標本共分散行列の固有値・固有ベクトルの漸近理論に基づいて母固有値の推定と検定を解説している．$\cref{data}$では，実データ解析を行っている．$\cref{syoumei}$では$\cref{chap1}$から$\cref{kenteitoukeiryou}$に登場した定理を証明している．$\cref{hoten}$では$\cref{syoumei}$の証明で用いた定義と補題を載せている．

本[記事]([https://github.com/ShoShohh/T.W.Anderson-2003-_Hypo/blob/main/Anderson(2003)_Hypo.pdf](https://github.com/ShoShohh/Asymptotic-Theory-of-PCA/blob/main/Asymptotic%20Theory%20of%20PCA.pdf))は確率論・数理統計学の基礎を既に学んだ学生を読者として想定している．確率論・数理統計学の基礎ではなじみのない確率変数ベクトルと確率変数行列を扱っているが，確率変数から連続して読み進められるように心がけた．本レポートが読者に主成分分析への興味を促し，行列代数による確率論と数理統計学の導入となれば幸いである．

pdfファイルは51ページあるので，ダウンロードしてお読みいただくことをオススメします．
# Code
実行しているコードは主に[R言語]([https://github.com/ShoShohh/T.W.Anderson-2003-_Hypo/tree/main/with%20R](https://github.com/ShoShohh/Asymptotic-Theory-of-PCA/tree/main/with%20R))ですが，同様の出力を行うような[Python]()も（準備でき次第）載せています．