# ⚛️ Simulação de Reator Nuclear com Arduino Uno R3

> Projeto escolar desenvolvido na disciplina de **Sistemas Embarcados** do Curso Técnico de Desenvolvimento de Sistemas — ETEC Basilides de Godoy (CEETEPS / Paula Souza) · São Paulo · 2026

---

## 👥 Integrantes

| Nome | Responsabilidade |
|---|---|
| **Cauã Martins** | Coordenação, loop principal e lógica de estados |
| **Davy Lucas** | Display LCD 16x2 e formatação de informações |
| **Enzo Chaves** | Montagem do circuito no TinkerCAD |
| **Guilherme Coelho** | Sistema de alarmes — LEDs e buzzer |
| **Gustavo Garcia** | Documentação ABNT e testes |

---

## 📋 Sobre o Projeto

Este repositório contém a simulação funcional de um sistema de monitoramento de reator nuclear, desenvolvida inteiramente na plataforma **TinkerCAD** utilizando um **Arduino Uno R3** programado em **C++**.

A ideia central foi representar, de forma didática e simplificada, a lógica de monitoramento e controle presente em sistemas industriais reais: leitura contínua de sensores, exibição de dados em tempo real e acionamento automático de alertas quando variáveis críticas saem dos limites seguros.

---

## 🎯 Objetivos

**Geral:** Desenvolver uma simulação de monitoramento de reator nuclear com leitura de sensores, display LCD e sistema de alertas visuais e sonoros.

**Específicos:**
- 🔌 Montar o circuito eletrônico virtualmente no TinkerCAD
- 🌡️ Ler o potenciômetro e calcular a temperatura do reator
- 📟 Exibir temperatura, potência e status no LCD 16x2 em tempo real
- 🚦 Implementar indicação por LEDs (verde / amarelo / vermelho) e buzzer
- 🔘 Criar botões para ligar/desligar o reator e para emergência (reset)
- 📄 Documentar todo o processo em relatório técnico (normas ABNT)

---

## 🛠️ Tecnologias e Ferramentas

