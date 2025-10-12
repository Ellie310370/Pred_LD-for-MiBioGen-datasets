# Pred_LD for MiBioGen datasets
Use Pred_LD to impute a large number of MiBioGen traits without overwriting outputs.

Pred_LD does not accept an output prefix/dir argument. It always writes files like:

[n11385332@aquarius01 PRED-LD]$ ls imputation*.txt
imputation_results_chr10.txt  imputation_results_chr14.txt  imputation_results_chr18.txt  imputation_results_chr21.txt  imputation_results_chr4.txt  imputation_results_chr8.txt
imputation_results_chr11.txt  imputation_results_chr15.txt  imputation_results_chr19.txt  imputation_results_chr22.txt  imputation_results_chr5.txt  imputation_results_chr9.txt
imputation_results_chr12.txt  imputation_results_chr16.txt  imputation_results_chr1.txt   imputation_results_chr2.txt   imputation_results_chr6.txt  imputation_results_chr_all.txt
imputation_results_chr13.txt  imputation_results_chr17.txt  imputation_results_chr20.txt  imputation_results_chr3.txt   imputation_results_chr7.txt

If you run many traits in one directory, later runs will overwrite earlier ones.
Here, I provide a PBS array that isolates each task's working directory and then renames/collects the results.

My idea is:
Run each array task in its own work folder (so identical filenames don't collide).
After pred_ld.py finishes, rename outputs with the trait's basename and move them to a shared results directory.
