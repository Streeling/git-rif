Comenzi
=======

.. _git-add:

git-add
"""""""

Adaugă fișiere (conținutul acestora) în :term:`index`.

Opțiunea :code:`-n` (:code:`--dry-run`) simulează adăugarea, adică afișează informație de parcă ar adăuga fișiere, dar n-o face ca atare.

:term:`Index` reprezintă ''fotografia'' :term:`dosarului de lucru <dosarul de lucru>` care va fi folosită drept conținut al următoarei comiteri. Din acest motiv după ce ați operat modificări asupra :term:`dosarului de lucru <dosarul de lucru>` și înainte de a efectua comiterea trebuie să adăugați acest schimbări în index.

Sintaxa este::

   git add [<opțiuni>] [<fișier>…​]

În cazul în care lista fișierelor care trebuie adăugate în :term:`Index` este voluminoasă comanda :ref:`git-add` ne pune la dispoziție opțiuni de filtrare:

* :code:`-u` (:code:`--update`) - actualizează doar înregistrările existente din index, adică pentru orice fișier din index acesta este actualizat dacă fișierul din dosarul de lucru conține modificări sau este șters din index dacă acesta a fost șters din dosarul de lucru.

* :code:`-A` (:code:`--all`, :code:`--no-ignore-removal`) - actualizează înregistrările existente, adăugă fișierele care n-au fost până acum în index [en. untracked] și șterge din index fișierele care au fost șterse din dosarul de lucru. 

* :code:`--no-all` (:code:`--ignore-removal`) - adaugă fișierele noi (care încă n-au fost adăugate în index [en. untracked]), actualizează cele existente, dar ignoră cele șterse.

.. _git-blame:

git-blame
"""""""""

Afișează autorii ultimilor modificări per rând.

Adnotează fiecare rând a fișierului cu informația din ultima comitere (autor, data etc) în care s-a modificat acest rând.

Putem limita raportul doar la un diapazon de rânduri cu opțiunea :code:`-L <început>,<sfârșit>`.

.. _git-branch:

git-branch
""""""""""

Comandă pentru manipularea ramurilor. De obicei se utilizează pentru:

.. rubric:: Afișarea ramurilor existente

.. code-block:: bash

   git branch

în rezultat se va afișa o listă ce va conține ramurile existente, iar ramura curentă va fi marcată cu ajutorul simbolului `*`::

     <ramura1>
     <ramura2>
   * <ramura3>
     <ramura4>
     <ramura5>

.. _git-branch-crearea-unei-ramuri-noi:

.. rubric:: Crearea unei ramuri noi

.. code-block:: bash

   git branch <ramura nouă>

în rezultat se va crea :code:`<ramura nouă>` care va avea drept punct de început comiterea curentă. Totodată această comandă nu schimbă ramura curentă. 

.. _git-branch-stergerea-unei-ramuri:

.. rubric:: Ștergerea unei ramuri

se realizează folosind opțiunea :code:`-d` (:code:`--delete`) ::

   git branch -d <ramură existentă>

.. _git-branch-redenumirea-unei-ramuri:

.. rubric:: Redenumirea unei ramuri

se realizează folosind opțiunea :code:`-d` (:code:`--delete`) ::

   git branch -m [<ramura veche>] <ramura nouă>
   
În cazul când :code:`<ramura veche>` este ramura curentă (altfel spus se dorește redenumirea ramurii curente) aceasta poate fi omisă. 
Anume din acest motiv în comanda de mai sus parametrul :code:`<ramura veche>` este opțional.    

.. _git-cat-file:

git-cat-file
""""""""""""

Afișează conținutul, tipul sau mărimea :term:`obiectelor git <obiect git>`. 

.. _git-cat-file-cum-arată-un-arbore:

.. rubric:: Cum arată un :term:`arbore`

