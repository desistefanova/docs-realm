.. example::

   The following diagram illustrates the commit process:

   .. figure:: /images/mvcc-diagram.png
      :alt: Realm Database copies the relevant part of the tree for writes, then replaces the latest version by updating a pointer.
      :lightbox:

   1. The realm is structured as a tree. The realm has a pointer
      to its latest version, V1.

   #. When writing, Realm Database creates a new version V2 based on V1.
      Realm Database makes copies of objects for modification (A\ :sup:`1`,
      C\ :sup:`1`),  while links to unmodified objects continue to
      point to the original versions (B, D).

   #. After validating the commit, Realm Database updates the realm's
      pointer to the new latest version, V2. Realm Database then discards
      old nodes no longer connected to the tree.
