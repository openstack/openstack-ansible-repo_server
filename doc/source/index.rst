=============================
OpenStack-Ansible Repo Server
=============================

Abstract
~~~~~~~~

Ansible role that deploys a repository server for built python packages
(wheels), requirements and constraints for specific builds.

To clone or view the source code for this repository, visit the role repository
for `repo_server <https://opendev.org/openstack/openstack-ansible-repo_server>`_.

Role purpose
~~~~~~~~~~~~

Repo container is used as a target by other OpenStack-Ansible roles and
collections when `venv_wheel_build_enable : true`.

In this scenario it is expected, that there will be a repo instance per each
Operating System family and major version, as well as for each CPU architecture
in the deployments.


Web server
~~~~~~~~~~

In order to serve pre-built content to clients (like ``pip`` or ``uv``), an
Apache Web server is being used.

We leverage `httpd <https://opendev.org/openstack/ansible-role-httpd>`_
role to set up a web server, and to manage a corresponding Virtual Host.


Using shared file system
~~~~~~~~~~~~~~~~~~~~~~~~

When multiple instances of a repo server exist, is designed to leverage a
shared filesystem, mounted for ``/var/www/repo`` directory.

This filesystem is used to store built results and ensure that each repo server
is able to serve wheels for all available variants in the deployment.

There are no requirements to filesystem performance or reliability, as stored
cache data can be re-built from scratch, in case of filesystem failure.

By default, ``openstack.osa.repo`` playbook will install a GlusterFS as a
shared filesystem directly on all repo servers.
You can disable this behavior by setting
``openstack_repo_server_enable_glusterfs: false``.

You can also use any existing shared filesystem by defining
``repo_server_systemd_mounts`` variable - in this case it will be mounted via
`systemd_mount  <https://opendev.org/openstack/ansible-role-systemd_mount>`_ role.


Default variables
~~~~~~~~~~~~~~~~~
.. literalinclude:: ../../defaults/main.yml
   :language: yaml
   :start-after: under the License.

Required variables
~~~~~~~~~~~~~~~~~~

None.

Example playbook
~~~~~~~~~~~~~~~~

.. literalinclude:: ../../examples/playbook.yml
   :language: yaml
