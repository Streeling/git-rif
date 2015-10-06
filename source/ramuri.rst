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
