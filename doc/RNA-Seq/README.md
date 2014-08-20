# Measuring differences between transcripts

Using [ucsctools](http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/):
 

```bash
genePredToBed GenePredIn GenePredIn.bed
genePredToBed GenePredOut GenePredOut.bed
sed 1p GenePredIn.bed > GenePredIn1.bed
sed 2p GenePredIn.bed >	GenePredIn2.bed
sed 1p GenePredOut.bed > GenePredOut1.bed
sed 2p GenePredOut.bed > GenePredOut2.bed

#a transcript is identical to itself (score=1.0)
bedtools jaccard -a GenePredIn1.bed -b GenePredIn1.bed
#difference between two transcripts in the same genePred file
bedtools jaccard -a GenePredIn1.bed -b GenePredIn2.bed

#difference between input gene model and output gene model
bedtools jaccard -a GenePredIn.bed -b GenePredOut.bed 

#difference between the input genePred file and the output genePred file transcript by transcript
lIn=`cat GenePredIn.bed | wc -l`
lOut=`cat GenePredOut.bed | wc -l`
for ((i=1; i <= $lIn ; i++)); do
    sed -n "$i"p GenePredIn.bed > GenePredIn$i.bed
    for ((j=1; j <= $lOut ; j++)); do
        sed -n "$j"p GenePredOut.bed > GenePredOut$j.bed
    	bedtools jaccard -a GenePredIn$i.bed -b GenePredIn$j.bed
    done
done
```

```
## intersection	union	jaccard
## 12761	12761	1
## intersection	union	jaccard
## 12761	12761	1
## intersection	union	jaccard
## 12309	12761	0.96458
## intersection	union	jaccard
## 12309	12309	1
## intersection	union	jaccard
## 12309	12761	0.96458
## intersection	union	jaccard
## 12309	12761	0.96458
## intersection	union	jaccard
## 12761	12761	1
## intersection	union	jaccard
## 12309	12309	1
## intersection	union	jaccard
## 12309	12761	0.96458
## intersection	union	jaccard
## 12309	12761	0.96458
## intersection	union	jaccard
## 12761	12761	1
## intersection	union	jaccard
## 12306	12692	0.969587
## intersection	union	jaccard
## 12689	12761	0.994358
```