![Arduino](https://img.shields.io/badge/Arduino-Uno_R3-00979D?style=flat&logo=arduino&logoColor=white)
![C++](https://img.shields.io/badge/Linguagem-C++-00599C?style=flat&logo=c%2B%2B&logoColor=white)
![TinkerCAD](https://img.shields.io/badge/Simulador-TinkerCAD-FF6D00?style=flat)

| Ferramenta | Uso |
|---|---|
| **Arduino Uno R3** | Microcontrolador principal (ATmega328P, 16 MHz) |
| **C++** | Linguagem de programação do firmware |
| **TinkerCAD Circuits** | Simulação virtual do circuito |
| **LiquidCrystal (lib)** | Controle do display LCD |

---

## 🧩 Componentes do Circuito

| Componente | Qtd. | Função no Projeto |
|---|:---:|---|
| Arduino Uno R3 | 1 | Processa leituras e controla os demais componentes |
| Display LCD 16x2 | 1 | Exibe temperatura, potência e status em tempo real |
| Potenciômetro 10 kΩ | 1 | Simula o nível de potência do reator (0–100%) |
| LED Verde (5mm) | 1 | Operação normal — abaixo de 70 °C |
| LED Amarelo (5mm) | 1 | Estado de alerta — entre 70 °C e 89 °C |
| LED Vermelho (5mm) | 1 | Estado crítico — 90 °C ou mais |
| Buzzer passivo | 1 | Alarme sonoro (1000 Hz) no estado crítico |
| Push Button | 2 | Ligar/desligar e desligamento de emergência |
| Resistor 220 Ω | 3 | Limitação de corrente nos LEDs |
| Protoboard | 1 | Organização das conexões |
| Fios de conexão | — | Interligação dos componentes |

---

## 🚦 Estados do Sistema

```
Temperatura < 70 °C  →  🟢 LED VERDE   — Operação Normal
70 °C ≤ Temp < 90 °C →  🟡 LED AMARELO — Estado de Alerta
Temperatura ≥ 90 °C  →  🔴 LED VERMELHO + 🔊 BUZZER — Estado Crítico
Reator desligado     →  ⚫ Todos os LEDs apagados — Inativo
```

---

## 📁 Estrutura do Repositório

```
📦 reactor-core-arduino
 ┣ 📂 src
 ┃ ┗ 📄 reator_nuclear.ino     # Código-fonte principal (C++)
 ┣ 📂 docs
 ┃ ┗ 📄 reator_nuclearABNT.docx # Relatório técnico (normas ABNT)
 ┗ 📄 README.md
```

---

## 💻 Código-Fonte

O firmware foi escrito em **C++** para Arduino Uno R3, utilizando a biblioteca `LiquidCrystal`. O programa é dividido em funções separadas para facilitar a leitura e manutenção:

| Função | Descrição |
|---|---|
| `simularTemperatura(pot)` | Calcula a temperatura a partir do nível de potência |
| `obterStatus(temp)` | Retorna o status textual do reator conforme a temperatura |
| `atualizarAlarmes(temp)` | Aciona os LEDs e o buzzer conforme o estado |
| `atualizarLCD(temp, pot)` | Atualiza as informações exibidas no display |
| `setup()` | Inicializa pinos, LCD e comunicação serial |
| `loop()` | Lê sensores, verifica botões e chama as demais funções |

> 📂 Veja o código completo em [`src/reator_nuclear.ino`](src/reator_nuclear.ino)

---

## 🔌 Esquema de Conexões (Resumo)

| Componente | Pino / Terminal | Conectado a |
|---|---|---|
| LCD RS | — | Pino digital 12 |
| LCD EN | — | Pino digital 11 |
| LCD D4–D7 | — | Pinos digitais 5, 4, 3, 2 |
| Potenciômetro | Pino central | Pino analógico A1 |
| LED Verde | Anodo (+) | Pino digital 6 (via 220 Ω) |
| LED Amarelo | Anodo (+) | Pino digital 7 (via 220 Ω) |
| LED Vermelho | Anodo (+) | Pino digital 8 (via 220 Ω) |
| Buzzer | Positivo (+) | Pino digital 9 |
| Botão INICIAR | Terminal 1 | Pino digital 10 (INPUT_PULLUP) |
| Botão RESET | Terminal 1 | Pino digital 13 (INPUT_PULLUP) |

---

## ▶️ Como Simular

1. Acesse [tinkercad.com](https://www.tinkercad.com) e faça login
2. Importe ou recrie o circuito conforme o esquema de conexões acima
3. Cole o código de [`src/reator_nuclear.ino`](src/reator_nuclear.ino) no editor do TinkerCAD
4. Clique em **"Iniciar Simulação"**
5. Use o **potenciômetro** para variar a potência e observar os estados do reator
6. Pressione o **botão INICIAR** para ligar/desligar o reator
7. Pressione o **botão RESET** para simular um desligamento de emergência
8. Acompanhe a saída de dados também pelo **Serial Monitor** (9600 baud)

---

## 📊 Resultados Esperados

- ⚫ Reator desligado → LCD exibe `"REATOR INATIVO"`
- 🟢 Temp. < 70 °C → LED verde aceso, sistema em silêncio
- 🟡 70 °C ≤ Temp. < 90 °C → LED amarelo aceso, estado de alerta
- 🔴 Temp. ≥ 90 °C → LED vermelho + alarme sonoro (1000 Hz), estado crítico
- 🔘 Botão RESET → desliga imediatamente o reator e silencia todos os alertas
- 🖥️ Serial Monitor → atualização a cada 500 ms com temperatura, potência e estado

---

## 🔭 Melhorias Futuras

- [ ] Registro de eventos com data e hora via módulo RTC
- [ ] Tela gráfica com histórico de temperatura ao longo do tempo
- [ ] Teste e validação com componentes físicos reais
- [ ] Comunicação via Bluetooth para monitoramento remoto

---

## 📚 Referências

- ARDUINO. *Arduino Uno Rev3*. Disponível em: https://store.arduino.cc/products/arduino-uno-rev3
- AUTODESK. *TinkerCAD Circuits*. Disponível em: https://www.tinkercad.com
- GLASSTONE, S.; SESONSKE, A. *Nuclear Reactor Engineering*. 4. ed. New York: Springer, 2004.
- MONK, S. *Programming Arduino: Getting Started with Sketches*. 3. ed. New York: McGraw-Hill, 2022.
- ABNT. *NBR 14724*: Trabalhos acadêmicos — Apresentação. Rio de Janeiro: ABNT, 2011.

---

<div align="center">

Desenvolvido com ⚡ por **Cauã · Davy · Enzo · Guilherme · Gustavo**  
ETEC Basilides de Godoy · Curso Técnico de Desenvolvimento de Sistemas · 2026

</div>
