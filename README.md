# Pred_LD for MiBioGen datasets
Here I show how I used Pred_LD (https://github.com/pbagos/PRED-LD) to impute a large number of traits without overwriting outputs.
Pred_LD does not accept an output prefix/dir argument. It always writes files like:

[n11385332@aquarius01 PRED-LD]$ ls imputation*.txt
imputation_results_chr10.txt  imputation_results_chr14.txt  imputation_results_chr18.txt  imputation_results_chr21.txt  imputation_results_chr4.txt  imputation_results_chr8.txt
imputation_results_chr11.txt  imputation_results_chr15.txt  imputation_results_chr19.txt  imputation_results_chr22.txt  imputation_results_chr5.txt  imputation_results_chr9.txt
imputation_results_chr12.txt  imputation_results_chr16.txt  imputation_results_chr1.txt   imputation_results_chr2.txt   imputation_results_chr6.txt  imputation_results_chr_all.txt
imputation_results_chr13.txt  imputation_results_chr17.txt  imputation_results_chr20.txt  imputation_results_chr3.txt   imputation_results_chr7.txt

If you run many traits in one directory, later runs will overwrite earlier ones.
This PBS array (pred-ld_array_MiBioGen.pbs) isolates each task in its own per-trait folder, so every job writes to a unique place and collisions are impossible.
Then I needed to rename the output files according to the name of each taxon (which corresponds to the subfolder names in the output directory):
for d in */; do cp "${d}imputation_results_chr_all.txt" "${d%/}_predLD.imputed.txt"; done
So, now I have all the files renamed in the output directory!
