Programma sviluppato in Processing,linguaggio OpenSource che eredita costrutti e sintassi dal Java,ma con funzioni aggiuntive che permettono di gestire al meglio aspetti grafici/interattivi rendendolo indicato per lo sviluppo di arte generativa.
Processing,differentemente da altri linguaggi,opera sulla GPU,di conseguenza qualche piccolo bug è dovuto alla scheda video e non al codice in sé(ad esempio potrebbe non percepire al primo click il segnale del mouse) dunque l'efficienza potrebbe variare tra un calcolatore e l'altro.
Per le reference e maggiori informazioni visionare il sito ufficiale : https://processing.org


Nello scaricabile saranno presente bin con eseguibile e librerie di supporto per ciascun sistema operativo e una cartella con il file sorgente da poter esaminare o modificare in seguito,inoltre vi sarà anche una pagina  html con relativo css che è una pagina a scopo più esplicativo/didattico (presente anche online nel link in basso alla pagina del simulatore sul server galileo).
Per testare il simulatore basta fare doppio click sul file eseguibile (.exe nel caso del windows).
<Si consiglia di estrarre prima il contenuto del file .zip(il tutto occupa poco più di 5,1 MB)>


GUIDA:
Il software implementato si sviluppa su 4 livelli di draw differenti,dal livello 0 infatti è possibile selezionare la modalità da voler provare per poi poter eventualmente tornare indietro con il tasto in alto a sinistra e testare gli altri.
Il tema sul quale è incentrato è la coerenza di cache e i vari protocolli ad essa dedicati in strutture multiprocessore a memoria condivisa.


Il primo livello simula il protocollo snoopy(conosciuto anche come "bus sniffing"):
Selezionando il processore e l'operazione da voler effettuare(Read o Write,ovvero lettura o scrittura) si può successivamente selezionare l'indirizzo d'interesse dalla memoria centrale.Se esso è un dato valido al momento della lettura verrà ricopiato nella cache del processore,se invece si seleziona la modalità di scrittura esso verrà invalidato (il bit a destra dell'indirizzo ne indicherà lo stato) e successivamente sarà caricato nella cache del processore che se ne prenderà in carico la proprietà modificandolo.Se invece il processore vuole leggere un dato in memoria che risulta in possesso di un altro processore,quest'ultimo manderà sul bus l'informazione sovrascritta bloccando un eventuale risposta non valida della Ram, la quale,però,coglierà l'informazione dal bus e riavrà il possesso del dato aggiornandolo.

Il secondo livello invece si occupa di simulare il protocollo di scrittura differita  nella quale,una volta selezionato il processore,si può selezionare il dato nella cache da poter modificare.Questo non sarà subito aggiornato nella Ram ma questo avverrà solo al momento in cui sarà necessario vuotare un indirizzo di cache.La liberazione della cache può avvenire secondo diverse modalità,in questo caso il tasto LRU si occupa di simulare l'omonimo protocollo,secondo il quale verrà eliminato l'indirizzo usato meno recentemente(piccolo "bug":non funziona se è stato usato solo un dato!).

Il terzo e ultimo livello emula il semplice protocollo di scrittura immediata aggiornando all'atto della modifica nella cache il valore presente nella memoria centrale.

(Si raccomanda in tutti i livelli di deselezionare il processore e,nel caso del bus snooping,l'operazione di Read e write precedentemente effettuata prima di procedere con altre azioni.)