De exemplu dosarul acestui proiect la un moment oarecare avea asociat :term:`arborele <arbore>` cu hash-ul **c5e8251aaa20f5a822b3dc12d03d68c78e8ccd30**, folosind comanda ::

   git cat-file -p c5e8251aaa20f5a822b3dc12d03d68c78e8ccd30

se va afișa::
 
   100644 blob d8539217c2eb6b51a86abe1279c37c8cc4139d22	.gitignore
   100644 blob d45a907923f682f533128fb344c8eefde1fb81fd	Makefile
   100644 blob a1c4e80ac1142e3e4a35039478b9ff3b0afc94eb	README.md
   040000 tree 4a3d4ac761ee7eeb491e5cd33a91bf147bb25552	locale
   100644 blob de2346e1cc0afae33b569cf12f2e9510dd422814	make.bat
   040000 tree 5be6adfbe1e7b690cf5abe4d61aa211cf1f411bd	source

.. _git-cat-file-cum-arată-o-comitere:

.. rubric:: Cum arată o :term:`comitere`

De exemplu folosind comanda pe ultima comitere::

   git cat-file -p HEAD

se va afișa::

   tree c5e8251aaa20f5a822b3dc12d03d68c78e8ccd30
   parent 9a7657e68c8c93f8944223175d855a8e2b8ccf2e
   author Radu Dumbraveanu <rdumbraveanu@amsoft-group.com> 1447341585 +0200
   committer Radu Dumbraveanu <rdumbraveanu@amsoft-group.com> 1447341585 +0200

.. _git-cat-file-cum-arată-o-etichetă-adnotată:

.. rubric:: Cum arată o :term:`etichetă adnotată`

De exemplu folosind comanda pentru o anumită etichetă cu hash-ul **b5b809ec5a83c0ebe15c41f4dacf61de9e12dd61** care se referă la comiterea **9afeed48d9654122a4c4f0f8e0ef0cd388550d7f**::

   git cat-file -p b5b809ec5a83c0ebe15c41f4dacf61de9e12dd61

se va afișa::

   object 9afeed48d9654122a4c4f0f8e0ef0cd388550d7f
   type commit
   tag v999
   tagger Radu Dumbraveanu <rdumbraveanu@amsoft-group.com> 1447411375 +0200

   Un exemplu de etichetă

.. _git-checkout:

git-checkout
""""""""""""

Comută poziția curentă a referinței :term:`HEAD`. 

Poate fi aplicată asupra fișierelor sau a întregului proiect.

Dacă este aplicată fișierelor::
 
   git checkout <comitere> <fișier>...
   
atunci actualizează conținutul fișierelor cu cel din :code:`<comitere>`.

Dacă nu este aplicată asupra fișierelor::

   git checkout <comitere>

atunci schimbă (atualizează) întreg dosarul de lucru. Dacă :code:`<comiterea>` reprezintă o ramură atunci are loc comutarea la acea ramură.   

.. _git-cherry-pick:

git-cherry-pick
"""""""""""""""

Aplică doar modificările care rezidă într-o anumită comitere. 

Pentru a copia comiterile se folosește sintaxa::

   git cherry-pick <comitere>
   
după ce s-au soluționat conflictele de integrare trebuie de rulat::

   git cherry-pick --continue

sau dacă se dorește anularea întregului proces::

   git cherry-pick --abort

.. _git-clean:

git-clean
"""""""""

Șterge fișierele neindexate (care nu-s supuse controlului versiunii).

Șterge recursiv fișierele care nu-s supuse controlului versiunii.

Pentru că reprezintă o operație într-un fel periculoasă are opțiunea de simulare :code:`-n` (:code:`--dry-run`). 

.. _git-clone:

