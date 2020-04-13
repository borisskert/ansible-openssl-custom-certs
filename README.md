# ansible-openssl-self-signed-certs

Creates self-signed certificates with OpenSSL

## Requirements

* Python
* Docker

## Tasks

* Create working directory
* Install pip package 'pyOpenSSL'
* Create certificate authority (CA)
* Create certificates for sites

## Role parameters

| Variable      | Type | Mandatory? | Default | Description           |
|---------------|------|------------|---------|-----------------------|
| working_directory | text | no     | /srv/openssl | Directory to which the CA and CSRs are saved |
| certificates_directory | text | no     | /srv/openssl/certs | Directory to which the certificates and keys are saved |
| sites                  | array of texts | no | []           | The sites for which certificates will be created       |
| ca_name                | text | no      | my_CA             | Your certificate name                                  |
| download_dir           | text | no      | ./.tmp            | Download directory where the created CA cert will be stored locally |

## Example Playbook

### Requirement

```yaml
- name: create-self-signed-certs
  src: https://github.com/borisskert/ansible-openssl-self-signed-certs.git
  scm: git
```

### Playbook

Usage (without parameters):

```yaml
- hosts: test_machine

  roles:
    - role: create-self-signed-certs
```

Usage (with parameters):

```yaml
- hosts: test_machine

  roles:
    - role: create-self-signed-certs
      ca_name: site.org
      sites:
        - my.first.site.org
        - my.second.site.org
        - my.third.site.org
```
