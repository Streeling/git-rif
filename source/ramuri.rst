Ramuri
======

.. _cum-să-mut-comiterile-dintr-o-ramură-în-alta:

Cum să mut comiterile dintr-o ramură în alta?
"""""""""""""""""""""""""""""""""""""""""""""

Am comis într-o ramură, dar ar fi trebuit să comit în alta; cum să mut aceste comiteri în ramura corectă?

.. rubric:: A. Ramura corectă încă nu există, adică fără a pierde din generalitate, putem considera că avem următoarea situație

.. code::

   (A) -- (B) -- (C) -- (D)
                         |
                     <ramura0>
                         |
                        HEAD

când de fapt ar fi trebuit să fie astfel::

            + -- (C) -- (D)
           /             |
   (A) -- (B)            |
           |             |
       <ramura0>     <ramura1>
                         |
                        HEAD

Pentru a muta comiterile (C) și (D) în ramura :code:`<ramura1>` trebuie în primul rând să :ref:`creăm o ramură fără a ne comuta la ea<git-branch-crearea-unei-ramuri-noi>`::

   git branch <ramura1>

apoi să excludem comiterile (C) și (D) din :code:`<ramura1>` mutând capul pe părintele comiterii (C)::

   git reset --hard (B)

și în final trecem la ramura nou creată::

   git checkout <ramura1>

.. rubric:: B. Ramura corectă există, adică avem următoarea situație

.. code::

            + -- (U) -- (V) -- (W) -- (X)
           /                           |  
   (A) -- (B) -- (C) -- (D)            |
                         |             |
                     <ramura0>     <ramura1>
                         |
                        HEAD

când de fapt ar fi trebuit să fie astfel

.. code::

            + -- (U) -- (V) -- (W) -- (X) -- (C) -- (D)
           /                                         |
   (A) -- (B)                                        |
           |                                         |
       <ramura0>                                 <ramura1>
                                                     |
                                                    HEAD

Pentru a muta comiterile (C) și (D) în ramura :code:`<ramura1>` trebuie să trecem în această ramură:: 

   git checkout <ramura1>

și să integrăm modificările din ramura :code:`<ramura0>` în ramura :code:`<ramura1>`::

   git merge <ramura0>

apoi să trecem în ramura :code:`<ramura0>`::
   
   git checkout <ramura1>

și să ''aruncăm'' comiterile (C) și (D) din ramură mutând capul pe părintele comiterii (C)::
 
   git reset --hard <comiterea B>

după aceste operații putem trece la ramura :code:`<ramura1>` pentru a continua lucrul::

   git checkout <ramura1>

.. rubric:: C. Ramura corectă există, dar nu putem integra direct ramura greșită în cea corectă

Putem presupune că avem următoarea situație

.. code::

     + -- (U) -- (V) -- (W) --------- (X)
    /                                  |  
   (A) -- (B) -- (C) -- (D)            |
                         |             |
                     <ramura0>     <ramura1>
                         |
                        HEAD

când de fapt ar fi trebuit să fie astfel

.. code::

     + -- (U) -- (V) -- (W) -- (X) -- (C) -- (D)
    /                                         |
   (A) -- (B)                                 |
           |                                  |
       <ramura0>                          <ramura1>
                                              |
                                             HEAD

Respectiv nu ne putem permite să integrăm ramura :code:`<ramura0>` în ramura :code:`<ramura1>` deoarece în rezultat comiterea (B) va nimeri în ramura :code:`<ramura1>`.

Pentru a muta doar comiterile (C) și (D) în ramura :code:`<ramura1>` trebuie să trecem în această ramură:: 

   git checkout <ramura1>

și să integrăm doar comiterile (B) și (C)::

   git cherry-pick (B)
   git cherry-pick --continue
   git cherry-pick (C)
   git cherry-pick --continue

apoi să trecem în ramura :code:`<ramura0>`::
   
   git checkout <ramura1>

și să ''aruncăm'' comiterile (C) și (D) din ramură mutând capul pe părintele comiterii (C)::
 
   git reset --hard <comiterea B>

după aceste operații putem trece la ramura :code:`<ramura1>` pentru a continua lucrul::

   git checkout <ramura1>

.. _cum-să-redenumesc-o-ramură:

Cum să redenumesc o ramură?
"""""""""""""""""""""""""""

Redenumirea unei ramuri se poate realiza folosind comanda::

   git branch -m <denumirea veche> <denumirea nouă>

Dacă ramura cu denumirea veche a fost deja încărcată pe server, adică nu este prezentă doar local, va fi nevoie de a finaliza operațiile de mai sus cu încărcarea ramurii noi pe server:: 

   git push origin [--set-upstream] <denumirea nouă>
   
și ștergerea celei vechi de pe server::
   
   git push origin :<denumirea veche>

sau (începând cu versiunea 1.7.0 a lui Git) ștergerea ramurii vechi de pe server mai poate fi realizată și astfel::
   
   git push origin --delete <denumirea veche>

.. _Cum-să-încarc-mai-multe-ramuri-pe-server-dintr-o-lovitură:

Cum să încarc mai multe ramuri pe server dintr-o lovitură?
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. code-block:: bash

   git push --all origin

Cum să integrez (merge) o ramură în alta?
"""""""""""""""""""""""""""""""""""""""""

Treceți pe ramura destinație (în care doriți să integrați)::

   git checkout <ramura destinație>

apoi rulați::

   git merge <ramura sursă>

în caz de conflicte de integrare va afișat mesajul corespunzator care se va sfârși cu următoarea propoziție::

   Automatic merge failed; fix conflicts and then commit the result.   

și va trebui să înlăturați conflictele pentru a finaliza integrarea.
   
Vezi și :ref:`Cum să integrez o ramură în alta în IntelliJ IDEA <idea-cum-să-integrez-o-ramură-în-alta>`
