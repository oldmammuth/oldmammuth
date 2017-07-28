---
layout: post
title: "Python Mega Tutorial (in Italiano) 01: Preparativi"
ref: pymt01
date: 2017-07-28
categories: python
lang: it
---
Ogni promessa è debito: ecco qui il primo articolo del mio mega-maxi tutorial sul python in italiano!

Può non sembrare molto, ma ho già una certa ideuzza su come dirigere al meglio questa serie: so da dove voglio partire (conoscenza pressochè zero) e so dove voglio arrivare (per adesso una sorpresa!).

Pronti? 3... 2... 1... Via!

## Istallare il python
Si comincia sempre dall'istallazione, no? Basta puntare il browser sul [sito ufficiale in italiano del python](http://python.it/) e scegliere dalla sezione dei download... Vi dò un aiutino...

|Sistema operativo | link utile |note           |
|------------------|------------|---------------|
| Windows (c)(tm)  | https://www.python.org/ftp/python/3.6.1/python-3.6.1-amd64.exe | x86 o x64 (non Itanium)|
|MAC OSX (c)(tm)   | https://www.python.org/ftp/python/3.6.1/python-3.6.1-macosx10.6.pkg | Mac OS X 10.6 e successivi |
| Linux | http://www.python.org/ftp/python/3.6.1/Python-3.6.1.tar.xz | **Meglio usare il package manafer della propria distribuzione**, e.g: ```apt-get install python3``` per Debian e derivati (Ubuntu, Mint...) |

Ovviamente è sempre possibile che già abbiate il python pre-istallato sul vostro sistema...

## Il primo programma in python
Come da tradizione ogni tutorial, guida o libro su un qualsivoglia linguaggio di programmazione deve insegnare al programmatore in fieri il programma "hello, world!", ovvero un programma che mostri la scritta *hello, world!* (*ciao mondo!*). Questo serve per dare una panoramica sulle basi linguaggio.

Per far ciò abbiamo bisogno di un editor di testi qualsiasi. Una nota per gli utenti Windows: il *notepad* andrebbe pure bene, ma fate un favore a voi stessi, e scaricate ed istallate qualche editor serio; [notepad++](https://notepad-plus-plus.org/download/) oppure [Visual Studio Code](https://code.visualstudio.com/download) vanno entrambi benissimo, e ve ne sono altri in giro che sono anch'essi carinissimi...

Se aprite l'editor e salvate il nuovo file con il nome di *helloworld.py* il vostro editor dovrebbe riconoscere automaticamente il linguaggio usato (tutti i file con estensione .py sono file python) e quindi predisporsi per aiutare il programmatore in qualche modo (alcuni editor sono capaci di autocompletare il codice, altri aiutano segnalando possibili errori, etc, etc).

Il codice del programma è il seguente:

#### helloworld.py
```python
print("Ciao, mondo!")
```

Più semplice di così si muore!

#### Spieghiamo il codice
Come primo programma non c'è molto da spiegare: *print()* scrive sul terminale la stringa passatagli in argomento 

???Stringa??? ???Argomento???

Se qualcuno è perplesso, niente paura, *Keep calm, siamo programmatori!*

*print()* è una funzione: gli si passa un *argomento* all'interno delle parentesi e *print* lo stampa a schermo.
Una funzione in ambito della programmazione è un po' come le funzioni matematiche.
Per esempio la funzione *somma* di solito si scrive come ```z = x + y``` (e.g.: ```5 = 3 + 2```); la funzione somma prende due numeri in argomento e restituisce la loro somma; ma nell'ambito dell'algebra universale è ben nota la forma ```+(z,y)``` per descrivere la somma di due insiemi per esempio.

L'*argomento* della funzione è tutto ciò che sta fra le parentesi. Può essere un entità sola o più di una, separate da virgole.

Una *stringa* è semplicemente un insieme di caratteri. Allora perché non ho usato l'espressione *insieme di caratteri*?

1. Essere precisi nell'ambito informatico è di importanza vitale.
2. Una stringa quando è esplicita (letterale) ha una forma canonica, cioè è racchiusa da virgolette, singole o doppie. ```"Questa è una stringa"``` e ```'anche questa è una stringa'```.
3. E' bene abituarsi da subito al linguaggio tecnico... :-)

Insomma, quanto ci sarebbe da dire per una riga sola di codice!
A proposito: ogni programma si divide in righe, che possono essere numerate. Ragion per cui mi posso riferire nelle spiegazioni alla riga 1 o riga 236 del codice e parlare di quella... Un buon editor di codice mostra in numeri di riga.

## Esecuzione del programma

Tutto bene fin'ora, ma come si fa girare il programma?
Se mi avete seguiro e avete salvato il file come *helloworld.py*, basta aprire un terminale ed eseguire:

```shell
python helloworld.py
```

Il risultato nel terminale dovrebbe essere:

```
Ciao, mondo!
```

Può non sembrare molto, e per ora non lo è; però intanto abbiamo fin qui un modello per i prossimi tutorial su come si scrivono ed eseguono programmi in python.

Se qualcuno si chiede: quando passiamo a scrivere programmi veri, in cui non c'è bisogno della shell... *Keep calm, siamo programmatori!* 
Aspettate i prossimi articoli :-)

## Il codice

Ho creato un *repository* su [GitHub](https://github.com) per mantenere il codice che produrremo su questi articoli.

REPO: [https://github.com/oldmammuth/pythonmegatutorial](https://github.com/oldmammuth/pythonmegatutorial)

Il codice di oggi sta nella sottocartella *tut01*

Per istallare git su windows puntate il browser su [https://git-for-windows.github.io/](https://git-for-windows.github.io/); oppure scaricate il codice di ogni programma visualizzandolo sul browser e facendo un copia-e-incolla.

Gli utenti Linux dovrebbero avere git già istallato, sennò il solito package manager della vostra distro (e.g. ```apt-get install git```)

per usare il repo con git basta scrivere nel terminale (shell):

```shell
git clone https://github.com/oldmammuth/pythonmegatutorial.git
```

Ogni articolo avrà la sua cartella chiamata ```tutNN``` dove ```NN``` è il numero del tutorial.

---

Per oggi è tutto, ciao ciao!

Davide.

