# Ansible Learning Repository

This repository contains my learning notes and basic playbooks while exploring **Ansible** for server configuration and automation.

The goal of this repo is to practice and understand how Ansible works for managing multiple servers, automating tasks, and simplifying infrastructure management.

---

## Running Playbooks on Multiple Servers

Ansible allows you to run playbooks on multiple servers simultaneously.

To configure which servers Ansible should manage, you need to define them in the **inventory file**:

```
/etc/ansible/hosts
```

In this file, you can organize servers:

* Individually
* By groups (recommended for larger environments)

Example:

```
[web_servers]
192.168.1.10
192.168.1.11

[db_servers]
192.168.1.20
```

You can also specify the target hosts directly inside your playbook under the `hosts` field.

---

## Running a Playbook

To run any playbook:

```
ansible-playbook playbookname.yml
```

Example:

```
ansible-playbook install_nginx.yml
```

---

## Running Playbook with SSH Password Prompt

If your remote servers require a password for SSH authentication, run:

```
ansible-playbook playbookname.yml -k
```

The `-k` flag tells Ansible to **ask for the SSH password**.

---

## Running Playbook with Sudo Privileges

If a task requires **sudo (root) privileges**, you need to:

1. Add `become: true` inside the playbook.
2. Run the playbook with the `--ask-become-pass` flag.

Example command:

```
ansible-playbook delete_file_folder.yml -k --ask-become-pass
```

Example playbook snippet:

```
- hosts: all
  become: true
  tasks:
    - name: Delete a folder
      file:
        path: /tmp/test-folder
        state: absent
```

---

## What You'll Find in This Repository

* Basic Ansible playbooks
* Server configuration examples
* File and package management automation
* Learning experiments while exploring Ansible

This repository is meant for **learning, experimenting, and improving Ansible skills step by step**.

---

## Connect With Me

This is part of my DevOps learning journey.
If you are also learning Ansible or have any suggestions, feel free to connect or reach out.

If you have any doubts, improvements, or ideas — I would be happy to discuss and learn together.

Let's grow and automate infrastructure together 🚀
