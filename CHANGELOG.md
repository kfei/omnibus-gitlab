# Omnibus-gitlab changelog

The latest version of this file can be found at the master branch of the
omnibus-gitlab repository.

7.7.0

- Update ruby to 2.1.5 79e6833045e70a43ac66f65252d40773c20438df
- Change the root_password setting to initial_root_password 577a4b7b895e17cbe159bf317169d173c6d3567a
- Include CI Oauth settings option 2e5ae7414ecd9f73cbfe284af5d38ee65ac892e4
- Include option to set global git config options 8eae0942ec27ffeec534ba02e4171a3b6cd6d193

7.6.0
- Update git to 2.0.5 0749ffc43b4583fae6fc8ac1b91111340a225f92
- Update libgit2 and rugged to version 0.21.2 66ac2e805a166ecb10bdf8ba001b106acd7e49f3
- Generate SMTP settings using one template for both applications (Michael Ruoss) a6d6ff11f102c6fa9da6209f80162c5e137feeb9
- Add gitlab-shell configuration settings for http_settings, audit_usernames, log_level 5e4310442a608c5c420ffe670a9ab6f111489151
- Enable Sidekiq MemoryKiller by default with a 1,000,000 kB limit 99bbe20b8f0968c4e3c4a42281014db3d3635a7f
- Change runit recipe for Fedora to systemd (Nathan) fbb7687f3cc2f38faaf6609d1396b76d2f6f7507
- Added kerberos lib to support gitlab dependency 66fd3a85cce74754e850034894a87d554fdb04b7
- gitlab.rb now lists all available configuration options 6080f125697f9fe7113af1dc80e0a7bc9ddb284e
- Add option to insert configuration settings in nginx template (Sander Boom) 5ba0485a489549a0bb33531e027a206b1775b3c0


7.5.0
- Use system UIDs and GIDs when creating accounts (Tim Bishop) cfc04342129a4c4dca5c4827d541c8888adadad3
- Bundle GitLab CI with the package 3715204d86900e8501483f70c6370ba4e3f2bb3d
- Fix inserting external_url in gitlab.rb after installation 59f5976562ce3439fb3a6e43caac489a5c230db4
- Avoid duplicate sidekiq log entries on remote syslog servers cb514282f03add2fa87427e4601438653882fa03
- Update nginx config and SSL ciphers (Ben Bodenmiller) 0722d29c 89afa691
- Remove duplicate http headers (Phill Campbell) 8ea0d201c32527f095d3afa707a38865984e27d2
- Parallelize bundle install during build c53e92b80f423c90f2169fbd2d9ef33ce0233cb6
- Use Ruby 2.1.4 e083162579f00814086f34c1cf02c96dc9796f69
- Remove exec symlinks after gitlab uninstall 70c9a6e00be8814b8cad337b1e6d212be88a3f99
- Generate required gitlab_shell_secret d65d4832f1164dfe62036a65d1899ccf80cbe0c6

7.4.0
- Fix broken environment variable removal
- Hard-code the environment directory for gitlab-rails
- Set PATH and RAILS_ENV via the env directory
- Set the environment for gitlab-rails and gitlab-rake via chpst
- Configure bundle exec wrapper with gitlab-rails-rc
- Add a logrotate service for `gitlab-rails/production.log` etc.
- Again using backwards compatible ssl ciphers
- Increased Unicorn timeout to 60s
- For non-bundled webserver added an option of supplying external webserver user username
- Add option for using backup uploader
- Update openssl to 1.0.1j
- If hostname is correctly set, omnibus will prefill external_url

7.3.1
- Fix web-server recipe order
- Make /var/opt/gitlab/nginx gitlab-www's home dir
- Remove unneeded write privileges from gitlab-www

7.3.0
- Add systemd support for Centos 7
- Add a Centos 7 SELinux module for ssh-keygen permissions
- Log `rake db:migrate` output in /tmp
- Support `issue_closing_pattern` via gitlab.rb (Michael Hill)
- Use SIGHUP for zero-downtime NGINX configuration changes
- Give NGINX its own working directory
- Use the default NGINX directory layout
- Raise the default Unicorn socket backlog to 1024 (upstream default)
- Connect to Redis via sockets by default
- Set Sidekiq shutdown timeout to 4 seconds
- Add the ability to insert custom NGINX settings into the gitlab server block
- Change the owner of gitlab-rails/public back to root:root
- Restart Redis and PostgreSQL immediately after configuration changes
- Perform chown 7.2.x security fix in postinst

