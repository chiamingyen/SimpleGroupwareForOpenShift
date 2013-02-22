Simple Groupware 0.745
===================

This is a Simple Groupware version 0.745 for OpenShift platform. 

Three directories need to move to persistent data directory, which includes:

simple_store: this directory stores web based modified content including upload files.

simple_cache: this directory stores system cache files.

ext: this directory stores extension files.

The OpenShift local repository should not include these three presistent directories but be uploaded to the $OPENSHIFT_DATA_DIR directory through SFTP.

Three symbolic links are also needed to allow the Simple Groupware system scripts to save the corresponding files into these directories.

content of the ".openshift\action_hooks\build" script:

ln -sf $OPENSHIFT_DATA_DIR/simple_store $OPENSHIFT_REPO_DIR/php/simple_store
ln -sf $OPENSHIFT_DATA_DIR/simple_cache $OPENSHIFT_REPO_DIR/php/simple_cache
ln -sf $OPENSHIFT_DATA_DIR/ext $OPENSHIFT_REPO_DIR/php/ext

This system use SQLite to save the data named sqlite3_sgs_0_745.db and located in simple_store directory.

The default administration account/password is "admin/admin".