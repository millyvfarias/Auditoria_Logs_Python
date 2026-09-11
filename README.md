# Auditoria de Logs - Detecção Automatizada de Ameaças (Logs Analyzer)
Script em Python e Pandas para auditoria de logs de servidores, com foco em detecção automatizada de anomalias e ameaças cibernéticas.

**Objetivo:** Automatizar a identificação das anomalias e possíveis ameaças de acessos a servidores, utilizando a análise de dados para apoiar a equipe de Segurança da Informação e Auditoria de TI.

**O Cenário:** Em uma infraestrutura real, os servidores geram milhões de linhas de log diariamente, e o objetivo da auditoria não é ler esses dados, mas sim identificar as exceções que representam riscos para o negócio.
Esse projeto simula um ambiente corporativo sob varredura, onde a missão é isolar o tráfego malicioso que conseguiu passar pelas camadas iniciais de defesa.

**Tecnologias Utilizadas:**
Python
Pandas (Manipulação, limpeza, e estruturação dos dados)
Google Colab

**Processo Investigativo:**
1. **Coleta e ingestão:** Carregamento de um dataset contendo registros brutos de acesso web (IP, Timestamp, Método, URL e Status HTTP).
2. **Filtragem e limpeza:** Aplicação de regras de negócio para separar o ruído (trafego benigno) das reais ameaças, reduzindo a base de análise para focar no que realmente importa.
3. **Mapeamento de Vulnerabilidade:** Identificação de IPs realizando varreduras automatizadas (bots e scanning) e tentativas de execução remota de código (RCE)

**Achado de Auditoria (evidência):**
A análise revelou que agentes externos automatizados estão recebendo respostas HTTP200 (OK) ao tatear a infraestrutura. Isso indica que o mapeamento malicioso está sendo bem-sucedido, expondo a arquitetura do sistema para possíveis injeções de código. O arquivo relatorio_auditoria_ameacas.csv foi gerado contendo o registro exato (IP e Horário) dessas anomalias.

**Plano de Ação Recomendado:**
1. Implementação do Rate Limiting (Limite de Taxa) para bloquear IPs com comportamento de varredura.
2. Revisão e Calibração das regras do Web Application Firewall (WAF) pela equipe de segurança, utilizando a lista de IPs isolados neste relatório como inteligência de ameaças (Threat Intelligence).
