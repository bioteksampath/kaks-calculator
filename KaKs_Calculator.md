


# Introduction #

KaKs\_Calculator is a program that calculates nonsynonymous (Ka) and synonymous (Ks) substitution rates through model selection and model averaging. In addition, several currently acknowledged methods for estimating Ka and Ks are also incorporated into it.

The KaKs\_Calculator package, including source codes, compiled executables and documentation, is freely available for academic use only at http://code.google.com/p/kaks-calculator/downloads/list.


# Installation #

For high efficiency and compatibility with more platforms, the kernel codes of KaKs\_Calculator are written in standard C++. For Windows version we use Visual C++ 6.0 for GUI (Graphics User Interface). And for MAC version we use Objective C for GUI.

## Linux/Unix ##

KaKs\_Calculator has been tested on AIX, IRIX and Solaris.

  * Unpack the package of KaKs\_CalculatorXXX.tar.gz by the following commands.

```
         gzip –d KaKs_CalculatorXXX.tar.gz
         tar –xf KaKs_CalculatorXXX.tar
```

  * If you use other Linux/Unix OS, you have to compile the program in the source codes folder with the help of g++/gcc compiler by yourselves.

```
         cd KaKs_CalculatorXXX/src
         make
```


## Windows ##

The Windows version of KaKs\_Calculator can run on any IBM compatible computer under Windows Operating System (tested on Windows 2000/XP).

  * Unpack the package of KaKs\_CalculatorXXX.tar.gz.
  * In the folder of “KaKs\_CalculatorXXX/bin/Windows/”, just click ‘setup.exe’ for installation.

## MAC ##

KaKs\_Calculator has been tested on MAC OS X version 10.6.6.

  * Open the disk image file of KaKs\_Calculator\_XXX.dmg.
  * Follow the installation instructions and drag the KaKs\_Calculator folder into Applications folder on MAC.
  * Please find KaKs\_Calculator folder in Applications.

# Methods for Calculating Ka and Ks #

Calculating Ka and Ks normally involves three steps. Let us assume that the number of lengths between two DNA sequences compared is n and the number of substitutions between them is m. To calculate Ka and Ks, we need to count the numbers of synonymous (S) and nonsynonymous (N) sites (S + N = n) and the numbers of synonymous (S<sub>d</sub>) and nonsynonymous (N<sub>d</sub>) substitutions (S<sub>d</sub> + N<sub>d</sub> = m). Then it is after correcting multiple substitutions that (N<sub>d</sub>/N) and (S<sub>d</sub>/S) could represent Ka and Ks, respectively, since the observed number of substitutions underestimates the real number of substitutions as sequences diverge over time. Therefore, we can conclude from mentioned above that these methods normally involve three steps to estimate Ka and Ks: counting S and N, counting S<sub>d</sub> and N<sub>d</sub>, and correction for multiple substitutions.

Methods for calculating Ka and Ks adopt different substitution models with subtle yet significant differences. They can be classified as approximate methods and maximum-likelihood methods. Different from approximate methods, maximum-likelihood methods adopt the probability theory to finish all three steps mentioned above in one go.

## Approximate Methods ##

There are several approximate methods incorporated into KaKs\_Calculator, and we list their abbreviations in the program and their corresponding reference(s) as follows.

  * NG: Nei, M. and Gojobori, T. (1986)
  * LWL: Li, W.H., et al. (1985)
  * LPB: Li, W.H. (1993) and Pamilo, P. and Bianchi, N.O. (1993)
  * MLWL (Modified LWL), MLPB (Modified LPB): Tzeng, Y.H., et al. (2004)
  * YN: Yang, Z. and Nielsen, R. (2000)
  * MYN (Modified YN): Zhang, Z., et al. (2006)

## Maximum-Likelihood Methods ##

The method of GY takes account of sequence evolutionary features, such as transition/transversion rate ratio and nucleotide frequencies (reflected in the HKY Model) and incorporates these features into a codon-based model. We extend this method to a set of candidate models in a maximum likelihood framework and use the AICc for model selection and model averaging.

  * GY: Goldman, N. and Yang, Z. (1994)
  * MS (Model Selection), MA (Model Averaging): based on a set of candidate models defined by Posada, D. (2003) as follows.

