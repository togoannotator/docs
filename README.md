# TogoAnnotator


## API request examples

1. Input "DnaA" query

```
#!sh
$ curl -s 'http://togoannotator.dbcls.jp/gene/DnaA' | jq
```

2. Input annotation_list.txt

```
#!sh
$ curl -s http://togoannotator.dbcls.jp/annotation_list.txt | curl -s -F 'upload=@-' 'http://togoannotator.dbcls.jp/genes' | jq
```

3. Input ddbj_submission.txt

```
#!sh
$ curl -s http://togoannotator.dbcls.jp/ddbj_submission.txt | curl -s -F 'upload=@-' 'http://togoannotator.dbcls.jp/ddbj' | jq
```

4. Input GenBank format file BA000022.gb

```
#!sh
$ curl -s http://togows.dbcls.jp/entry/nucleotide/BA000022.gb | curl -s -F 'upload=@-' 'http://togoannotator.dbcls.jp/genbank' | jq
```

5. Input BLAST report file 7XS7A95B015-Alignment.txt

```
#!sh
$ curl -s http://togoannotator.dbcls.jp/7XS7A95B015-Alignment.txt | curl -s -F 'upload=@-' 'http://togoannotator.dbcls.jp/blast' | jq
```

6. Input GFF3 format file BA000022.gff

```
#!sh
$ curl -s http://togows.dbcls.jp/entry/nucleotide/BA000022.gff | curl -s -F 'upload=@-' 'http://togoannotator.dbcls.jp/gff'
```

7. Input FASTA format file ABA25090.1.fasta

```
#!sh
$ curl -s http://togows.dbcls.jp/entry/nucleotide/ABA25090.1.fasta | curl -s -F 'upload=@-' 'http://togoannotator.dbcls.jp/fasta' | jq
```