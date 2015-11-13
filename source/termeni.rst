Termeni
=======

.. glossary::

   obiect git
      Un obiect git [en. git object] poate fi: un :term:`blob`, un :term:`arbore`, o :term:`comitere` sau :term:`etichetă adnotată`; orice altă entitate în afara acestei liste nu este obiect git. Obiectele se identifică prin :term:`hash`-uri și se păstrează în dosarul **.git/objects** sub formă de fișiere. Aceste fișiere sunt organizate într-un mod special și anume, fiecare fișier se păstrează într-un dosar a cărui denumire conține primele 2 simboluri ale :term:`hash`-ului obiectului, iar însăși denumirea fișierului conține celelalte 38 de simboluri rămase ale :term:`hash`-ului. De exemplu fișierul obiectului cu :term:`hash`-ul **fe5f927c084fdf216c00cc15d21ddd0a5c299006** are numele **5f927c084fdf216c00cc15d21ddd0a5c299006** și se păstrează în dosarul **.git/objects/fe**. Conținutul fișierelor nu poate fi citit cu ''ochiul liber'' în acest scop există comanda :ref:`git-cat-file`.
      
   blob
      Un blob este un :term:`obiect git` folosit pentru a păstra conținutul unui fișier. Altfel spus blob-urile sunt utilizate pentru a reprezenta fișierele.
      
   arbore
      [en. tree] Un arbore este un :term:`obiect git` folosit pentru a modela un dosar. Orice arbore conține o listă de referințe către obiectele asociate fișierelor și subdosarelor dintr-un anumit dosar. Pentru mai multe detalii vezi :ref:`cum arată un arbore <git-cat-file-cum-arată-un-arbore>` folosind comanda :ref:`git-cat-file`.
   
   comitere
      Comiterea [en. commit] reprezintă o ''fotografie'' a dosarului într-un moment de timp. Ca :term:`obiect git` comiterea constă din: o referință către un :term:`arbore` (dosarul ''fotografiat''), una sau mai multe referințe către comiterile părinte ale acesteia, autorul original al comiterii, ultimul autor [en. commiter] al comiterii și nota (comentariul) asociată. Pentru mai multe detalii vezi :ref:`cum arată o comitere <git-cat-file-cum-arată-o-comitere>` folosind comanda :ref:`git-cat-file`.
      
   etichetă   
      Un nume asociat unui :term:`obiect git`. Poate fi de 2 tipuri: :term:`etichetă simplă` sau :term:`etichetă adnotată`.

   etichetă simplă
      O etichetă simplă [en. lightweight tag] este o referință simbolică către un :term:`obiect git`. Spre deosebire o :term:`etichetă adnotată` cele simple se păstrează doar în dosarul **.git/refs/tags**. 

   etichetă adnotată
      Eticheta adnotată [en. annotated tag] reprezintă un nume împreună cu o notă asociate unui :term:`obiect git`. Însăși eticheta ca :term:`obiect git` constă din: o referință către un :term:`obiect git` [en. object], tipul obiectului referit [en. type], eticheta [en. tag], autorul etichetei [en. tagger] și nota (comentariul) asociată. Pentru mai multe detalii vezi :ref:`cum arată o etichetă adnotată <git-cat-file-cum-arată-o-etichetă-adnotată>` folosind comanda :ref:`git-cat-file`.
      
   ramură
      O ramură este un lanț de comiteri care reprezintă la nivel logic o direcție paralelă de dezvoltare a proiectului supus controlului versiunii. La nivel tehnic ramura nu-i altceva decât o :term:`referință` (precum e :term:`HEAD`) care este actualizată automat de Git astfel încât să indice permanent la ultima comitere din ramura respectivă.
      
   referință
      Referințele [en. referencies, refs] sunt nume simbolice pentru :term:`hash`-uri, la fel cum numele de domeniu sunt nume simbolice pentru adresele IP. Git păstrează referințele în formă de fișiere în dosarul **.git/refs**: denumirea fișierului este însăși referința, iar conținutul - :term:`hash`-ul. Exemple de referințe: :term:`ramură`, :term:`etichetă`, :term:`HEAD` etc. 
      
   head
      O referință simbolică către ultima comitere dintr-o ramură. Git creează automat câte o astfel de referință pentru fiecare ramura și le stochează în dosarul **.git/refs/heads**.

   HEAD
      HEAD este o referință rezervată care indică spre referința :term:`head` curentă. Se păstrează în dosarul **.git**.
   
   upstream
      Proiectul inițial (de origine) cu care se sincronizează regulat proiectul local.
      
   tracking branch
      Ramură locală pentru care este specificată ramura corespunzătoare de pe proiectul inițial.   
      
   ORIG_HEAD
      Referință rezervată care conține valoarea (poziția) precedentă a referinței :term:`HEAD`. Se păstrează în dosarul **.git**.
      
   hash
      Valoare generată cu ajutorul algoritmului SHA-1 (Secure Hash Algorithm 1) folosită drept nume pentru :term:`obicetele git <obiect git>`. Are lungimea de 160 biți (20 octeți sau 40 simboluri hexazecimale) și de regulă se utilizează în forma hexazecimală. 
