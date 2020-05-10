# LDAP 认证

!!! info "LDAP 支持 使用 LADP 与 Windows AD 的用户作为 jumpserver 登录用户"
    username 和 mail 具有唯一性, 且不能为空值


!!! note "LDAP 设置"
    ??? tip "勾选 使用SSL LDAP地址 需要使用 ssl 端口, 默认 636"

    `LDAP地址`      `ldap://serverurl:389`  
    `绑定DN`        `cn=administrator,cn=Users,dc=jumpserver,dc=org`  
    `用户OU`        `ou=jumpserver,dc=jumpserver,dc=org`  
    `用户过滤器`     `(cn=%(user)s)`  
    `LADP属性映射`  `{"username": "cn", "name": "sn", "email": "mail"}`
    `启动LDAP认证`  `☑️`

    !!! tip "选项说明"
        `DN` 一定要是完整的DN, 不能跳过OU, 可以使用其他工具查询  
        `cn=admin,ou=aaa,dc=jumpserver,dc=org` 不能缩写成 `cn=admin,dc=jumpserver,dc=org`

        `用户OU` 用户OU可以只写顶层OU, 不写子OU  
        `ou=aaa,ou=bbb,ou=ccc,dc=jumpserver,dc=org`, 可以只写 `ou=ccc,dc=jumpserver,dc=org`

        `用户过滤器` 根据规则到 `用户OU` 里面去检索用户, 支持 memberof  
        `(uid=%(user)s)` 或 `(sAMAccountName=%(user)s)`

        `LADP属性映射` username name email 这三项不可修改删除  
        `{"username": "uid", "name": "sn", "email": "mail"}` 或 `{"username": "sAMAccountName", "name": "cn", "email": "mail"}`

        注意: 用户过滤器用什么筛选, LDAP属性映射字段要与其一致, 过滤器用 uid, LDAP属性映射也要用 uid
