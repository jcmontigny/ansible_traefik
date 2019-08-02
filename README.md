Traefik Ansible Role
====================

A simple role to deploy traefik (host mode) on an existing swarm cluster.

Requirements
------------

- An existing swarm cluster
- The Ansible inventory group name for the manager nodes should be passed to the role

Role Variables
--------------

__Defaults__
Required variables
- `traefik_swarm_managers_ansible_group` : the ansible group containing the managers ; no default value
- `traefik_letsencrypt_email` : email address for letsencrypt certificate generation ; no default value
- `traefik_domain` : domain name - traefik UI will be available at traefik.domain and consul UI at consul.domain ; no default value

Optional variables
- `traefik_admin_user` : admin user for traefik and consul (basic http auth) ; defaults to `admin`
- `traefik_admin_password` : password for the admin user ; defaults to `_changeme_`
- `traefik_traefik_replica_count` : number of traefik replicas ; defaults to 3
- `traefik_consul_replica_count` : number of consul replicas ; defaults to 3
- `traefik_stack_name` : name of the stack to deploy ; defaults to `traefik-consul`
- `traefik_stack_path` : path to the the stack files ; defaults to `/docker/stack_files`
- `traefik_stack_file` : file name of the traefik stack file ; defaults to `docker-stack-traefik.yml`

__Vars__
- `traefik_stack_url` : URL where to fetch the stack file ; default to dockerswarm.rocks url with ports in host-mode
- `traefik_network_overlay` : name of the overlay network for traefik ; defaults to `traefik-public` (hardcoded into the dockerswarm.rocks stack file)

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: swarm_managers
      become: true
      roles:
        - jcmontigny.ansible_traefik
      vars:
        - traefik_swarm_managers_ansible_group: swarm_managers
        - traefik_letsencrypt_email: mail@example.com
        - traefik_domain: sys.example.com
        - traefik_admin_user: admin
        - traefik_admin_password: changeme


License
-------

MIT

Author Information
------------------

Jean-Christophe Montigny ( https://github.com/jcmontigny )
With basic automation of the instructions at https://dockerswarm.rocks/traefik/ 
