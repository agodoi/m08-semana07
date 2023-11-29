# Validação do Sistema

O principal objetivo deste encontro é validar a integração do sistema embarcado com o projeto desenvolvido. Os subsistemas embarcados e a validação da arquitetura de comunicação é realizada durante este encontro. Conceitos de aprimoramento de desenvolvimento embarcado e formas distintas de realizada a integração do sistema também são realizadas nesta interação. Espera-se que os estudantes consigam construir testes de integração da plataforma embarcada com o restante do projeto desenvolvido. Neste encontro serão abordados: Testes em sistemas embarcados; Testes para sistemas de comunicação; Tópicos avançados de sistemas embarcados.

Algumas questões a serem respondidas nessa instrução:

## Seu projeto é um sistema RTO?

## Como testar o seu projeto do ponto de vista do hardware?

## Como ler mouse e teclado na tela do Windows?

## Cuidados com a ponderada dessa semana.

## Você estará pronto para o Kahoot (hahaha)?

## Assuntos relacionados

- Atuadores

- Dispositivos lógico-programáveis

- Energia em sistemas embarcados

- Interfaces de comunicação

- Microcontroladores

- Programação de microcontroladores

- Segurança em sistemas embarcados

- Sensores analógicos e digitais


## Revisando alguns conceitos vistos no autoestudo

### O que são Sistemas Embarcados?

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

### O que são Sistemas RTO?

Sistemas de Tempo Real (RTOS) são projetados para responder a eventos em tempo real, garantindo que determinadas tarefas sejam concluídas dentro de prazos predefinidos. 

Por exemplo, considerando os dois microcontroladores abordados nesse módulo:

#### Arduino Uno:

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

