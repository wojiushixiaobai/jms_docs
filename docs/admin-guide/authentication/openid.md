# OpenID 认证

!!! info "使用 OpenID 来进行认证设置"
    修改 JumpServer 配置文件启用 OpenID 认证
    ```sh
    vi /opt/jumpserver/config.yml
    ```
    ```yaml
    BASE_SITE_URL: http://localhost:8080
    AUTH_OPENID: true  # True or False
    AUTH_OPENID_SERVER_URL: https://openid-auth-server.com/
    AUTH_OPENID_REALM_NAME: realm-name
    AUTH_OPENID_CLIENT_ID: client-id
    AUTH_OPENID_CLIENT_SECRET: client-secret
    ```
