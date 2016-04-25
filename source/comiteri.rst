Comiteri
========

.. _cum-să-schimb-mesajul-ultimei-comiteri:

Cum să schimb mesajul ultimei comiteri?
"""""""""""""""""""""""""""""""""""""""

În cazul când ați depistat greșeli gramaticale sau greșeli de sintaxă în mesajul ultimei comiteri sau poate considerați că mesajul nu descrie suficient de clar modificările comise, puteți *împrospăta* mesajul după bunul dumnevoastră plac folosind opțiunea ``--amend`` a comenzii 
``git-commit``

.. code-block:: bash

   git commit --amend -m '<mesaj nou>'

În cazul când doriți să consultați mesajul ultimei comiteri sau fișierele conținute în aceasta, înainte de a actualiza mesajul, puteți exclude 
opțiunea ``-m``

.. code-block:: bash

   git commit --amend

În rezultat se va deschide editorul implicit (vezi :ref:`git-config`) în care veți putea introduce noul mesaj și veți putea vizualiza mesajul vechi împreună cu fișierele din comitere 

.. code-block:: bash

   <mesaj vechi>

   # Please enter the commit message for your changes. Lines starting
   # with '#' will be ignored, and an empty message aborts the commit.
   # On branch master
   # Changes to be committed:
   #       modified:   <fisier1>
   #       modified:   <fisier2>
   #       modified:   <fisier3>
   #

Dacă ultima comitere a fost deja încărcată pe server, adică nu este prezentă doar local, va fi nevoie de a finaliza operațiile de mai sus cu o :ref:`încărcare forțată <git-push-force>` a ramurii, adică:: 

   git push -f ...

.. warning::

   1111111111111111111111

.. _cum-să-schimb-mesajul-oricărei-sau-oricăror-comiteri:

Cum să schimb mesajul oricărei sau oricăror comiteri?
""""""""""""""""""""""""""""""""""""""""""""""""""""""

Acest lucru este posibil folosind comanda ``git-rebase`` cu opțiunea ``-i`` (sau ``--interactive``) doar că parametrul trimis acestei comenzi nu este comiterea care trebuie modificată ci comiterea părinte a celei care trebuie modificată sau părintele comun ale comiterilor ce trebuie modificate. Astfel această comandă primește drept parametru o comitere de pornire oferind posibilitatea de a modifica comiterile din intervalul (<comitere de pornire>, HEAD] 

.. code-block:: bash

   git rebase -i <comitere de pornire>

În caz că doriți să schimbați mesajul unei singure comiteri puteți folosi 

.. code-block:: bash

   git rebase -i <comitere>~1

În rezultatul execuției comenzii va apărea editorul implicit 

.. code-block:: bash

   pick <comitere6> <mesaj6>
   pick <comitere5> <mesaj5>
   pick <comitere4> <mesaj4>
   pick <comitere3> <mesaj3>
   pick <comitere2> <mesaj2>
   pick <comitere1> <mesaj1>

   # Rebase 7e2035a..e3335d3 onto 7e2035a
   #
   # Commands:
   #  p, pick = use commit
   #  r, reword = use commit, but edit the commit message
   #  e, edit = use commit, but stop for amending
   #  s, squash = use commit, but meld into previous commit
   #  f, fixup = like "squash", but discard this commit's log message
   #  x, exec = run command (the rest of the line) using shell
   #
   # These lines can be re-ordered; they are executed from top to bottom.
   #
 
Înlocuiți cuvântul „pick” cu „reword” în dreptul fiecărei comiteri al cărei mesaj doriți să-l schimbați. 
 
.. _cum-să-exclud-un-fișier-din-ultima-comitere:

Cum să exclud un fișier din ultima comitere?
""""""""""""""""""""""""""""""""""""""""""""

Dacă ați inclus un fișier (sau mai multe) în plus în ultima comitere, atunci puteți *corecta* acest lucru fie folosind opțiunea ``--amend`` a comenzii ``git-commit``::

   git reset HEAD~1 <fisier>
   git commit --amend
   
fie mutând capul pe penultima comitere::

   git reset --soft HEAD~1
   git reset HEAD <fisier>
   git commit

.. _cum-să-adaug-un-fișier-la-ultima-comitere:

Cum sa revin la ultima comitere?
""""""""""""""""""""""""""""""""

Dacă ați operat careva modificări nereușite și doriți să le anulați, atunci următoarea comandă va șterge noile modificări și va reveni la ultima comitere::

   git reset --hard HEAD 

Cum să adaug un fișier la ultima comitere?
""""""""""""""""""""""""""""""""""""""""""

Dacă ați uitat să adăugați un fișier în ultima comitere, atunci fie folosiți opțiunea ``--amend`` a comenzii ``git-commit``::

   git add <fisier>
   git commit --amend
   
fie mutați capul pe penultima comitere::

   git reset --soft HEAD~1
   git add <fisier>
   git commit

.. _cum-să-modific-un-fișier-din-ultima-comitere:

Cum să modific un fișier din ultima comitere?
"""""""""""""""""""""""""""""""""""""""""""""

