Download Link: https://assignmentchef.com/product/solved-pl-homework3
<br>



<ol>

 <li>Please go to the following link to find the SSW library:</li>

</ol>

<u>https://github.com/mengyao/Complete-Striped-Smith-Waterman-Library</u>

<ol start="2">

 <li>Find the /src/ssw.c for the implementation in C of the Striped Smith Waterman algorithm as your reference.</li>

</ol>

(https://academic.oup.com/bioinformatics/article/23/2/156/205631)

<ol start="3">

 <li>Write a software using a modern C++ SIMD library (e.g., simdpp:</li>

</ol>

<u>https://github.com/p12tic/libsimdpp</u>) that can perform pairwise alignment with the Striped Smither Waterman algorithm.

<ol>

 <li>INPUT: Two sequences (i.e., Seq1 and Seq2) in the FASTA format (<u>https://en.wikipedia.org/wiki/FASTA_format</u>), it is OK to assume no newline in a sequence.</li>

 <li>OUTPUT: BLAST like output but simplified</li>

</ol>




Speedup: 0.4X

Seq1:      453    CCAATGCCACAAAACATCTGTCTCTAACTGGTG–TGTGTGT    492

|||  ||| ||||  |||||| | ||| |||||  |*|||||

Seq2:       17    CCA–GCC-CAAA–ATCTGT-TTTAA-TGGTGGATTTGTGT    51




“|”: match

“ ”: indel, add gaps “-” in the corresponding sequences.

“*” : mismatch




The speedup is calculated against the time needed for the regular banded Smith-Waterman implementeation without SIMD, which means that you need to implemented both versions (i.e., w/ and w/o SIMD).




#include&lt;queue&gt;

#include&lt;functional&gt;

#include&lt;iostream&gt;

Void add()

{

std::cerr&lt;&lt;“1”&lt;&lt;std::endl;

}




struct ADD

{

void operator()()

{

std::cerr&lt;&lt;”2”&lt;&lt;std::endl;

}

};




int main(void)

{

ADD a;

std::queue&lt; std::function&lt;void(void)&gt; &gt; jobs;             jobs.push( std::bind(add) );                 jobs.push( std::bind( std::bind(a) ) );

jobs.push( std::bind(a) );




while(!jobs.empty() )

{

jobs.front()();                          jobs.pop();

}

return 0;

}