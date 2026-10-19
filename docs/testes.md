# TECHDEX 1.0 — Roteiro de Testes e Validação de Aceitação

## 1. Matriz de Testes Executados

| ID | Cenário de Teste | Critério de Aceitação | Resultado | Evidência / Observações |
|---|---|---|---|---|
| **TC-01** | Filtrar somente dispositivos da família ESP32 | O catálogo deve restringir a exibição aos SoCs e placas da linhagem Espressif (ESP32, S2, S3, C3, C6). | **APROVADO** | Filtro funcional via coluna `Familia` e segmentação dinâmica. |
| **TC-02** | Filtrar sensores ambientais (Categoria 3) | Apenas sensores físicos (BME280, BMP280, DHT22, SCD40) devem constar na lista. | **APROVADO** | 15 sensores auditados com dados de temperatura e umidade. |
| **TC-03** | Abrir ficha técnica do ESP32-S3 (TDX-0002) | Exibir imagem oficial, núcleos LX7, suporte a instruções vetoriais AI, 45 GPIOs e datasheet. | **APROVADO** | Link para documentação oficial da Espressif validado. |
| **TC-04** | Abrir ficha técnica do sensor BME280 (TDX-0030) | Exibir barramentos I2C/SPI, resolução de 20 bits e datasheet da Bosch Sensortec. | **APROVADO** | Distinção explícita entre o chip BME280 e módulos com regulador de 5V. |
| **TC-05** | Comparar duas placas: Arduino UNO R3 vs ESP32 DevKit | Confrontar especificações elétricas e de processamento lado a lado na Arena de Comparação. | **APROVADO** | Evidencia: AVR 8-bit @ 16MHz (UNO) vs Xtensa LX6 dual-core @ 240MHz (ESP32); Tensão lógica 5V (UNO) vs 3.3V (ESP32). |
| **TC-06** | Comparar dispositivos de categorias distintas (Microcontrolador vs Sensor) | Não gerar falsos escores de superioridade universal. | **APROVADO** | DAX isola atributos compatíveis e sinaliza campos sem equivalência lógica direta. |
| **TC-07** | Acessar datasheets oficiais | Todos os hyperlinks de datasheets devem apontar para os domínios autênticos dos fabricantes. | **APROVADO** | Links diretos para Espressif, Raspberry Pi, ST, TI, Semtech, Bosch e Microchip. |
| **TC-08** | Acoplamento elétrico: ESP32 + HC-SR04 | Sinalizar perigo de nível de tensão no pino Echo de 5V. | **APROVADO** | Status: **Compatibilidade Condicionada** com alerta de proteção e divisor de tensão. |
| **TC-09** | Adicionar novo dispositivo e atualizar base | Novo registro inserido em CSV deve refletir no modelo após atualização. | **APROVADO** | Script `build_datasets.py` compilou 85 itens com integridade referencial total. |
| **TC-10** | Limpeza de filtros de navegação | Restaurar a listagem completa de 85 itens e os 4 KPIs agregados do topo. | **APROVADO** | Mecanismo de reset de contexto validado. |

---

## 2. Resumo de Cobertura da Base
- **Total de Dispositivos Auditados**: 85 (Superou a meta mínima inicial de 80).
- **Categorias Tecnológicas Cobertas**: 8 macrocategorias completas.
- **Fabricantes Oficiais Registrados**: 26 fabricantes internacionais com sedes e sites oficiais.
- **Protocolos e Barramentos Mapeados**: 19 tecnologias sem fio, seriais, industriais e automotivas.
- **Relações de Especificação Fato**: 1.275 registros detalhados com rastreabilidade em datasheet.
