# Validação do Sistema

O principal objetivo deste encontro é validar a integração do sistema embarcado com o projeto desenvolvido. Os subsistemas embarcados e a validação da arquitetura de comunicação é realizada durante este encontro. Conceitos de aprimoramento de desenvolvimento embarcado e formas distintas de realizada a integração do sistema também são realizadas nesta interação. Espera-se que os estudantes consigam construir testes de integração da plataforma embarcada com o restante do projeto desenvolvido. Neste encontro serão abordados: Testes em sistemas embarcados; Testes para sistemas de comunicação; Tópicos avançados de sistemas embarcados.

## Assuntos relacionados

- Atuadores

- Dispositivos lógico-programáveis

- Energia em sistemas embarcados

- Interfaces de comunicação

- Microcontroladores

- Programação de microcontroladores

- Segurança em sistemas embarcados

- Sensores analógicos e digitais


## O que é Sistemas Embarcados?

É uma junção de hardware com software para uma função bem específica. Exemplos: 

* Uma máquina de café;
* Uma máquina de lavar e secar com várias funções;
* Uma SmartTV;
* Um drone;
* Um Smart Watch;
* Um celular;
* Um carro moderno;
* Uma calculadora;
* Uma máquina fotográfica;
* Um notebook ou PC não é um sistema embarcado porque ele possui propósitos gerais;

O sistema embarcado precisa conter um microcontrolador, além de sensores trazendo informações para tomadas de decisão, que influenciarão os atuadores, atuando em uma ação (esquentar, cortar, lavar, girar, abrir, travar/destravar, apitar, acender, apagar, etc).

## O que são Sistemas RTO?

Sistemas de Tempo Real (RTOS) são projetados para responder a eventos em tempo real, garantindo que determinadas tarefas sejam concluídas dentro de prazos predefinidos. 

Por exemplo, considerando os dois microcontroladores abordados nesse módulo:

### Arduino Uno:

1. **Simplicidade:**
   - O Arduino Uno geralmente é usado em projetos simples e pequenos, e muitas vezes não é a escolha primária para sistemas de tempo real complexos.

2. **Limitações de Recursos:**
   - Recursos limitados, como processamento, memória e armazenamento, podem impor desafios na implementação de sistemas de tempo real mais avançados.

3. **Sistema de Execução Única (Single-threaded):**
   - A maioria dos programas Arduino é single-threaded, o que significa que as tarefas são executadas sequencialmente. Isso pode ser uma limitação em sistemas que exigem respostas rápidas a eventos.

4. **Interrupções:**
   O Arduino Uno posui interrupção e por isso, é possível abordar determinados elementos de **tempo real** por meio do uso cuidadoso de interrupções programadas. As interrupções são eventos que interrompem a sequência normal de execução do programa para lidar com eventos específicos. No contexto do tempo real, as interrupções podem ser utilizadas para garantir respostas rápidas a eventos externos. Aqui estão algumas relações entre o conceito de RTO (Real-Time Operating System) ou tempo real e as chamadas de interrupções no Arduino Uno:

   4.1. **Tempo de Resposta Rápida:**
   A implementação de interrupções permite que o Arduino Uno responda rapidamente a eventos externos. Se houver a necessidade de lidar com eventos em tempo real, como a leitura de sensores ou a resposta a botões, as interrupções podem ser usadas para garantir uma resposta rápida.

   4.2. **Priorização de Tarefas:**
   Ao programar interrupções, é possível priorizar tarefas críticas. Por exemplo, se houver várias tarefas a serem executadas, as interrupções podem ser usadas para garantir que a tarefa mais crítica seja atendida imediatamente.

   4.3. **Temporizadores para Agendamento:**
   Os temporizadores e as interrupções relacionadas a eles podem ser usados para agendar tarefas em intervalos específicos. Isso é útil para a execução periódica de operações em sistemas de tempo real.

   4.4. **Manuseio de Eventos Externos:**
   Se o projeto envolver a leitura de sensores ou a resposta a eventos externos, como botões ou sinais, as interrupções podem ser configuradas para lidar com esses eventos assim que ocorrerem, garantindo uma resposta rápida.

   4.5. **Evitar Bloqueios:**
   Em sistemas de tempo real, é crucial evitar bloqueios (delays longos que impedem a execução de outras tarefas). As interrupções podem ser usadas para realizar tarefas assíncronas, permitindo que o programa principal continue sua execução enquanto eventos específicos são tratados em segundo plano.

   4.6. **Otimização do Código:**
   Ao usar interrupções de maneira eficiente, é possível otimizar o código para garantir que tarefas críticas sejam atendidas sem atrasos significativos, mesmo em um ambiente sem um RTOS completo.

Embora o Arduino Uno não seja tradicionalmente associado a sistemas de tempo real complexos, a compreensão e o uso adequado de interrupções podem ajudar a introduzir elementos de tempo real em projetos mais simples, equilibrando as limitações de recursos do microcontrolador. 

