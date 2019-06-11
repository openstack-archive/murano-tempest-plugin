========================
Team and repository tags
========================

.. image:: http://governance.openstack.org/tc/badges/murano-tempest-plugin.svg
    :target: http://governance.openstack.org/tc/reference/tags/index.html

=====================
murano-tempest-plugin
=====================

This directory contains Tempest tests to cover the Murano project, as well
as a plugin to automatically load these tests into tempest.

See the Tempest plugin docs for information on using it:
https://docs.openstack.org/tempest/latest/#using-plugins

* Free software: Apache license
* Documentation: https://docs.openstack.org/murano/latest/
* Release notes: https://docs.openstack.org/releasenotes/murano/
* Source: https://opendev.org/openstack/murano-tempest-plugin
* Bugs: https://bugs.launchpad.net/murano

Running the tests
-----------------

To run all tests from this plugin, install Murano into your environment and
navigate to tempest directory::

    $ cd /opt/stack/tempest

Run this command::

    $ tox -e all-plugin -- application_catalog 

To run a single test case, run with the test case name, for example::

    $ tox -e all-plugin -- murano_tempest_tests.tests.api.application_catalog.test_categories.TestCategories.test_list_categories
