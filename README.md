# Introduction à la Bioinformatique - Session 1

---

### Exercice 1 : Identifier une séquence ADN inconnue avec BLAST

1. Téléchargez le fichier “gène-mystère.fna”
2. Ouvrez le fichier avec l'éditeur de texte de votre choix et regardez de quoi est composée la séquence
3. Accédez au site BLAST : https://blast.ncbi.nlm.nih.gov/Blast.cgi
  
<img width="1299" alt="Screenshot 2024-10-01 at 17 25 11" src="https://github.com/user-attachments/assets/bf956ec6-28ed-4655-b470-0f582548baf9">

#### Quel outil choisir pour identifier la séquence ?

<details>
<summary>Solution</summary>
Il faut utiliser l'outil “Nucleotide BLAST” car la séquence ADN mystère contient un ensemble de nucléotides (A, C, T ou G) et non pas d'acides aminés, dans quel cas il faudrait utiliser l'outil "Protein BLAST".
</details>

4. Copiez/collez l'intégralité de la séquence OU sélectionnez l'option "upload file" pour directement la téléverser.

<img width="945" alt="Screenshot 2024-10-01 at 17 34 00" src="https://github.com/user-attachments/assets/6d4c305a-06c0-4354-9c05-b10c9384a2e3">

5. Cliquez ensuite sur le bouton bleu **BLAST** en bas de la page (inutile de toucher aux autres options pour l'instant).
<img width="132" alt="Screenshot 2024-10-01 at 17 39 51" src="https://github.com/user-attachments/assets/bcc515db-0d41-4f30-8250-2c44f3963666">

6. Patientez une minute

#### Quel gène correspond à cette séquence ?
* A. APOE1
* B. HOXA1
* C. BRCA1
* D. EEF1A1

<details>
<summary>Solution</summary>
Réponse C : Le gène BRCA1, dont la mutation est liée au développement du cancer du sein.
</details>

#### À quel organisme appartient ce gène ?

* A. *Mus musculus* (souris)
* B. *Homo sapiens* (humain)
* C. *Drosophila melanogaster* (drosophile)
* D. *Caenorhabditis elegans* (nématode)

<details>
<summary>Solution</summary>
Réponse B : L'humain.
</details>

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


