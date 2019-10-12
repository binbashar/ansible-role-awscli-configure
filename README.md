# Ansible Role: christiangda.awscli

[![Build Status](https://travis-ci.org/christiangda/ansible-role-awscli_configure.svg?branch=master)](https://travis-ci.org/christiangda/ansible-role-awscli-configure)
[![Ansible Role](https://img.shields.io/ansible/role/40514.svg)](https://galaxy.ansible.com/christiangda/awscli_configure)

This role [Configure AWS Command Line Interface (awscli)](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html)

**NOTE:** This ROLE is a Work In Progress (WIP), so you need to take care of use this

**Features:**


## Requirements

This role work on RedHat, CentOS, Debian and Ubuntu distributions

* RedHat
  * 6
  * 7
  * 8
* CentOS
  * 6
  * 7
  * 8
* Ubuntu
  * 14.*
  * 16.*
  * 18.*
  * 19.*
* Debian
  * jessie (8)
  * stretch (9)
  * buster (10)
  * sid (unstable)

To see the compatibility matrix of Python vs. Ansible see the project [Travis-CI build matrix](https://travis-ci.org/christiangda/ansible-role-awscli-configure)

## Role Variables

None

## Dependencies

## Example Playbook

### RedHat/CentOS, Ubuntu and Debian

If you have installed [AWS Command Line Interface (awscli)](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html) already

```yaml
- hosts: redhat-8
    gather_facts: True
    roles:
      - role: christiangda.awscli_configure
```

When you have RedHat/CentOS 8 or Debian/Ubuntu target

```yaml
- hosts: redhat-8
    gather_facts: True
    roles:
      - role: christiangda.awscli
      - role: christiangda.awscli_configure
```

When you have RedHat/CentOS 6/7 target

```yaml
- hosts: redhat-7
    gather_facts: True
    roles:
      - role: christiangda.epel_repo
      - role: christiangda.awscli
      - role: christiangda.awscli_configure
```

When you have multiples OS targets, install EPEL repository only in RedHat/CentOS 6/7

```yaml
- hosts: servers
    gather_facts: True
    roles:
    - role: christiangda.epel_repo
      when: >
        ansible_os_family == 'RedHat' and (
          ansible_distribution == 'CentOS' or
          ansible_distribution == 'RedHat'
        )
        and (
          ansible_distribution_major_version == '6' or
          ansible_distribution_major_version == '7'
        )
      changed_when: false
    - role: christiangda.awscli
    - role: christiangda.awscli_configure

```

## Development / Contributing

This role is tested using [Molecule](https://molecule.readthedocs.io/en/latest/) and was developed using
[Python Virtual Environments](https://docs.python.org/3/tutorial/venv.html)

**Prepare your environment**

**Python 3**

```bash
mkdir ansible-roles
cd ansible-roles/

python3 -m venv venv
source venv/bin/activate
pip install pip --upgrade
pip install ansible
pip install molecule">=2.22rc1"
pip install molecule[vagrant]
pip install selinux
pip install docker
pip install pytest
pip install pytest-mock
pip install pylint
pip install rope
pip install autopep8
pip install yamllint
pip install flake8
```

**Python 2.7**

Dependencies

```bash
sudo dnf install redhat-rpm-config
sudo dnf install python-devel
sudo dnf install libselinux-python
```

```bash
mkdir ansible-roles
cd ansible-roles/

python2.7 -m virtualenv venv
source venv/bin/activate
pip install pip --upgrade
pip install ansible
pip install molecule">=2.22rc1"
pip install molecule[vagrant]
pip install selinux
pip install docker
pip install pytest
pip install pytest-mock
pip install pylint
pip install rope
pip install autopep8
pip install yamllint
pip install flake8
```

**Clone the role repository and create symbolic link**

```bash
git clone https://github.com/christiangda/ansible-role-awscli-configure.git
ln -s ansible-role-awscli-configure christiangda.awscli_configure
cd christiangda.awscli_configure
```

**Execute the test**

Using docker in local

```bash
molecule test [--scenario-name default]
```

Using vagrant in local

```bash
molecule create --scenario-name vagrant
molecule converge --scenario-name vagrant
molecule verify --scenario-name vagrant
```

or

```bash
molecule test --scenario-name vagrant
```

**Additionally if you want to test it using VMs, I have a very nice [ansible-playground project](https://github.com/christiangda/ansible-playground) that use Vagrant and VirtualBox, try it!.**

## License

This module is released under the GNU General Public License Version 3:

* [http://www.gnu.org/licenses/gpl-3.0-standalone.html](http://www.gnu.org/licenses/gpl-3.0-standalone.html)

## Author Information

* [Christian González Di Antonio](https://github.com/christiangda)
