# I Powłoka systemu GNU/Linux. Wyrażenia regularne.

Rezultaty ćwiczenia:
- umiejętność pracy w konsoli Linux
- zastosowania wyrażeń regularnych
- umiejętność posługiwania się bazą Prosite

### Do przygotowania przed ćwiczeniem!

> - praca w terminalu Linux   
> https://ubuntu.com/tutorials/command-line-for-beginners#4-creating-folders-and-files

> - wyrażenia regularne  
> https://regexone.com/

### Gdzie można przećwiczyć komendy?

> - online  
> https://jslinux.org/

> - lokalnie na komputerze z systemem Linux

> - lokalnie na komputerze z systemem Windows po zainstalowaniu WSL <br>
  (Windows Subsystem for Linux) i wybranej dystrybucji Linux  
> https://docs.microsoft.com/en-us/windows/wsl/install  
> <br>lub<br>  
> Ubuntu przez Windows Store  
> ![Ubuntu przez Windows Store](https://raw.githubusercontent.com/frogmaker/Bioinformatyka1/main/assets/images/ubuntuWindowsStore.png?token=GHSAT0AAAAAACTD7WUHB3WYTHWEU2QS7RU4ZTAI4IQ)


### Pliki, które zostaną użyte podczas ćwiczenia:

<table>
<tr>
<td>  

- zinc-finger.fasta   <br>
- p450.fasta<br>
- aldolazy.fasta  
</td>
<td>
pliki zawierają sekwencje aminokwasowe,  <br>
które będą analizowane podczas wykonywania  
ćwiczenia  
</td>  
</tr>
</table>

### Przygotowanie do ćwiczeń:

Pobierz pliki Pobierz pliki do utworzonego katalogu cw1:
 - Bioinformatyka1_cw1.doc
 - p450.fasta
 - zinc_finger.fasta
 - Praca_zdalna_Linux.pdf
 - Instalacja_WSL.pdf

Polecenia:    
>     mkdir cw1

>     cd cw1

>     cp /home/ksarapata/dydaktyka/bioinf1/cw1/cw1.docx

>     cp /home/ksarapata/dydaktyka/bioinf1/cw1/p450.fasta

itd.

$${\color{red}ścieżka\space do\space plików,\space polecenia\space wget,\space git\space clone?}$$

![ls](https://raw.githubusercontent.com/frogmaker/Bioinformatyka1/main/assets/images/ls.png?token=GHSAT0AAAAAACTD7WUGMWIZU5GDZCH6KYZKZTAIZLQ)   
![mkdir](https://raw.githubusercontent.com/frogmaker/Bioinformatyka1/main/assets/images/mkdir.png?token=GHSAT0AAAAAACTD7WUH7KO3T562FE6KEJVYZTAI2IA)

<br><br>
# II Format FASTA

Format FASTA to ujednolicony sposób zapisu sekwencji biologicznych: kwasów nukleinowych lub białek. Plik FASTA może zawierać  
jedną lub więcej sekwencji. Każda sekwencja jest zapisana w postaci kodu jednoliterowego i poprzedzona linią zaczynającą się  
od znaku ">", po którym wymieniany jest zawsze identyfikator sekwencji, a następnie jej opis.  

Przykładowa sekwencja zapisana w formacie FASTA:  

![FASTA1](https://raw.githubusercontent.com/frogmaker/Bioinformatyka1/main/assets/images/fasta1.png?token=GHSAT0AAAAAACTD7WUGIGN3HVEMLAEGGJEWZTAI2RA)  

<table>
<tr>
<th>  
<img width="70%", src="https://raw.githubusercontent.com/frogmaker/Bioinformatyka1/main/assets/images/sekwencje_biologiczne.png?token=GHSAT0AAAAAACTD7WUGMWJI7CXLLWX6PZX6ZTAI25A">  
</th>
<th>
<img width="80%", src="https://raw.githubusercontent.com/frogmaker/Bioinformatyka1/main/assets/images/NA_notation.png?token=GHSAT0AAAAAACTD7WUGIWLQ655PNXULSPQEZTAI5AQ"><br><br>
https://en.wikipedia.org/wiki/Nucleic_acid_notation
</th>  
</tr>
<tr>
<td colspan="2">  
>gi|90421312|ref|NM_000492.3| Homo sapiens cystic fibrosis transmembrane conductance <br>
regulator (ATP-binding cassette sub-family C, member 7) (CFTR), mRNA <br>
AATTGGAAGCAAATGACATCACAGCAGGTCAGAGAAAAAGGGTTGAGCGGCAGGCACCCAGAGTAGTAGGTCTTTGGCAT <br>
TAGGAGCTTGAGCCCAGACGGCCCTAGCAGGGACCCCAGCGCCCGAGAGACCATGCAGAGGTCGCCTCTGGAAAAGGCCA <br>
GCGTTGTCTCCAAACTTTTTTTCAGCTGGACCAGACCAATTTTGAGGAAAGGATACAGACAGCGCCTGGAATTGTCAGAC <br>
ATATACCAAATCCCTTCTGTTGATTCTGCTGACAATCTATCTGAAAAATTGGAAAGAGAATGGGATAGAGAGCTGGCTTC <br>
AAAGAAAAATCCTAAACTCATTAATGCCCTTCGGCGATGTTTTTTCTGGAGATTTATGTTCTATGGAATCTTTTTATATT <br>
TAGGGGAAGTCACCAAAGCAGTACAGCCTCTCTTACTGGGAAGAATCATAGCTTCCTATGACCCGGATAACAAGGAGGAA <br>
CGCTCTATCGCGATTTATCTAGGCATAGGCTTATGCCTTCTCTTTATTGTGAGGACACTGCTCCTACACCCAGCCATTTT <br>
TGGCCTTCATCACATTGGAATGCAGATGAGAATAGCTATGTTTAGTTTGATTTATAAGAAGACTTTAAAGCTGTCAAGCC <br>
GTGTTCTAGATAAAATAAGTATTGGACAACTTGTTAGTCTCCTTTCCAACAACCTGAACAAATTTGATGAAGGACTTGCA <br>
TTGGCACATTTCGTGTGGATCGCTCCTTTGCAAGTGGCACTCCTCATGGGGCTAATCTGGGAGTTGTTACAGGCGTCTGC <br>
CTTCTGTGGACTTGGTTTCCTGATAGTCCTTGCCCTTTTTCAGGCTGGGCTAGGGAGAATGATGATGAAGTACAGAGATC <br>
AGAGAGCTGGGAAGATCAGTGAAAGACTTGTGATTACCTCAGAAATGATTGAAAATATCCAATCTGTTAAGGCATACTGC <br>
TGGGAAGAAGCAATGGAAAAAATGATTGAAAACTTAAGACAAACAGAACTGAAACTGACTCGGAAGGCAGCCTATGTGAG <br>
ATACTTCAATAGCTCAGCCTTCTTCTTCTCAGGGTTCTTTGTGGTGTTTTTATCTGTGCTTCCCTATGCACTAATCAAAG <br>
GAATCATCCTCCGGAAAATATTCACCACCATCTCATTCTGCATTGTTCTGCGCATGGCGGTCACTCGGCAATTTCCCTGG <br>
GCTGTACAAACATGGTATGACTCTCTTGGAGCAATAAACAAAATACAGGATTTCTTACAAAAGCAAGAATATAAGACATT <br>
.........
</td> 
</tr>
</table>
<br><br>
<table>
<tr>
<td>
synonimy – wyrazy bliskoznaczne<br>
antonimy – przeciwieństwa<br>
homonimy – wyrazy, które tak samo się pisze<br>
  i wymawia, ale znaczą coś innego<br>
homofony – wyrazy, które tak samo brzmią,<br>
  ale inaczej się je pisze i znaczą coś innego<br>
ananim – relacja dwóch wyrazów, wyraz pisany od tyłu<br>
palindrom – wyraz tak samo czytany od przodu <br>
  jak i od tyłu  <br><br><br><br><br><br>
<table>
<tr>
<td>zdanie</td><td>profil</td>
  
</tr>
  <tr>
<td>słowo</td><td>motyw</td>
  
</tr><tr>
<td>słowo konserwatywne</td><td>wzorzec, synonim</td>
  
</tr><tr>
<td>palindrom</td><td>miejsce aktywności<br>
nukleazy<br>
spinki RNA<br></td>
  
</tr>
</table>
<br><br><br><br><br><br><br><br><br><br><br><br>
</td>
<th>
<img width="100%", src="https://raw.githubusercontent.com/frogmaker/Bioinformatyka1/main/assets/images/zdanie.png?token=GHSAT0AAAAAACTD7WUGXPAF4Y77LPTNBK74ZTAI3LQ"> 
  
</th>
  
</tr>


  
</table>
