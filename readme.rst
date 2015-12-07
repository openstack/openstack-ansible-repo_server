repo_server role
#############
:tags: openstack, cloud, ansible, repo_server
:category: \*nix

repo_server Role

.. code-block:: yaml

    - name: repo_server role
      hosts: "hosts"
      user: root
      roles:
        - { role: "repo_server" }


Note. The template role has the template name within it. Please change the name 
throughout the code base.

.. code-block:: bsah

    find . -type f -exec sed -i 's/repo_server/CHANGE_ME_PLEASE/g' {} \;
