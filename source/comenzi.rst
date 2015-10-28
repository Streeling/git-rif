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
Dacă ramura de la distanță are alt nume atunci va fi nevoie de schimbat puțin formatul comenzii  

.. code-block:: bash

   git push <proiect la distanță> <ramura locală>:<ramura la distanță>

În cazul când nu este specificată ramura sursă (:code:`ramura locală>`)

.. code-block:: bash

   git push <proiect la distanță> :<ramura la distanță>

efectul rulării comenzii este ștergerea ramurii :code:`<ramura la distanță>`.

Modificările locale pot fi respinse de :code:`<proiect la distanță>` atunci când acesta conține modificări mai proaspete decât cele locale.
În așa caz fie că se integrează noile modificări și apoi se execută încă o dată :ref:`git-push` fie, dacă țineți cu tot adinsul, se suprascriu folodind opțiunea :code:`-f` (:code:`--force`)

.. code-block:: bash

   git push -f <proiect la distanță> <ramura locală>

.. warning::

   În rezultatul încăracării forțate toate modificările mai proaspete decât cele locale vor dispărea din proiectul de la distanță. Din acest motiv asigurați-vă că nu sunt modificări importante pe proiectul la distanță. Printre situațiile când este nevoie de încărcare forțată se numără: :ref:`cum-să-schimb-mesajul-ultimei-comiteri` sau :ref:`cum-să-redenumesc-o-ramură`.

.. _git-rebase:

git-rebase
""""""""""

.. _git-remote:

git-remote
""""""""""
