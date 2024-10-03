# Introduction à la Bioinformatique - Session 1

---

### Exercice 1 : Analyser et identifier une séquence ADN inconnue

1. Téléchargez le fichier “gène-mystère.fna”.

#### A. À l'aide du terminal, imprimez les premières lignes du document, que remarquez-vous?

<details> <summary>Indice</summary>
La fonction <code>head</code> peut être utilisée pour imprimer les premières lignes d'un ficher texte dans le terminal.
</details>

<details> <summary>Solution</summary>
  
```bash
head gène-mystère.fna
```

Le fichier est composé d'une ligne de titre suivie d'une séquence de caractères (A, C, T ou G).

</details>

---

#### B. Toujours avec le terminal, déterminez combien de caractères alpha-numériques contient ce ficher texte.

<details> <summary>Indice</summary>

La fonction <code>wc</code> peut être utilisée pour compter le nombre de caractères d'un fichier texte avec l'option <code>-m</code>.
</details>

<details> <summary>Solution</summary>

```bash
wc -m gène-mystère.fna
```

&rarr; <b>Le ficher contient 172 826 caractères.</b>

Pas évident mais bon à savoir, le caractère "\n" est compris alors qu'il ne devrait pas (il représente le passage à la prochaine ligne). 

Pour l'exclure, on peut utiliser la fonction <code>tr</code> avec l'option <code>-d</code> pour "delete".

```bash
cat gène-mystère.fna | tr -d '\n' | wc -m
```

&rarr; <b>Le ficher contient donc 170 389 caractères alpha-numériques.</b>
</details>

---

#### C. Combien de nucléotides (A, C, G ou T) contient cette séquence ?

<details> <summary>Indice</summary> 
  
La fonction <code>grep</code> avec l'option <code>-o</code> peut être utilisée pour chercher un caractère et imprimer chaque instance de ce caractère dans le ficher. La fonction <code>uniq</code> avec l'option <code>-c</code> peut être utilisée pour compter le nombre de fois qu'un caractère apparaît.

Les deux fonctions peuvent être combinées avec un pipe <code>|</code>.

</details>

<details> <summary>Solution</summary> 

On peut compter le nombre de fois que chaque nucléotide apparaît séparément :
```bash
grep -o "A" gène-mystère.fna | uniq -c
grep -o "C" gène-mystère.fna | uniq -c
grep -o "T" gène-mystère.fna | uniq -c
grep -o "G" gène-mystère.fna | uniq -c
```

Équivalent avec un for loop :
```bash
for char in "A" "C" "T" "G"; do grep -o $char gène-mystère.fna | uniq -c ; done
```

Ou en une ligne :
```bash
grep -o "[ACTG]" gène-mystère.fna | sort | uniq -c | sort -r
```

</details>

---

#### D. Pourquoi le nombre total de caractères alpha-numériques et le nombre de nucléotides ne sont pas le même ?

<details> <summary>Solution</summary> 
Parce que le fichier contient deux séquences séparées qui sont chacune précédées par une ligne commençant par le symbole ">" indiquant les caractéristiques de la séquence. Ici, les caractéristiques ont été enlevées afin de ne pas révéler l'indentité du gène.
</details>

---

#### E. En génétique, un motif est un court segment d'ADN ou d'acides aminés répétés à de nombreuses reprises le long d'une séquence. Combien de fois le motif "ATAT" apparaît-il dans la séquence mystère ?

<details> <summary>Indice</summary> 
  
Ici on pourrait réutiliser la fonction <code>grep</code> mais un <code>control+F</code> suffira à déterminer le nombre de fois que ce motif apparaît dans la séquence.

</details>

<details> <summary>Solution</summary> 
Le motif "ATAT" apparaît 1007 fois dans la séquence.
</details>

---

#### F. En génétique, le taux de GC (guanine-cytosine) correspond à la proportion de bases nucléiques d'une séquence étant soit une guanine (G), soit une cytosine (C). Le taux de GC est associé à de nombreuses caractéristiques du génome telle que sa taille et peut refléter des traits d'évolution. Estimez le taux de GC de la séquence.

<details> <summary>Solution</summary>
  
(31126 + 33966) / 170389 ≈ 0.382

&rarr; <b>Le taux de GC de la séquence est d'à peu près 38,2%</b>

</details>


