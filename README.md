/*
	Author Louiza HANIS
	Date : 01/09/2016
*/
------------------------------------------------------------------	
Purpose 

This software is used in metagenomic field. It takes as input a matrix generated by another software and calculates correlation between all its vectors and draw histogam of the results.  
------------------------------------------------------------------
Compilation 
go run main.go -i data/Matrix.txt -o outputFile

Input / Ouput parameters 
-i <>: The file containing the input matrix  
-o <>: The file containing the output matrix  
------------------------------------------------------------------
Notice :
******  

All outputs of this software are generated in outputData folder
------------------------------------------------------------------
profiler

In order to profile the program, i implemented a function that call the go profiler "pprof"

If you want to run the code with profiling you need to compile using go build , this way : 
	go build main.go 

Run the program using the flag -cpuprofile 
	./main <parameters> -cpuprofile=<fileName>

You can visualize the result by generate a pdf. Tape this command in your terminal 
	go tool pprof --pdf ./main outputData/fileName.prof > outputData/fileName.pdf
	xpdf fileName.pdf
-------------------------------------------------------------------
Race detector 

In order to detect concurrency conflicts, compile the program adding the flag -race this way 
	go run -race main.go <parameters> 
-------------------------------------------------------------------
validator 

Its contains a code i implemented by R langage, its serves to validate the results of metaGo. 
By taking the same input matrix you can compare the two output files , doing the following operation : 
	diff -b metaGo_outputFile validator_outputFile 