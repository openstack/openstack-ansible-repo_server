OpenStack-Ansible Repo Server
#############################
:tags: openstack, repo, server, cloud, ansible
:category: \*nix

Ansible role that deploys a repository server for python packages and git
sources.

.. code-block:: yaml

    - name: Setup repo servers
      hosts: repo_all
      user: root
      roles:
        - { role: "repo_server", tags: [ "repo-server" ] }