git-clone
"""""""""

Copiază un proiect Git într-o altă locație (local sau la distanță).

Sintaxa este::

   git clone [<opțiuni>] <URL proiect Git> <dosar destinație>

În cazul când copierea se face local, adică locația nouă se află pe același calculator ca și proiectul sursă, se poate salva din spațiul folosit (pe disc) utilizând opțiunea :code:`-l` (:code:`--local`)::

   git clone -l <URL proiect Git> <dosar destinație>

efectul utilizării acestei opțiuni este acela că dosarul **.git/objects** din :code:`<dosarul destinație>` nu va conține :term:`obiectele Git <obiect Git>` ca atare ci doar :term:`legături tari <legătură tare>` către fișierele din proiectul sursă. Dacă nu folosim această opțiune atunci se creează copii ale fișierelor și nu legături, dar dacă dorim să ne asigurăm și să forțăm acest comportament în mod obligatoriu putem folosi opțiunea :code:`--no-hardlinks`.

După clonare proiectul sursă devine :term:`upstream` pentru :term:`<proiectul destinație>` și respectiv referința :term:`origin` a acestuia este modificată astfel încât să indice către proiectul sursă. Pentru a modifica puțin acest comportament putem folosi opțiunea :code:`-o` (:code:`--origin`) pentru a schimba numele referinței care va indica către proiectul sursă. De exemplu în rezultatul rulării comenzii::

   git clone -o source <URL proiect Git> <dosar destinație>

în proiectul destinație va fi creată referința **source** în dosarul **.git/refs/remotes** care va indica către proiectul sursă. Deopotrivă cu această opțiune există și alte opțiuni pentru modificare anumitor lucruri din proiectul destinație cum ar fi:

* :code:`-b <nume ramură>` (:code:`--branch <nume ramură>`) -- schimbă ramura curentă în proiectul destinație;

* :code:`-c <cheie>=<valoare>` (:code:`--config <cheie>=<valoare>`) -- schimbă valori ale parametrilor în proiectul destinație;

* :code:`--depth <numărul de comiteri>` -- copiază doar ultimele comiteri în proiectul destinație (în așa caz acesta se numește :term:`clonă superficială`).

.. _git-commit:

git-commit
""""""""""

Înregistrează modificările în istoria proiectului.

Stochează conținutul indexului în istorie împreună cu un mesaj, autorul comiterii și data.

Cu :code:`-a` (:code:`--all`) automat actualizează index-ul pentru fișierele modificate sau șterse (dar nu  și pentru cele noi).

Ne poate ușura puțin lucrul dacă vrem să folosim mesajul dintr-o altă comitere cu 

* :code:`-c <comiterea>` (:code:`--reedit-message=<comiterea>`) -- cu deschiderea editorul;
* :code:`-C <comiterea>` (:code:`--reuse-message=<comiterea>`) -- fără a deschide editorul;


Mesajul :code:`-m <mesaj>` (:code:`--message=<mesaj>`).

.. _git-commit-amend:

.. rubric:: Modificarea ultimei comiteri

Cu ajutorul opțiunii :code:`--amend` avem posibilitatea să redactăm ultima comitere: începând cu mesajul, autorul și terminând cu conținutul acesteia. 
De notat însă că atunci când redactați ultima comitere se schimbă automat și :term:`hash`-ul acesteia. 
Respectiv pot apărea situații neclare atunci când proiectul dvs. nu este doar local. De exemplu, să presupunem că proiectul local și cel de la distanță arată astfel

.. code::

   (A) -- (B) -- (C)
                  |
               <master>
                  |
                 HEAD

după ce ați aplicat opțiunea :code:`--amend` proiectul dvs local va arăta astfel

