Ramuri
======

Cum să mut comiterile dintr-o ramură în alta?
"""""""""""""""""""""""""""""""""""""""""""""

Am comis într-o ramură, dar ar fi trebuit să comit în alta; cum să mut aceste comiteri în ramura corectă?
De exemplu avem următoarea situație

A. Ramura corectă încă nu există, adică fără a pierde din generalitate, putem considera că avem următoarea situație

.. code::

   (A) -- (B) -- (C) -- (D)
                         |
                     <ramura0>
                         |
                        HEAD

când de fapt ar fi trebuit să fie astfel

.. code::

            + -- (C) -- (D)
           /             |
   (A) -- (B)            |
           |             |
       <ramura0>     <ramura1>
                         |
                        HEAD

Pentru a muta comiterile (C) și (D) în ramura <ramura1> trebuie să rulăm următoarele comenzi

.. code-block:: bash

   git branch <ramura1>
   git reset --hard <comiterea B>
   git checkout <ramura1>

B. Ramura corectă există, adică avem următoarea situație

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

Pentru a muta comiterile (C) și (D) în ramura <ramura1> trebuie să rulăm următoarele comenzi

Cum să redenumesc o ramură?
"""""""""""""""""""""""""""

Redenumirea unei ramuri se poate realiza folosind comanda

.. code-block:: bash

   git branch -m <denumirea veche> <denumirea nouă>

Dacă ramura cu denumirea veche a fost deja încărcată pe server, adică nu este prezentă doar local, va fi nevoie de a finaliza operațiile de mai sus cu încărcarea ramurii noi pe server 

.. code-block:: bash

   git push origin --set-upstream <denumirea nouă>
   
și ștergerea celei vechi de pe server
   
.. code-block:: bash

   git push origin :<denumirea veche>

sau (începând cu versiunea 1.7.0 a lui Git) ștergerea ramurii vechi de pe server mai poate fi realizată și astfel 
   
.. code-block:: bash

   git push origin --delete <denumirea veche>

Cum să încarc mai multe ramuri pe server dintr-o lovitură?
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""


      
