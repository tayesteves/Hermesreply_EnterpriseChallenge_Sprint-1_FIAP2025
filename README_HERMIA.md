# HERMIA - Hermes Reply Intelligent Assistant

### FIAP - Faculdade de Informática e Administração Paulista

## 📅 **HERMIA - Sistema Inteligente de Prevenção de Falhas Industriais**


## 👥 Integrantes
- **Carlos** - RM566487
- **Endrew** - RM563646
- **João** - RM565999
- **Tayná** - RM562491
- **Vinicius** - RM566269

---

## 📄 Descrição
O projeto **HERMIA (Hermes Reply Intelligent Assistant)** é um sistema inteligente que visa otimizar a manutenção preditiva em ambientes industriais. Ao monitorar continuamente variáveis críticas de funcionamento de máquinas, o sistema identifica padrões de anomalias em tempo real, sugere ações corretivas e fornece insights para evitar falhas graves que venha a impactar a produção causando prejuízo para a empresa.

A solução combina sensores, protocolo MQTT, análise com IA e visualização em dashboards gerenciais. O objetivo é reduzir paradas não planejadas, aumentar a produtividade e garantir mais segurança operacional.

---

## 🧱 Estrutura por Camadas

### 1. Camada de Percepção
- Responsável pela coleta de dados em tempo real de pontos críticos das máquinas industriais.
- Dados monitorados serão definidos conforme os sensores fornecidos pela empresa. Possíveis variáveis:
  - Temperatura;
  - Pressão;
  - Vibração;
  - Outros dados a serem definidos.
- Frequência de coleta de dados adaptável de acordo com a necessidade de cada tipo de dado e sensor. 
- Localização dos Sensores: 
  - Pontos críticos das máquinas: motores, válvulas, rolamentos ou onde o dado possa ser captado com mais precisão.
- Os sensores estão conectados a um microcontrolador **ESP32**, que envia os dados via Wi-Fi.
- Caso haja desconexão, os dados são armazenados localmente em buffer e reenviados automaticamente.

### 2. Camada de Comunicação
- Responsável pela transmissão segura e eficiente dos dados coletados para a camada de processamento. 
- Utiliza o protocolo **MQTT**, leve e ideal para IoT.
- Vantagens:
  - Baixa latência e uso eficiente de banda;
  - Suporte a comunicação desacoplada, promovendo escalabilidade e modularidade;
  - Confiabilidade em redes instáveis.
- Inicialmente configurado com o **broker Mosquitto** em ambiente local.
- Segurança: autenticação por usuário e senha no broker MQTT.
- Implementação inicial com broker MQTT local (Mosquitto), com potencial migração futura para **AWS IoT Core**.

### 3. Camada de Processamento
- Responsável pelo armazenamento, análise dos dados e aplicação de técnicas de inteligência artificial para detecção de anomalias e previsão de falhas.
- O processamento dos dados é feito localmente com códigos em **Python**.
- Dados armazenados em um **banco de dados Oracle**.
  - Estrutura dos Dados:
        "timestamp": "AAAA-MM-DD HH:MM:SS",
        "sensor_id": "ID_do_Sensor",
        "sensor_type": "Temperatura|Pressão|Vibração|Corrente|Velocidade|OUTRO",
        "value": 123.45,
        "status": "normal|anômalo".

- Utilização de IA para análise preditiva:
  - **Prophet**: previsão de séries temporais;
  - **Isolation Forest**: detecção de anomalias;
  - **Random Forest**: classificação de padrões de falha.
- Os modelos serão treinados com dados simulados, normalizados e validados para garantir robustez.

### 4. Camada de Aplicação
- Responsável pela visualização dos dados processados e pela interação do usuário com o sistema através de dashboards intuitivos.
- Visualização dos dados por meio de **dashboards desenvolvidos no Power BI**.
- Tipos de dashboards:
  - **Operacional**: status em tempo real das máquinas
  - **Gerencial**: análise histórica, gráficos de tendência, relatórios detalhados e previsões de falha.
- Atualização automática a cada minuto (em protótipo).
- Inicialmente acessível localmente. Acesso remoto é um passo futuro.
- - Experiência do Usuário (UX):
    - Interface intuitiva com ícones coloridos e mensagens claras.
    - Opções analíticas avançadas para gestores, incluindo a exportação de relatórios.

### 5. Camada de Ação
- Responsável por gerar **alertas automáticos** em caso de anomalia detectada.
- Notificações por **e-mail ou WhatsApp** para os responsáveis.
- Sugestão de ações imediatas, como desligar equipamento, reduzir carga, etc.
- Registro detalhado no banco de dados, incluindo timestamp do alerta, ação recomendada e ação realizada.
- Previsão de Falha:
    -Capacidade de prever falhas com um intervalo de dias de antecedência, permitindo um planejamento proativo da manutenção preventiva.
- Futuramente: possibilidade de integração com sistemas de controle para automatizar respostas.

---

## 🛠️ Tecnologias Utilizadas
- **Hardware:** ESP32, sensores industriais.
- **Linguagem:** Python, com bibliotecas Scikit-learn, PyCaret, Pandas, Prophet, IsolationForest.
- **Protocolos:** MQTT.
- **Broker MQTT (Inicial):** Mosquitto.
- **IA:** Prophet, Isolation Forest, Random Forest, Scikit-learn, PyCaret.
- **Banco de Dados:** Oracle (possível migração futura para PostgreSQL ou AWS RDS).
- **Visualização:** Power BI.
- **Serviços de Mensagens:** WhatsApp (via API) ou e-mail.

---

## 🚀 Próximos Passos
- Definir os sensores reais e as variáveis que serão monitoradas.
- Criar e testar o protótipo funcional da comunicação MQTT.
- Implementar o broker MQTT e configurar os parâmetros de segurança.
- Criar o banco de dados Oracle e populá-lo com dados coletados.
- Desenvolver e treinar os modelos de IA para detecção de anomalias e previsão de falhas.
- Testar os modelos com dados simulados para validação inicial.
 -Desenvolver dashboards interativos e configurar sua atualização em tempo real.
- Implementar o sistema de alertas automáticos e recomendações preventivas.
- Documentar os testes, aprendizados e resultados obtidos.