Dacă ați mai făcut niște schimbări care nu merită comise aparte ci se înscriu perfect în ultima comitere, atunci fie folosiți opțiunea ``--amend`` a comenzii ``git-commit``::

   git add <fisier>
   git commit --amend

fie mutați capul pe penultima comitere::

   git reset --soft HEAD~1
   git add <fisier>
   git commit

.. _cum-sa-anulez-ultima-operație-de-comitere:

Cum să anulez ultima operație de comitere?
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

După comitere ați înțeles că v-ați grăbit și că mai sunt fișiere care trebuie incluse în acestă comitere, dar asupra lor mai este de lucru; atunci::

   git reset --soft HEAD~1

apoi după ce ați finalizat lucrul::

   git add ...
   git commit ...

.. _cum-sa-revin-la-versiunea-fișierul-dintr-o-anumită-comitere:

Cum sa revin la versiunea fișierul dintr-o anumită comitere?
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. rubric:: A. Vreau doar să vizualizez acestă versiune (o privire în trecut)

.. code-block:: bash

   git show <comitere>:<fișier>

.. rubric:: B. Vreau să văd diferența

.. code-block:: bash

   git diff <comitere>:<fișier>

.. rubric:: C. Vreau sa înlocuiesc fișierul actual cu acea versiune (restabilirea)

.. code-block:: bash

   git checkout <comitere> <fisier>

.. warning::

   Ultima comandă alterează atât conținutul din șantier cât și șterge conținutul din index.

.. rubric:: D. Vreau să înlocuiesc doar conținutul din index

.. code-block:: bash

   git reset <comitere> <fisier>

În rezultat fișier rămâne nealterat și se schimbă doar conținutul din index.

.. _cum-să-văd-istoria-unui-fișier:

Cum să văd istoria unui fișier?
"""""""""""""""""""""""""""""""

.. rubric:: Vreau să văd doar comiterile referitoare la fișier

.. code-block:: bash

   git log --oneline <fisier>

sau dacă aveți instalat programul ``gitk`` puteți îmbunătăți experiența grafică::

   gitk <fisier>

.. rubric:: B. Vreau să văd diferențele dintre fișier și versiunea sa dintr-o comitere

.. code-block:: bash

   git diff <comitere> <fișier>

.. rubric:: C. Vreau să văd diferența dintre fișier și versiunea sa din index

.. code-block:: bash

   git diff --cached <fisier>

sau

.. code-block:: bash

   git diff -- <fișier>

.. rubric:: D. Vreau să văd cine a modificat ultimul un anumit rând din fișier

.. code-block:: bash

   git blame <fișier>

.. rubric:: E. Vreau să văd cine a modificat ultimul un anumit rând din fișier dintr-o anumită comitere

.. code-block:: bash

   git blame <comitere> <fișier>

.. _cum-să-scot-fișierele-adăugate-în-index:

Cum să scot fișierele adăugate în index?
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Dacă din greșeală ați actualizat index-ul atât cu fișiere pe care doriți să le comiteți cât și cu fișiere pe care nu doriți să le comiteți această eroare poate fi înlăturată folosind comanda ``git-reset`` 

.. code-block:: bash

   git reset [HEAD] <fișier>

sau puteți aplica comanda pe mai multe fișiere concomitent

.. code-block:: bash

   git reset [HEAD] -- <fișier1> <fișier2> ... <fișiern> 

.. warning::
   Folosind Google puteți găsi și alte recomandări pentru a soluționa această problemă printre care și folosirea ``git rm --cached <fisier>``. Folosirea cestei comenzi nu este identică cu ``git-reset`` deoarece ``git-reset`` înlocuiește versiunea fișierului din index cu versiunea    aceluiași fișier din ultima comitere (adică cea la care indică HEAD), astfel fișierul va fi prezent în următoarea comitere, dar cu conținutul vechi. Pe când ``git rm --cached`` șterge complet fișierul din index astfel fișierul va lipsi complet din următoarea comitere (adică nu va fi inclus în istorie). 

.. _cum-să-mă-debarasez-de-un-fișier:

Cum să mă debarasez de un fișier?
"""""""""""""""""""""""""""""""""
Eu am avut o astfel de situație când cineva a făcut ``git add`` la un fișier inclus în fișierul ``.gitignotre``, eu l-am preluat și vina a fost a mea.
