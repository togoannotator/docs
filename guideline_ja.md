# 国際タンパク質命名ガイドライン
## 国際タンパク質命名ガイドラインとは

国際タンパク質命名ガイドラインは、 European Bioinformatics Institute (EMBL-EBI)、National Center for Biotechnology Information (NCBI)、Protein Information Resource (PIR) および Swiss Institute for Bioinformatics (SIB)によって共同で作成され、タンパク質に名前を付けたい人が、データベース間でのタンパク質命名の一貫性を高め、データ検索を支援し、コミュニケーションを改善するために使用することを目的としている。

一貫した蛋白質の命名法は,コミュニケーション,文献検索,エントリー検索に不可欠である。よいタンパク質名とは、他の種からのオーソログに帰属させることができ、適切な場合には公式の遺伝子命名法に従うことができる、ユニークで明確なタンパク質名である。名前をタンパク質シークエンスに関連付けるプロセスには、シークエンス機能の同定/予測、名前の選択、フォーマットの適用など、さまざまな要素がある。ここでは、名前の選択と汎用フォーマットに関するガイドラインを示しており、配列からの機能同定/予測に使用される方法に関するベストプラクティスは対象とされていない。

## TogoAnnotatorにおけるガイドラインへの準拠
TogoAnnotatorにおいては、以下の２つのプロセスにおいてガイドラインが利用している
1. 入力クエリーに対して国際タンパク質命名ガイドライン項目に準拠しているかの情報を提供
2. 類似マッチの結果に対して、ガイドラインに準拠している辞書データが検索上位となるような最適化

### ガイドライン項目詳細の定義
TogoAnnotatorでは、ガイドラインの項目詳細をIDで管理し、情報を提供している。以下で良い例、悪い例とともにTogoAnnotatorの実装による対応状況を示す。

