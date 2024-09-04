# Ansible-Role: acr-ansible-mastodon-install

AIT-CyberRange: Installs and configures Mastodon 


## Requirements

- Ubuntu 24.04

## Role Variables

```yaml
mastodon_user: mastodon
mastodon_db: "{{ mastodon_user }}_instance"
mastodon_db_user: "{{ mastodon_user }}"
mastodon_db_login_unix_socket: /var/run/postgresql
mastodon_db_password: iKas78%gha!
mastodon_version: main
mastodon_basepath: /var/www/mastodon
mastodon_fqdn: mastodon.cyberrange.at

mastodon_admin_user: admin
mastodon_admin_email: admin@cyberrange.at

mastodon_email_user: mastodon@cyberrange.at
mastodon_email_user_password: email-password
mastodon_smtp_auth: STARTTLS
mastodon_smtp_port: 25
mastodon_email_server: mail.cyberrange.at

ssl_cert: /etc/ssl/cert
ssl_key: /etc/ssl/key

mastodon_dependencies:
  - redis-server
  - optipng
  - pngquant
  - jhead
  - jpegoptim
  - gifsicle
  - nodejs
  - imagemagick
  - ffmpeg
  - libpq-dev
  - libxml2-dev
  - libxslt1-dev
  - file
  - g++
  - libprotobuf-dev
  - protobuf-compiler
  - pkg-config
  - gcc
  - autoconf
  - bison
  - build-essential
  - libssl-dev
  - libyaml-dev
  - libreadline6-dev
  - zlib1g-dev
  - libncurses5-dev
  - libffi-dev
  - libgdbm-dev
  - libidn11-dev
  - libicu-dev
  - libjemalloc-dev

setup_responses:
      # Domain name:
      -  "{{ mastodon_fqdn }}"
      # Do you want to enable single user mode?
      -  "n"
      # Are you using Docker to run Mastodon?
      -  "n"
      # PostgreSQL host:
      -  "127.0.0.1"
      # PostgreSQL port:
      -  "5432"
      # Name of PostgreSQL database:
      -  "{{ mastodon_db }}"
      # Name of PostgreSQL user:
      -  "{{ mastodon_db_user }}"
      # Password of PostgreSQL user:
      -  "{{ mastodon_db_password }}"
      # Redis host:
      -  "127.0.0.1"
      # Redis port:
      -  "6379"
      # Redis password:
      -  ""
      # Do you want to store uploaded files on the cloud?
      -  "n"
      # Do you want to send e-mails from localhost?
      -  "n"
      # SMTP server:
      -  "{{ mastodon_email_server }}"
      # SMTP port:
      -  "{{ mastodon_smtp_port }}"
      # SMTP username:
      -  "{{ mastodon_email_user }}"
      # SMTP password:
      -  "{{ mastodon_email_user_password }}"
      # SMTP authentication:
      -  "{{ mastodon_smtp_auth }}"
      # SMTP OpenSSL verify mode:
      -  "none"
      # Enable STARTTLS:
      -  "auto"
      # E-mail address to send e-mails "from":
      -  "Mastodon <{{ mastodon_email_user }}>"
      # Send a test e-mail with this configuration right now?
      -  "n"
      # Check periodically for important updates?
      -  "n"
      # Save configuration?
      -  "y"
      # Prepare the database now?
      -  "y"
      # Compile the assets now?
      -  "y"
      # Do you want to create an admin user straight away?
      -  "y"
      # Username (admin):
      -  "{{ mastodon_admin_user }}"
      # E-mail (admin): 
      -  "{{ mastodon_admin_email }}"
```

## Example Playbook

```yaml
- hosts: all
  roles:
    - acr-ansible-mastodon-install
      vars:
        mastodon_user: "mastodon"
```

## License

GPL-3.0

## Author

- Lenhard Reuter