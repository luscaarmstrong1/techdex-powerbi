# TECHDEX 1.0 — Guia de Metodologia e Auditoria Técnica

## 1. Princípios Éticos e Rigor de Coleta
1. **Verificabilidade Absoluta**: Nenhuma especificação técnica, frequência de rádio, consumo ou contagem de pinos foi inventada ou estimada por extrapolação cega.
2. **Fontes Primárias Obrigatórias**: Prioridade absoluta para datasheets emitidos por fabricantes líderes (Espressif, STMicroelectronics, Raspberry Pi Ltd, Arduino LLC, Semtech, Bosch Sensortec, Texas Instruments, Microchip, Nordic Semi).
3. **Diferenciação Estrita entre Chip, Módulo e Placa**:
   - *Chip / SoC*: O silício individual (ex: ESP32-D0WD-V3, ATmega328P).
   - *Módulo Eletrônico*: O chip montado sobre PCB com componentes de desacoplamento, cristal e blindagem (ex: ESP-WROOM-32, RFM95W).
   - *Placa de Desenvolvimento*: O ecossistema completo com regulador de tensão (LDO/Buck), conversor USB-Serial (CP2102/CH340/FT232) e conectores pinheader (ex: ESP32 DevKit v1, Arduino UNO R3).

---

## 2. Padrões de Normalização Elétrica e Térmica
- **Tensão de Alimentação da Placa vs Nível Lógico do GPIO**:
  - *Tensão de Alimentação*: Intervalo aceito pelo pino VIN ou conector jack (ex: 7V a 12V no Arduino UNO).
  - *Nível Lógico de E/S*: Tensão de operação efetiva dos sinais digitais do barramento (3.3V para ESP32/Pico/STM32 vs 5.0V para Arduino UNO/Mega). É explicitamente documentado que alimentar o ESP32 com 5V via USB não torna suas portas tolerantes a 5V.
- **Corrente em Modo de Suspensão (Deep Sleep)**:
  - Todas as correntes de sleep registradas explicitam condições reais: alimentação nominal a 3.3V com apenas o RTC ou coprocessador ULP em repouso. Correntes em placas com reguladores LDO passivos consideram o consumo quiescente do regulador.
- **Sensibilidade e Potência LoRa**:
  - Distinção explícita entre modulação LoRa (camada física RF com spreading factor SF5 a SF12) e protocolo de rede em estrela LoRaWAN (camada MAC).