| id | code | message | bad example | good example | implementation |
|-|-|-|-|-|-|
| PN001 | 2-A | Use American spelling, not British spelling | uncharacterised protein catalyse | characterise | TRUE |
| PN002 | 2-A | Use protein names ending in 'in' (not 'ine') | maurocalcine | maurocalcin | TRUE |
| PN003 | 2-A | Avoid diacritics such as accents, umlauts etc. | protein spätzle 5  | protein spaetzle 5 | TRUE |
| PN004 | 2-A | Avoid pluralization for names based on domain and repeat content | ankyrin repeats-containing protein | ankyrin repeat-containing protein | TRUE |
| PN005 | 2-A | Avoid common words | protein IMPACT |  | TRUE |
| PN006 | 2-A | Avoid duplication |  |  | FALSE |
| PN007 | 2-B | Avoid using an abbreviation as the complete name | ACP | acyl carrier protein | TRUE |
| PN008 | 2-B | An abbreviation may be part of a protein name | (3R)-hydroxymyristoyl-ACP dehydratase | (3R)-hydroxymyristoyl-ACP dehydratase | FALSE |
| PN009 | 2-B | Protein name based on a protein symbol (PS) or gene symbol (GS): Prokaryote symbol guidelines |  |  | FALSE |
| PN010 | 2-B | Protein name based on a protein symbol (PS) or gene symbol (GS): Eukaryote symbol guidelines |  |  | FALSE |
| PN011 | 2-B | Prime symbol (') | 5-prime-nucleotidase | H(+)-transporting V0 sector ATPase subunit c' | TRUE |
| PN012 | 2-B | Chemical symbols may be part of a protein name | Na(+)/Li(+)-exporting P-type ATPase | sodium/lithium-exporting P-type ATPase | TRUE |
| PN013 | 2-B | Standard scientific abbreviations may be part of a protein name | ribosomal RNA methyltransferase | ABC transporter | TRUE |
| PN014 | 2-C | Do not use a back slash: ‘\’. | adenylyltransferase\ADP-heptose synthase cyclohydrolase | adenylyltransferase/ADP-heptose synthase cyclohydrolase | TRUE |
| PN015 | 2-C | For separating multiple domains or functions, the forward slash ‘/’ or the word ‘and’ may be used. | adenylyltransferase\ADP-heptose synthase cyclohydrolase | WD repeat and FYVE domain-containing protein 3 | FALSE |
| PN016 | 2-C | Compound adjective: a hyphen should be used to form compound modifiers (i.e. two or more words that are acting as a single modifier for a noun) | Ras GTPase activating protein | Ras GTPase activating protein | TRUE |
| PN017 | 2-C | Remove trailing periods from names. | hypotheical protein. | hypothetical protein | TRUE |
| PN018 | 2-C | Avoid use of commas except when their usage is part of accepted chemical names. | Phycobilisome 27.9 kDa linker polypeptide, phycoerythrin-associated, rod | SGT2 family TPR domain-containing protein | TRUE |
| PN019 | 2-C | Avoid the semi-colon ";" or colon “:” except when it is part of an enzyme name. | Nucleosome assembly protein 1;1 | Nucleosome assembly protein 1 | TRUE |
| PN020 | 2-C | Avoid the percentage sign ‘%’ |  |  | TRUE |
| PN021 | 2-C | Avoid the at sign '@’ |  |  | TRUE |
| PN022 | 2-C | Avoid the equal sign ‘=’ | gustducin:SUBUNIT=alpha | guanine nucleotide-binding protein G(t) subunit alpha-3 | TRUE |
| PN023 | 2-C | Data submitters should not let Microsoft Excel, Word, Outlook, or any other utility with format interpolation and spelling autocorrection touch any protein names, especially those with quotes and double-hyphens. | Phospholipase A2 "basic" | basic phospholipase A2 | FALSE |
| PN024 | 2-D | Use Arabic rather than Roman numerals | caveolin-II | caveolin-2 | TRUE |
| PN025 | 2-D | Specifying different members encoded by a multigene family |  |  | FALSE |
| PN026 | 2-E | Capitalization | Proteasome CORE PARTICLE  subunit BETA 5 | proteasome core particle subunit beta 5 | TRUE |
| PN027 | 2-E | Greek letters should be written in full and entirely in lower case when indicating one of a series of proteins e.g. "alpha", "beta", “gamma”. | Mating-type protein ALPHA1 | Mating-type protein alpha 1 | TRUE |
| PN028 | 2-E | In the context of steroid/fatty acid metabolism nomenclature, “Delta” should start with an upper case letter. | 3beta-hydroxy-delta5-steroid | 3beta-hydroxy-Delta5-steroid | TRUE |
| PN029 | 2-E | Usage of the term 'protein' in a name | Accessory gene regulator protein A | Accessory gene regulator A | TRUE |
| PN030 | 2-E | Usage of the term ‘enzyme’ in a name | Phosphotransferase enzyme IIA component | Phosphotransferase IIA component | TRUE |
| PN031 | 2-E | Use this format: "<Pathway> synthesis protein <GS>" |  | thiamine synthesis protein ThiC | FALSE |
| PN032 | 2-E | Transfer enzymes |  | formylmethanofuran--tetrahydromethanopterin formyltransferase | FALSE |
| PN033 | 2-E | Use this format: <amino acid being attached>--tRNA (tRNA type using the three-letter amino acid code with the first letter capitalized) ligase |  | tyrosine--tRNA (Tyr) ligase | FALSE |
| PN034 | 2-E | Identifier types to avoid | 5-formyltetrahydrofolate cyclo-ligase-like protein COG0212 | 5-formyltetrahydrofolate cyclo-ligase-like protein | TRUE |
| PN035 | 2-E | Avoid kingdom, genus or species-specific characteristics in a name |  |  | FALSE |
| PN036 | 2-F | Avoid linking words and phrases | histidine kinase  sensor of two component system | two-component system sensor histidine kinase | TRUE |
| PN037 | 2-F | Other phrases to avoid | ATPase involved in chromosome partitioning | chromosome-partitioning ATPase | TRUE |
| PN038 | 2-F | Terms to avoid | Ephrin-B1 C-terminal fragment | Ephrin-B1 | TRUE |
| PN039 | 3-A | Established and maintained database authorities such as species-specific nomenclature bodies (some are listed here: http://www.uniprot.org/docs/nomlist). |  |  | FALSE |
| PN040 | 3-A | Avoid names from species-specific authorities that relate to phenotype, anatomical features or any taxon-specific characteristics. In these cases, use the widely recognized gene symbol in combination with a functional name rather than a phenotypical name. For example, ‘minichromosome maintenance complex component 7’ is not applicable to organisms which do not have minichromosomes so to avoid transferring such a protein name, use the gene symbol MCM7 combined with a functional name instead. |  |  | FALSE |
| PN041 | 3-A | a) Expert sources of specific and definitive names may include: Enzyme names from Enzyme Commission (EC) |  |  | TRUE |
| PN042 | 3-A | Expert sources of specific and definitive names may include: NCBIfam |  |  | TRUE |
| PN043 | 3-A | a) Expert sources of specific and definitive names may include: UniProtKB/Swiss-Prot |  |  | TRUE |
| PN044 | 3-A | Individual scientists who specialize in a protein family. |  |  | FALSE |
| PN045 | 3-A | A recent literature-supported name from a paper that characterized the protein function is likely the most specific and definitive name to apply (with format refinement as needed). The literature may provide a history of names over time. |  |  | FALSE |
| PN046 | 3-A | Expert sources of specific and definitive names may include: TIGRFam |  |  | FALSE |
| PN047 | 3-A | Expert sources of specific and definitive names may include: Pfam |  |  | TRUE |
| PN048 | 3-B | If no other name is applicable, the words bifunctional or multifunctional may be used in combination with the functional names. | Bifunctional protein | Peroxisomal multifunctional enzyme | TRUE |
| PN049 | 3-B | Use 'subunit', not 'chain' or 'component', for members of protein complexes. The exception is historical cases where ‘chain’ is exclusively used e.g. myosins, clathrins, dyneins. | Sarcosine reductase complex component B alpha chain | Ammonia monooxygenase gamma subunit | TRUE |
| PN050 | 3-B | Inactive proteins do not refer to pseudogenes. Inactive versions of proteins refer to proteins with altered catalytic residues or inability to undergo autocatalytic cleavage, resulting in loss of expected activity. Reserve the usage of “inactive” in a protein name for such cases. | inactive glutathione hydrolase 2 | inactive glutathione hydrolase 2 | TRUE |
| PN051 | 3-B | use the default name ‘hypothetical protein’ or ‘uncharacterized protein’ (all lowercase) with no further specifications. | hypothetical protein, conserved | hypothetical protein | TRUE |

### 検索結果の表示
TBW

### 検索アルゴリズム
TBW

### 国際タンパク質命名ガイドラインの詳細




### リファレンス
* International Protein Nomenclature Guidelines https://www.ncbi.nlm.nih.gov/genome/doc/internatprot_nomenguide/
