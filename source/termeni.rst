Termeni
=======

.. glossary::

   obiect git
      Un obiect git [en. git object] poate fi: un :term:`blob`, un :term:`arbore` sau o :term:`comitere`; orice altă entitate în afara acestei liste nu este obiect git. Obiectele se identifică prin hash-uri și se păstrează în dosarul **.git/objects** sub formă de fișiere. Aceste fișiere sunt organizate într-un mod special și anume: fiecare fișier se păstrează într-un dosar a cărui denumire conține primele 2 litere ale hash-ului obiectului, iar însăși denumirea fișierului conține celelalte 38 de litere rămase ale hash-ului. De exemplu fișierul obiectului cu hash-ul **fe5f927c084fdf216c00cc15d21ddd0a5c299006** are **.git/objects/fe/5f927c084fdf216c00cc15d21ddd0a5c299006**. Conținutul fișierelor este păstrat într-un format special și pentru a-l citi veți avea nevoie de comanda git-cat-file.
      
   blob
      O clecție de octeți care cel mai des reprezintă conținutul unui fișier.
      
   arbore
      [en. tree] O structură care conține refințe către alți arbori și blob-uri. De fapt arborii reprezintă dosarele proiectului, dacă dosarul conține n subdosare și m fișiere atunci arborele va conține n referințe către arborii coresponzători subdosarelor și m referințe către blob-urile corespunzătoare fișierelor.
            
   comitere
      Comiterea [en. commit] reprezintă o ''fotografie'' a dosarului într-un moment de timp. Ca :term:`obiect git` comiterea constă din: o singură referință către un :term:`arbore`, referințe către părinții acesteia, autorul comiterii, data când a fost creată și o notă (comentariu). Fiecare comitere se păstrează sub formă de fișier (în dosarul :code:`.git/objects`) a cărui nume este hash-ul comiterii, iar conținutul este conținutul comiterii într-un format specific. 
      
   etichetă   
      Un nume asociat unei comiteri.
      
   ramură
      O ramură este un lanț de comiteri care reprezintă la nivel logic o altă direcție de dezvoltare a proiectului supus controlului versiunii. La cel mai jos nivel ramura nu-i altceva decât o :term:`referință` (precum e :term:`HEAD`).
      
   referință
      Referințele [en. referencies, refs] sunt nume simbolice pentru hash-uri, la fel numele de domeniu sunt nume simbolice pentru adresele IP. Git păstrează referințele în formă de fișiere în dosarul :code:`.git/refs` : denumirea fișierului este însăși referința, iar conținutul - hash-ul. Exemple de referințe: :term:`ramură`, :term:`etichetă`, :term:`HEAD`. 
      
   HEAD
      HEAD (sau capul) este o referință rezervată indică spre ultima comitere din ramura curentă.  
   
   upstream
      Proiectul inițial (de origine) cu care se sincronizează regulat proiectul local.
      
   tracking branch
      Ramură locală pentru care este specificată ramura corespunzătoare de pe proiectul inițial.   
      
   ORIG_HEAD
      Referință rezervată care conține valoarea (poziția) precedentă a referinței HEAD.
