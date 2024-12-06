# Certificado do AD no Linux.

Este guia tem como objetivo configurar um certificado do Active Directory para um servidor Linux.

## Primeiro

Exportar a CA do Active Directory.

Acesse o Servidor que contém o Serviço de "Certification Authority".

*Clique no Iniciar, Digite "certlm.msc"*

*Certificates - Local Computer, Personal, Certificates.*

*Clique com o botão direito do mouse sobre o Certificado-CA, All Tasks, Export.*\

*Next, Não exporte a senha, Next, Base-64 encoded X.509 (.CER), Next, Escolha um local e um nome para Salvar, Next, Finish.*

Copiar este arquivo de Certificado para o servidor Linux.

## Derivados RedHat

Executar os comandos abaixo como root:
```
trust anchor CA.cer
update-ca-trust
```

## Derivados Debian

Executar os comandos abaixo como root:
```
mv CA.cer /usr/local/share/ca-certificates/CA.crt
update-ca-certificates
```
