# ATP-Protein_Interaction
In this ATP binding protein data is used to get ATP bind residue

In this assignment to get input feature, protein sequence is divided into array of size 17 
for eg in sequence VNIKTNPfkaVSFVESAIKKALDNAGYL
arrays are:-
XXXXXXXXVNIKTNPf
XXXXXXXVNIKTNPfk
XXXXXXVNIKTNPfka
:
:
similarly others 
in which middle element or 8th was target ie label for for middle element was taken.
In this X is placeholder or dummy amino acid to complete our 17 array length.

After getting this array I converted this into onehot arrays which is size 21 as 20 ammino acids and X dummy amino acid
For each array or row 17x21 array was build then it was flatten to get 357 length array

After this i consider the hydrophobicity and charged amino acids 
hydrophobic was marked as 1 
hydrophilic was marked as -1 
charged amino acid as 0

Another 17 length array was created from this physiochemical property which was append to onehot array so total 374 length array was created.

This 374 array is input feature for each sequence.

This data contains 49k row if we change the protein sequence as stated above but in this data only about 2500 are ATP interacting so maintain good quality of data I fillered 
2500 ATP interacting sequence and same number of non ATP interacting arrays, so that 50% data is for positive label and same for negative label.

After doing all these operation data of 5000 rows and 2 columns(sequence, label) was created.
In this X is sequence column which is created by onehot and hydrophobic property of amino acid 
and Y is label column.

To get best model of classifier model selection function is used with roc and auc as scoring criteria.
In this test randomforest performed best with about 0.70 AUC and following this SVM which gives about 67% auc.

For this test models were taken from list of model that were K nearest neighbor, naive bayes, support vector machine, modified support vector machine, random forest.
AUC for all is calculated using 5 fold cross validation method, and mean of auc is greatest in random forest followed by SVM.

Now to get best parameters for model gridCV function was used with roc auc as scoring criteria.

After getting best parameter from the list that is given to gridCV model were trained on 80% data and rest for testing purpose.

After getting best model same operation is done for test data to get feature matrix and output is given.




PS:- I trained and tested models in online python notebook so that will work best if run on online notebook ,ipyub file is also attached
