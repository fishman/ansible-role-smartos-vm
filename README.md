# SmartOS vmadm role


## Deleting zones and reprovisioning them

    ansible-playbook --extra-vars "stop_zone=True delete_zone=True" --limit hugo_provision provision_vm.yml

## Filesystems

    filesystems:
      - {source: "/zones/data/hugo", target: "/var/lib/www", read_only: false}

## Sample playbook

    ---
    - hosts: vms
      remote_user: root
      environment:
        PATH: "/opt/local/sbin:/opt/local/bin:{{
          (ansible_env|default({})).PATH|default('/usr/bin:/usr/sbin') }}"
      vars:
        - ansible_python_interpreter: /opt/local/bin/python
      roles:
        - smartos_vm
        