|Model|Substitution Rates|Nucleotide Frequency|
|:----|:-----------------|:-------------------|
|JC<br>F81<table><thead><th>r<sub>TC</sub>=r<sub>AG</sub>=r<sub>TA</sub>=r<sub>CG</sub>=r<sub>TG</sub>=r<sub>CA</sub></th><th>Equal<br>Unequal</th></thead><tbody>
<tr><td>K2P<br>HKY</td><td>r<sub>TC</sub>=r<sub>AG</sub> ≠ r<sub>TA</sub>=r<sub>CG</sub>=r<sub>TG</sub>=r<sub>CA</sub></td><td>Equal<br>Unequal</td></tr>
<tr><td>TrNEF<br>TrN</td><td>r<sub>TC</sub> ≠ r<sub>AG</sub> ≠ r<sub>TA</sub>=r<sub>CG</sub>=r<sub>TG</sub>=r<sub>CA</sub></td><td>Equal<br>Unequal</td></tr>
<tr><td>K3P<br>K3PUF</td><td>r<sub>TC</sub>=r<sub>AG</sub> ≠ r<sub>TA</sub>=r<sub>CG</sub> ≠ r<sub>TG</sub>=r<sub>CA</sub></td><td>Equal<br>Unequal</td></tr>
<tr><td>TIMEF<br>TIM</td><td>r<sub>TC</sub> ≠ r<sub>AG</sub> ≠ r<sub>TA</sub>=r<sub>CG</sub> ≠ r<sub>TG</sub>=r<sub>CA</sub></td><td>Equal<br>Unequal</td></tr>
<tr><td>TVMEF<br>TVM</td><td>r<sub>TC</sub>=r<sub>AG</sub> ≠ r<sub>TA</sub> ≠ r<sub>CG</sub> ≠ r<sub>TG</sub> ≠ r<sub>CA</sub></td><td>Equal<br>Unequal</td></tr>
<tr><td>SYM<br>GTR</td><td>r<sub>TC</sub>≠r<sub>AG</sub>≠r<sub>TA</sub>≠r<sub>CG</sub>≠r<sub>TG</sub>≠r<sub>CA</sub></td><td>Equal<br>Unequal</td></tr></tbody></table>

r<sub>ij</sub>: substitution rate between i and j, where i ≠ j and i, j∈{A, C, G, T}<br>
<br>
<h1>Format of Sequence</h1>

KaKs_Calculator accepts quasi-AXT sequence format as follows. Before calculation, gaps and stop codons between compared sequences will be removed. You can also see “example.axt” in the folder of “KaKs_CalculatorXXX/examples/”.<br>
<br>
For example:<br>
<br>
<pre><code>        NP_000026<br>
        ATGCTCCTGTG-CCACTGGCC <br>
        ATCCCC-TGCGCTCACTGGAC<br>
</code></pre>

<pre><code>        NP_000053<br>
        ACAGaTtCTACCc-GCCcACTA--GgtGtt<br>
        ---ggTTCTCCtACCcA-G-CACTACTggg<br>
</code></pre>

Each pair of sequences in an AXT file contains three lines: one sequence name line and two sequence lines. Any pairwise sequence is separated from one another by one blank line.<br>
<br>
<ul><li>Sequence name line</li></ul>

<pre><code>        NP_000026<br>
</code></pre>

<ul><li>Pairwise sequences lines</li></ul>

<pre><code>        ATGCTCCTGTG-CCACTGGCC<br>
        ATCCCC-TGCGCTCACTGGAC<br>
</code></pre>

<h1>Parameters setting</h1>

<h2>Linux/Unix</h2>

KaKs_Calculator are more suitable for a large number of dataset to calculate Ka and Ks. It reads a pair of sequences and computes corresponding estimates one by one, so that it requires memory proportional to the maximum length among pairwise sequences. In addition, KaKs_Calculator allows user to choose more than one method to calculate Ka and Ks at one running time. The following is the parameters’ setting in Linux version.<br>
<br>
<ul><li>-i   AXT sequence file name for calculating Ka and Ks<br>
</li><li>-o   File name for outputting results<br>
</li><li>-c   Genetic code (Default = 1-Standard Code). For more information about the Genetic Codes, please see the link <a href='http://www.ncbi.nlm.nih.gov/Taxonomy/Utils/wprintgc.cgi?mode=c'>http://www.ncbi.nlm.nih.gov/Taxonomy/Utils/wprintgc.cgi?mode=c</a>
</li><li>-m	 Methods for calculating Ka and Ks (Default = MA): NG, LWL, LPB, MLWL, MLPB, YN, MYN, GY, MS, MA, ALL (including all above methods)<br>
</li><li>-d	 File name for details about each candidate model only when using the method of MS or MA<br>
</li><li>-h	 Show help information</li></ul>

For example:<br>
<br>
<ul><li>use MA method and standard code</li></ul>

