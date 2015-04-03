# QUASSI #
The major histocompatibility complex (MHC), a cell-surface protein
mediating immune recognition, plays important roles on immune
response system in all higher vertebrates. The polymorphism of MHC
in the regions determining the peptide binding specificity complexes
MHC molecule classification. Serotype information also provides
important evidence for MHC classification. As well known, both
protein structure and function are determined by sequence contents,
especially at some specific positions which play crucial roles in
entire MHC. A 21-residue pseudo sequence was found by Nielson enough
to capture the encoded information. Here, we proposed a linear
programming based approach called quassi to find significance residue positions as
well as quantifying their significance in MHC II DR molecules.
## INPUT ##
Input is a string of fasta sequences of MHC II DR molecules. 1284 protein sequences of HLA-DR molecules downloaded from
ImMunoGeneTicsHLA database. After removing all the less
preferable data, the remaining 962 sequences were aligned and conserved region (89bp) of β chain were kept. The 962 sequences are divided into 19 groups, and each group of sequences are stored in a file named with prefix "fasta" (fasta1 to fasta19). Each sequence is in the format of FASTA, which is as follows:

>DRB1\_0101

WQLKFECHFFNGTERVRLLERCIYNQEESVRFDSDVGEYRAVTELGRPDAEYWNSQKDLLEQRRAAVDTYCRHNYGVGESF

The first line gives the allele name after a ">" symbol, while the following lines give the respective amino acids.
Another input file is named "blossum62.txt", which is the blossum file for a set of 20 amino acids union a gap symbol. All the input files are stored in "newinput" folder under the path of source code.
## ENVIRONMENT CONFIGURATION ##
Before running any one of the programs, you must make sure cplex has been successfully installed in your computer.

In windows：
  * Edit system variable
variable name: ILOG\_LICENSE\_FILE;
variable value: the location where access.ilm lies, for example: C:\ILOG\ILM\access.ilm.
  * Add cplex.jar in eclipse
right click a class/package/project, Build Path->Configure Build Path->Libraries->Add External JARs->point to the location where cplex.jar is, for example: cplex.jar - C:\ILOG\CPLEX111\lib
  * Add .dll in the path
Run->Run Configurations->Select your main class->Arguments->VM arguments->add library path, the location where cplexxxx.dll is, for example: -Djava.library.path=C:\ILOG\CPLEX111\bin\x86\_win32

In linux:

To install, you put the package x86-64.bin anywhere on your machine and then do the following:
  * chmod +x x86-32.bin or chmod +x x86-64.bin
  * sudo ./x86-32.bin or sudo ./x86-64.bin
  * For example, our java file is named HLAnewdata.java, do the following:
> javac -classpath /home/yfan/opt/ibm/ILOG/CPLEX\_Studio124/cplex/lib/cplex.jar -O HLAnewdata.java
> nohup java -d64 -Djava.library.path=/home/yfan/opt/ibm/ILOG/CPLEX\_Studio124/cplex/bin/x86-64\_sles10\_4.1 -classpath /home/yfan/opt/ibm/ILOG/CPLEX\_Studio124/cplex/lib/cplex.jar: HLAnewdata  &
For more explanations, please look at the manual:
http://pic.dhe.ibm.com/infocenter/cosinfoc/v12r2/index.jsp?topic=%2Filog.odms.cplex.help%2FContent%2FOptimization%2FDocumentation%2FCPLEX%2F_pubskel%2FCPLEX19.html ;
## PROGRAM ##
Quassi is composed of three main programs as follows.
    * HLAsolver.java
It aims to solve out the minumum number of failure inequalities, as well as the corresponding positions and significance values of MHC II DR molecules.
    * HLAsolver\_z.java
When the number of failure inequalities is limited, this program aims to solve out the significance positions and their corresponding values.
    * HLAsolver\_lim.java
When the number of significance positions is limited, this program aims to solve out the number of failure inequalities, as well as the positions and their corresponding values.
## OUTPUT ##
All the output files are stored in "output" folder under the path of source code. You can find an example file named "output.txt" in Dowloads to seee the format of output.

The first line is the status of solution for this program, for example "Feasible", "Optimal", etc.

The second line gives of optimal solution for this program.

The third line shows the significance positions solved as well as corresponding values.

The fourth line gives the failure inequalities as well as the corresponding HLA alleles.

# COPYRIGHT #
All are welcome to use my source code, but the copyright belongs to Ying FAN. If you have any advises or questions, please contact yingying1988@gmail.com