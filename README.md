# Docker Web Server

Application development environment with Docker

## Guia para Certificados SSL com Certbot

Este guia abrange o processo de criação de certificados SSL usando o Certbot, a configuração da renovação automática e a visualização de certificados.

### Criação de Certificados SSL

1. **Instale o Certbot**:
   Certifique-se de que o Certbot esteja instalado no seu servidor. Se não estiver, siga as instruções no site oficial: [Certbot Installation Guide](https://certbot.eff.org/instructions).

2. **Configure o Diretório de Webroot**:
   Escolha um diretório no seu servidor para ser usado como diretório de webroot. Por exemplo, `/var/www/html`.

3. **Solicite o Certificado SSL**:
   Use o Certbot para solicitar um certificado SSL para seu domínio (substitua `mydomain.com` pelo seu domínio real) com a opção `--webroot` e `--webroot-path`:

```bash
sudo certbot certonly --webroot --webroot-path /var/www/html -d mydomain.com
```

### Renovação Automática

**Instale o Certbot**:
O Certbot configura uma tarefa cron para a renovação automática dos certificados. Certifique-se de que a renovação automática esteja habilitada:

```bash
sudo certbot renew --dry-run
```

### Verificar Detalhes dos Certificados

**Instale o Certbot**:
Para listar os certificados SSL gerenciados pelo Certbot, use o comando:

```bash
sudo certbot certificates
```

