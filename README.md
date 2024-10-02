# Introduction à la Bioinformatique - Session 1

---

### Exercice 1 : Identifier une séquence ADN inconnue avec BLAST

1. Téléchargez le fichier “gène-mystère.fna”.
2. Ouvrez le fichier avec l'éditeur de texte de votre choix et examinez la séquence.

#### A. À l'aide du terminal, déterminez combien de caractères alpha-numériques contient ce ficher texte.

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

#### B. Combien de nucléotides (A, C, G ou T) contient cette séquence ?

<details> <summary>Indice</summary> 
  
La fonction <code>grep</code> peut être utilisée pour compter le nombre de fois qu'un caractère spécifique apparaît dans un fichier texte

</details>

<details> <summary>Solution</summary> 

```bash
grep -o "[ACTG]" gène-mystère.fna | sort | uniq -c
```

</details>

---

#### C. Pourquoi le nombre total de caractères alpha-numériques et le nombre de nucléotides ne sont pas le même ?

<details> <summary>Solution</summary> 
Parce que le fichier contient deux séquences séparées qui sont chacune précédées par une ligne commençant par le symbole ">" indiquant les caractéristiques de la séquence. Ici, les caractéristiques ont été enlevées afin de ne pas révéler l'indentité du gène.
</details>

---

#### D. En génétique, un motif est un court segment d'ADN ou d'acides aminés répétés à de nombreuses reprises le long d'une séquence. Combien de fois le motif "ATAT" apparaît-il dans la séquence mystère ?

<details> <summary>Indice</summary> 
  
Ici on pourrait réutiliser la fonction <code>grep</code> mais un <code>control+F</code> suffira à déterminer le nombre de fois que ce motif apparaît dans la séquence.

</details>

<details> <summary>Solution</summary> 
Le motif "ATAT" apparaît 910 fois dans la séquence.
</details>

---

#### E. En génétique, le taux de GC (guanine-cytosine) correspond à la proportion de bases nucléiques d'une séquence étant soit une guanine (G), soit une cytosine (C). Le taux de GC est associé à de nombreuses caractéristiques du génome telle que sa taille et peut refléter des traits d'évolution. Estimez le taux de GC de la séquence.

<details> <summary>Solution</summary>
  
(31126 + 33966) / 170389 ≈ 0.382

&rarr; <b>Le taux de GC de la séquence est d'à peu près 38.2%</b>

</details>


3. Accédez au site BLAST : https://blast.ncbi.nlm.nih.gov/Blast.cgi

---
  
<img width="1299" alt="Screenshot 2024-10-01 at 17 25 11" src="https://github.com/user-attachments/assets/bf956ec6-28ed-4655-b470-0f582548baf9">

#### F. Quel outil choisir pour identifier la séquence ?

<details>
<summary>Solution</summary>
  
Il faut utiliser l'outil <b>Nucleotide BLAST</b> car la séquence ADN mystère contient un ensemble de nucléotides (A, C, T ou G) et non pas d'acides aminés, dans quel cas il faudrait utiliser l'outil <b>Protein BLAST</b>.

</details>

4. Copiez/collez l'intégralité de la séquence OU sélectionnez l'option "upload file" pour directement la téléverser.

<img width="945" alt="Screenshot 2024-10-01 at 17 34 00" src="https://github.com/user-attachments/assets/6d4c305a-06c0-4354-9c05-b10c9384a2e3">

5. Cliquez ensuite sur le bouton bleu **BLAST** en bas de la page (inutile de toucher aux autres options pour l'instant).
<img width="132" alt="Screenshot 2024-10-01 at 17 39 51" src="https://github.com/user-attachments/assets/bcc515db-0d41-4f30-8250-2c44f3963666">

6. Patientez une minute.

---

#### G. Quel est le pourcentage d'identité entre la séquence soumise et le résultat BLAST le plus significatif ?

<details> <summary>Solution</summary> Le pourcentage d'identité entre la séquence et le premier résultat est de 100%, ce qui signifie que la séquence mystère correspond à l'identique à un gène présent dans la base de données. </details>

---

#### H. À quel gène correspond cette séquence ?
* A. APOE1
* B. HOXA1
* C. BRCA1
* D. EEF1A1

<details>
<summary>Solution</summary>

&rarr; <bold>Réponse C : Le gène BRCA1, dont la mutation est liée au développement du cancer du sein.</bold>
  
</details>

---

#### I. À quel organisme appartient ce gène ?

* A. *Mus musculus* (souris)
* B. *Homo sapiens* (humain)
* C. *Drosophila melanogaster* (drosophile)
* D. *Caenorhabditis elegans* (nématode)

<details>
<summary>Solution</summary>
  
&rarr; <bold>Réponse B : L'humain.</bold>

</details>

<br></br>

---




### Exercice 2 : Télécharger une séquence depuis une base de donnée
1. Rendez-vous sur le site GenBank : https://www.ncbi.nlm.nih.gov/genbank/

<img width="1070" alt="Screenshot 2024-10-01 at 18 08 18" src="https://github.com/user-attachments/assets/c6b135dc-bf16-41c0-b99b-2570718c4f01">

2. Assurez-vous que l'option de recherche "All Databases" ou "Gene" soit cochée
3. Entrez **BRCA2** dans la barre de recherche puis cliquez sur le bouton "search"
4. Cliquez sur la première option (montrée ci-dessous) puis sur le bouton "download datasets" en cochant uniquement l'option "Gene Sequences (FASTA)"

<img width="799" alt="Screenshot 2024-10-01 at 18 10 46" src="https://github.com/user-attachments/assets/7bbf7cd1-709e-4912-a3f9-8f15f01dae09">

5. Décompressez le fichier ZIP

#### Où se trouve le fichier contenant la séquence de nucléotides ?


<details>
<summary>Solution</summary>
~/ncbi_dataset/data/gene.fna (dans le dossier obtenu après avoir décompressé le fichier ZIP)
</details>