<pre><code>        KaKs_Calculator -i test.axt -o test.axt.kaks<br>
</code></pre>

<ul><li>use MA method and vertebrate mitochondrial code</li></ul>

<pre><code>        KaKs_Calculator -i test.axt -o test.axt.kaks -c 2<br>
</code></pre>

<ul><li>use MA method and standard code and output details of model selection on each candidate model</li></ul>

<pre><code>        KaKs_Calculator -i test.axt -o test.axt.kaks -d test.axt.details<br>
</code></pre>

<ul><li>use LWL, YN and MYN and standard Code</li></ul>

<pre><code>        KaKs_Calculator -i test.axt -o test.axt.kaks -m LWL -m YN -m MYN<br>
</code></pre>

<h2>Windows</h2>

The Windows version provides users with a friendly interface to select input sequences’ file, genetic code and method(s) for estimating Ka and Ks. During calculating you can minimize the application window and send it to tray. After finishing calculation, KaKs_Calculator allows users to export results to file or clipboard at will.<br>
<br>
<br>
<h1>Output Format</h1>

KaKs_Calculator provides comprehensive information estimated from compared sequences, including numbers of synonymous and nonsynonymous sites, numbers of synonymous and nonsynonymous substitutions, GC contents, maximum-likelihood score, and AICC, in addition to synonymous and nonsynonymous substitution rates and their ratio. Meanwhile, Fisher’s exact test for small sample is applied to justify the validity of Ka and Ks calculated by these methods.<br>
<br>
<ul><li>Sequence: Name of Pairwise sequence<br>
</li><li>Method: Name of method for calculation of Ka and Ks<br>
</li><li>Ka: Nonsynonymous substitution rate<br>
</li><li>Ks: Synonymous substitution rate<br>
</li><li>Ka/Ks: Selective strength<br>
</li><li>P-Value(Fisher): The value computed by Fisher exact test<br>
</li><li>Length: Sequence length (after removing gaps and stop codon(s))<br>
</li><li>S-Sites: Synonymous sites<br>
</li><li>N-Sites: Nonsynonymous sites<br>
</li><li>Fold-Sites(0:2:4): 0,2,4-fold degenerate sites<br>
</li><li>Substitutions: Substitutions between sequences<br>
</li><li>S-Substitutions: Synonymous substitutions<br>
</li><li>N-Substitutions: Nonsynonymous substitutions<br>
</li><li>Fold-S-Substitutions(0:2:4): Synonymous substitutions at 0,2,4-fold<br>
</li><li>Fold-N-Substitutions(0:2:4): Nonsynonymous substitutions at 0,2,4-fold<br>
</li><li>Divergence-Time: Divergence time<br>
</li><li>Substitution-Rate-Ratio(rTC:rAG:rTA:rCG:rTG:rCA/rCA): Ratios of six substitution rates to the substitution rate between C and A<br>
</li><li>GC(1:2:3): GC content of entire sequences and of three codon positions<br>
</li><li>ML-Score: Maximum likelihood score<br>
</li><li>AICc: Value of AICc<br>
</li><li>Akaike-Weight: Value of Akaike weight for model selection<br>
</li><li>Model: Selected model for the method of MS</li></ul>

<h1>Acknowledgements</h1>

We thank Professor Wen-Hsiung Li for providing us with his computer program and Professor Ziheng Yang for his invaluable source codes in PAML. We are grateful to Heng Li for his advice and Yafeng Hu for his help in software designing. We also thank all anonymous users for reporting bugs and sending suggestions.<br>
<br>
<h1>References</h1>

