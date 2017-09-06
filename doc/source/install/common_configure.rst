2. Edit the ``/etc/murano_tempest_tests/murano_tempest_tests.conf`` file and complete the following
   actions:

   * In the ``[database]`` section, configure database access:

     .. code-block:: ini

        [database]
        ...
        connection = mysql+pymysql://murano_tempest_tests:MURANO_TEMPEST_TESTS_DBPASS@controller/murano_tempest_tests
