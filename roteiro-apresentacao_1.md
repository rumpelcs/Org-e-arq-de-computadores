# Roteiro — Injeção Eletrônica e Sistemas Embarcados
*(apresentação de ~7-8 minutos, 9 slides)*

---

## Slide 1 — Capa
**Tempo sugerido: ~20s**

- Boa tarde/noite a todos. O trabalho de hoje é sobre **Injeção Eletrônica e Sistemas Embarcados**, da disciplina de Organização e Arquitetura de Computadores, do professor Alessandro Mainardi.
- Trabalho apresentado por Gabriel Rumpel e José Veronez.

---

## Slide 2 — O que é um sistema embarcado?
**Tempo sugerido: ~1min15**

- Um **sistema embarcado** é um sistema de computação — hardware e software juntos — projetado para executar **uma função específica e dedicada**, quase sempre embutido dentro de um equipamento maior. É diferente de um computador de uso geral, como um notebook, que roda dezenas de programas diferentes para finalidades diferentes.
- Características principais:
  - **Dedicado**: nasceu para fazer uma tarefa, e só essa tarefa, muito bem feita;
  - **Tempo real**: precisa responder dentro de prazos rígidos — um atraso pode significar falha de segurança;
  - **Recursos limitados**: processador, memória e energia são dimensionados apenas para o necessário, reduzindo custo e consumo;
  - **Geralmente formado por um microcontrolador**: um único chip que já reúne processador, memória e portas de entrada/saída, ao contrário de um PC que separa CPU, RAM e periféricos.
- Exemplos do dia a dia, para fixar o conceito: o controlador de um micro-ondas, um marca-passo, o sistema de freios ABS, uma smartband, roteadores Wi-Fi, controladores industriais — e, como veremos, a central que comanda a injeção de combustível do seu carro.

---

## Slide 3 — Sistemas embarcados no automóvel
**Tempo sugerido: ~1min**

- Um carro moderno não tem só uma "central eletrônica" — ele é uma rede de **dezenas de sistemas embarcados** conversando entre si, cada um dedicado a uma função: a central do motor, a central de câmbio, o módulo de airbag, o ABS/ESC (controle de estabilidade), o painel digital, o sistema de infotainment.
- Essas centrais trocam informações por redes internas, como o barramento **CAN (Controller Area Network)**, criado justamente para permitir que dezenas de sistemas embarcados de um veículo conversem de forma rápida e confiável.
- Dentro desse ecossistema, vamos focar em uma das mais importantes: a **central de injeção eletrônica**, responsável por controlar o funcionamento do motor.

---

## Slide 4 — Por que a injeção eletrônica é um sistema embarcado? Como ela funciona?
**Tempo sugerido: ~1min45**

- A **ECU** (Engine Control Unit / Central de Injeção) é um exemplo perfeito de sistema embarcado: um computador dedicado, com microcontrolador próprio, cuja única missão é controlar o motor em tempo real.
- **Como ela funciona**, em ciclo contínuo, repetido milhares de vezes por segundo:
  1. **Sensores** captam o estado do motor: rotação (RPM), pressão no coletor de admissão (MAP), posição da borboleta de aceleração (TPS), temperatura do motor e do ar, e a sonda lambda (O2), que mede o oxigênio no escapamento;
  2. A **ECU processa** esses dados, cruzando-os com mapas de injeção e ignição gravados em memória, e calcula o tempo exato de abertura dos bicos injetores e o ponto ideal da centelha;
  3. Os **atuadores** — bicos injetores e bobinas de ignição — executam o comando, entregando combustível pressurizado e faísca no instante certo.
- Esse processo é uma **malha fechada de controle**: a sonda lambda informa o resultado da queima, e a ECU ajusta a próxima injeção com base nesse retorno — um verdadeiro sistema de controle em tempo real, característica central de qualquer sistema embarcado.
- Existem diferentes arquiteturas de injeção: **monoponto** (um único bico central, mais simples e antiga), **multiponto** (um bico por cilindro, o padrão atual) e **injeção direta** (o combustível é injetado diretamente na câmara de combustão, com altíssima pressão, usada em motores mais modernos e eficientes).
- **Para que ela serve**: garantir a mistura ideal de ar e combustível em qualquer condição de uso — partida a frio, marcha lenta, aceleração forte — otimizando três frentes ao mesmo tempo: **potência, consumo de combustível e emissões de poluentes**.

