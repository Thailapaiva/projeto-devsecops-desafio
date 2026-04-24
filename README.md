# Desafio DevSecOps — Gerenciador de Tarefas

## Sobre o Projeto
Este repositório faz parte do desafio prático do módulo de DevSecOps da ADA Tech.
Este projeto estava com vulnerabilidades propositais e uma pipeline incompleta.
O objetivo era **implementar a pipeline de segurança** e **corrigir as vulnerabilidades**.

## Estado atual
A pipeline está **completa**. Os steps de segurança foram implementados.

## A Missão era:
1. Implementar os steps de segurança no `pipeline.yml`
2. Fazer a pipeline **quebrar** ao detectar os problemas
3. Corrigir as vulnerabilidades encontradas
4. Fazer a pipeline **passar** com tudo verde ✅
5. Documentar o funcionamento da pipeline neste README

## O que foi implementado
- [ ] Secrets Scanning com **Gitleaks**
- [ ] SAST com **Semgrep**
- [ ] SCA com **Grype**
- [ ] Deploy com **GitHub Pages**

## Como a pipeline funciona
A pipeline foi projetada para garantir a segurança do código em diferentes camadas do desenvolvimento, seguindo práticas de DevSecOps. Cada etapa atua em um tipo específico de vulnerabilidade, garantindo uma análise abrangente antes do deploy.

🔎 1. Secrets Scanning com Gitleaks

Essa etapa verifica se há segredos expostos no código, como tokens, senhas, chaves de API ou credenciais.

🔧 Como funciona: o Gitleaks analisa todo o histórico e os arquivos do repositório em busca de padrões conhecidos de secrets.
🚨 Por que é importante: vazamentos de credenciais são uma das falhas mais críticas, podendo comprometer sistemas inteiros.
❌ Falha na pipeline: se qualquer segredo for detectado, a pipeline é interrompida.

🧠 2. SAST com Semgrep

Essa etapa realiza análise estática do código para encontrar vulnerabilidades diretamente na lógica da aplicação.

🔧 Como funciona: o Semgrep utiliza regras para identificar padrões inseguros no código (ex: SQL Injection, uso inseguro de funções, etc.).
🛡️ Por que é importante: detecta falhas antes mesmo da aplicação ser executada.
❌ Falha na pipeline: qualquer vulnerabilidade crítica encontrada faz a pipeline falhar.

📦 3. SCA com Grype

Essa etapa analisa as dependências do projeto em busca de vulnerabilidades conhecidas.

🔧 Como funciona: o Grype verifica bibliotecas e pacotes utilizados comparando com bancos de dados de vulnerabilidades (como CVEs).
⚠️ Por que é importante: muitas falhas vêm de dependências externas, não do código em si.
❌ Falha na pipeline: vulnerabilidades com severidade alta/crítica interrompem o fluxo.

🚀 4. Deploy com GitHub Pages

Após todas as verificações de segurança passarem com sucesso, o deploy é realizado automaticamente.

🔧 Como funciona: a aplicação é publicada via GitHub Pages.
✅ Pré-requisito: todas as etapas anteriores devem estar “verdes”.
🌐 Resultado: versão segura da aplicação disponível publicamente.
✅ Resumo da estratégia

A pipeline segue o princípio de "shift left security", trazendo a segurança para o início do ciclo de desenvolvimento:

Detecta vazamento de credenciais (Gitleaks)
Identifica falhas no código (Semgrep)
Verifica vulnerabilidades em dependências (Grype)
Só permite deploy se tudo estiver seguro (GitHub Pages)

## URL de Produção
> https://thailapaiva.github.io/projeto-devsecops-desafio/
