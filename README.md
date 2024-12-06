# LDAP

## Config basic

Server: **servidor**\
Base DN: **OU=Usuarios,OU=Empresa,DC=dominio,DC=com.br**\
Users DN: **OU=Usuarios,OU=Empresa,DC=dominio,DC=com.br**\
Bind User: **Userldap** or **RootDN: CN=Userldap,OU=Serviço,DC=dominio,DC=com.br**\
Bind pass: **password**\
Atribute Login: **sAMAccountName**\
Atribute name: **givenName**\
Filter LDAP: 
**(&(objectClass=user)(memberOf=CN=Acesso Aplicacao,OU=Grupos,OU=Empresa,DC=dominio,DC=com.br))**\
**(&(objectClass=user)(sAMAccountName={0})(memberOf=CN=Acesso Aplicacao,OU=Grupos,OU=Empresa,DC=dominio,DC=com.br))**\
*Verificar na documentação da aplicação a melhor forma*

## Consulta LDAP SSL
*O nome do servidor deve estar com o FQDN completo*
```
ldapsearch -x -H ldaps://server.dominio.com.br:636 -b "DC=dominio,dc=com,dc=br" -D 'Userldap@dominio.com.br' -W
```
Se retornar erro, será necessário colocar o certificado CA no Servidor de origem da consulta.

[Certificado AD no Linux](AD.md)

## Zabbix

Ref: <https://www.zabbix.com/documentation/current/en/manual/web_interface/frontend_sections/users/authentication/ldap>

Será necesário colocar o fqdn completo no nome do host/servidor. 

Nome: **Conexão LDAP**\
host: **ldaps://servidor.dominio.com.br**\
Porta: **636**\
Base DN: **OU=Usuarios,OU=EMPRESA,DC=dominio,DC=com,DC=br**\
Atributo de pesquisa: **sAMAccountName**\
Bind DN: **CN=Userldap,OU=Serviço,OU=EMPRESA,DC=dominio,DC=com,DC=br**\
Senha para Bind: *******
