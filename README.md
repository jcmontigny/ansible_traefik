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
- `traefik_compose_path` : path to the the compose files ; defaults to `/docker/compose`
- `traefik_compose_file` : file name of the traefik compose file ; defaults to `docker-compose-traefik.yml`

__Vars__
- `traefik_compose_url` : URL to get the URL ; default to dockerswarm.rocks url
- `traefik_network_overlay` : name of the overlay network for traefik ; defaults to `traefik-public` (hardcoded into the dockerswarm.rocks compose file)

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


License
-------

MIT

Author Information
------------------

Jean-Christophe Montigny ( https://github.com/jcmontigny )
