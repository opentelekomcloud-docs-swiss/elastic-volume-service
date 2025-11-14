:original_name: evs_faq_0064.html

.. _evs_faq_0064:

Do Snapshots Take Space on the Disk?
====================================

No.

Creating legacy snapshots establishes relationships between snapshots and the disk data. Though snapshots are stored on disks, they do not occupy the disk space.

Standard snapshots are stored in OBS, instead of on disks. They can be used to restore data when the disk is damaged.
