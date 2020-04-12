# Ansible Role for Jira

[![Travis](https://img.shields.io/travis/com/kube-cloud/ansible-role-jira/master?style=flat)](https://travis-ci.com/kube-cloud/ansible-role-jira)
[![GitHub release](https://img.shields.io/github/release/kube-cloud/ansible-role-jira.svg)](https://github.com/kube-cloud/ansible-role-jira)
[![GitHub license](https://img.shields.io/github/license/kube-cloud/ansible-role-jira.svg)](https://github.com/kube-cloud/ansible-role-jira/blob/master/LICENSE)
[![Ansible Role](https://img.shields.io/ansible/role/d/46827.svg?style=flat)](https://galaxy.ansible.com/kube-cloud/jira)

Ansible Role for Atlassian Jira Installation.

<a href="https://www.kube-cloud.com/"><img width="300" src="https://kube-cloud.com/images/branding/logo/kubecloud-logo-single_writing_horizontal_color_300x112px.png" /></a>
<a href="https://www.redhat.com/fr/technologies/management/ansible"><img width="200" src="https://getvectorlogo.com/wp-content/uploads/2019/01/red-hat-ansible-vector-logo.png" /></a>
<a href="https://www.atlassian.com/software/jira"><img width="120" src="https://store-images.s-microsoft.com/image/apps.56884.9be9d623-c94a-4957-ba1f-70d7fad2970a.8c7d74c7-3a09-4260-8c78-13f1f6ebc0fa.866a644f-0168-45c2-9049-80f8bc1ff08a.png" /></a>

# Supported Version

* Atlassian Jira 6+

# Supported OS

* CentOS 6/7
* RedHat 6/7
* Ubuntu Trusty/Xenial/Bionic

# Depend On

* jetune.java (Java 1.8+)

# Usage

* Install Role ``` ansible-galaxy install jetune.jira ```
* use in your playbook
```
---

- hosts: all
  become: true
  tasks:

    - name: "Include jira role"
      import_role:
        name: ansible-role-jira
      vars:
        jira_version: "8.7.1"
        jira_download:
          url: "https://product-downloads.atlassian.com/software/jira/downloads/atlassian-jira-software-8.7.1.tar.gz"
          dest: "{{ ansible_user_dir }}/.ansible/tmp/atlassian-jira-software-8.7.1.tar.gz"
          checksum: "sha1:23d8815d2fd39f7e32759d2f4677ffebacf358b1"
        mysql_jdbc_download:
          url: "https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.48.tar.gz"
          dest: "{{ ansible_user_dir }}/.ansible/tmp/mysql-connector-java-5.1.48.tar.gz"
          checksum: "sha1:a8067480d7d7e4a975771e08b48b64de18837341"
        postgresql_jdbc_download:
          url: "https://jdbc.postgresql.org/download/postgresql-42.2.10.jar"
          dest: "{{ ansible_user_dir }}/.ansible/tmp/postgresql-42.2.10.jar"
          checksum: "sha1:338af492789fd198dbd52735a22b1946030ecc96"
        jira_owner: "jira"
        jira_group: "jira"
        jira_shell: "/usr/sbin/nologin"
        jira_create_home: false
        jira_owner_system: true
        jira_jvm_minimum_memory: "256m"
        jira_jvm_maximum_memory: "512m"
        jira_catalina: "/opt/atlassian/jira"
        jira_catalina_connector_scheme: "http"
        jira_catalina_connector_secure: "true"
        jira_catalina_context_path: "/"
        jira_catalina_connector_port: 8080
        jira_properties_file_generation: true
        jira_catalina_connector_connexion_timeout: 20000
        jira_catalina_connector_ssl_enabled: false
        jira_catalina_connector_ssl_implementation_jsse: false
        jira_catalina_connector_ssl_certificate_file: ""
        jira_catalina_connector_ssl_key_file: ""
        jira_catalina_connector_ssl_keystore_file: ""
        jira_catalina_connector_ssl_keystore_pass: ""
        jira_catalina_connector_ssl_keystore_alias: ""
        jira_catalina_connector_redirect_port: 8443
        jira_catalina_connector_proxyname: ""
        jira_session_timeout: "300"
        jira_home: "/var/atlassian/applicationdata/jira"
        jira_backup_home: "/var/atlassian/application-backups/jira"
        jira_extra_properties:
          - key: "plugin.auth-crowd.sso.enabled"
            value: "false"
          - key: "avatar.gravatar.default"
            value: "mm"
          - key: "avatar.max.size"
            value: 1048576
          - key: "db.pool.size.idle"
            value: 0
          - key: "db.pool.size.max"
            value: 80
          - key: "jmx.enabled"
            value: true
          - key: "password.reset.validity.period"
            value: 4320
