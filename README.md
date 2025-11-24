# ComedouroIoT

🐟 Sistema Inteligente de Aquario: Monitoramento e Alimentação Automatizada
Contexto e Objetivo Estratégico
Este projeto técnico descreve o desenvolvimento de um sistema de Alimentação Inteligente e Monitoramento Contínuo para aquários, alinhado aos princípios da Aquicultura 4.0. O objetivo central é mitigar as falhas humanas da alimentação manual (como a superalimentação) , que causam o desequilíbrio químico do ecossistema aquático e o desperdício de ração.

O sistema foi desenhado para ser escalável e flexível, suportando a gestão independente de múltiplos aquários (Ativos) e controlável via uma interface web centralizada.

🚀 Arquitetura e Tecnologias
A solução é baseada em uma arquitetura de Internet das Coisas (IoT) ponta a ponta, usando uma pilha de código aberto e serviços cloud:

1. Hardware Simulado (Coleta de Dados)
Os dispositivos foram simulados usando o Wokwi (ESP32)  e são responsáveis por enviar dados via MQTT.


Microcontrolador: ESP32 (para gestão e conectividade Wi-Fi).


Sensores: DHT22 (Temperatura) e Potenciômetro (simulando pH).


Atuador: Servo Motor (para dosagem precisa da ração).


Controle Local: Pushbutton (para acionamento manual imediato).

2. Back-end e Lógica de Automação (Node-RED)
O Node-RED atua como o cérebro do sistema:

Comunicação: Assinatura de tópicos MQTT (HiveMQ).

Gestão de Horários: Criação de um Endpoint HTTP (/config) com nós Template para permitir ao usuário definir horários de alimentação dinamicamente via um painel web (substituindo a injeção manual de código).

Controle: Lógica de agendamento que verifica a cada 30 segundos se deve enviar o comando feed via MQTT para os respectivos dispositivos (Aquário 1 e Aquário 2).


Notificação: Integração com a API do WhatsApp (CallMeBot) para envio de alertas de sucesso/erro e relatórios com dados de Temp/pH no momento da alimentação.

3. Persistência e Visualização (Data Analytics)

Banco de Dados: InfluxDB Cloud (v2.0), configurado para receber os dados de todos os sensores e eventos (alimentação, problemas) .

Visualização (Dashboard): Grafana, utilizado para criar Dashboards independentes e profissionais, focados na gestão de risco e análise histórica:

Média Diária: Gráficos de barras que mostram a média de Temp e pH agrupada por períodos do dia (simulação de Manhã/Tarde/Noite).

Alertas: Tabela de "Problemas Ocorridos" que filtra e exibe apenas os registros de sensores fora das faixas de segurança (ex: Temp > 28°C ou pH < 6.0).

💡 Resultados e Valor Agregado
O sistema alcança os seguintes resultados:

Consistência e Redução de Poluição: Garante a regularidade da dieta e minimiza o desperdício de ração.
Escalabilidade (B2C/B2B): A arquitetura MQTT com tópicos distintos permite gerenciar desde o aquário doméstico até múltiplos ativos corporativos.
Rastreabilidade: Todos os eventos de alimentação e medições são registrados no InfluxDB para análise histórica e suporte à decisão.

Integrantes:
- Ali Ahmad
- Lucas Souza Santos
- Lucas Lacerda
- Wendell Rodrigues da Costa

Apresentação: https://www.youtube.com/watch?v=vL0FQ6-sxP0&t=2s