---

## Slide 5 — Um pouco de história
**Tempo sugerido: ~1min**

- Até os anos 80, a maioria dos motores usava **carburador**, um sistema puramente mecânico que misturava ar e combustível sem nenhum controle eletrônico — impreciso e pouco eficiente.
- A partir das décadas de 1970-1980, a pressão por **normas de emissão de poluentes** mais rígidas e pela eficiência no consumo empurrou a indústria para sistemas eletrônicos de injeção, capazes de controlar a mistura com muito mais precisão.
- Com a eletrônica embarcada vieram também os sistemas de **autodiagnóstico (OBD)**, que monitoram falhas do motor em tempo real — outra função tipicamente embarcada.
- Hoje, praticamente 100% dos veículos novos usam injeção eletrônica, e essa mesma lógica se espalhou para motos, geradores e motores estacionários.

---

## Slide 6 — FuelTech: como começaram
**Tempo sugerido: ~1min**

- A **FuelTech** é uma empresa brasileira, fundada com foco no mercado de **performance automotiva e motorsport** — preparação de motores para competição.
- No início, os produtos eram **módulos de injeção standalone**: centrais independentes, sem tela, que substituíam a eletrônica original de fábrica em carros preparados, permitindo controlar motores turbinados, com nitro ou etanol, fora do que a ECU de fábrica suportava.
- A programação era feita conectando a central a um **notebook**, ajustando manualmente os mapas de injeção e ignição — um trabalho voltado a preparadores e equipes de competição, não ao consumidor comum.
- Essa fase inicial construiu a reputação da marca dentro do meio do automobilismo brasileiro e, depois, internacional.

---

## Slide 7 — FuelTech: como estão hoje
**Tempo sugerido: ~1min**

- As linhas atuais, como **FT450, FT550 e FT600**, evoluíram muito em relação aos primeiros módulos:
  - **Display integrado** colorido, mostrando dados do motor em tempo real direto no painel do carro;
  - **Sonda de oxigênio wideband embutida**, sem precisar de módulo externo separado;
  - Controle avançado de **turbo (boost)**, **câmbio automatizado** e sistemas de **nitro**;
  - Configuração e monitoramento por **aplicativo de celular**, facilitando ajustes finos;
  - **Datalogger** completo, para registrar e analisar o comportamento do motor em cada volta ou arrancada.
- A empresa também expandiu para **acessórios eletrônicos completos** (câmbio, telas de performance, sensores) e hoje tem presença em competições e mercados fora do Brasil, mantendo o mesmo princípio: uma central de injeção como um sistema embarcado dedicado e de altíssima performance.

---

## Slide 8 — Resumo
**Tempo sugerido: ~45s**

- Recapitulando os pontos principais:
  - Sistema embarcado = hardware + software dedicados a uma função específica, em tempo real, com recursos limitados;
  - O carro moderno é uma rede de vários sistemas embarcados conectados por redes como o CAN;
  - A ECU de injeção é um exemplo clássico: sensores → processamento → atuadores, em malha fechada;
  - A eletrônica embarcada substituiu o carburador por precisão, eficiência e menor emissão de poluentes;
  - A FuelTech ilustra bem essa evolução: de módulos simples de competição para centrais completas, com tela, wideband, câmbio e app.

---

## Slide 9 — Encerramento / Dúvidas
**Tempo sugerido: ~15s + tempo de perguntas**

- Esse slide repete a estrutura da capa, agora abrindo espaço para perguntas.
- Fala de encerramento: "Espero ter deixado claro por que a injeção eletrônica é um dos exemplos mais presentes de sistema embarcado no nosso dia a dia. Fico à disposição para dúvidas."
- Abrir para perguntas da plateia.

---

### Observações gerais
- Tempo total estimado: **~7 a 8 minutos** de fala corrida (dentro da faixa de 5-10 min pedida), sem contar perguntas.
- Slides 4, 6 e 7 são os mais densos — reserve mais tempo e fale com calma neles.
- Slides 1, 3, 8 e 9 são mais curtos — bons pontos para recuperar o ritmo.