**Portanto, o GREG é um microcontrolador limitado, sem condições de memória para embarcar qualquer tipo de solução complexa nesse projeto. Além disso, seu chip UART foi modificado e por isso, ele não aceita novas gravações de código-fonte Arduino**. Assista esse [Short](https://www.youtube.com/watch?v=AhRiUZzxyBI) para melhor entender o Arduino Uno no quesito microPython.


#### Raspberry Pico:

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
   - Embora não venha com um RTOS integrado, o Raspberry Pico é capaz de suportar sistemas operacionais em tempo real, como FreeRTOS, que podem ser implementados conforme necessário. Esse [Vídeo](https://www.youtube.com/watch?v=vVVphE1ycpc) de mostra o caminho. 

### Considerações Gerais em sistemas RTO:

1. **Clock e Precisão:**
   - A precisão do relógio interno é crucial em sistemas de tempo real. Certifique-se de que os microcontroladores estão configurados corretamente para garantir tempos precisos.

2. **Gerenciamento de Interrupções:**
   - Ambos os microcontroladores exigem um gerenciamento eficiente de interrupções para garantir respostas rápidas a eventos externos.

3. **Otimização de Código:**
   - A otimização de código é essencial para garantir a eficiência no uso dos recursos limitados do microcontrolador, especialmente em sistemas de tempo real.

4. **Testes de Latência:**
   - Realize testes para medir a latência do sistema, garantindo que as tarefas críticas sejam concluídas dentro dos prazos especificados.

Ao projetar sistemas de tempo real com Arduino Uno ou Raspberry Pico, é crucial equilibrar os requisitos de tempo real com as limitações de recursos específicas de cada microcontrolador.

## Como testar o seu projeto do ponto de vista do hardware?


1. **Teste de Funcionalidade Básica:**
   - Certifique-se de que o microcontrolador estão funcionando minimamente conectando-o na porta USB, e vendo LEDs acenderem. Caso não os veja, o cabo USB pode estar quebrado internamente;
   - Verifique a condutividade dos circuitos de cada quadrante do tapete com a ajuda de um multímetro. Coloque-o na escala de condutividade (onde ao encostar as duas pontas de prova, o multímetro emite um apito) e encoste uma ponta num borne vermelho ou preto afixados na extremidade do tapete e a outra ponta do multímetro, você encosta em várias partes do fio de cobre exposto no respectivo quadrante. O multímetro deve apitar indicando que a corrente elétrica está passando normalmente.

2. **Teste do Tapete com Greg:**
   - Plug o Greg Maker na sua porta USB do seu PC;
   - Plug uma ponta do cabo banana-jacaré no quadrante Q1 do seu tapete e a outra ponta, plug na seta para cima do mouse no Greg;
   - Vista a pulseira anti-estática no seu pulso e plugue-a no GND do Greg Maker;
   - Toque suavemente na textura do Q1 do seu tapete e seu mouse deve se mexer para cima na sua tela;
   - Faça o mesmo procedimento nos quadrante Q2, Q3, Q4 e A5.
     
3. **Teste de Comunicação Serial:**
   - Se o teste do item (2) ocorreu com sucesso, significa que sua comunicação Serial via USB/UART está funcionando corretamente;
   - Caso não, tente trocar o cabo USB ou verificar outros quadrantes do seu tapete.

4. **Teste de Alimentação:**
   - Se sua porta USB não estiver com eficiência no sistema alimentação, o Greg não vai se comportar adequadamente;
   - Nesse caso, troque de porta USB ou até o PC;
   - Flutuações de energia interferem no bom funcionamento do microcontrolador.

5. **Teste de Consumo de Energia:**
   - O microcontrolador possui níveis diferentes de consumo de corrente elétrica a depender da carga computacional exigido a ele;
   - Carga computacional alta requer níveis maiores de consumo de corrente elétrica;
   - Você pode medir o consumo de energia do sistema em diferentes estados, por exemplo, em espera, em execução;
   - Você deve colocar seu multímetro na escala de corrente e colocá-lo em série na porta USB. Como não temos cabos especiais para isso, deixo aqui essa sugestão, mas não vamos praticá-lo agora.

6. **Teste de Interrupções:**
   - No caso do Greg Maker não é possível alterar seu código, mas se fosse o Raspberry Pico, implemente interrupções para lidar com eventos específicos, como pressionar um botão;
   - Verifique se as interrupções estão sendo tratadas corretamente imprimindo mensagens na Serial todas as vezes que você pressiona o botão.

7. **Teste de Conectividade (Raspberry Pico):**
   - O Greg não tem WiFi, mas se fosse o Raspberry Pico, faça testes da comunicação WiFi por meio de request do protocolos como MQTT ou HTTP;
   - Implemente um servidor simples no Raspberry Pico para interagir com ele remotamente;

8. **Teste de Desempenho:**
   - Avalie o desempenho do código em termos de velocidade de leitura do sensor e resposta a eventos.

9. **Teste de Tolerância a Falhas:**
   - Simule condições de falha (como desconexão temporária de um sensor) e observe como o sistema lida com essas situações;
   - Ele trava ou continua funcionando adequadamente com o retorno do sensor?
   - A falta do sensor gera ruídos inesperados no sistema ou comportamentos estranhos?

10. **Teste de Armazenamento (Raspberry Pico):**
    - O Greg Maker não tem memória externa. Mas se estiver utilizando o Raspberry Pico, teste a leitura e escrita em dispositivos de armazenamento, como uma unidade (shield) de cartão microSD.

Esses testes não apenas ajudarão a verificar a funcionalidade do projeto, mas também proporcionarão uma compreensão prática dos conceitos de sistemas embarcados.


## Como detectar movimentos do mouse e teclado?

[Biblioteca Pygame](https://www.geeksforgeeks.org/how-to-get-keyboard-input-in-pygame/)

[Exemplo Mouse e Teclado](http://www.codingwithruss.com/pygame/how-to-get-mouse-input-in-pygame)

[Biblioteca pynput](https://pynput.readthedocs.io/en/latest/)

[Vídeo 1 - Lendo Mouse](https://www.youtube.com/watch?v=eK7p1e8-6jU)

[Vídeo 2 - Lendo Teclado](https://www.youtube.com/watch?v=MYQnqyVqCDc)

### Exemplo de código em python

### Atividade da Aula


Desenvolva um código em Python que detecte o movimento do mouse ou a tecla [ENTER] ou barra de espaço. Se você o fizer e apresentar ao professor, vai ganhar um voucher valendo um Bis


## Cuidados com a ponderada dessa semana

A ponderada dessa semana está com o título **PROTOCOLOS: UART - I2C - SPI - Serial communications**

**Pergunta:**

Elabore uma solução usando Raspberry Pi Pico W que use um sensor disponível com comunicação I2C, e que demonstre seus dados no terminal da IDE de comunicação adotada.

**Barema:**

No entregável anterior, é provável que sua dupla tenha usado um sensor I2C. Se não usou, está na hora! E se já usou, parabéns! Você já fez uma parte da entrega dessa semana. O aluno deve elaborar um documento descritivo que detalhe seu embarcado, em especial:

a) Diagrama de blocos com a pinagem entre microcontrolador e sensor (nesse item, você deve elaborar do zero uma documentação bacana tratando desse item);

b) Descritivo de como funciona a comunicação I2C entre microcontrolador e sensor e a comunicação serial entre microcontrolador e PC (esse item já foi abordado no primeiro entregável, mas lá estava falando do Arduino Uno. Aqui precisa ser do Raspberry Pi Pico. Dependendo da sua documentação, você vai aproveitar quase tudo);

c) Gravar um vídeo-pitchl explicativo, técnico, claro e objetivo, de no mínimo 3 e máximo 5 minutos que demonstre claramente o funcionamento do microcontrolador e sensor, além de demonstrar a impressão de dados no terminal da IDE usada para a comunicação com o Raspberry. Esse vídeo você provavelmente já possui, então você pode aproveitá-lo desde que seu conteúdo esteja correto ou senão, reeditá-lo para concorrer à nota máxima.
