Termeni
=======

.. glossary::

   obiect git
      Un obiect git [en. git object] poate fi: un :term:`blob`, un :term:`arbore`, o :term:`comitere` sau o :term:`etichetă`; orice altă entitate în afara acestei liste nu este obiect git. Obiectele se păstrează în dosarul :code:`.git/objects`.
      
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
      