2. Accédez au site BLAST : https://blast.ncbi.nlm.nih.gov/Blast.cgi

---
  
<img width="1299" alt="Screenshot 2024-10-01 at 17 25 11" src="https://github.com/user-attachments/assets/bf956ec6-28ed-4655-b470-0f582548baf9">

#### G. Quel outil choisir pour identifier la séquence ?

<details>
<summary>Solution</summary>
  
Il faut utiliser l'outil <b>Nucleotide BLAST</b> car la séquence ADN mystère contient un ensemble de nucléotides (A, C, T ou G) et non pas d'acides aminés, dans quel cas il faudrait utiliser l'outil <b>Protein BLAST</b>.

</details>

3. Copiez/collez l'intégralité de la séquence OU sélectionnez l'option "upload file" pour directement la téléverser.

<img width="945" alt="Screenshot 2024-10-01 at 17 34 00" src="https://github.com/user-attachments/assets/6d4c305a-06c0-4354-9c05-b10c9384a2e3">

4. Cliquez ensuite sur le bouton bleu **BLAST** en bas de la page (inutile de toucher aux autres options pour l'instant).
<img width="132" alt="Screenshot 2024-10-01 at 17 39 51" src="https://github.com/user-attachments/assets/bcc515db-0d41-4f30-8250-2c44f3963666">

5. Patientez une minute.

---

#### H. Qu'indiquent les résultats?

<details> <summary>Solution</summary> La séquence mystère possède un pourcentage d'identité de 100% avec au moins une séquence, ce qui signifie qu'elle correspond à l'identique à un gène présent dans la base de données. </details>

---

#### I. À quel gène correspond cette séquence ?
* A. _FBXO2_
* B. _HOXA2_
* C. _BRCA2_
* D. _EEF1A2_

<details>
<summary>Solution</summary>

&rarr; <b>Réponse C : Le gène _BRCA2_.</b>
  
</details>

---

#### J. À quel organisme appartient ce gène ?

* A. *Mus musculus* (souris)
* B. *Homo sapiens* (humain)
* C. *Drosophila melanogaster* (drosophile)
* D. *Caenorhabditis elegans* (nématode)

<details>
<summary>Solution</summary>
  
&rarr; <b>Réponse B : L'humain.</b>

</details>

---

#### K. Pourquoi un chromosome apparaît comme premier résultat ?

<details>
<summary>Solution</summary>
Le chromosome 13 apparaît comme premier résultat tout simplement car le gène _BRCA2_ se situe sur ce chromosome. Son code génétique est donc contenu dans la séquence du chromosome. 
</details>

---

#### K. Sans quitter le site, déterminez la fonction biologique du gène

<details> <summary>Indice</summary> 
Cliquer sur "l'accession" du gène (dernière colonne du tableau des résultats) vous amènera sur une page descriptive du gène où sa fonction biologique est donnée en détail.
</details>

<details>
<summary>Solution</summary>

BRCA2 est un gène suppresseur de tumeurs dont la mutation est liée à des risques plus élevés de développer un cancer du sein ou un cancer ovarien.
  
</details>

---

<br></br>


### Exercice 2 : Télécharger une séquence depuis une base de donnée
1. Rendez-vous sur le site GenBank : https://www.ncbi.nlm.nih.gov/genbank/

<img width="1070" alt="Screenshot 2024-10-01 at 18 08 18" src="https://github.com/user-attachments/assets/c6b135dc-bf16-41c0-b99b-2570718c4f01">

2. Sélectionnez l'option de recherche "All Databases" ou "Gene".
3. Entrez **_BRCA1_** dans la barre de recherche puis cliquez sur le bouton "search".
4. Cliquez sur la première option (montrée ci-dessous) puis sur le bouton "download datasets" en cochant uniquement l'option "Gene Sequences (FASTA)".

<img width="875" alt="Screenshot 2024-10-03 at 12 09 34" src="https://github.com/user-attachments/assets/c150bb23-f7cd-4564-ae2a-cd7c4922008d">

5. Décompressez le fichier ZIP.

#### Où se trouve le fichier contenant la séquence de nucléotides ?

<details>
<summary>Solution</summary>
  
À l'adresse suivante, dans le dossier obtenu après avoir décompressé le fichier ZIP :

```bash
~/ncbi_dataset/data/gene.fna
```

</details>


