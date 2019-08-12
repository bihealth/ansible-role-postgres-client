[![Build Status](https://travis-ci.org/bihealth/ansible-role-postgres-client.svg?branch=master)](https://travis-ci.org/bihealth/ansible-role-postgres-client)

# Setup of PostgreSQL Client

Setup a host as a PostgreSQL client.
If you have SSH root access to the PostgreSQL server, the role can also create the user and database for you.

## Requirements

A host setup as a PostgreSQL database server.

## Role Variables

See `defaults/main.yml` for all role variables and their documentation.

## Dependencies

none

## Example Playbook

For setting up the postgres client only:

```yaml
- name: configure hosts as postgres client
  hosts: all
  vars:
    postgres_client_db: "example"
    postgres_client_host: server.example.com
    postgres_client_user: "example"
    postgres_client_password: "{{ lookup('passwordstore', 'client.example.com/password_example@server.example.com') }}"
  roles:
    - role: bihealth.postgres_client
```

For also creating the postgres user and database.

```yaml
- name: configure hosts as postgres client
  hosts: all
  vars:
    postgres_client_create_user_and_db: true
    postgres_client_db: "example"
    postgres_client_host: server.example.com
    postgres_client_user: "example"
    postgres_client_password: "{{ lookup('passwordstore', 'client.example.com/password_example@server.example.com') }}"
  roles:
    - role: bihealth.postgres_client
```

## Open Issues

- Test the user and database creation features.

## License

MIT

## Author Information

- Manuel Holtgrewe

Created with love at [Core Unit Bioinformatics (CUBI), Berlin Institute of Health (BIH)](https://www.cubi.bihealth.org).