### Raspberry Pico:

1. **Dual-Core:**
   - O Raspberry Pico possui dois núcleos ARM Cortex-M0+, permitindo a execução simultânea de tarefas em paralelo. Essa capacidade é benéfica para lidar com operações em tempo real.

2. **Multithreading:**
   - A capacidade de multithreading é útil para implementar sistemas de tempo real mais complexos, onde várias tarefas podem ser executadas concorrentemente.

3. **Temporizadores Avançados:**
   - O Raspberry Pico possui temporizadores avançados que podem ser configurados para gerar interrupções em momentos específicos. Isso é crucial para o cumprimento de prazos em sistemas de tempo real.

4. **PIO (Programmable I/O):**
   - O Pico introduz o conceito de PIO, que permite a implementação de lógica programável para I/O. Isso pode ser aproveitado para controlar periféricos em tempo real de maneira eficiente.

5. **Conectividade:**
   - Se o projeto envolver comunicação sem fio ou conectividade de rede, o Pico oferece interfaces que facilitam a implementação de sistemas de tempo real distribuídos.

6. **Suporte a RTOS:**
   - Embora não venha com um RTOS integrado, o Raspberry Pico é capaz de suportar sistemas operacionais em tempo real, como FreeRTOS, que podem ser implementados conforme necessário.

### Considerações Gerais:

1. **Clock e Precisão:**
   - A precisão do relógio interno é crucial em sistemas de tempo real. Certifique-se de que os microcontroladores estão configurados corretamente para garantir tempos precisos.

2. **Gerenciamento de Interrupções:**
   - Ambos os microcontroladores exigem um gerenciamento eficiente de interrupções para garantir respostas rápidas a eventos externos.

3. **Otimização de Código:**
   - A otimização de código é essencial para garantir a eficiência no uso dos recursos limitados do microcontrolador, especialmente em sistemas de tempo real.

4. **Testes de Latência:**
   - Realize testes para medir a latência do sistema, garantindo que as tarefas críticas sejam concluídas dentro dos prazos especificados.

Ao projetar sistemas de tempo real com Arduino Uno ou Raspberry Pico, é crucial equilibrar os requisitos de tempo real com as limitações de recursos específicas de cada microcontrolador.







É ótimo que você esteja pensando em testes práticos para os alunos envolvidos em sistemas embarcados com Arduino Uno e Raspberry Pico, especialmente em um projeto que lê um sensor de umidade da mão humana. Aqui estão alguns testes que podem abranger conceitos importantes de sistemas embarcados:

1. **Teste de Funcionalidade Básica:**
   - Certifique-se de que os microcontroladores estão funcionando corretamente.
   - Execute um programa simples para acender um LED ou exibir uma mensagem no console serial.

2. **Teste do Sensor de Umidade:**
   - Verifique se o sensor de umidade está conectado corretamente ao microcontrolador.
   - Implemente um código para ler os valores do sensor e exibi-los no console serial.
   - Realize medições com diferentes níveis de umidade para garantir que o sensor esteja respondendo corretamente.

3. **Teste de Comunicação Serial:**
   - Se estiver usando o Arduino Uno, teste a comunicação serial entre o microcontrolador e o computador. Certifique-se de que é possível enviar e receber dados pelo console serial.
   - No Raspberry Pico, teste a comunicação serial via USB ou UART.

4. **Teste de Alimentação:**
   - Avalie a eficiência do sistema alimentando-o com diferentes fontes de energia.
   - Verifique se o sistema responde de maneira adequada a flutuações de energia.

5. **Teste de Consumo de Energia:**
   - Meça o consumo de energia do sistema em diferentes estados (por exemplo, em espera, em execução).
   - Otimize o código para minimizar o consumo de energia, se possível.

6. **Teste de Interrupções:**
   - Implemente interrupções para lidar com eventos específicos, como pressionar um botão.
   - Verifique se as interrupções estão sendo tratadas corretamente.

7. **Teste de Conectividade (Raspberry Pico):**
   - Se o Raspberry Pico estiver conectado à rede, teste a comunicação por meio de protocolos como MQTT ou HTTP.
   - Implemente um servidor simples no Raspberry Pico para interagir com ele remotamente.

8. **Teste de Desempenho:**
   - Avalie o desempenho do código em termos de velocidade de leitura do sensor e resposta a eventos.

9. **Teste de Tolerância a Falhas:**
   - Simule condições de falha (como desconexão temporária do sensor) e observe como o sistema lida com essas situações.

10. **Teste de Armazenamento (Raspberry Pico):**
    - Se estiver utilizando o Raspberry Pico, teste a leitura e escrita em dispositivos de armazenamento, como uma unidade flash.

Lembre-se de documentar os resultados de cada teste, analisar possíveis problemas e otimizar o código conforme necessário. Esses testes não apenas ajudarão a verificar a funcionalidade do projeto, mas também proporcionarão uma compreensão prática dos conceitos de sistemas embarcados.
