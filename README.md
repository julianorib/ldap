# LDAP

## Config basic

```
Server: servidor
Base DN: OU=Usuarios,OU=Empresa,DC=domain,DC=local
Users DN: OU=Usuarios,OU=Empresa,DC=domain,DC=local
Bind User: ldap.user or RootDN: CN=ldap.user,OU=Serviço,DC=domain,DC=local
Bind pass: password
Atribute Login: sAMAccountName
Atribute name: givenName
Filter LDAP: 
(&(objectClass=user)(memberOf=CN=Acesso Aplicacao,OU=Grupos,OU=Empresa,DC=domain,DC=local))
(&(objectClass=user)(sAMAccountName={0})(memberOf=CN=Acesso Aplicacao,OU=Grupos,OU=Empresa,DC=domain,DC=local))
```


## Consulta LDAP SSL
*O nome do servidor deve estar com o FQDN completo*
```
ldapsearch -x -H ldaps://server.domain.local:636 -b "DC=domain,dc=com,dc=br" -D 'ldap.user@domain.com.br' -W
```
Se retornar erro, será necessário colocar o certificado CA no Servidor local. 


## Zabbix

Ref: <https://www.zabbix.com/documentation/current/en/manual/web_interface/frontend_sections/users/authentication/ldap>

Será necesário colocar o fqdn completo no nome do host/servidor. Portanto precisa alterar o DNS da origem, para enxergar o host.

Nome: **Conexão LDAP**\
host: **ldaps://servidor.dominio.com.br**\
Porta: **636**\
Base DN: **OU=Usuarios,OU=EMPRESA,DC=dominio,DC=com,DC=br**\
Atributo de pesquisa: **sAMAccountName**\
Bind DN: **CN=Userldap,OU=Serviço,OU=EMPRESA,DC=dominio,DC=com,DC=br**\
Senha para Bind: *******
