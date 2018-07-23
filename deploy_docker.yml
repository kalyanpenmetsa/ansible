---
# tasks file for docker
- name: create docker container
  hosts: kube-workers
  become: yes
  tasks:
    - name: include variables
      include_vars: ../vars/lannister.yml
    - name: Install python-docker on Red Hat based distribution
      yum:
            name: python-docker-py
            enablerepo: extras
            state: latest
    - name: docker login
      docker_login:
        username: penmetsa29
        password: {{ password }}
        email: penmetsa29@docker.io
    - name: docker pull
      docker_image:
        name: penmetsa29/house-lannister
        state: present
        force: yes
    - name: Create Container
      command: 'docker run -d -p 9090:8080 -t penmetsa29/house-lannister'

#      docker_container:
#            name: house-lannister
#            image: penmetsa29/house-lannister
#            ports:
#              - 9090:8080