.. code::

   (A) -- (B) -- (C')
                  |
               <master>
                  |
                 HEAD

unde :code:`(C')` este comiterea :code:`(C)` redactată respectiv cu alt :term:`hash`. În așa fel dacă ar fi să comparăm proiectul local cu cel de la distanță situația e următoarea

.. code::

            (C) - <origin/master>
            /
   (A) -- (B)
            \
           (C')
            |
         <master>
            |
           HEAD

astfel dacă veți încerca să încărcați modificările să nu vă surprindă mesajul::

    ! [rejected]        master -> master (non-fast-forward)
   error: failed to push some refs to '<proiectul dvs.>'
   hint: Updates were rejected because the tip of your current branch is behind
   hint: its remote counterpart. Integrate the remote changes (e.g.
   hint: 'git pull ...') before pushing again.
   hint: See the 'Note about fast-forwards' in 'git push --help' for details.

.. _git-config:

git-config
""""""""""

Schimbă parametrii Git pentru proiectul curent (:code:`--local`), pentru toate proiectele utilizatorului curent (:code:`--global`) și pentru pentru toate proiectele din sistem (:code:`--system`).

.. _git-diff:

git-diff
""""""""

Afișează diferențele dintre conținutul ultimei comiteri, :term:`index` și :term:`dosarul de lucru`.

.. _git-fetch:

git-fetch
"""""""""

Descarcă obiecte git și referințe din alt proiect git.

.. _git-init:

git-init
""""""""

Creează un proiect Git nou sau reinițializează unul existent. 

Pentru a inițializa proiectul Git în dosarul curent se rulează comanda::

   git init
   
iar pentru a inițializa proiectul în alt dosar decât cel curent este nevoie de a indica calea spre acest dosar::

   git init <dosarul proiectului>
   
Inițializarea proiectului Git din punct de vedere tehnic constă în crearea în dosarul destinație a unui dosar ascuns numit **.git** împreună cu subdosarele **objects** (unde se vor păstra :term:`obiectele git <obiect git>`), **refs/heads** (pentru stocarea :term:`referințelor <referință>`), **refs/tags** (pentru stocarea :term:`etichetelor <etichetă>`) și fișierul **HEAD** (pentru stocarea referinței :term:`HEAD`).    

.. _git-log:

git-log
"""""""

Afișează istoria.

.. _git-ls-files:

git-ls-files
""""""""""""

Afișează informații despre fișierele din :term:`index` și `dosarul de lucru`.

De exemplu,

:code:`-u` (:code:`--unmerged`) fișierele care n-au fost integrate (cu conflicte).

.. _git-merge:

git-merge
""""""""""

Integrează două sau mai multe ramuri.

Cum sunt prezentate conflictele; sun marcate prin ``<<<<<<<``, ``=======``, și ``>>>>>>>``. Fragmentul până la `=======` este cel din ramura sursă, și partea după - din ramura destinație.

.. _git-merge-tool:

git-merge-tool
""""""""""""""

Rulează instrumente pentru soluționarea conflictelor de integrare.

.. _git-pull:

git-pull
""""""""""

Descarcă toate modificările operate asupra proiectului la distanță și le integrează în proiectul local.
Altfel spus realizează sincronizarea proiectul local cu un proiect la distanță.
Cel mai des se utilizează în formatul următor::

   git push <proiect la distanță> <ramura la distanță>

Unde :code:`<proiect la distanță>` poate fi specificat direct prin URL (https://git-scm.com/book/tr/v2/Git-on-the-Server-The-Protocols) 
sau printr-un nume creat cu ajutorul comenzii :ref:`git-remote`. 
În rezultat modificările din ramura din :code:`<proiect la distanță>` sunt descărcate în ramura cu același nume din proiectul local.
Dacă ramura locală are alt nume atunci va fi nevoie de schimbat puțin formatul comenzii::

   git push <proiect la distanță> <ramura la distanță>:<ramura locală>

.. _git-push:

git-push
""""""""

Încarcă toate modificările operate asupra proiectului local într-un alt proiect aflat de regulă la distanță.
Altfel spus realizează sincronizarea unui proiect la distanță cu proiectul local.
Cel mai des se utilizează în formatul următor

.. code-block:: bash

   git push <proiect la distanță> <ramura locală>

Unde :code:`<proiect la distanță>` poate fi specificat direct prin URL (https://git-scm.com/book/tr/v2/Git-on-the-Server-The-Protocols) 
sau printr-un nume creat cu ajutorul comenzii :ref:`git-remote`. 
În rezultat modificările din ramura locală sunt încărcate în ramura cu același nume din proiectul :code:`<proiect la distanță>`.
Dacă ramura de la distanță are alt nume atunci va fi nevoie de schimbat puțin formatul comenzii  

.. code-block:: bash

   git push <proiect la distanță> <ramura locală>:<ramura la distanță>

În cazul când nu este specificată ramura sursă (:code:`ramura locală>`)

.. code-block:: bash

   git push <proiect la distanță> :<ramura la distanță>

efectul rulării comenzii este ștergerea ramurii :code:`<ramura la distanță>`.

.. _git-push-force:

.. rubric:: Încărcare forțată

Modificările locale pot fi respinse de :code:`<proiect la distanță>` atunci când acesta conține modificări mai proaspete decât cele locale.
În așa caz fie că se integrează noile modificări și apoi se execută încă o dată :ref:`git-push` fie, dacă țineți cu tot adinsul, se suprascriu folosind opțiunea :code:`-f` (:code:`--force`)

.. code-block:: bash

   git push -f <proiect la distanță> <ramura locală>

.. warning::

   În rezultatul încărcării forțate toate modificările mai proaspete decât cele locale vor dispărea din proiectul de la distanță. Din acest motiv asigurați-vă că nu sunt modificări importante pe proiectul la distanță. Printre situațiile când este nevoie de încărcare forțată se numără: :ref:`cum-să-schimb-mesajul-ultimei-comiteri` sau :ref:`cum-să-redenumesc-o-ramură`.

.. _git-rebase:

git-rebase
""""""""""

Schimbă punctele de început ale ramurilor.

.. _git-reset:

git-reset
"""""""""

Schimbă :term:`index`-ul pentru anumite fișiere sau în general schimbă ''poziția'' referinței :term:`HEAD`. 

.. rubric:: Sintaxa

.. code-block:: bash

   git reset [-q] [<arbore git>] [--] <fișier>…​
   git reset (--patch | -p) [<arbore git>] [--] [<fișier>…​]
   git reset [--soft | --mixed [-N] | --hard | --merge | --keep] [-q] [<comitere>]

În prima și în a doua formă înlocuiește conținutul (versiunea) :code:`<fișier>…` din :term:`index` cu versiunea :code:`<fișier>…` din :code:`<arbore git>`. În a treia formă schimbă comiterea curentă, adică ''poziția'' referinței :term:`HEAD`.

Opțiunile: :code:`--soft`, :code:`--mixed` și :code:`--hard` sunt într-o anumită relație și anume: 

* :code:`--soft` -- schimbă valoarea referinței :term:`HEAD` astfel încât să indice către comiterea :code:`<comitere>`;

* :code:`--mixed` -- pe lângă faptul că schimbă valoarea referinței :term:`HEAD` astfel încât să indice către comiterea :code:`<comitere>` mai actualizează și index-ul ca să reflecte conținutul comiterii :code:`<comitere>`;

* :code:`--hard` -- la fel ca și :code:`--mixed` doar că mai actualizează și conținutul dosarului de lucru.

.. warning::

   În caz că nu vă place ce a ieșit după schimbarea referinței :term:`HEAD` puteți întotdeauna reveni la poziția inițială folosind referința :term:`ORIG_HEAD`

Un articol în engleză în care se folosesc imagini vizuale pentru descrierea acestei comenzi: `Reset Demystified <https://git-scm.com/blog/2011/07/11/reset.html>`_ 

.. _git-remote:

git-remote
""""""""""

Comandă pentru manipularea numelor asociate :term:`proiectelor la distanță <proiect la distanță>` conexe proiectului curent.

Adăugarea, redenumirea și ștergerea se fac cu ajutorul opțiunilor :code:`add`, :code:`rename` și :code:`rm` (:code:`remove`) în felul următor::

   git remote add <nume> <URL-ul proiectului> 
   
   git remote rename <vechi> <nou>
   
și respectiv ștergerea::

   git remote remove <nume existent>
   
în rezultat se șterge nu doar numele ci și toate ramurile la distanță din acest proiect stocate local prin :ref:`git-fetch` sau :ref:`git-pull`.   

Pentru a lista alias-urile existente::

   git remote -v

De exemplu în cazul acestui proiect în rezultatul rulării comenzii de mai sus avem::

   git remote -v
   origin	https://github.com/Streeling/git-rif.git (fetch)
   origin	https://github.com/Streeling/git-rif.git (push)

sau simplu::

   git remote
   
   fară multe detalii

Dacă ați greșit se poate schimba url-ul::

  git remote set-url <nume> <URL nou>
  
Pentru a curăța de ramurile care nu există pe proiectul la distanță :code:`prune` și ca orice comandă ''periculoasă'' are opțiunea de simulare :code:`--dry-run`.  

.. _git-show:

git-show
""""""""

Afișează informația despre obiecte.

Sintaxa::

   git show [<opțiuni>] <obiect>…​

.. _git-show-ref:

git-show-ref
""""""""""""

Afișează informația despre referințele proiectului.

Sintaxa::

  git show-ref [<opțiuni>] [--] [<șablon de căutare>…​]

Dacă nu este specificat șablonul de căutare sunt afișate toate referințele. 
Când acesta (șablonul) este specificat atunci se afișează toate referințele a căror cale absolută conține drept prefix șablonul indicat.
Dacă se dorește afișarea informației despre o referință care are exact numele căutat se folosește opțiunea :code:`--verify`, de exemplu::

   git show-ref --verify refs/heads/master

.. _git-status:

git-status
""""""""""

Afișează diferențele dintre conținutul ultimei comiteri, :term:`index` și :term:`dosarul de lucru`.

Sintaxa::

   git status [<opțiuni>] [--] [<fișier>…​]

Atunci când nu este specificat nici un fișier este aplicată pentru toate fișierele din proiect.

Practic afișează 3 zone informaționale:

* fișierele care-s în index și se deosebesc de versiunea din ultima comitere (:term:`HEAD`) - anume aceste modificări vor fi înregistrate la rularea comenzii :ref:`git-commit`;

* fișierele care-s în dosarul de lucru și se deosebesc de versiunea din index - de regulă asupra acestor fișiere aplicăm :ref:`git-add`;

* fișierele care-s în dosarul de lucru, dar încă n-au fost adăugate în index, adică nu-s supuse controlului versiunii.  

.. _git-tag:

git-tag
"""""""

Comandă pentru manipularea etichetelor.

Pentru a crea o :term:`etichetă simplă` se folosește în formatul următor::

   git tag <nume etichetă> [<comitere>|<obiect git>]

Pentru a crea o :term:`etichetă adnotată` se folosește opțiunea :code:`-a` (:code:`--annotate`)::

   git tag -a [-m <notă>] <nume etichetă> [<comitere>|<obiect git>]

dacă nu este folosită opținea :code:`-m` (:code:`--message`) atunci se va deschitde editorul implicit (ca și în situația cu :ref:`git-commit`).

Pentru a altera referința unei etichete existente poate fi utilizată opțiunea :code:`-f` (:code:`--force`) doar că în cazul când eticheta a fost încărcată pe server nu se recomandă această procedură. Etichetele sunt descărcate o singură dată de pe server, adică va fi nevoie de anunțat toate persoanele care au descărcat eticheta modificată să o șteargă și s-o descarce încă o dată.

Ștergerea unei etichete se realizează cu ajutorul opțiunii :code:`-d` (:code:`--delete`)::

   git tag -d <etichetă existentă>… 
 

