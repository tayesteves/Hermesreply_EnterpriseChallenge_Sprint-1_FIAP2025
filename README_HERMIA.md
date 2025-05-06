# HERMIA - Hermes Reply Intelligent Assistant

### FIAP - Faculdade de Informática e Administração Paulista

## 📅 Nome do Projeto
**HERMIA - Sistema Inteligente de Prevenção de Falhas Industriais**

## 👥 Integrantes
- **Carlos** - RM566487
- **Endrew** - RM563646
- **João** - RM565999
- **Tayná** - RM562491
- **Vinicius** - RM566269

## 📚 Professores
**Tutor(a):** Nome do Tutor  
**Coordenador(a):** Nome do Coordenador

---

## 📄 Descrição
O projeto **HERMIA (Hermes Reply Intelligent Assistant)** é um sistema inteligente que visa otimizar a manutenção preditiva em ambientes industriais. Ao monitorar continuamente variáveis críticas de funcionamento de máquinas, o sistema identifica padrões de anomalias em tempo real, sugere ações corretivas e fornece insights para evitar falhas graves.

A solução combina sensores, protocolo MQTT, análise com IA e visualização em dashboards gerenciais. O objetivo é reduzir paradas não planejadas, aumentar a produtividade e garantir mais segurança operacional.

---

## 🧱 Estrutura por Camadas

### 1. Camada de Percepção
- Responsável pela coleta de dados em tempo real de pontos críticos das máquinas industriais.
- Dados monitorados serão definidos conforme os sensores fornecidos pela empresa. Possíveis variáveis:
  - Temperatura
  - Pressão
  - Vibração
  - Outros dados a serem definidos
- Os sensores estão conectados a um microcontrolador **ESP32**, que envia os dados via Wi-Fi.
- Caso haja desconexão, os dados são armazenados localmente em buffer e reenviados automaticamente.

### 2. Camada de Comunicação
- Utiliza o protocolo **MQTT**, leve e ideal para IoT.
- Vantagens:
  - Baixa latência e uso eficiente de banda
  - Suporte a comunicação assíncrona
  - Tolerante a falhas
- Inicialmente configurado com o **broker Mosquitto** em ambiente local.
- Segurança: autenticação por usuário e senha no broker MQTT.

### 3. Camada de Processamento
- O processamento dos dados é feito localmente com códigos em **Python**.
- Dados armazenados em um **banco de dados Oracle XE**.
- Utilização de IA para análise preditiva:
  - **Prophet**: previsão de séries temporais
  - **Isolation Forest**: detecção de anomalias
  - **Random Forest**: classificação de padrões de falha
- Os modelos serão treinados com dados simulados, normalizados e validados para garantir robustez.

### 4. Camada de Aplicação
- Visualização dos dados por meio de **dashboards desenvolvidos no Power BI**.
- Tipos de dashboards:
  - **Operacional**: status em tempo real das máquinas
  - **Gerencial**: análise histórica, relatórios e KPIs
- Atualização automática a cada minuto (em protótipo).
- Inicialmente acessível localmente. Acesso remoto é um passo futuro.

### 5. Camada de Ação
- Responsável por gerar **alertas automáticos** em caso de anomalia detectada.
- Notificações por **e-mail ou WhatsApp** para os responsáveis.
- Sugestão de ações imediatas, como desligar equipamento, reduzir carga, etc.
- Futuramente: possibilidade de integração com sistemas de controle para automatizar respostas.

---

## 🛠️ Tecnologias Utilizadas
- **Hardware:** ESP32, sensores industriais
- **Linguagem:** Python
- **Protocolos:** MQTT
- **IA:** Prophet, Isolation Forest, Random Forest, Scikit-learn, PyCaret
- **Banco de Dados:** Oracle XE (possível migração futura para PostgreSQL ou AWS RDS)
- **Visualização:** Power BI
- **Serviços de Mensagens:** WhatsApp (via API) ou e-mail

---

## 🚀 Próximos Passos
- Definir sensores reais e variáveis que serão usados
- Criar protótipo funcional da comunicação MQTT
- Treinar e testar modelos de IA com dados simulados
- Criar banco Oracle e popular com dados coletados
- Desenvolver dashboards e configurar atualização em tempo real
- Implementar sistema de alerta
- Documentar testes e resultados finais

---

**Nota:** Este projeto é de caráter acadêmico, desenvolvido para o desafio Enterprise Challenge da FIAP em parceria com a empresa Hermes Reply. Nenhuma parte do sistema está publicada sob licença de software livre neste momento.
