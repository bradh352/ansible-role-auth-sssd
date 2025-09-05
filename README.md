# Authentication Enrollment for FreeIPA Role

Author: Brad House<br/>
License: MIT<br/>
Original Repository: https://github.com/bradh352/ansible-role-auth-sssd

## Overview

Configure a machine to authenticate using Kerberos and LDAP via SSSD.  An
optional host keytab may be specified if needed.  In some circumstances, like
NFS kerberos mounts, it may be desirable to deploy a shared host keytab for
users to be able to mount NFS shares as otherwise they are unable to even if
they have their own TGT.

## Variables used by this role

In most environments these settings will likely be global and stored under the
group `all` vars.

* `auth_sssd_cacert_url`: URL to CA Certificate path to install for trusting LDAPS
  connections.  For FreeIPA this is `https://freeipa.my.domain/ipa/config/ca.crt`
* `auth_sssd_servers`: List of ldap servers.  This should be the bare domain
  names and not include ldap:// or ldaps:// prefixes or ports.
* `auth_sssd_realm`: Kerberos Realm.  All uppercase.
* `auth_sssd_search_base`: Search base. E.g. `dc=testenv,dc=bradhouse,dc=dev`
* `auth_sssd_binddn`: Bind DN. E.g. `uid=bind,cn=sysaccounts,cn=etc,dc=testenv,dc=bradhouse,dc=dev`
* `auth_sssd_bindpass`: Bind Password associated with Bind DN.  Typically should
  be stored in the vault.
* `auth_sssd_host_keytab`: Optional. Base64-encoded host keytab data to install as
  `/etc/krb5.keytab`.


