---

# Configuração de Múltiplos Subdomínios com Apache2 e Servidor DNS Local (BIND9)

Este script automatiza a criação de um ambiente web local com múltiplos subdomínios usando **Apache2** e **BIND9** em sistemas baseados em Debian/Ubuntu.

## 📜 Descrição

O script instala e configura o servidor web **Apache2**, cria diretórios e páginas HTML para múltiplos subdomínios, configura Virtual Hosts, instala e configura o **servidor DNS (BIND9)** para resolver os subdomínios localmente, e ajusta o `/etc/hosts` e o `resolv.conf` para garantir que os domínios funcionem sem internet externa.

## ⚙️ Requisitos

* Distribuição baseada em Debian/Ubuntu
* Acesso com `sudo`
* IP local estático definido (ajustar se necessário)
* Git opcional (caso queira clonar sites externos)

## 🧾 Variáveis no Script

* `DOMINIO="ifrn.com"` – domínio base usado localmente
* `IP="192.168.0.10"` – IP do servidor DNS e do Apache
* `SUBDOMINIOS=("site1" "site2" "ivaldo")` – subdomínios que serão criados

## 🖥️ Funcionalidades Executadas

1. **Instalação do Apache2 (caso necessário)**
2. **Criação de diretórios e arquivos HTML para cada subdomínio**
3. **Criação e ativação de VirtualHosts no Apache**
4. **Instalação e configuração do BIND9 como servidor DNS local**
5. **Criação de zona DNS com registros A para cada subdomínio**
6. **Configuração do `/etc/resolv.conf` para usar o DNS local**
7. **Atualização do `/etc/hosts` para compatibilidade**
8. **Reinicialização e habilitação dos serviços**

## 📂 Estrutura Criada

```text
/var/www/site1.ifrn.com/public_html/index.html
/var/www/site2.ifrn.com/public_html/index.html
/var/www/ivaldo.ifrn.com/public_html/index.html
/etc/apache2/sites-available/site1.ifrn.com.conf
/etc/bind/db.ifrn.com
```

## 💡 Como Usar

1. Dê permissão de execução ao script:

```bash
chmod +x configurar_sites_dns.sh
```

2. Execute com privilégios de superusuário:

```bash
sudo ./configurar_sites_dns.sh
```

## 🌐 Acesso aos Subdomínios

Após a execução, você poderá acessar via navegador:

```
http://site1.ifrn.com
http://site2.ifrn.com
http://ivaldo.ifrn.com
```

> 🔧 Se estiver usando uma máquina cliente, aponte o DNS dela para o IP configurado no script (`192.168.0.10`).

## 🛠️ Melhorias Sugeridas

* Verificação se o IP já está em uso ou é válido
* Validação de entradas DNS duplicadas
* Suporte a domínios reais ou SSL com Let's Encrypt (em rede pública)
* Adição de logs e tratamento de erros

---
