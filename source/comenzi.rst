Comenzi
=======

.. _git-fetch:

git-fetch
""""""""""

.. _git-merge:

git-merge
""""""""""

.. _git-pull:

git-pull
""""""""""

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
Dacă ramura de la distanță are alt nume atunci  

.. code-block:: bash

   git push <proiect la distanță> <ramura locală>:<ramura la distanță>

În cazul când nu este specificată ramura sursă

.. code-block:: bash

   git push <proiect la distanță> :<ramura la distanță>

efectul rulării comenzii este ștergerea ramurii :code:`<ramurii la distanță>`.

Modificările locale pot fi respinse de :code:`<proiect la distanță>` atunci când acesta conține modificări mai proaspete decât cele locale.
În așa caz fie folosiți comenzile :ref:`git-fetch`, :ref:`git-merge`, :ref:`git-pull`, :ref:`git-rebase`.
Sau dacă țineți cu tot adinsul să rescrieți modificările de la distanță folosiți opțiunea :code:`-f`(:code:`--force`)

.. _git-rebase:

git-rebase
""""""""""

.. _git-remote:

git-remote
""""""""""
