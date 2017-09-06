Prerequisites
-------------

Before you install and configure the murano service,
you must create a database, service credentials, and API endpoints.

#. To create the database, complete these steps:

   * Use the database access client to connect to the database
     server as the ``root`` user:

     .. code-block:: console

        $ mysql -u root -p

   * Create the ``murano_tempest_tests`` database:

     .. code-block:: none

        CREATE DATABASE murano_tempest_tests;

   * Grant proper access to the ``murano_tempest_tests`` database:

     .. code-block:: none

        GRANT ALL PRIVILEGES ON murano_tempest_tests.* TO 'murano_tempest_tests'@'localhost' \
          IDENTIFIED BY 'MURANO_TEMPEST_TESTS_DBPASS';
        GRANT ALL PRIVILEGES ON murano_tempest_tests.* TO 'murano_tempest_tests'@'%' \
          IDENTIFIED BY 'MURANO_TEMPEST_TESTS_DBPASS';

     Replace ``MURANO_TEMPEST_TESTS_DBPASS`` with a suitable password.

   * Exit the database access client.

     .. code-block:: none

        exit;

#. Source the ``admin`` credentials to gain access to
   admin-only CLI commands:

   .. code-block:: console

      $ . admin-openrc

#. To create the service credentials, complete these steps:

   * Create the ``murano_tempest_tests`` user:

     .. code-block:: console

        $ openstack user create --domain default --password-prompt murano_tempest_tests

   * Add the ``admin`` role to the ``murano_tempest_tests`` user:

     .. code-block:: console

        $ openstack role add --project service --user murano_tempest_tests admin

   * Create the murano_tempest_tests service entities:

     .. code-block:: console

        $ openstack service create --name murano_tempest_tests --description "murano" murano

#. Create the murano service API endpoints:

   .. code-block:: console

      $ openstack endpoint create --region RegionOne \
        murano public http://controller:XXXX/vY/%\(tenant_id\)s
      $ openstack endpoint create --region RegionOne \
        murano internal http://controller:XXXX/vY/%\(tenant_id\)s
      $ openstack endpoint create --region RegionOne \
        murano admin http://controller:XXXX/vY/%\(tenant_id\)s
