# Exerciții laborator 2 – 2025

# Bine de știut: 
Rețineți că, pentru a evita problemele legate de actualizarea componentelor Swing
dintr-un alt fir de execuție decât cel numit *Event Dispatch Thread*, ar trebui să folosiți metoda
*SwingUtilities.invokeLater()* sau *SwingUtilities.invokeAndWait()* pentru a actualiza *JTextArea* cu
noile mesaje.
```
SwingUtilities.invokeLater(new Runnable() {
    public void run() {
        // Code to update the UI, e.g., setText() or repaint().
    }
});
```

## Exercițiul 1: 
Creați și porniți două fire de execuție cu nume personalizate:
1. Creați o nouă clasă MyThread care extinde clasa Thread.
2. Suprascrieți metoda run() a clasei Thread pentru a afișa numele firului de execuție curent.
3. Creați două instanțe ale clasei MyThread cu nume personalizate și porniți-le.

## Exercițiul 2:
Creați două fire de execuție care generează numere prime și folosesc interrupt()
În acest exercițiu, veți crea două fire care generează numere prime. După un timp specificat, firul
principal va întrerupe firele generatoare de numere prime, împiedicându-le să găsească mai multe
numere prime.
1. Creați o nouă clasă PrimeGenerator care implementează interfața Runnable.
2. Definiți atributele clasei PrimeGenerator, daca sunt necesare.
3. Creați un constructor pentru clasa PrimeGenerator, daca este necesar.
4. Implementați o metodă booleană isPrime(int number) în clasa PrimeGenerator pentru a verifica
dacă un anumit număr este prim.
5. Implementați metoda run() a interfeței Runnable pentru a genera numere prime în ordine
crescătoare. Dacă firul curent este întrerupt, nu mai generați numere prime și-și tiparește numele,
prioritatea și ultimul număr calculat. Firul curent verifică dacă a fost întrerupt cu ajutorul metodei
isInterrupted();
6. În metoda principală, creați două instanțe Thread folosind clasa PrimeGenerator cu nume
personalizate și priorități diferite și porniți-le.
7. După ce ați așteptat un timp specificat (de exemplu, 2 secunde), întrerupeți ambele fire.
8. Creșteți numărul de fire de execuție până când se observă importanța priorităților.

## Exercițiul 3: 
Modificați aplicația anterioră astfel încât pornirea și întreruperea firelor de execuție să se realizeze
dintr-o intefață grafică prin intermediul a două butoane. Afișarea rezultatelor se va face tot aici.

# Exercițiul 4: 
Aplicație Swing cu JTextArea și buton pentru afișarea mesajelor în paralel
Cerință: Creați o aplicație cu o interfață grafică ce va fi compusă dintr-un buton și o zonă de text
(JTextArea). De fiecare dată când se apasă butonul, se creează un nou fir de execuție (cu nume
implicit) care afișează la interval de 1 secundă câte 10 mesaje în zona de text, pe câte o nouă linie.
Mesajele vor fi de forma: "nume - mesajul n". Evident, este faptul că firele de execuție vor scrie în
paralel dacă se apasă butonul de mai multe ori suficient de repede.
Pentru a realiza acest exercițiu, urmați pașii de mai jos:
1. Creați o nouă clasă MessageRunnable care implementează interfața Runnable.
2. Implementați metoda run() în clasa MessageRunnable. În această metodă, generați și afișați cele
10 mesaje, cu o pauză de 1 secundă între ele. Fiecare mesaj va avea forma: "nume - mesajul n",
unde "nume" este numele firului de execuție și "n" este numărul curent al mesajului.
3. Creați o nouă clasă MessageApp care extinde clasa JFrame. Aceasta va conține interfața grafică
a aplicației.
4. În clasa MessageApp, adăugați un obiect JButton și un obiect JTextArea într-un layout adecvat.
5. Adăugați un ActionListener la buton, astfel încât, atunci când se apasă butonul, să se creeze și să
se ruleze un nou fir de execuție cu o instanță a clasei MessageRunnable.
6. Implementați logica necesară pentru a adăuga mesajele generate de fiecare fir de execuție în
zona de text JTextArea în mod corespunzător, fără a interfera cu celelalte fire de execuție.

# Exercițiul 5: 
Aplicație Java (Swing) cu butoane 'Start' și 'Stop' și o formă geometrică în mișcare
Creați o aplicație Java (Swing) cu două butoane, 'Start' și 'Stop', plasate în partea de sus a ferestrei.
În partea de jos a ferestrei, în zona centrală, va fi afișată o formă geometrică sau un alt buton. Forma
geometrică va începe să se miște înspre dreapta până va ajunge la marginea ferestrei, apoi înspre
stânga până la marginea ferestrei, și așa mai departe. Forma va fi controlată de un fir de execuție
nou. Pornirea și oprirea mișcării se realizează prin intermediul celor două butoane.
Pentru a realiza acest exercițiu, urmați pașii de mai jos:
1. Creați o nouă clasă care extinde JFrame, numită MovingShapeApp, pentru a conține interfața
grafică a aplicației.
2. În clasa MovingShapeApp, adăugați obiectele JButton pentru butoanele 'Start' și 'Stop', precum
și o componentă personalizată (de exemplu, o clasă care extinde JPanel) pentru a desena și afișa
forma geometrică în mișcare.
3. Adăugați ActionListener-i pentru butoanele 'Start' și 'Stop'. Când se apasă butonul 'Start', creați
și porniți un nou fir de execuție care controlează mișcarea formei geometrice. Când se apasă
butonul 'Stop', opriți firul de execuție.
4. Implementați logica pentru mișcarea formei geometrice în firul de execuție. Forma se va deplasa
înspre dreapta până când atinge marginea ferestrei, apoi înspre stânga până la marginea ferestrei, și
așa mai departe.
5. Asigurați-vă că actualizarea componentei personalizate care afișează forma geometrică se face
pe Event Dispatch Thread (EDT), folosind SwingUtilities.invokeLater().
