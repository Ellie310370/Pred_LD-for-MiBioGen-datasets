# Pred_LD for MiBioGen datasets
Use Pred_LD to impute a large number of traits without overwriting outputs.

Pred_LD does not accept an output prefix/dir argument. It always writes files like:

[n11385332@aquarius01 PRED-LD]$ ls imputation*.txt
imputation_results_chr10.txt  imputation_results_chr14.txt  imputation_results_chr18.txt  imputation_results_chr21.txt  imputation_results_chr4.txt  imputation_results_chr8.txt
imputation_results_chr11.txt  imputation_results_chr15.txt  imputation_results_chr19.txt  imputation_results_chr22.txt  imputation_results_chr5.txt  imputation_results_chr9.txt
imputation_results_chr12.txt  imputation_results_chr16.txt  imputation_results_chr1.txt   imputation_results_chr2.txt   imputation_results_chr6.txt  imputation_results_chr_all.txt
imputation_results_chr13.txt  imputation_results_chr17.txt  imputation_results_chr20.txt  imputation_results_chr3.txt   imputation_results_chr7.txt

If you run many traits in one directory, later runs will overwrite earlier ones.
This PBS array isolates each task in its own per-trait folder, so every job writes to a unique place and collisions are impossible.

