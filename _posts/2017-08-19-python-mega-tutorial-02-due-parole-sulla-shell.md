---
layout: post
title: "Python Mega Tutorial (in Italiano) 02: Due parole sulla shell"
ref: pymt02
date: 2017-08-19
categories: python
lang: it
---
Due parole sulla shell? So che perdo metà dei miei 3 lettori proprio qui, al secondo post, ma... non si può evitare!

Nota bene: ho scritto il seguente anche per darvi un assaggio del python e delle sue reali possibilità.

## Come si mangia una shell?

La shell non è una cosa che si mangia: è il terminale, dove vuoi o non vuoi ha vita la tua applicazione.

Ma io voglio scrivere programmi che ci fai doppio click sopra, non che devo lanciare in un terminale!
Perfetto! Però permettimi prima due parole sulla shell.

Due parole... e un po' di codice... Perciò apri il tuo editor preferito, questo è il listato del tuo nuovo programma.

(**NB**: il codice sul solito [repo](https://github.com/oldmammuth/pythonmegatutorial), cartella *tut02*)

#### app.py

```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Ciao, mondo!'

if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0')
```

### Aspetta un attimo: che è sta roba???

*Keep calm, siamo programmatori!*

Andiamo passo passo.

#### Spieghiamo il codice

```python
from flask import Flask
```

Con questo comando diciamo all'interprete python che abbiamo bisogno del modulo ```Flask``` della libreria ```flask```.
Nota bene: maiuscole e minuscole sono importanti!

Terminology (lo studio del T3):
- *libreria*, o *framework*, o *library* (in realtà ci sono distinzioni fra questi termini, ma sono sottigliezze!): una collezione di funzioni riutilizzabili creata da un programmatore per uno specifico compito: ci sono librerie per la grafica, librerie per le funzioni matematiche, etc. etc.
- le librerie sono organizzate in *moduli*(o *funzioni*) che si occupano di funzioni più specifiche.
(*NB*: la terminologia inglese in materia è a dir poco confusa, e quella italiana agginge confusione a confusione. Con il passare del tempo sarà tutto molto più chiaro, anche perché il codice non è confuso, solo il linguaggio per descriverlo. Fidatevi più del codice che dei programmatori in questo caso!)

Esempio: voglio creare una libreria per l'interfaccia utente? Ci dovrò mettere su un modulo che si occupi delle finestre, uno che si occupi di icone, uno che si occupi di bottoni...

Nota II: è importante avere installato le librerie che usiamo sulla macchina (il computer) sul quale eseguiamo il programma. Se il Flask non è installato, uno dei seguenti lo dovrebbe istallare (dipende dal vostro ambiente di sviluppo):
```shell
pip install Flask
# oppure
pip3 install Flask
# oppure (inserire la propria password di root)
sudo pip install Flask
# oppure (inserire la propria password di root)
sudo pip3 install Flask
```
Altrimenti una ricerca veloce su come installare ```pip``` o alternative a *pip* dovrebbero funzionare. (Gli ambienti di sviluppo python sono molto eterogenei, purtroppo!)

Proseguiamo.

```python
app = Flask(__name__)
```

- ```app``` è una variabile cui assegniamo un valore; in questo caso gli assegniamo la funzione ```Flask()``` che abbiamo appena importato
- una variabile in informatica è molto simile (a prima vista) ad una variabile matematica: in matematica possiamo scrivere ```y = 2X```, usando due variabili, *X* ed *Y*; la stessa cosa per le variabili in python, anche se le variabili in python hanno un po' più di proprietà che le variabili matematiche... Tutto a tempo debito! 
- la funzione ```Flask()``` come si vede dalle parentesi prende un argomento: è buona prassi con questa funzione passargli la variabile ```__name__```. Ma da quale cappello vien fuori questa variabile? le variabili con due ```_``` (*underscore*) sono assegnate dall'interprete python, per dare informazioni al programma: in questo caso, se il programma che stiamo eseguendo è parte di una libreria, il python mette dentro ```__name___``` il nome del modulo quando è importato, cosicché il programma conosce il suo "nome". Per esempio, nel modulo ```Flask``` che abbiamo importato prima il python assegnerà il valore *flask* alla variabile. Se invece il programma viene eseguito direttamente la variabile avrà il nome di ```__main__``` a significare che è il programma principale e non un modulo importato. Quindi, in parole povere, è come se avessimo passato il valore *__main__* alla funzione ```Flask()``` direttamente... Dunque avremmo potuto scrivere direttamente ```app = Flask('__main__')```? Sì, e funziona pure... Ma è assolutamente da evitare: Flask ha i suoi buoni motivi per farsi passare la variabile *__name__*, fidatevi!

Bene, l'istruzione seguente,
```python
@app.route('/')
```
è un *decoratore*, come indicato dal ```@```. Il decoratore altera la funzione che lo segue; senza scendere in dettagli scabrosi, un decoratore è una funzione che accetta parametri e li usa per modificare un'altra funzione. Quindi sappiamo che ```@app.route('/')``` sta lì per modificare la funzione seguente

```python
@app.route('/')
def hello_world():
    return 'Ciao, mondo!'
```

(Ho lasciato bene in vista il decoratore, perché è parte del blocco-funzione).

Una funzione (decorata o meno che sia) si definisce con la parola chiave ```def``` seguita dal nome della funzione, i parametri che accetta fra parentesi (parentesi vuote ```()``` se non prende nessun parametro) e i **due punti**: da notare bene questi due punti, perché sono causa di errori nell'esecuzione dei programmi.

Inoltre, il corpo della funzione (o un *blocco di codice* in genere) **va indentato obbligatoriamente**. Quindi imparate la regola: mettete 4 spazi prima di ogni riga che è parte del corpo di una funzione, un *if*, etc, etc... Insomma, tutti i *corpus* vanno separati dal resto e messi insieme, anche graficamente, all'interno del codice
(Nota: altri programmi racchiudono questi blocchi di codice tra parentesi graffe, e l'indentazione è semplicemente una buona pratica per visualizzare velocemente il codice; in python **non si mettono delimitatori di sorta** (```{}```), ma quando finisce l'indentazione è segno che è finito il blocco di codice; anche questo è causa di indicibili errori di esecuzione, quindi applicatevi diligentemente all'indentazione!)

Una funzione di solito (ma non sempre) dà come risultato un valore, il risultato di tutti i calcoli. Il *ritorno* della funzione si indica attraverso ```return``` seguito da ciò che si vuole rimandare indietro come risultato; in questo caso abbiamo una stringa che dice ```'ciao, mondo!```, il solito *helloworld*!

Siccome stiamo usando *Flask* il decoratore *route* che abbiamo chiamato dalla nostra ```app``` si occuperà di usare questo valore di ritorno nel modo più consono...

Proseguendo,
```python
if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0')
```

Ancora un altro blocco, da come si vede dall'indentazione, ed ancora una volta la variabile ```__name__```. Questa volta, però, non abbiamo la definizione di una funzione, ma un *if*:

```if``` è una struttura di controllo: si usa per controllare qualcosa ed agire di conseguenza. In inglese *if* significa *se*; in una *if* si usa il doppio uguale ```==``` per controllare che due valori siano identici (infatti un uguale solo assegna un valore ad una variabile, vi ricordate ```app = Flask()```?).
Il costrutto è un po' come se dicesse (tradotto in italiano):

	se il valore di __name__ è uguale a '__main__', allora esegui questo blocco di codice
quindi, ricapitolando, la sintassi dell'*if* è:
```python
if condizione-da-verificare :
    // blocco di codice da eseguire se la condizione è vera //
```
Quindi il blocco di codice viene eseguito se è vero che la variabile ```__name__``` contiene il valore ```'__main__'```. Ma noi sapiamo che tutte le volte che il programma viene eseguito direttamente l'interprete assegna il valore di ```'__main__'``` alla variabile  ```__name__```. Quindi sappiamo che se questo codice viene eseguito e non chiamato da qualche altro programma, la condizione sarà sempre vera ed il blocco che segue verà eseguito. E' una maniera molto conveniente per mettere tutte le procedure da eseguire solo in caso il codice venga eseguito direttamente. Tra l'altro, adesso si intuisce facilmente che se ne fa il Flask della variabile ```__name__```: ha delle funzioni da eseguire solo se il programma è principale, ed altre se invece è parte di un programma più grande!

Ma cosa fa il codice nel blocco da eseguire? Chiama la funzione ```run()``` del Flask con opportuni parametri. Di solito i parametri vanno passati in ordine, ma se si specifica il nome nel formato ```nomeparametro=valore```, come in questo caso, si possono passare in qualsiasi ordine, oppure saltarne qualcuno ed affidarsi ai parametri di default.

## Conclusioni

Abbiamo imparato molte cose nuove oggi...

...ma non abbiamo la benché minima idea di quello che faccia questo programma, nè che c'entra con la famigerata *shell* (non ce n'eravamo dimenticati, spero!)

Eseguiamo il codice:

(se non avete installato il Flask con il pip adesso è il momento! Sennò controllate l'utility che ho messo nel repo, è carina...)

```python
python app.py
```
Wow, cioè? Nella mia console io ottengo qualcosa di simile al seguente:

```
 * Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 138-352-976
```
Per capire cosa sta succedendo, aprite il vostro browser sul "sito" 

```localhost:5000``` oppure ``` http://0.0.0.0:5000/```

Dove *localhost* rappresenta la vostra macchina e *5000* è la porta (occhio ai firewall, ma dovrebbero acconsentire automaticamente...)

Io ottengo nel browser il seguente 

```Ciao, mondo!```

E se modificate il file, nella return della funzione, ci mettete

```python
@app.route('/')
def hello_world():
    return 'Ciao, a tutti,<br> belli e brutti!'
```
Il Flask dovrebbe automagicamente rieseguire se stesso, e con un *refresh* del browser (```F5``` o icona appropriata) il risultato dovrebbe apparire nel browser (Sì, il ```<br>``` è un codice HTML che viene correttamente interpretato dal browser, mandando a capo: è la prova che il Flask fa il dovere suo). Se il Flask non si riavvia, ```CTRL+C``` per stopparlo e ```python app.py``` per ricominciare daccapo.

Flask è una libreria per creare microserver, cioè server che svolgano un determinato programma e mostrino il risultato nel browser...

...e la shell? E' tutta lì la magia: in realtà ogni server è come se fosse una shell, e le pagine HTML dei siti vengono inviate da questa particolarissima shell... dopotutto i primi browser erano applicazioni a riga di comando per leggere documenti di ipertesto nella shell!

Nel repo trovate anche una utility della riga di comando che è da un po' che vengo usando nei miei progetti. Se avete istallato il python3 dovrebbe funzionare egregiamente nella maniera seguente:

```shell
./run app.py
```

Questa utility crea un ambiente virtuale per la nostra app.py e all'occorrenza scarica le librerie specificate dal file ```requirements.txt```

Fatene buon uso, e a presto!