Comenzi
=======

.. _git-branch:

git-branch
""""""""""

Comandă pentru manipularea ramurilor. De obicei se utilizează pentru:

.. rubric:: Afișarea ramurilor existente

.. code-block:: bash

   git branch

în rezultat se va afișa o listă cu ramurile existente, iar ramura curentă va fi marcată cu ajutorul simbolului `*`::

     <ramura1>
     <ramura2>
   * <ramura3>
     <ramura4>
     <ramura5>

.. _git-branch-crearea-unei-ramuri-noi:

.. rubric:: Crearea unei ramuri noi

.. code-block:: bash

   git branch <ramura nouă>

în rezultat se va crea :code:`<ramura nouă>` care va avea drept punct de început comiterea curentă. Totodată acestă comandă nu schimbă ramura curentă. 

.. _git-branch-stergerea-unei-ramuri:

.. rubric:: Ștergerea unei ramuri

se realizează folosind opțiunea :code:`-d` (:code:`--delete`) ::

   git branch -d <ramură existentă>

.. _git-branch-redenumirea-unei-ramuri:

.. rubric:: Redenumirea unei ramuri

se realizează folosind opțiunea :code:`-d` (:code:`--delete`) ::

   git branch -m [<ramura veche>] <ramura nouă>

.. _git-cat-file:

git-cat-file
""""""""""""

Afișează conținutul, tipul sau marimea :term:`obiectelor git <obiect git>`. 

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

.. _git-config:

git-config
""""""""""

.. _git-fetch:

git-fetch
"""""""""

.. _git-ls-files:

git-ls-files
""""""""""""

Afișează informații despre fișierele din :term:`index` și `dosarul de lucru`.

.. _git-merge:

git-merge
""""""""""

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

.. _git-reset:

git-reset
"""""""""

Schimbă ''poziția'' referinței :term:`HEAD`. Cel mai des se utilizează în formatul::

   git reset <mod> <comitere>
   
unde în loc de :code:`<mode>` putem folosi oricare dintre următoarele opțiuni: 

* :code:`--soft` -- schimbă valoarea referinței :term:`HEAD` astfel încât să indice către comiterea :code:`<comitere>`;

* :code:`--mixed` -- pe lângă faptul că schimbă valoarea referinței :term:`HEAD` astfel încât să indice către comiterea :code:`<comitere>` mai actualizează și index-ul ca să reflecte conținutul comiterii :code:`<comitere>`;

* :code:`--hard` -- la fel ca și :code:`--mixed` doar că mai actualizează și conținutul dosarului de lucru.

șantierul rămâne intact

opțiunile: :code:`--soft`, :code:`--mixed`, :code:`--hard`, :code:`--merge` și :code:`--keep`. 

cu :code:`--soft` se schimbă doar poziția capului fără a altera index-ul sau șantierul ... vezi anularea comiterilor

cu :code:`--mixed` se schimbă poziția capului și index-ul coincide cu acea comitere, șantierul rămâne intact

cu :code:`--hard` se schimbă poziția capului, index-ul coincide cu acea comitere și șantierul

putem revni prin :term:`ORIG_HEAD`

https://www.kernel.org/pub/software/scm/git/docs/gitglossary.html#def_head

`Reset Demystified <https://git-scm.com/blog/2011/07/11/reset.html>`_ 

.. rubric:: xxx



.. _git-remote:

git-remote
""""""""""

Gestionează informațiile privind proiectele la distanță (adăugare, ștergere, vizualizare etc). De regulă în cazul unui singur proiect la distanță (proiect pe server) se folosește în formatul

.. code-block:: bash

   git remote add origin <URL-ul proiectului>

Pentru a lista alias-urile existente

.. code-block:: bash

   git remote -v

De exemplu în cazul acestui proiect în rezultatul rulării comenzii de mai sus avem

.. code-block:: bash

   git remote -v
   origin	https://github.com/Streeling/git-rif.git (fetch)
   origin	https://github.com/Streeling/git-rif.git (push)