<ol><li>Agresti, A. 1992. A Survey of Exact Inference for Contingency Tables. Statistical Science. 7, 131 -177.<br>
</li><li>Akaike, H. 1973 Information theory as an extension of the maximum likelihood principle. In Petrov, B.N. and Csaki, F. (eds), Second International Symposium on Information Theory. Akademiai Kiado, Budapest, 267-281<br>
</li><li>Akaike, H. 1974 A new look at the statistical model identification. IEEE Trans. Autom. Contr. 19, 716-723.<br>
</li><li>Bierne, N. and Eyre-Walker, A. 2003. The Problem of Counting Sites in the Estimation of the Synonymous and Nonsynonymous Substitution Rates: Implications for the Correlation Between the Synonymous Substitution Rate and Codon Usage Bias. Genetics. 165, 1587-1597.<br>
</li><li>Burnham, K.P. and Anderson, D.R. 2002 Model Selection and Multimodel Inference: A Practical Information Theoretic Approach. In. Springer-Verlag, New York, 488.<br>
</li><li>Burnham, K.P. and Anderson, D.R. 2004 Multimodel Inference: Understanding AIC and BIC in Model Selection, Sociological Methods Research, 33, 261-304.<br>
</li><li>Comeron, J.M. 1999. K-Estimator: calculation of the number of nucleotide substitutions per site and the confidence intervals. Bioinformatics. 15, 763-764.<br>
</li><li>Gillespie, J.H. 1991. The causes of molecular evolution. Oxford University Press, Oxford, England.<br>
</li><li>Goldman, N. and Yang, Z. 1994. A codon-based model of nucleotide substitution for protein-coding DNA sequences. Mol. Biol. Evol. 11, 725-736.<br>
</li><li>Hasegawa, M., H. Kishino, and T. Yano 1985. Dating the human-ape splitting by a molecular clock of mitochondrial DNA. J. Mol. Evol. 22, 160-174.<br>
</li><li>Hurst, L.D. 2002. The Ka/Ks ratio: diagnosing the form of sequence evolution. Trends in Genetics. 18, 486-487.<br>
</li><li>Jukes, T.H., and C. R. Cantor 1969. Evolution of protein molecules, 21-123. In Munro, H.N. eds., Mammalian Protein Metabolism. Academic Press, New York.<br>
</li><li>Kimura, M. 1980. A simple method for estimating evolutionary rate of base substitutions through comparative studies of nucleotide sequences. J. Mol. Evol. 16, 111-120.<br>
</li><li>Kimura, M. 1983. The neutral theory of molecular evolution. Cambridge University Press, Cambridge, England.<br>
</li><li>Li, W.H. 1993. Unbiased estimation of the Rates of synonymous and nonsynonymous substitution. J. Mol. Evol. 36, 96-99.<br>
</li><li>Li, W.H. 1997. Molecular evolution. Sinauer Associates. Sunderland, Mass.<br>
</li><li>Li, W.H., Wu, C.I. and Luo, C.C. 1985. A new method for estimating synonymous and nonsynonymous rates of nucleotide substitution considering the relative likelihood of nucleotide and codon changes. Mol. Biol. Evol. 2, 150-174.<br>
</li><li>Muse, S.V. 1996. Estimating synonymous and nonsynonymous substitution rates. Mol. Biol. Evol. 13, 105-114.<br>
</li><li>Nei, M. and Gojobori, T. 1986. Simple methods for estimating the numbers of synonymous and nonsynonymous nucleotide substitutions. Mol Biol Evol. 3, 418-426.<br>
</li><li>Pamilo, P. and Bianchi, N.O. 1993. Evolution of the Zfx and Zfy genes: rates and interdependence between the genes. Mol. Biol. Evol. 10, 271-281.<br>
</li><li>Posada, D. 2003 Using Modeltest and PAUP<code>*</code> to select a model of nucleotide substitution. In Baxevanis, A.D. (ed), Current Protocols in Bioinformatics. JohnWiley & Sons, New York, 6.5.1-6.5.14.<br>
</li><li>Posada, D. and Buckley, T.R. 2004 Model Selection and Model Averaging in Phylogenetics: Advantages of Akaike Information Criterion and Bayesian Approaches over Likelihood Ratio Tests, Syst. Biol., 53, 793-808.<br>
</li><li>Sullivan, J. and Joyce, P. 2005 Model Selection in Phylogenetics, Annual Review of Ecology, Evolution, and Systematics, 36, 445-466.<br>
</li><li>Torrents, D., Suyama, M., Zdobnov, E. and Bork, P. 2003. A Genome-Wide Survey of Human Pseudogenes. Genome Res. 13, 2559-2567.<br>
</li><li>Tzeng, Y.-H., Pan, R. and Li, W.-H. 2004. Comparison of Three Methods for Estimating Rates of Synonymous and Nonsynonymous Nucleotide Substitutions. Mol. Biol. Evol. 21, 2290-2298.<br>
</li><li>Yang, Z. 1997. PAML: a program package for phylogenetic analysis by maximum likelihood. CABIOS. 13, 555-556.<br>
</li><li>Yang, Z. and Nielsen, R. 2000. Estimating Synonymous and Nonsynonymous Substitution Rates Under Realistic Evolutionary Models. Mol Biol Evol. 17, 32-43.<br>
</li><li>Zhang, Z., Li, J. and Yu, J. 2006 Computing Ka and Ks with a consideration of unequal transitional substitutions, BMC Evolutionary Biology, 6, 44.