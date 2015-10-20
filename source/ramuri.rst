Ramuri
======

Cum să mut comiterile dintr-o ramură în alta?
"""""""""""""""""""""""""""""""""""""""""""""

Am comis într-o ramură, dar ar fi trebuit să comit în alta; cum să mut aceste comiteri în ramura corectă?

A. Ramura corectă încă nu exsită

.. code-block:: bash

   git branch <ramura corectă>
   git reset --hard <comiterea B>
   git checkout <ramura corectă>

Cum să redenumesc o ramură?
"""""""""""""""""""""""""""

Redenumirea unei ramuri se poate realiza folosind comanda

.. code-block:: bash

   git branch -m <denumirea veche> <denumirea nouă>

Dacă ramura cu denumirea veche a fost deja încărcată pe server, adică nu este prezentă doar local, va fi nevoie de a finaliza operațiile de mai sus cu

.. code-block:: bash

   git push origin --set-upstream <denumirea nouă>
   git push origin :<denumirea veche>
