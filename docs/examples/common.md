<!-- Space: AnsibleRoleCommon -->
<!-- Parent: Project -->
<!-- Title: Project Examples -->

<!-- Label: Examples -->
<!-- Include: docs/disclaimer.md -->
<!-- Include: ac:toc -->

## packages

To run this playbook with default settings, for install package like this:

```yaml
- hosts: all

  vars:
    user: ubuntu
    common_packages:
      - vim
      - git
      - build-essential

    common_user: '{{ user }}'

  roles:
    - hadenlabs.common
```

## Create Files

To run this playbook create a files playbook like this:

```yaml
- hosts: all

  vars:
    user: ubuntu
    common_user: '{{ user }}'

    common_create_files:
      - path: 'full_path/.env'
        owner: '{{ user }}'
        mode: '0755'

  roles:
    - hadenlabs.common
```

## Create Directories

To run this playbook create a directories playbook like this:

```yaml
- hosts: all

  vars:
    user: ubuntu
    common_user: '{{ user }}'

    common_create_directories:
      - path: 'full_path/directory'
        owner: '{{ user }}'
        mode: '0755'

  roles:
    - hadenlabs.common
```

## Deployment

To run this playbook deployment a files playbook like this:

```yaml
- hosts: all

  vars:
    user: ubuntu
    common_user: '{{ user }}'

    common_deployments:
      - name: '{{ app_name }}'
        version: '{{ git.branch.deployment }}' # Could be a hash, branch or tag name
        repo: 'git@github.com:hadenlabs/test-repository'
        force: yes
        location: '{{ apps_path }}'

  roles:
    - hadenlabs.common
```

## Environment

To run this playbook environment a files playbook like this:

```yaml
- hosts: all

  vars:
    user: ubuntu
    common_user: '{{ user }}'

    common_environment_dict:
      path: /usr/src/server/file
      owner: '{{ user }}'
      group: '{{ group_name }}'
      permissions: '0640'
      envs:
        KEY: Value

  roles:
    - hadenlabs.common
```
