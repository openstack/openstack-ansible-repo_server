OpenStack repo server
#####################
:tags: openstack, repo, server, cloud, ansible
:category: \*nix

Role to deploy a repository server for both python packages and git sources.

.. code-block:: yaml

    - name: Setup repo servers
      hosts: repo_all
      user: root
      roles:
        - { role: "repo_server", tags: [ "repo-server" ] }