7.2.0
- Pass environment variables to Unicorn and Sidekiq (Chris Portman)
- Add openssl_verify_mode to SMTP email configuration (Dionysius Marquis)
- Enable the 'ssh_host' field in gitlab.yml (Florent Baldino)
- Create git's home directory if necessary
- Update openssl to 1.0.1i
- Fix missing sidekiq.log in the GitLab admin interface
- Defer more gitlab.yml defaults to upstream
- Allow more than one NGINX listen address
- Enable NGINX SSL session caching by default
- Update omnibus-ruby to 3.2.1
- Add rugged and libgit2 as dependencies at the omnibus level
- Remove outdated Vagrantfile

7.1.0
- Build: explicitly use .forward for sending notifications
- Fix MySQL build for Ubuntu 14.04
- Built-in UDP log shipping (Enterprise Edition only)
- Trigger Unicorn/Sidekiq restart during version change
- Recursively set the SELinux type of ~git/.ssh
- Add support for the LDAP admin_group attribute (GitLab EE)
- Fix TLS issue in SMTP email configuration (provides new attribute tls) (Ricardo Langner)
- Support external Redis instances (sponsored by O'Reilly Media)
- Only reject SMTP attributes which are nil
- Support changing the 'restricted_visibility_levels' option (Javier Palomo)
- Only start omnibus-gitlab services after a given filesystem is mounted
- Support the repository_downloads_path setting in gitlab.yml
- Use Ruby 2.1.2
- Pin down chef-gem's ohai dependency to 7.0.4
- Raise the default maximum Git output to 20 MB

7.0.0-ee.omnibus.1
- Fix MySQL build for Ubuntu 14.04

7.0.0
- Specify numeric user / group identifiers
- Support AWS S3 attachment storage
- Send application email via SMTP
- Support changing the name of the "git" user / group (Michael Fenn)
- Configure omniauth in gitlab.yml
- Expose more fields under 'extra' in gitlab.yml
- Zero-downtime Unicorn restarts
- Support changing the 'signin_enabled' option (Konstantinos Paliouras)
- Fix Nginx HTTP-to-HTTPS log configuration error (Konstantinos Paliouras)
- Create the authorized-keys.lock file for gitlab-shell 1.9.4
- Include Python and docutils for reStructuredText support
- Update Ruby to version 2.1.1
- Update Git to version 2.0.0
- Make Runit log rotation configurable
- Change default Runit log rotation from 10x1MB to 30x24h
- Security: Restrict redis and postgresql log directory permissions to 0700
- Add a 'gitlab-ctl deploy-page' command
- Automatically create /etc/gitlab/gitlab.rb after the package is installed
- Security: Use sockets and peer authentication for Postgres
- Avoid empty Piwik or Google Analytics settings
- Respect custom Unicorn port setting in gitlab-shell

6.9.4-ee.omnibus.1
- Security: Use sockets and peer authentication for Postgres

6.9.2.omnibus.2
- Security: Use sockets and peer authentication for Postgres

6.9.2
- Create the authorized-keys.lock file for gitlab-shell 1.9.4

6.9.1
- Fix Nginx HTTP-to-HTTPS log configuration error (Konstantinos Paliouras)

6.9.0
- Make SSH port in clone URLs configurable (Julien Pivotto)
- Fix default Postgres port for non-packaged DBMS (Drew Blessing)
- Add migration instructions coming from an existing GitLab installation (Goni Zahavy)
- Add a gitlab.yml conversion support script
- Correct default gravatar configuration (#112) (Julien Pivotto)
- Update Ruby to 2.0.0p451
- Fix name clash between release.sh and `make release`
- Fix Git CRLF bug
- Enable the 'sign_in_text' field in gitlab.yml (Mike Nestor)
- Use more fancy SSL ciphers for Nginx
- Use sane LDAP defaults
- Clear the Rails cache after modifying gitlab.yml
- Only run `rake db:migrate` when the gitlab-rails version has changed
- Ability to change the Redis port

6.8.1
- Use gitlab-rails 6.8.1

6.8.0
- MySQL client support (EE only)
- Update to omnibus-ruby 3.0
- Update omnibus-software (e.g. Postgres to 9.2.8)
- Email notifications in release.sh
- Rewrite parts of release.sh as a Makefile
- HTTPS support (Chuck Schweizer)
- Specify the Nginx bind address (Marco Wessel)
- Debian 7 build instructions (Kay Strobach)

6.7.3-ee.omnibus.1
- Update gitlab-rails to v6.7.3-ee

6.7.3-ee.omnibus

6.7.4.omnibus
- Update gitlab-rails to v6.7.4

6.7.2-ee.omnibus.2
- Update OpenSSL to 1.0.1g to address CVE-2014-0160

6.7.3.omnibus.3
- Update OpenSSL to 1.0.1g to address CVE-2014-0160
