---
title: pt-duplicate-key-checker 工具
date: 2019-06-09
---

- docs:  https://www.percona.com/doc/percona-toolkit/2.2/pt-duplicate-key-checker.html
- 下载地址: https://www.percona.com/downloads/percona-toolkit/LATEST/


安装依赖 

`yum install perl-DB perl-DBD-MySQL perl-IO-Socket-SSL perl-Digest-MD5`

安装 `percona-toolkit-3.0.13-1.el7.x86_64.rpm` 

`rpm -ivh percona-toolkit-3.0.13-1.el7.x86_64.rpm`

demo 

```
[root@rails-prod-2 shared]# pt-duplicate-key-checker --host host --ask-pass --databases dbname --user username
Enter password:
*******************************************************************
 Using the default of SSL_verify_mode of SSL_VERIFY_NONE for client
 is deprecated! Please set SSL_verify_mode to SSL_VERIFY_PEER
 possibly with SSL_ca_file|SSL_ca_path for verification.
 If you really don't want to verify the certificate and keep the
 connection open to Man-In-The-Middle attacks please set
 SSL_verify_mode explicitly to SSL_VERIFY_NONE in your application.
*******************************************************************
  at /usr/bin/pt-duplicate-key-checker line 3914.
*******************************************************************
 Using the default of SSL_verify_mode of SSL_VERIFY_NONE for client
 is deprecated! Please set SSL_verify_mode to SSL_VERIFY_PEER
 possibly with SSL_ca_file|SSL_ca_path for verification.
 If you really don't want to verify the certificate and keep the
 connection open to Man-In-The-Middle attacks please set
 SSL_verify_mode explicitly to SSL_VERIFY_NONE in your application.
*******************************************************************
  at /usr/bin/pt-duplicate-key-checker line 3914.

# A software update is available:
# ########################################################################
# shiji_production.admins_roles
# ########################################################################

# index_admins_roles_on_admin_id is a left-prefix of index_admins_roles_on_admin_id_and_role_id
# Key definitions:
#   KEY `index_admins_roles_on_admin_id` (`admin_id`),
#   KEY `index_admins_roles_on_admin_id_and_role_id` (`admin_id`,`role_id`),
# Column types:
#	  `admin_id` bigint(20) default null
#	  `role_id` bigint(20) default null
# To remove this duplicate index, execute:
ALTER TABLE `shiji_production`.`admins_roles` DROP INDEX `index_admins_roles_on_admin_id`;

# ########################################################################
# shiji_production.partner_users
# ########################################################################

# index_partner_users_on_partner_id is a left-prefix of index_partner_users_on_partner_id_and_user_id
# Key definitions:
#   KEY `index_partner_users_on_partner_id` (`partner_id`),
#   UNIQUE KEY `index_partner_users_on_partner_id_and_user_id` (`partner_id`,`user_id`),
# Column types:
#	  `partner_id` bigint(20) default null
#	  `user_id` bigint(20) default null
# To remove this duplicate index, execute:
ALTER TABLE `shiji_production`.`partner_users` DROP INDEX `index_partner_users_on_partner_id`;

# ########################################################################
# shiji_production.roles
# ########################################################################

# index_roles_on_name is a left-prefix of index_roles_on_name_and_resource_type_and_resource_id
# Key definitions:
#   KEY `index_roles_on_name` (`name`)
#   KEY `index_roles_on_name_and_resource_type_and_resource_id` (`name`,`resource_type`,`resource_id`),
# Column types:
#	  `name` varchar(50) default null
#	  `resource_type` varchar(50) default null
#	  `resource_id` bigint(20) default null
# To remove this duplicate index, execute:
ALTER TABLE `shiji_production`.`roles` DROP INDEX `index_roles_on_name`;

# ########################################################################
# Summary of indexes
# ########################################################################

# Size Duplicate Indexes   2164781
# Total Duplicate Indexes  3
# Total Indexes            341

```






