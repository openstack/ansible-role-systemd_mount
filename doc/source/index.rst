========================================
systemd_mount role for OpenStack-Ansible
========================================

This role will configure Systemd units:

This role requires the ``ansible-config_template`` collection to be available
on your local system.

To get collection you can use use the ``ansible-galaxy`` command on the
``requirements.yml`` file. You need to install collection **before**
running this role.

.. code-block:: bash

    ansible-galaxy install -r requirements.yml

Default variables
~~~~~~~~~~~~~~~~~

.. literalinclude:: ../../defaults/main.yml
   :language: yaml
   :start-after: under the License.

Example playbook
~~~~~~~~~~~~~~~~

.. literalinclude:: ../../examples/playbook.yml
   :language: yaml

Tags
~~~~

This role supports one tag: ``systemd-init``.
