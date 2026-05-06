# 📘 Apostila de Eletrônica Básica
## Curso Técnico em Eletrônica — Nível Iniciante ao Intermediário

> **Versão:** 1.0 | **Idioma:** Português do Brasil | **Nível:** Técnico/Profissionalizante  
> **Normas de Referência:** ABNT NBR 5410, IEC 61131, IEC 61800, INMETRO

---

## 📋 Sumário

1. [Introdução: Eletricidade vs Eletrônica](#cap1)
2. [História da Eletricidade e Eletrônica](#cap2)
3. [Aplicações da Eletrônica](#cap3)
4. [Estrutura Atômica e Materiais](#cap4)
5. [Tensão, Corrente e Resistência](#cap5)
6. [Lei de Ohm e Leis de Kirchhoff](#cap6)
7. [Componentes Passivos](#cap7)
8. [Semicondutores e Dopagem](#cap8)
9. [Diodos: Tipos e Aplicações](#cap9)
10. [Transistores BJT e MOSFET](#cap10)
11. [Amplificadores Operacionais](#cap11)
12. [Eletrônica Digital e Portas Lógicas](#cap12)
13. [Referências, Recursos e Links YouTube](#referencias)

---

<a name="cap1"></a>
## 📗 Capítulo 1 — Introdução: Eletricidade vs Eletrônica

### 1.1 O que é Eletricidade?

A **eletricidade** é o conjunto de fenômenos físicos relacionados com a presença e o movimento de cargas elétricas. Ela é a base da civilização moderna: ilumina cidades, move motores industriais, alimenta hospitais e faz turbinas gerarem energia.

> 💡 **Analogia:** Pense na eletricidade como a estrada e o caminhão de carga — ela move grandes quantidades de energia de um ponto ao outro.

**Características da Eletricidade de Potência:**
- Opera em tensões de 127 V / 220 V (residencial) até 500 kV (linhas de transmissão)
- Correntes de dezenas de ampères até quiloampères
- Frequência de 60 Hz no Brasil (padrão ANEEL)
- Potências de 1 kW a 1 GW (usinas)

### 1.2 O que é Eletrônica?

A **eletrônica** é a ciência e tecnologia que estuda o controle do fluxo de elétrons em materiais semicondutores para processar, amplificar, gerar, transmitir e armazenar **informação**.

> 💡 **Analogia:** Se a eletricidade é a estrada, a eletrônica é o sistema de semáforos e GPS que **controla** e **direciona** o tráfego com precisão.

**Características da Eletrônica de Sinais:**
- Opera em tensões de 0 a 12 V DC (microvolts a 5 V típico)
- Correntes de 1 µA a 100 mA
- Frequências de DC até MHz (áudio, digital, RF)
- Potências de 1 mW a 100 W

### 1.3 Eletrônica de Potência: A Ponte Entre os Dois Mundos

A **eletrônica de potência** é o ramo que combina os princípios da eletrônica com o controle de grandes quantidades de energia elétrica. É a tecnologia por trás dos carros elétricos, painéis solares, inversores e fontes chaveadas.

```
    MUNDO DA ELETRICIDADE          ELETRÔNICA DE POTÊNCIA          MUNDO DA ELETRÔNICA
    ━━━━━━━━━━━━━━━━━━━             ━━━━━━━━━━━━━━━━━━━━━           ━━━━━━━━━━━━━━━━━
    220 VAC / 60 Hz           →    Retificador + IGBT          →    3,3 V / 5 V DC
    Rede Elétrica             →    Inversor Solar               →    Microcontrolador
    Motor Trifásico           →    Inversor de Frequência       →    Controle PID
    1 kW – 1 GW               →    100 W – MW                   →    1 mW – 100 W
```

### 1.4 Estrutura Universal de um Sistema Eletrônico

Todo sistema eletrônico, por mais complexo que seja, segue esta estrutura fundamental:

```
┌──────────┐     ┌─────────────────┐     ┌──────────┐
│  SENSOR  │────▶│  PROCESSAMENTO  │────▶│ ATUADOR  │
│          │     │  (µC / CI / CPU)│     │          │
└──────────┘     └────────┬────────┘     └──────────┘
   Entrada                │                 Saída
   (mundo físico)         ▼              (mundo físico)
                   ┌─────────────┐
                   │    FONTE    │
                   │  REGULADA   │
                   └─────────────┘
```

**Exemplos reais desta estrutura:**

| Sistema | Sensor | Processamento | Atuador |
|---------|--------|---------------|---------|
| Ar-condicionado | Termistor (temperatura) | Microcontrolador | Compressor (motor) |
| Smartphone | Câmera CMOS, acelerômetro | SoC (ARM) | Tela OLED, alto-falante |
| Carro Elétrico | Encoder de velocidade | ECU + IGBT | Motor elétrico |
| Painel Solar | Sensor de tensão/corrente | MPPT (DSP) | Inversor → Rede |

### 1.5 Tabela Comparativa Completa

| Parâmetro | Eletricidade Potência | Eletrônica Sinais | Eletrônica Potência |
|-----------|----------------------|-------------------|---------------------|
| **Potência** | 1 kW – 1 GW | 1 mW – 100 W | 100 W – MW |
| **Tensão** | 127/220 V – 500 kV CA | 0–12 V DC (µV–5 V) | 220 VAC → 48 VDC PWM |
| **Corrente** | 10 A – kA | 1 µA – 100 mA | 1 A – kA (heatsink) |
| **Frequência** | 50/60 Hz | DC–MHz (áudio/digital) | 10–100 kHz comutação |
| **Componentes** | Motores, cabos Cu | Diodos sinal, op-amps, CIs | IGBT, SCR, MOSFET pot. |
| **Eficiência** | 85–95% (I²R) | > 98% | 95–99% (PWM) |
| **Normas** | NBR 5410 | IEC 61131 | IEC 61800 |
| **Exemplos** | Motor 3~ 5 HP | Placa som PC | Inversor solar 10 kW |

### 🎯 Exercícios do Capítulo 1

**1.** Classifique os sistemas abaixo como "Eletricidade", "Eletrônica de Sinais" ou "Eletrônica de Potência":
   - a) Carregador de celular (entrada 220 V, saída 5 V/2 A)
   - b) Amplificador de guitarra (entrada µV do captador, saída 50 W para caixa)
   - c) Linha de transmissão de energia (345 kV, 500 A)
   - d) Controlador de temperatura de forno industrial (PLC + triac)

**2.** Desenhe o diagrama Sensor → Processamento → Atuador para um **sistema de irrigação automática**.

**3.** Por que a eletrônica de potência precisa de dissipadores de calor (heatsinks)?

> 📝 **Gabarito:**  
> 1a) Eletrônica de Potência | 1b) Eletrônica de Sinais | 1c) Eletricidade | 1d) Eletrônica de Potência  
> 3) Mesmo com eficiência de 95–99%, a potência dissipada em calor pode ser significativa (ex: 500 W × 2% = 10 W de calor que deve ser removido para não danificar os componentes).

---

<a name="cap2"></a>
## 📗 Capítulo 2 — História da Eletricidade e Eletrônica

### 2.1 Linha do Tempo: Das Descobertas à Era Digital

```
1600  ▶ William Gilbert: cunha o termo "elétrico"
1752  ▶ Benjamin Franklin: pipa na tempestade → para-raios
1800  ▶ Alessandro Volta: primeira pilha (bateria)
1820  ▶ André-Marie Ampère: relação entre corrente e campo magnético
1827  ▶ Georg Ohm: Lei de Ohm (V = R × I)
1831  ▶ Michael Faraday: indução eletromagnética (gerador, transformador)
1864  ▶ James Maxwell: equações do eletromagnetismo (luz = onda EM)
1876  ▶ Alexander Graham Bell: telefone
1882  ▶ Thomas Edison: primeira usina elétrica CC (New York)
1888  ▶ Nikola Tesla: motor CA bifásico; sistema de transmissão CA
1895  ▶ Guglielmo Marconi: rádio (telegrafía sem fio)
1904  ▶ John Fleming: válvula termiônica (diodo de vácuo)
1906  ▶ Lee de Forest: tríodo de vácuo (primeiro amplificador)
1947  ▶ Bardeen, Brattain, Shockley (Bell Labs): TRANSISTOR 🎉
1958  ▶ Jack Kilby (TI): primeiro circuito integrado
1965  ▶ Gordon Moore: Lei de Moore (transistores dobram a cada 2 anos)
1971  ▶ Intel 4004: primeiro microprocessador comercial (2300 transistores)
1981  ▶ IBM PC: computador pessoal (8088, 4,77 MHz)
1991  ▶ Tim Berners-Lee: World Wide Web
2007  ▶ Apple iPhone: smartphone moderno (SoC ARM + GPU + sensores)
2020  ▶ TSMC 5 nm: 170 bilhões de transistores por cm²
2023  ▶ IA generativa: chips A100/H100 NVIDIA (80 bilhões transistores)
```

### 2.2 A "Guerra das Correntes": CA vs CC

Um dos episódios mais famosos da história da eletricidade foi a disputa entre **Thomas Edison** (corrente contínua - CC) e **Nikola Tesla/George Westinghouse** (corrente alternada - CA) no final do século XIX.

| Aspecto | Thomas Edison (CC) | Nikola Tesla (CA) |
|---------|-------------------|-------------------|
| **Sistema** | Corrente Contínua (DC) | Corrente Alternada (AC) |
| **Tensão** | 110 V (baixa) | Alta tensão transmissão |
| **Transmissão** | Máx ~1,5 km (perdas I²R) | Centenas de km |
| **Transformadores** | Não funcionam em CC | Funcionam perfeitamente |
| **Vencedor?** | ❌ Inviável para longas distâncias | ✅ Padrão mundial até hoje |

> 🎬 **Vídeo Recomendado:** [A Guerra das Correntes — Pirula #197](https://www.youtube.com/watch?v=WUwkFNnnJdA) — explicação didática do conflito histórico.

### 2.3 A Revolução do Transistor

O transistor, inventado em 1947 nos Bell Labs, é considerado **a invenção mais importante do século XX**. Ele substituiu as válvulas termiônicas, que eram frágeis, grandes, quentes e consumiam muita energia.

```
    VÁLVULA TERMIÔNICA (1906)        TRANSISTOR BJT (1947)
    ┌─────────────────────┐          ┌──────────────────┐
    │   Tamanho: ≈ 10 cm  │          │ Tamanho: ≈ 1 cm  │
    │   Consumo: > 5 W    │   →→→    │ Consumo: µW–mW   │
    │   Vida útil: 1000 h │          │ Vida útil: décadas│
    │   Fragilidade: Alta │          │ Robusto, sólido  │
    └─────────────────────┘          └──────────────────┘
    
    CIRCUITO INTEGRADO (1958)        CHIP MODERNO (2023)
    ┌─────────────────────┐          ┌──────────────────────┐
    │   ~10 transistores  │   →→→    │ 170 bilhões transistores│
    │   em 1 cm²          │          │ em 1 cm² (TSMC 3 nm) │
    └─────────────────────┘          └──────────────────────┘
```

### 2.4 Lei de Moore e o Futuro

**Gordon Moore** (cofundador da Intel) observou em 1965 que o número de transistores em um chip dobrava aproximadamente a cada **2 anos**, mantendo o custo constante. Essa observação empírica, conhecida como **Lei de Moore**, orientou a indústria por décadas.

```
    ANO    TRANSISTORES POR CHIP      PROCESSO
    1971   2.300                      10 µm (Intel 4004)
    1979   29.000                     3 µm (Intel 8086)
    1993   3.100.000                  0,8 µm (Intel Pentium)
    2006   291.000.000                65 nm (Intel Core 2)
    2012   1.400.000.000              22 nm (Intel Ivy Bridge)
    2020   11.800.000.000             5 nm (Apple M1)
    2023   92.000.000.000             3 nm (Apple M3 Pro)
```

### 2.5 Tabela Histórica por Décadas

| Década | Eletricidade | Eletrônica | Revolução |
|--------|-------------|------------|-----------|
| **1900** | Redes CA de Tesla | Válvulas (rádio) | 1ª era da informação |
| **1950** | Motores industriais | Transistor/CI | Computadores viáveis |
| **1980** | Redes 500 kV | Microcontroladores + IGBT | Automação/PCs |
| **2000** | Renováveis iniciais | SoCs + Internet | Globalização digital |
| **2020** | Renováveis 1 TW | 3 nm + IA | EVs/IA/5G |
| **2030** | Fusão nuclear? | 1 nm + computação quântica | Singularidade? |

### 🎯 Exercícios do Capítulo 2

**1.** Por que a corrente alternada venceu a corrente contínua para transmissão de energia?

**2.** Qual foi o impacto da invenção do transistor na indústria eletrónica?

**3.** Se a Lei de Moore continuar, em quantos anos o número de transistores por chip quadruplicará?

> 📝 **Gabarito:**  
> 1) Porque transformadores funcionam somente com CA, permitindo elevar a tensão para centenas de kV e reduzir as perdas I²R na transmissão por longas distâncias, depois abaixar para uso seguro.  
> 3) Em 4 anos (duplica a cada 2 anos, logo quadruplica em 4 anos).

---

<a name="cap3"></a>
## 📗 Capítulo 3 — Aplicações da Eletrônica

### 3.1 Áudio

**Função:** Captura, processamento e reprodução de sinais sonoros.

```
    MICROFONE          PRÉ-AMP          PROCESSADOR          AMPLIFICADOR         CAIXA DE SOM
    (Transdutor)  →   (Op-Amp)    →    (DSP/EQ/Efeitos) →   (Classe A/B/D)  →   (Alto-falante)
    Tensão: µV        Ganho: 20-60 dB   Digital 24 bits       1 W – 1000 W        Acústico
```

**Exemplos práticos:**
- **Caixas de som Bluetooth** (SoC + amplificador classe D + bateria Li-ion)
- **Placas de som** (ADC/DAC 24 bits, codec de áudio)
- **Sistemas automotivos** (DSP + amplificadores multicanal)
- **Sistemas de PA** (Public Address) para auditórios e shows

**Componentes chave:**
| Componente | Função | Exemplo |
|-----------|--------|---------|
| Op-Amp | Pré-amplificação | TL071, NE5532 |
| Amp Classe D | Amplificação eficiente | TPA3116, IRS2092 |
| DAC | Digital → Analógico | PCM5102, ES9038 |
| ADC | Analógico → Digital | PCM1808, AK5720 |
| DSP | Processamento de sinal | ADAU1701, STM32 |

**Especificações típicas:**
- Potência: 1 W – 1000 W (fone a sistema de PA)
- Frequência: 20 Hz – 20 kHz (faixa audível humana)
- THD: < 0,1% em sistemas de qualidade profissional
- Relação S/N (SNR): > 90 dB em áudio de qualidade

### 3.2 Vídeo

**Função:** Captura, processamento, transmissão e exibição de imagens e vídeo.

```
    SENSOR CMOS    →   ISP            →   CODEC         →   INTERFACE    →   DISPLAY
    (Luz → Elétrico)  (Processamento     (H.264/H.265      (HDMI/DP/     (LCD/OLED/
    10 MP – 100 MP    da imagem)         compressão)        MIPI DSI)      MicroLED)
```

**Resolução e taxa de dados:**
| Padrão | Resolução | Taxa (30fps) | Codec |
|--------|-----------|-------------|-------|
| HD | 1280×720 | ~3 Mbps | H.264 |
| Full HD | 1920×1080 | ~6 Mbps | H.264/H.265 |
| 4K | 3840×2160 | ~25 Mbps | H.265/AV1 |
| 8K | 7680×4320 | ~100 Mbps | H.266/AV1 |

### 3.3 Informática (Computação)

**Função:** Processamento, armazenamento e troca de informações digitais.

```
    Hierarquia de memória (velocidade ↑, capacidade ↓):
    
    REGISTRADORES → CACHE L1 → CACHE L2 → CACHE L3 → RAM → SSD → HDD → FITA
       < 1 ns        1 ns        4 ns       10 ns     50 ns  100µs  10 ms  min
       KB             KB          MB          MB        GB    TB     TB     PB
```

**Arquiteturas de processador:**
| Tipo | Exemplos | Uso típico |
|------|---------|-----------|
| CISC | Intel x86, AMD Ryzen | Computadores desktop/laptop |
| RISC | ARM Cortex, RISC-V | Celulares, embarcados |
| GPU | NVIDIA CUDA, AMD ROCm | Gráficos, IA, mineração |
| DSP | TI C6000, ADSP | Áudio, rádio, controle |
| FPGA | Xilinx, Intel Altera | Prototipagem, aceleração |

### 3.4 Telecomunicações

**Função:** Transmissão de informação (voz, dados, vídeo) por meios eletromagnéticos.

```
    Espectro de Frequências de Rádio:
    
    ELF    VLF    LF     MF     HF     VHF    UHF    SHF    EHF
    3Hz    30Hz   300Hz  3kHz   3MHz   30MHz  300MHz 3GHz   30GHz
    ←→      ←→     ←→     ←→     ←→     ←→     ←→     ←→     ←→
    Submarinos  Rádio AM   CB    FM/VHF  4G/LTE  5G mmWave
```

**Evolução das redes celulares no Brasil:**
| Geração | Lançamento BR | Velocidade Máx | Latência | Tecnologia |
|---------|--------------|----------------|----------|-----------|
| 2G (GSM) | 1997 | 14,4 kbps | 300 ms | TDMA/CDMA |
| 3G (UMTS) | 2007 | 42 Mbps | 100 ms | WCDMA/HSPA |
| 4G (LTE) | 2013 | 150 Mbps | 30 ms | OFDMA/MIMO |
| 5G (NR) | 2022 | 10 Gbps | 1 ms | Massive MIMO |

### 3.5 Automação

**Função:** Monitoramento, controle e otimização de processos com mínima intervenção humana.

```
    NÍVEL DE CAMPO          NÍVEL DE CONTROLE        NÍVEL DE SUPERVISÃO
    ┌────────────────┐      ┌──────────────────┐      ┌─────────────────┐
    │ Sensores       │ →    │ PLC / CLP        │ →   │ SCADA / IHM     │
    │ Atuadores      │      │ DCS              │      │ MES / ERP       │
    │ Transmissores  │      │ Controladores PID│      │ Nuvem / IIoT    │
    └────────────────┘      └──────────────────┘      └─────────────────┘
    Modbus/4-20mA           Ethernet Industrial        TCP/IP / OPC-UA
```

**Protocolos industriais:**
| Protocolo | Nível | Velocidade | Uso no Brasil |
|-----------|-------|-----------|--------------|
| Modbus RTU | Campo | 19,2 kbps | Muito comum (legado) |
| PROFIBUS | Campo | 12 Mbps | Indústria automotiva |
| EtherCAT | Campo | 100 Mbps | Robótica, CNC |
| OPC-UA | Supervisório | Ethernet | Indústria 4.0 |
| MQTT | IIoT/Nuvem | Internet | IoT Industrial |

### 3.6 Dispositivos Móveis

**Função:** Sistemas compactos, portáteis, alimentados por bateria, com integração de comunicação, computação e sensores.

```
    SMARTPHONE MODERNO — Componentes internos:
    
    ┌────────────────────────────────────────────┐
    │  Tela OLED/AMOLED (6") — 2400×1080 120 Hz │
    ├────────┬───────────┬───────────────────────┤
    │  SoC   │  Câmeras  │  Modem 5G + Wi-Fi     │
    │ 8 cores│ 50 MP +   │  + Bluetooth + NFC    │
    │ 3nm    │ ultrawide │                       │
    ├────────┴───────────┤  ┌────────────────┐   │
    │  RAM 8–16 GB LPDDR5│  │  Bateria 5000  │   │
    │  Storage 128–512 GB│  │  mAh Li-ion    │   │
    │  UFS 3.1           │  │  Carga 120 W   │   │
    ├────────────────────┘  └────────────────┘   │
    │  Sensores: Giroscópio, Acelerômetro, GPS   │
    │  Barômetro, Biométrico, Proximidade, Luz   │
    └────────────────────────────────────────────┘
```

### 3.7 Tabela Comparativa das Aplicações

| Aplicação | Potência | Frequência | Componente Destaque | Exemplo Real |
|-----------|----------|-----------|--------------------|-----------  |
| Áudio | 1 W – 1 kW | 20 Hz – 20 kHz | Op-amp, Classe D | Caixa Bluetooth JBL |
| Vídeo | 5 – 50 W | MHz (pixels) | CMOS sensor, LED driver | Smart TV Samsung |
| Informática | 10 – 500 W | GHz (clock) | SoC CMOS, DDR5 RAM | Notebook Dell |
| Telecom | 0,1 – 10 W | MHz – GHz RF | Mixer, PLL, PA | Roteador 5G |
| Automação | 100 W – kW | 50 Hz – kHz | IGBT, PLC | Inversor WEG |
| Móveis | 1 – 10 W | GHz | PMIC, SoC ARM | iPhone / Galaxy |

### 🎬 Vídeos Recomendados — Aplicações da Eletrônica

- 📺 [**Eletrônica Fácil** — Canal completo para iniciantes](https://www.youtube.com/@ElectronicaFacil)
- 📺 [**WR Kits** — Projetos práticos de eletrônica brasileiros](https://www.youtube.com/@WRKits)
- 📺 [**Brincando com Ideias** — Arduino e automação](https://www.youtube.com/@BrincandocomIdeias)
- 📺 [**Curso em Vídeo** — Computação e eletrônica](https://www.youtube.com/@CursoemVideo)

---

<a name="cap4"></a>
## 📗 Capítulo 4 — Estrutura Atômica e Materiais

### 4.1 O Átomo: A Base de Tudo

Toda a eletrônica começa aqui: no **átomo**. Para entender por que alguns materiais conduzem eletricidade e outros não, precisamos entender a estrutura atômica.

> 💡 **Analogia:** Imagine o átomo como um sistema solar em miniatura. O **núcleo** é o Sol (pesado, no centro) e os **elétrons** são os planetas (leves, orbitando ao redor).

```
         ESTRUTURA DO ÁTOMO DE SILÍCIO (Si, Z=14)

                    ·  ·
                  ·      ·
              ·              ·       ← Camada M (4 elétrons de valência)
           ·    ╔══════╗      ·
          ·     ║ +14p ║       ·     ← Camada L (8 elétrons)
         ·      ║  14n ║        ·
          ·     ╚══════╝       ·     ← Camada K (2 elétrons)
           ·                  ·
              ·              ·
                  ·      ·
                    ·  ·

    Núcleo:  14 Prótons (+) + 14 Nêutrons (neutros)
    Elétrons: K=2, L=8, M=4  → Total: 14 elétrons
    Elétrons de valência: 4 (camada mais externa)
```

### 4.2 Camadas Eletrônicas (Níveis de Energia)

Os elétrons não orbitam aleatoriamente — eles ocupam **camadas de energia** bem definidas, como "andares" de um prédio:

| Camada | Símbolo | Capacidade Máxima | Número Quântico |
|--------|---------|-----------------|----------------|
| 1ª | K | 2 elétrons | n = 1 |
| 2ª | L | 8 elétrons | n = 2 |
| 3ª | M | 18 elétrons | n = 3 |
| 4ª | N | 32 elétrons | n = 4 |
| 5ª | O | 32 elétrons | n = 5 |
| 6ª | P | 18 elétrons | n = 6 |
| 7ª | Q | 2 elétrons | n = 7 |

> 🔑 **Regra de Ouro:** A camada mais **externa** (de valência) é quem determina as propriedades elétricas do material!

**Distribuição eletrônica de elementos importantes na eletrônica:**

| Elemento | Símbolo | Z | Distribuição | Val. | Tipo |
|---------|---------|---|-------------|------|------|
| Cobre | Cu | 29 | K²L⁸M¹⁸N¹ | **1** | Condutor |
| Ouro | Au | 79 | ... N³² O¹⁸ P¹ | **1** | Condutor |
| Germânio | Ge | 32 | K²L⁸M¹⁸N⁴ | **4** | Semicondutor |
| Silício | Si | 14 | K²L⁸M⁴ | **4** | Semicondutor |
| Carbono | C | 6 | K²L⁴ | **4** | Semicond./Diam. |
| Enxofre | S | 16 | K²L⁸M⁶ | **6** | Isolante |

### 4.3 Por Que Alguns Materiais Conduzem e Outros Não?

A resposta está na **estrutura de bandas de energia**:

```
    CONDUTOR (Cu)        SEMICONDUTOR (Si)       ISOLANTE (SiO₂)
    
    ╔═══════════╗        ╔═══════════╗           ╔═══════════╗
    ║  Banda de ║        ║  Banda de ║           ║  Banda de ║
    ║ Condução  ║        ║ Condução  ║    Gap    ║ Condução  ║
    ║  [CHEIA]  ║        ║  [VAZIA]  ║   grande  ║  [VAZIA]  ║
    ╠═══════════╣        ╠═══════════╣    ↕↕↕    ╠═══════════╣
    ║  Banda de ║        ║   Gap:    ║  > 5 eV   ║   Gap:    ║
    ║ Valência  ║        ║  1,12 eV  ║           ║  ~9 eV    ║
    ╚═══════════╝        ╚═══════════╝           ╚═══════════╝
    
    Bandas se            Gap pequeno →           Gap grande →
    sobrepõem →          dopagem controla        elétrons
    elétrons livres      condução                aprisionados
```

### 4.4 Os Três Tipos de Materiais

```
    ╔══════════════╦══════════════════╦══════════════╦══════════════════════════╗
    ║   CONDUTOR   ║  SEMICONDUTOR    ║   ISOLANTE   ║    SUPERCONDUTOR         ║
    ╠══════════════╬══════════════════╬══════════════╬══════════════════════════╣
    ║ 1-3 e⁻ val.  ║ 4 e⁻ valência   ║ 5-8 e⁻ val. ║ Resistência = 0 Ω       ║
    ║ Muitos e⁻    ║ Controlamos a   ║ Zero e⁻     ║ (abaixo de Tc)           ║
    ║ livres       ║ condução        ║ livres       ║                          ║
    ╠══════════════╬══════════════════╬══════════════╬══════════════════════════╣
    ║ Cu, Ag, Au   ║ Si, Ge, GaAs    ║ PVC, SiO₂   ║ Nb, YBaCuO, MgB₂        ║
    ║ Al, Fe, W    ║ SiC, InP, GaN   ║ Vidro, Ar   ║                          ║
    ╠══════════════╬══════════════════╬══════════════╬══════════════════════════╣
    ║ ρ = 10⁻⁸ Ωm  ║ ρ = 10³ Ωm puro ║ ρ > 10¹² Ωm ║ ρ = 0 (T < Tc)          ║
    ╠══════════════╬══════════════════╬══════════════╬══════════════════════════╣
    ║ Cabos, PCBs  ║ Diodos, chips   ║ Revestimento ║ Pesquisa, MRI, trens     ║
    ║ pistas de Cu ║ LEDs, sensores  ║ capacitores  ║ maglev (Japão)           ║
    ╚══════════════╩══════════════════╩══════════════╩══════════════════════════╝
```

### 4.5 Por Que o Silício Domina a Eletrônica?

O silício (Si) não é o **melhor** semicondutor — é o mais **conveniente**:

| Critério | Silício (Si) | Germânio (Ge) | GaAs | Carbono (diamante) |
|----------|-------------|--------------|------|-------------------|
| Abundância | ✅ 2º elemento + abundante | ❌ Raro | ❌ Raro | ❌ Sintético |
| Óxido natural | ✅ SiO₂ (excelente isolante) | ❌ Instável | ❌ Inadequado | ❌ |
| Band gap | ✅ 1,12 eV (bom) | ⚠️ 0,67 eV (baixo) | ✅ 1,42 eV | ✅✅ 5,5 eV |
| Temperatura max. | ✅ ~150°C | ❌ ~75°C | ✅ ~300°C | ✅✅ >500°C |
| Custo | ✅ Muito barato | ❌ Caro | ❌ Caro | ❌❌ Caríssimo |
| **Resultado** | **PADRÃO MUNDIAL** | Obsoleto (BJT legacy) | RF/LED/Laser | Futuro (pesquisa) |

### 🎬 Vídeos Recomendados — Estrutura Atômica

- 📺 [**Khan Academy PT** — Estrutura Atômica](https://pt.khanacademy.org/science/chemistry/electronic-structure-of-atoms)
- 📺 [**Física e Química A** — Distribuição Eletrônica](https://www.youtube.com/watch?v=LJmKJH_lbAE)
- 📺 [**Prof. Boaro** — Eletrônica dos Semicondutores](https://www.youtube.com/watch?v=QO9YXBaxYRE)

### 🎯 Exercícios do Capítulo 4

**1.** Determine a configuração eletrônica e o número de elétrons de valência do Alumínio (Al, Z=13).

**2.** Por que o cobre (Cu) conduz melhor que o alumínio (Al), mesmo tendo mais camadas eletrônicas?

**3.** Se você precisasse escolher um material para isolar trilhas de cobre em uma placa de circuito impresso (PCB), qual usaria e por quê?

> 📝 **Gabarito:**  
> 1) Al: K²L⁸M³ → 3 elétrons de valência → Condutor  
> 2) Cu tem resistividade menor (1,7×10⁻⁸ Ωm) vs Al (2,8×10⁻⁸ Ωm), pois tem 1 elétron de valência muito fracamente ligado. Porém Al é mais leve e mais barato.  
> 3) FR4 (fibra de vidro epóxi) — excelente isolante, rigidez mecânica, baixo custo, padrão da indústria para PCBs.


---

<a name="cap5"></a>
## 📗 Capítulo 5 — Tensão, Corrente e Resistência

### 5.1 Tensão Elétrica (V)

A **tensão elétrica** (também chamada de **diferença de potencial** ou **força eletromotriz**) é a "pressão" que empurra os elétrons pelo circuito.

> �� **Analogia Hidráulica:** Tensão = Pressão da água. Quanto maior a pressão, mais água flui pelo cano.

```
    ANALOGIA ELÉTRICA × HIDRÁULICA
    
    CIRCUITO ELÉTRICO              CIRCUITO HIDRÁULICO
    ┌─────────────────┐            ┌──────────────────┐
    │   ┌─ TENSÃO     │            │   ┌─ PRESSÃO      │
    │   │  (Bateria)  │            │   │  (Bomba)       │
    │   │  = 12 V     │            │   │  = 2 bar       │
    │  [+]           [-]           │  [↑]             [↓]
    │   │             │            │   │               │
    │   │  ┌──────┐  │            │   │  ┌────────┐   │
    │   └──┤RESIST├──┘            │   └──┤TUBO    ├───┘
    │      │ 100Ω │               │      │ (atrito)│
    │      └──────┘               │      └─────────┘
    └─────────────────┘            └──────────────────┘
    Corrente:                      Fluxo:
    I = V/R = 12/100 = 0,12 A     Q = P/R_hid
```

**Tipos de tensão:**
| Tipo | Símbolo | Descrição | Exemplo |
|------|---------|-----------|---------|
| Contínua (DC) | ─── | Polaridade fixa | Bateria, fonte regulada |
| Alternada (AC) | ∿ | Polaridade varia (senoidal) | Tomada 127/220 V |
| Pulsada | ⊓⊔ | DC com variações (PWM) | Controle de motor |
| Senoidal | ∿ | Onda seno | Rede elétrica |

**Unidades e múltiplos:**
```
    1 GV = 10⁹ V    (Gigavolt — raios)
    1 MV = 10⁶ V    (Megavolt — aceleradores de partículas)
    1 kV = 10³ V    (Quilovolt — linhas de transmissão: 13,8 kV / 138 kV)
    1  V = 10⁰ V    (Volt — bateria AA = 1,5 V; celular = 3,7 V; tomada = 127 V)
    1 mV = 10⁻³ V   (Milivolt — sinais de áudio, sensores)
    1 µV = 10⁻⁶ V   (Microvolt — sinais de EEG, termopar)
    1 nV = 10⁻⁹ V   (Nanovolt — equipamentos científicos de alta precisão)
```

### 5.2 Corrente Elétrica (I)

A **corrente elétrica** é o fluxo de cargas elétricas (elétrons) através de um condutor. É medida em **Ampères (A)**.

> 💡 **Analogia:** Corrente = Vazão de água (litros por segundo). Mede QUANTOS elétrons passam por segundo.

**Definição formal:**
```
    I = Q / t

    Onde:
    I = corrente elétrica (Ampères, A)
    Q = carga elétrica (Coulombs, C)
    t = tempo (segundos, s)

    1 Coulomb = 6,24 × 10¹⁸ elétrons
    1 Ampère = 1 Coulomb por segundo
```

**Corrente Convencional vs Corrente Real:**
```
    CORRENTE CONVENCIONAL (Benjamin Franklin):    ────►  (+ para -)
    FLUXO REAL DE ELÉTRONS:                       ◄────  (- para +)
    
    Por convenção histórica, usamos a corrente convencional nos circuitos!
    Os elétrons se movem na direção OPOSTA à corrente convencional.
```

**Densidades de corrente típicas:**
```
    1 kA  ──── Relâmpago, soldagem a arco
    100 A ──── Motor industrial grande
    10 A  ──── Aquecedor doméstico
    1 A   ──── Carregador de celular
    100 mA ─── Limite letal para seres humanos (!)
    10 mA ──── LED, sensor
    1 mA  ──── Op-amp (corrente de entrada)
    1 µA  ──── Corrente de fuga de MOSFET
    1 nA  ──── Corrente de escuro de fotodetector
```

> ⚠️ **SEGURANÇA:** Correntes acima de **10 mA** podem causar contrações musculares involuntárias. Acima de **100 mA** podem ser letais por fibrilação cardíaca. A proteção NÃO é pela tensão, é pela CORRENTE! (Por isso o choque de 220 V é mais perigoso que o de 127 V — força mais corrente pelo corpo).

### 5.3 Resistência Elétrica (R)

A **resistência elétrica** é a oposição que um material oferece à passagem de corrente elétrica. É medida em **Ohms (Ω)**.

> 💡 **Analogia:** Resistência = Estreitamento do cano. Quanto mais estreito, mais difícil passar água (corrente).

**Fatores que influenciam a resistência:**
```
    R = ρ × L / A

    Onde:
    R = resistência (Ω)
    ρ = resistividade do material (Ω·m) — propriedade do material
    L = comprimento do condutor (m)  — quanto MAIOR, MAIOR a R
    A = área da seção transversal (m²) — quanto MAIOR, MENOR a R
```

**Exemplo prático — fio de cobre:**
```
    Fio de cobre, L = 1 m, diâmetro = 1 mm (AWG 18), ρ_Cu = 1,7×10⁻⁸ Ωm
    
    A = π × (0,0005)² = 7,85 × 10⁻⁷ m²
    R = (1,7×10⁻⁸) × 1 / (7,85×10⁻⁷) = 0,0217 Ω ≈ 22 mΩ/m
    
    Para 100 m de fio: R = 100 × 22 mΩ = 2,2 Ω (relevante para circuitos de potência!)
```

**Efeito da temperatura na resistência:**
```
    Metais:       R aumenta com temperatura (coeficiente α positivo)
    Semicondutores: R diminui com temperatura (NTC — Negative Temperature Coefficient)
    Carvão/grafite: R diminui com temperatura
    
    R(T) = R₀ × [1 + α × (T - T₀)]
    
    Exemplo: Resistor de carbono 100 Ω a 25°C
    A 100°C: R = 100 × [1 + (-0,0005) × 75] = 100 × 0,9625 = 96,25 Ω
```

### 5.4 Potência Elétrica (P)

A **potência elétrica** é a taxa de transferência (ou consumo) de energia elétrica. É medida em **Watts (W)**.

```
    P = V × I = I² × R = V² / R

    Onde:
    P = potência (Watts, W)
    V = tensão (Volts, V)
    I = corrente (Ampères, A)
    R = resistência (Ohms, Ω)
```

**Fórmula do triângulo (PIV):**
```
         P
        ╱ ╲
       ╱   ╲
      I  ×  V
      
    P = I × V
    I = P / V
    V = P / I
```

**Exemplos de potência:**
| Dispositivo | Tensão | Corrente | Potência |
|------------|--------|---------|---------|
| LED 5 mm | 3,2 V | 20 mA | **64 mW** |
| Smartphone (uso) | 3,7 V | 1,4 A | **5 W** |
| Lâmpada LED 9 W | 127 V | 71 mA | **9 W** |
| Micro-ondas | 127 V | 7,9 A | **1000 W = 1 kW** |
| Chuveiro elétrico | 220 V | 27 A | **6000 W = 6 kW** |
| Motor industrial | 380 V | 26 A | **10 kW (3 fases)** |

### 5.5 Energia Elétrica (E)

**Energia** é potência multiplicada pelo tempo. No Brasil, pagamos a energia em **kWh** (quilowatt-hora).

```
    E = P × t

    Onde:
    E = energia (Joules, J  ou  Wh  ou  kWh)
    P = potência (W)
    t = tempo (s  ou  h)

    1 kWh = 1000 W × 1 hora = 3.600.000 J
```

**Calculando sua conta de luz:**
```
    Chuveiro de 6 kW, 30 min/dia, 30 dias/mês:
    E = 6 kW × 0,5 h × 30 = 90 kWh/mês
    
    Tarifa ANEEL 2024 (tarifa bandeira verde): ≈ R$ 0,75/kWh
    Custo: 90 × R$ 0,75 = R$ 67,50/mês  ← só do chuveiro!
```

### 🎯 Exercícios do Capítulo 5

**1.** Um resistor de 470 Ω é ligado a uma bateria de 9 V. Calcule:
   - a) A corrente que flui pelo circuito
   - b) A potência dissipada no resistor

**2.** Uma lâmpada LED de 12 W é ligada em 127 V. Qual a corrente consumida?

**3.** Um cabo de cobre de 2,5 mm² (AWG 14) tem resistividade ρ = 1,7×10⁻⁸ Ωm. Qual a resistência de 50 m deste cabo? (Conversão: 2,5 mm² = 2,5×10⁻⁶ m²)

**4.** Uma residência usa em média 250 kWh/mês. Considerando a tarifa de R$ 0,75/kWh, qual é o custo mensal?

> 📝 **Gabarito:**  
> 1a) I = V/R = 9/470 = 0,0191 A ≈ 19,1 mA  
> 1b) P = V×I = 9 × 0,0191 = 0,172 W ≈ 172 mW (ou P = I²×R = 0,0191² × 470 = 172 mW)  
> 2) I = P/V = 12/127 = 0,094 A ≈ 94 mA  
> 3) R = ρ×L/A = (1,7×10⁻⁸ × 50) / (2,5×10⁻⁶) = 0,34 Ω  
> 4) Custo = 250 × R$ 0,75 = **R$ 187,50/mês**

---

<a name="cap6"></a>
## 📗 Capítulo 6 — Lei de Ohm e Leis de Kirchhoff

### 6.1 Lei de Ohm

Formulada por **Georg Simon Ohm** em 1827, é a lei fundamental dos circuitos elétricos.

```
    V = R × I

    V = tensão em Volts (V)
    R = resistência em Ohms (Ω)
    I = corrente em Ampères (A)

    O triângulo de Ohm:
         V
        ╱ ╲
       ╱   ╲
      R  ×  I

    Cubra o que quer calcular:
    V = R × I    |    R = V / I    |    I = V / R
```

> ⚠️ **Atenção:** A Lei de Ohm se aplica apenas a **componentes ôhmicos** (resistores lineares). Diodos, transistores, LEDs e capacitores **NÃO** obedecem a Lei de Ohm!

### 6.2 Circuitos em Série

Em um **circuito série**, os componentes são ligados em sequência — a mesma corrente flui por todos.

```
    ┌────[R1]────[R2]────[R3]────┐
    │     10Ω     22Ω     47Ω    │
   [+]                          [-]
    │                            │
    └────────────────────────────┘
           Vs = 12 V

    R_total = R1 + R2 + R3 = 10 + 22 + 47 = 79 Ω
    I = Vs / R_total = 12 / 79 = 0,152 A ≈ 152 mA

    Tensão em cada resistor (Divisor de Tensão):
    V_R1 = I × R1 = 0,152 × 10 = 1,52 V
    V_R2 = I × R2 = 0,152 × 22 = 3,34 V
    V_R3 = I × R3 = 0,152 × 47 = 7,14 V
    
    Verificação: 1,52 + 3,34 + 7,14 = 12 V ✅
```

**Regras do circuito série:**
- ✅ A corrente é a **mesma** em todos os componentes: `I_total = I_R1 = I_R2 = I_R3`
- ✅ As tensões se **somam**: `V_total = V_R1 + V_R2 + V_R3`
- ✅ As resistências se **somam**: `R_total = R1 + R2 + R3`

### 6.3 Circuitos em Paralelo

Em um **circuito paralelo**, todos os componentes compartilham os mesmos terminais — a mesma tensão aparece em todos.

```
    ┌──────┬──────┬──────┐
    │      │      │      │
   [+]   [R1]  [R2]   [R3]
    │    100Ω   47Ω   220Ω
   [-]    │      │      │
    │      └──────┴──────┘
    │                    │
    └────────────────────┘
           Vs = 12 V

    1/R_total = 1/R1 + 1/R2 + 1/R3
    1/R_total = 1/100 + 1/47 + 1/220
    1/R_total = 0,01 + 0,02128 + 0,00455 = 0,03583
    R_total = 1 / 0,03583 = 27,9 Ω

    I_R1 = 12/100 = 120 mA
    I_R2 = 12/47  = 255 mA
    I_R3 = 12/220 =  55 mA
    I_total = 120 + 255 + 55 = 430 mA

    Verificação: I = V/R = 12/27,9 = 430 mA ✅
```

**Regras do circuito paralelo:**
- ✅ A tensão é a **mesma** em todos: `V_total = V_R1 = V_R2 = V_R3`
- ✅ As correntes se **somam**: `I_total = I_R1 + I_R2 + I_R3`
- ✅ As resistências se **combinam**: `1/R_total = 1/R1 + 1/R2 + 1/R3`

**Caso especial — dois resistores iguais em paralelo:**
```
    R_total = R / 2

    Exemplo: R1 = R2 = 100 Ω → R_total = 50 Ω
```

### 6.4 Leis de Kirchhoff

**Gustav Kirchhoff** (1824–1887) formulou duas leis fundamentais para análise de circuitos complexos.

#### Lei de Kirchhoff para Correntes (LKC — 1ª Lei)

> 🔑 **LKC:** A **soma** de todas as correntes que **entram** em um nó é igual à soma das que **saem**.

```
    Nó A:
              I2=2A
               ↑
    I1=5A →──[A]──→ I3=?
               ↓
              I4=1A

    LKC: I1 = I2 + I3 + I4 (correntes que entram = correntes que saem)
    5 = 2 + I3 + 1
    I3 = 5 - 2 - 1 = 2 A
    
    (Conservação de carga — elétrons não somem!)
```

#### Lei de Kirchhoff para Tensões (LKT — 2ª Lei)

> 🔑 **LKT:** A **soma** de todas as tensões em uma **malha fechada** é igual a zero.

```
    Malha simples:
    
    ┌──────[R1=10Ω]──────┐
    │                    │
   [VS=12V]           [R2=20Ω]
    │                    │
    └────────────────────┘

    Percorrendo no sentido horário:
    +VS - V_R1 - V_R2 = 0
    +12 - (I×10) - (I×20) = 0
    12 = 30 × I
    I = 0,4 A = 400 mA
    
    V_R1 = 0,4 × 10 = 4 V
    V_R2 = 0,4 × 20 = 8 V
    
    Verificação: 4 + 8 = 12 V ✅
```

### 6.5 Divisor de Tensão

O **divisor de tensão** é um dos circuitos mais utilizados em eletrônica. Converte uma tensão maior em uma menor.

```
    Vin ──[R1]──┬── Vout
                │
               [R2]
                │
               GND

    Vout = Vin × R2 / (R1 + R2)
```

**Exemplo prático — sensor com Arduino:**
```
    Problema: Sensor de 5 V, Arduino tolera 3,3 V.
    Solução: Divisor de tensão.
    
    Vin = 5 V, Vout = 3,3 V
    
    R2 / (R1 + R2) = 3,3 / 5 = 0,66
    
    Escolhendo R2 = 33 kΩ (padrão comercial):
    33 / (R1 + 33) = 0,66
    R1 + 33 = 33/0,66 = 50 kΩ
    R1 = 50 - 33 = 17 kΩ → usar 18 kΩ (valor padrão mais próximo)
    
    Verificação: Vout = 5 × 33/(18+33) = 5 × 33/51 = 3,24 V ≈ 3,3 V ✅
```

### 🎬 Vídeos Recomendados — Lei de Ohm e Kirchhoff

- 📺 [**Nerdologia** — Lei de Ohm explicada com analogias](https://www.youtube.com/watch?v=XSFAKOJMiSY)
- 📺 [**Tinkercad Circuits** — Simulação online gratuita de circuitos](https://www.tinkercad.com/circuits)
- 📺 [**Canal do Ensino** — Leis de Kirchhoff com exemplos resolvidos](https://www.youtube.com/watch?v=7CKGJHFnMIk)
- 📺 [**Professor Marcelo Nascimento** — Circuitos elétricos básicos](https://www.youtube.com/@ProfMarceloNascimento)

### 🎯 Exercícios do Capítulo 6

**1.** No circuito abaixo, encontre a corrente total e a tensão em cada resistor:
   - Fonte: 24 V, R1 = 150 Ω (série), R2 = 330 Ω (série)

**2.** Três resistores de 120 Ω cada estão em paralelo com uma fonte de 12 V. Calcule:
   - a) Resistência equivalente
   - b) Corrente total
   - c) Corrente em cada resistor

**3.** Projete um divisor de tensão para obter 2,5 V a partir de 5 V, usando um resistor de 10 kΩ.

> 📝 **Gabarito:**  
> 1) R_total = 150+330 = 480 Ω; I = 24/480 = 50 mA; V_R1 = 7,5 V; V_R2 = 16,5 V  
> 2a) R_eq = 120/3 = 40 Ω; 2b) I = 12/40 = 300 mA; 2c) I_cada = 12/120 = 100 mA  
> 3) Vout = Vin × R2/(R1+R2) → 2,5 = 5 × R2/(10k+R2) → R2 = 10 kΩ


---

<a name="cap7"></a>
## 📗 Capítulo 7 — Componentes Passivos: Resistores, Capacitores e Indutores

> **Componentes passivos** são aqueles que não necessitam de fonte externa de energia para funcionar e não amplificam sinais. Eles apenas consomem, armazenam ou dissipam energia.

### 7.1 Resistores

O **resistor** é o componente mais básico da eletrônica. Sua função é **limitar a corrente** e **dividir tensões**.

#### 7.1.1 Código de Cores

Os resistores convencionais (PTH — Through Hole) têm seu valor indicado por **faixas coloridas**:

```
    RESISTOR DE 4 FAIXAS:

    ┌──────────────────────────────────────┐
    │  Faixa1  Faixa2  Faixa3  Faixa4      │
    │  (1º dígito) (2º dígito) (Multiplicador) (Tolerância) │
    └──────────────────────────────────────┘

    COR        DÍGITO    MULTIPLICADOR    TOLERÂNCIA
    ─────────────────────────────────────────────────
    Preto        0         ×1 (10⁰)
    Marrom       1         ×10 (10¹)         ±1%
    Vermelho     2         ×100 (10²)        ±2%
    Laranja      3         ×1k (10³)
    Amarelo      4         ×10k (10⁴)
    Verde        5         ×100k (10⁵)       ±0,5%
    Azul         6         ×1M (10⁶)         ±0,25%
    Violeta      7         ×10M (10⁷)        ±0,1%
    Cinza        8         ×100M             ±0,05%
    Branco       9         ×1G
    Dourado      —         ×0,1              ±5%
    Prata        —         ×0,01             ±10%

    EXEMPLO: Vermelho-Vermelho-Laranja-Dourado
             2          2        ×1k      ±5%
             = 22 × 1000 = 22.000 Ω = 22 kΩ ±5%
```

**Mnemônico popular para memorizar as cores:**
> **"P**reto **M**arrom **V**ermelho **L**aranja **A**marelo **V**erde **A**zul **V**ioleta **C**inza **B**ranco"  
> → "**P**ode **M**atar **V**árias **L**arvas **A**través **V**oltas **A**o **V**ento **C**hegando **B**rasileiro"

#### 7.1.2 Série E (Valores Comerciais Padronizados)

Os resistores são fabricados em valores **padronizados** (série E):

| Série | Tolerância | Valores por décade | Uso |
|-------|-----------|-------------------|-----|
| **E12** | ±10% | 12 valores | Projetos gerais |
| **E24** | ±5% | 24 valores | Mais comum |
| **E48** | ±2% | 48 valores | Aplicações precisas |
| **E96** | ±1% | 96 valores | Profissional |

**Série E24 (valores mais comuns):**
```
    1.0  1.1  1.2  1.3  1.5  1.6  1.8  2.0  2.2  2.4  2.7  3.0
    3.3  3.6  3.9  4.3  4.7  5.1  5.6  6.2  6.8  7.5  8.2  9.1
    (×1, ×10, ×100, ×1k, ×10k, ×100k, ×1M)
```

#### 7.1.3 Potência dos Resistores

Os resistores têm uma **potência máxima** que podem dissipar sem danificar:

```
    TAMANHO FÍSICO VS POTÊNCIA (PTH):
    
    ◉  (menor)  →  1/8 W  = 0,125 W  → Para sinais baixos
    ◉◉          →  1/4 W  = 0,25 W   → Mais comum em projetos
    ◉◉◉         →  1/2 W  = 0,5 W    → Moderado
    ◉◉◉◉        →  1 W              → Potência média
    ◉◉◉◉◉       →  2 W              → Alta corrente
    ████        →  5 W / 10 W       → Cargas de potência
    
    REGRA PRÁTICA: dimensione para 2× a potência calculada!
    Exemplo: P_calculada = 0,1 W → use resistor de 1/4 W (0,25 W)
```

#### 7.1.4 Tipos Especiais de Resistores

| Tipo | Símbolo | Característica | Aplicação |
|------|---------|---------------|-----------|
| **NTC** (Termistor neg.) | R↓T↑ | Resistência cai com temperatura | Sensor temp., inrush limiter |
| **PTC** (Termistor pos.) | R↑T↑ | Resistência sobe com temperatura | Proteção sobreaquecimento |
| **LDR** (Fotoresistor) | R↓luz↑ | Resistência cai com luz | Sensores de luz, automação |
| **VDR/Varistor** | R↓V↑ | Resistência cai com tensão | Proteção surtos (DPS) |
| **Potenciômetro** | R variável | Resistência ajustável | Volume, controle, calibração |
| **Trimpot** | R variável | Ajuste fino | Calibração em circuitos |

### 7.2 Capacitores

O **capacitor** armazena energia na forma de **campo elétrico** entre duas placas condutoras separadas por um **dielétrico** (isolante).

#### 7.2.1 Princípio de Funcionamento

```
    ESTRUTURA BÁSICA DO CAPACITOR:
    
    Terminal (+) ──────┤████████┃████████├────── Terminal (-)
                       Placa+  Dielétrico Placa-
                       (+++)   (isolante)  (---)
    
    Campo elétrico E → → → → → →
    
    Cargas opostas nas placas criam campo elétrico.
    Energia armazenada no campo elétrico!
    
    C = ε × A / d
    
    Onde:
    C = capacitância (Farads, F)
    ε = permissividade do dielétrico (F/m)
    A = área das placas (m²) — maior área = maior capacitância
    d = distância entre as placas (m) — menor distância = maior capacitância
```

#### 7.2.2 Equação do Capacitor

```
    Q = C × V

    I = C × dV/dt    (capacitor conduz APENAS quando a tensão MUDA)
    
    Energia armazenada:
    E = ½ × C × V²
```

**Implicações importantes:**
- ⚡ Capacitor com tensão **constante** → corrente = 0 (aberto para DC!)
- ⚡ Em corrente alternada (AC) → capacitor **conduz** (reactância capacitiva)
- ⚡ Tensão no capacitor **não pode mudar instantaneamente**

#### 7.2.3 Tipos de Capacitores

```
    ┌─────────────────────────────────────────────────────┐
    │                   CAPACITORES                        │
    ├──────────────┬───────────────────────────────────────┤
    │  POLARIZADOS │        NÃO POLARIZADOS                │
    ├──────────────┼───────────────────────────────────────┤
    │ Eletrolítico │ Cerâmico  │ Filme │ Mica  │ Tantalio  │
    │ 1µF–100mF    │ 1pF–100µF │ 1nF–  │ 1pF– │ 0,1µF–    │
    │ 6V–450V      │ 16V–5kV   │ 10µF  │ 10nF │ 100µF     │
    │ Barato       │ Comum     │ Preciso│ RF   │ Compacto  │
    └──────────────┴───────────┴───────┴──────┴───────────┘
```

| Tipo | Capacitância | Tensão | Polaridade | Uso principal |
|------|-------------|--------|-----------|--------------|
| Eletrolítico Al | 1 µF – 100 mF | 6–450 V | Polarizado (+/-) | Filtro fontes, desacoplamento |
| Cerâmico MLCC | 1 pF – 100 µF | 16–5000 V | Não polarizado | Desacoplamento, RF, SMD |
| Filme poliéster | 1 nF – 10 µF | 63–630 V | Não polarizado | Áudio, filtros, precisão |
| Tantalio | 0,1 – 100 µF | 6–35 V | Polarizado | SMD, compacto, estável |
| Supercapacitor | 0,1 – 3000 F | 2–5 V | Polarizado | Backup energia, harvesting |

#### 7.2.4 Aplicações do Capacitor

```
    1. FILTRO DE FONTES (desacoplamento):
    ┌──────────────────────────────────┐
    │  VCC ──[C1=100µF]── GND          │  Filtra ripple (ondulação)
    │  VCC ──[C2=100nF]── GND          │  C grande: baixa frequência
    │                                  │  C pequeno: alta frequência
    └──────────────────────────────────┘

    2. TEMPORIZADOR RC:
    ┌──────────────────────────────────┐
    │  Vs ──[R]──┬── Saída             │  τ = R × C
    │            │                    │  τ = 10kΩ × 100µF = 1 s
    │           [C] (carrega/descarrega)│  Usado em osciladores, timers
    │            │                    │
    │           GND                   │
    └──────────────────────────────────┘

    3. ACOPLAMENTO AC (bloqueia DC):
    ┌──────────────────────────────────┐
    │  Sinal DC+AC ──[C]──► Sinal AC   │  Só passa AC, bloqueia DC
    │  (com offset 2V)       (puro)    │  Ex: entrada de amplificadores
    └──────────────────────────────────┘
```

### 7.3 Indutores

O **indutor** (bobina/solenóide) armazena energia na forma de **campo magnético** quando a corrente flui por seus enrolamentos.

#### 7.3.1 Princípio de Funcionamento

```
    ESTRUTURA BÁSICA DO INDUTOR:
    
    ─────OOOOOOOOOOOOOOOO─────
    
    Corrente I → fluxo magnético Φ → campo B (dentro do núcleo)
    
    V = L × dI/dt    (indutor resiste a MUDANÇAS de corrente)
    
    Energia armazenada:
    E = ½ × L × I²
    
    L = (µ × N² × A) / l
    
    Onde:
    L = indutância (Henries, H)
    µ = permeabilidade do núcleo
    N = número de espiras
    A = área da seção transversal do núcleo
    l = comprimento do núcleo
```

#### 7.3.2 Comportamento do Indutor

```
    CORRENTE CONSTANTE → Tensão = 0 (curto-circuito para DC!)
    VARIAÇÃO DE CORRENTE → Indutor gera tensão que se opõe à mudança (Lenz)
    
    Tempo de carga:    τ = L / R
    
    Exemplo: L = 10 mH, R = 100 Ω
    τ = 10×10⁻³ / 100 = 0,1 ms
    Em 5τ = 0,5 ms → corrente atingiu 99,3% do valor final
```

#### 7.3.3 Tipos de Indutores

| Tipo | Indutância | Corrente | Núcleo | Uso |
|------|-----------|---------|--------|-----|
| Ar (air core) | nH – µH | A | Ar | RF, alta frequência |
| Ferrite | µH – mH | mA – A | Ferrite | Fontes chaveadas, filtros |
| Pó de ferro | µH – mH | A – kA | Pó Fe | Conversores potência |
| Toróide | µH – H | A | Ferrite/Fe-Si | Filtros EMI, transformadores |
| SMD Power | µH – mH | A | Ferrite | Reguladores DC-DC (buck/boost) |

#### 7.3.4 Transformador: Indutores Acoplados

O **transformador** é composto de dois ou mais indutores acoplados magneticamente — sem contato elétrico entre primário e secundário:

```
    TRANSFORMADOR:
    
    Primário           Núcleo Fe          Secundário
    N1 espiras         ╔════════╗          N2 espiras
    ────OOOO──────────►║        ║◄────────────OOOO────
                       ║  Φ     ║
    V1                 ╚════════╝                V2
    
    Relação de transformação:
    V1/V2 = N1/N2 = I2/I1
    
    Potência conservada (η ≈ 95–99%):
    P1 = V1 × I1 ≈ P2 = V2 × I2
    
    Exemplo — Transformador de rede:
    N1/N2 = 127/12 ≈ 10,6
    V2 = 12 V CA, I2 = 1 A → P2 = 12 W
    I1 = P1/V1 = 12/127 = 94,5 mA
```

### 7.4 Comparativo dos Componentes Passivos

| Propriedade | Resistor (R) | Capacitor (C) | Indutor (L) |
|------------|-------------|--------------|-------------|
| **Armazena?** | ❌ (dissipa) | ✅ Campo elétrico | ✅ Campo magnético |
| **Para DC** | Conduz (R) | Aberto (bloqueia) | Curto-circuito |
| **Para AC** | Conduz (R) | Conduz (Xc = 1/ωC) | Conduz (Xl = ωL) |
| **Defasagem** | 0° | I adianta V em 90° | V adianta I em 90° |
| **Unidade** | Ohm (Ω) | Farad (F) | Henry (H) |
| **Energia** | P = V²/R (calor) | E = ½CV² | E = ½LI² |

### 🎬 Vídeos Recomendados — Componentes Passivos

- 📺 [**Eletrônica para Curiosos** — Resistores: Código de Cores](https://www.youtube.com/watch?v=h7HknLDHiDE)
- 📺 [**FilipeFlop** — Capacitores: Tipos e Aplicações](https://www.youtube.com/watch?v=R6VFfAT2DGo)
- 📺 [**Spice Simulations** — Circuitos RC e RL no Falstad](https://www.falstad.com/circuit/)
- 📺 [**Mundo dos Componentes** — Indutores e Transformadores](https://www.youtube.com/watch?v=KSylo01n5FY)

### 🎯 Exercícios do Capítulo 7

**1.** Identifique o valor dos resistores com as seguintes faixas de cores:
   - a) Amarelo-Violeta-Vermelho-Dourado
   - b) Marrom-Preto-Laranja-Dourado
   - c) Azul-Cinza-Dourado-Prata

**2.** Um capacitor eletrolítico de 470 µF está carregado a 12 V. Calcule a energia armazenada.

**3.** Um transformador tem 500 espiras no primário (220 V) e precisa fornecer 12 V no secundário. Quantas espiras deve ter o secundário?

**4.** Qual tipo de capacitor você usaria para desacoplar a alimentação de um microcontrolador (VCC = 3,3 V, perto do pino VCC/GND)? Por quê?

> 📝 **Gabarito:**  
> 1a) 4.700 Ω = 4,7 kΩ ±5% | 1b) 10.000 Ω = 10 kΩ ±5% | 1c) 6,8 Ω ±10%  
> 2) E = ½ × 470×10⁻⁶ × 12² = ½ × 470×10⁻⁶ × 144 = 0,0338 J = 33,8 mJ  
> 3) N2 = N1 × (V2/V1) = 500 × (12/220) = 27,3 → 27 espiras  
> 4) Cerâmico MLCC 100 nF (0603 ou 0402 SMD) — baixa indutância parasita, resposta rápida a transientes digitais, compacto e barato.

---

<a name="cap8"></a>
## 📗 Capítulo 8 — Semicondutores e Dopagem

### 8.1 Revisando a Estrutura do Silício Puro

O silício puro (intrínseco) tem **4 elétrons de valência**. Cada átomo forma **4 ligações covalentes** com seus vizinhos, criando uma estrutura cristalina muito estável:

```
    REDE CRISTALINA DO SILÍCIO PURO (2D simplificada):

         Si        Si        Si
        ╱│╲      ╱│╲      ╱│╲
    ───Si─Si─Si─Si─Si─Si─Si─Si───
        ╲│╱      ╲│╱      ╲│╱
         Si        Si        Si

    Cada Si compartilha 4 pares de elétrons (ligações covalentes)
    → Todos os elétrons estão "ocupados" nas ligações
    → A temperatura ambiente: pouquíssimos elétrons livres
    → Resistividade alta: ≈ 2300 Ω·m (ruim condutor!)
```

**Por que o silício puro não presta para fazer dispositivos?**
- Resistividade muito alta (≈ 2300 Ω·m) — quase isolante
- Impossível controlar a condução
- Solução: **DOPAGEM**

### 8.2 Dopagem: Adicionando Impurezas Controladas

**Dopagem** é o processo de inserir átomos de outras substâncias (impurezas) no cristal de silício para **controlar** suas propriedades de condução. As impurezas são adicionadas em proporções muito pequenas (1 átomo de impureza para cada 10⁶ a 10⁸ átomos de Si).

#### 8.2.1 Semicondutor Tipo N (Doador de Elétrons)

Adiciona-se um elemento da **coluna V** da tabela periódica (5 elétrons de valência): Fósforo (P), Arsênio (As) ou Antimônio (Sb).

```
    SEMICONDUTOR TIPO N (com Fósforo):

         Si        Si        Si
        ╱│╲      ╱│╲      ╱│╲
    ───Si─Si─Si─[P]─Si─Si─Si─Si───
        ╲│╱      ╲│⊕╱      ╲│╱
         Si        Si        Si
                   ↑
                   e⁻ LIVRE! (elétron extra do Fósforo)
                   Portador majoritário: elétrons (negativo → Tipo N)
    
    Portadores MAJORITÁRIOS: Elétrons (e⁻)
    Portadores MINORITÁRIOS: Lacunas (h⁺)
```

#### 8.2.2 Semicondutor Tipo P (Aceitador de Elétrons)

Adiciona-se um elemento da **coluna III** da tabela periódica (3 elétrons de valência): Boro (B), Alumínio (Al) ou Gálio (Ga).

```
    SEMICONDUTOR TIPO P (com Boro):

         Si        Si        Si
        ╱│╲      ╱│╲      ╱│╲
    ───Si─Si─Si─[B]─Si─Si─Si─Si───
        ╲│╱      ╲│○╱      ╲│╱
         Si        Si        Si
                   ↑
                   LACUNA (ausência de e⁻ — comporta como carga +)
                   Portador majoritário: lacunas (positivo → Tipo P)

    Portadores MAJORITÁRIOS: Lacunas (h⁺)
    Portadores MINORITÁRIOS: Elétrons (e⁻)
```

### 8.3 A Junção P-N: O Coração dos Semicondutores

Quando colocamos um material tipo P em contato com um tipo N, forma-se a **junção P-N** — a base de todos os dispositivos semicondutores.

#### 8.3.1 Formação da Zona de Depleção

```
    JUNÇÃO P-N RECÉM-FORMADA (sem tensão aplicada):
    
    ┌──────────────────┬──────────────────┐
    │  REGIÃO P        │    REGIÃO N       │
    │  ○ ○ ○ ○ ○ ○   │   • • • • • •    │
    │  ○ ○ ○ ○ ○ ○   │   • • • • • •    │
    │  (lacunas)       │   (elétrons)      │
    └──────────────────┴──────────────────┘
                 ↓ Difusão ↓
    ┌──────────────────────────────────────┐
    │  P        │ ZONA DE  │     N          │
    │  ⊕ ⊕ ⊕   │ DEPLEÇÃO │  ⊖ ⊖ ⊖       │
    │  ⊕ ⊕ ⊕   │ (vazia!) │  ⊖ ⊖ ⊖       │
    │          ←──────────→                │
    │          Campo E →→→→                │
    │          Barreira: ≈ 0,6–0,7 V (Si)  │
    └──────────────────────────────────────┘
    
    Difusão cria campo elétrico interno
    Campo cria barreira de potencial ≈ 0,6 V (Si) ou 0,3 V (Ge)
```

#### 8.3.2 Polarização Direta (Forward Bias)

```
    (+) ──── P │ N ──── (-)
    
    Tensão externa > barreira (0,6 V para Si):
    → Campo externo OPÕE ao campo interno
    → Zona de depleção ESTREITA
    → Corrente FLUI!
    
    Curva: I cresce exponencialmente com V
    Acima de ≈ 0,7 V: corrente cresce muito rápido
```

#### 8.3.3 Polarização Reversa (Reverse Bias)

```
    (-) ──── P │ N ──── (+)
    
    Tensão externa REFORÇA o campo interno:
    → Zona de depleção ALARGA
    → Praticamente NENHUMA corrente flui
    → Apenas corrente de fuga minúscula (nA)
    
    Exceção: tensão reversa muito alta → AVALANCHE (ruptura)
```

### 8.4 Outros Semicondutores Importantes

| Material | Band Gap | Cor LED | Frequência | Aplicação |
|---------|---------|---------|------------|----------|
| Si | 1,12 eV | Infravermelho | DC–GHz | Transistores, diodos |
| Ge | 0,67 eV | Infravermelho | DC–GHz | Diodos sinal (legado) |
| GaAs | 1,42 eV | Infravermelho | DC–THz | LEDs IR, laser, RF |
| GaP | 2,26 eV | Verde/Amarelo | — | LEDs verdes antigos |
| GaN | 3,4 eV | Azul/UV | GHz | LEDs azuis, 5G, EV |
| SiC | 3,26 eV | UV | GHz | Potência em alta temp. |
| InGaN | 2,5–3,4 eV | Azul/Verde | — | LEDs brancos modernos |

> 🏆 **Nobel de Física 2014:** Isamu Akasaki, Hiroshi Amano e Shuji Nakamura ganharam o Prêmio Nobel pela invenção do **LED azul** (GaN), que tornou possível a iluminação LED branca eficiente — revolucionando o consumo de energia mundial.

### 🎬 Vídeos Recomendados — Semicondutores

- 📺 [**Lesics** (legendado PT) — Como funciona um Semicondutor](https://www.youtube.com/watch?v=tz62t-s_FRw)
- 📺 [**Transistor Man** — Dopagem tipo N e P animada](https://www.youtube.com/watch?v=IcrBqCFLHIY)
- 📺 [**NHK World Documentary** — A invenção do LED azul](https://www.youtube.com/watch?v=lZuuB5YXLXQ)

### 🎯 Exercícios do Capítulo 8

**1.** Qual é a diferença fundamental entre um semicondutor tipo N e tipo P?

**2.** Por que a zona de depleção de uma junção P-N é chamada de "zona de depleção"?

**3.** Uma junção P-N de silício precisa de qual tensão mínima (aproximada) para entrar em condução na polarização direta?

**4.** Por que o GaN (nitreto de gálio) está substituindo o Si em aplicações de eletrônica de potência em veículos elétricos?

> 📝 **Gabarito:**  
> 1) Tipo N: portadores majoritários são elétrons (dopagem com elemento da coluna V). Tipo P: portadores majoritários são lacunas (dopagem com elemento da coluna III).  
> 2) Porque a região foi "depletada" (esvaziada) de portadores livres pela recombinação de elétrons e lacunas na interface, formando uma barreira sem portadores móveis.  
> 3) ≈ 0,6 a 0,7 V (tensão de barreira da junção P-N de Si)  
> 4) GaN tem band gap maior (3,4 eV vs 1,12 eV do Si): suporta tensões mais altas, opera em temperaturas mais elevadas, tem menor resistência em condução (RDS_on menor) e pode comutar muito mais rápido (menos perdas).


---

<a name="cap9"></a>
## 📗 Capítulo 9 — Diodos: Tipos e Aplicações

### 9.1 O Diodo Retificador

O **diodo** é o componente semicondutor mais simples: uma junção P-N com dois terminais — **Ânodo** (A, lado P) e **Cátodo** (K, lado N).

```
    SÍMBOLO DO DIODO:
    
         A (Ânodo)     K (Cátodo)
              │              │
              ▼
         ─────►|─────
                ↑
                Barra = Cátodo (K)
                Triângulo aponta o sentido da corrente convencional
    
    CONDUTOR quando: V_AK > +0,6 V (Si) → polarização direta
    BLOQUEADO quando: V_AK < +0,6 V → polarização reversa
```

#### 9.1.1 Curva Característica I-V do Diodo

```
    Corrente (I)
         ↑
    Imax─┤                          /
         │                        /
     100─┤                      /
      mA │                    /
         │                  /
      20─┤                /
      mA │______________/________________→ Tensão (V)
         │  ←Ruptura     │    0,6  0,7 V
      µA─┤ ↑Corrente    │
         │  reversa     │
         │  (leakage)   │
         ↓ (negativo)   └── Zona morta (0 a 0,6V)
    
    Equação de Shockley:
    I = Is × (e^(V/Vt) - 1)
    
    Vt = kT/q ≈ 26 mV a 25°C (tensão térmica)
    Is = corrente de saturação reversa (pA para diodos Si)
```

### 9.2 Retificação: Convertendo CA em CC

A principal aplicação do diodo é **retificar** corrente alternada (CA), convertendo-a em corrente contínua (CC):

#### 9.2.1 Retificador de Meia Onda

```
    Circuito:
    Vs (CA) ──[D1]──┬── Vout (CC pulsada)
                    │
                   [RL]
                    │
                   GND

    Entrada (CA):    ∿∿∿∿∿∿∿∿∿∿
    Saída (CC):      _╱‾╲__╱‾╲__  (só meio ciclo positivo)
    
    Vout_médio = Vpico / π = 0,318 × Vpico
    
    Eficiência: 40,6% (desperdício do semiciclo negativo)
    Ripple: 121% → filtro grande necessário
```

#### 9.2.2 Retificador de Onda Completa em Ponte (Ponte de Graetz)

```
    Circuito:
         D1      D3
    A ──►|──┬──►|── +Vout
            │
    Vs CA  [RL]  → GND
            │
    B ──►|──┴──►|── -Vout
         D2      D4
    
    Mais simples:

         +────[D1]────+────[D3]────+
         │            │            │
    AC ──┤            RL           ├── AC
         │            │            │
         +────[D4]────+────[D2]────+
                      │
                      GND
    
    Saída (CC):   ╱‾╲╱‾╲╱‾╲╱‾╲  (ambos ciclos aproveitados)
    
    Vout_médio = 2 × Vpico / π = 0,636 × Vpico
    Ripple: 48% → filtro menor que meia onda
    
    MÓDULO KBP-série (pontes prontas): KBP206 (2A/600V)
```

#### 9.2.3 Filtro com Capacitor

```
    Com capacitor após a ponte:
    
    Ponte ──[C]──┬── Vout_DC_filtrada
                 │
                [RL]
                 │
                GND
    
    Sem filtro:  ╱‾╲╱‾╲╱‾╲  (pulsante)
    Com filtro:  ─────────  (praticamente contínuo, com pequeno ripple)
    
    Ripple (Vpp) ≈ Iout / (f × C)
    
    Exemplo: Fonte 12 V / 1 A, f=120 Hz (onda completa):
    C = I / (f × Vripple) = 1 / (120 × 1) = 8.333 µF → usar 10.000 µF
```

### 9.3 Tipos de Diodos

#### 9.3.1 Diodo Zener

O **diodo Zener** opera em **polarização reversa** e mantém a tensão estável — é o regulador de tensão mais simples.

```
    SÍMBOLO:                CIRCUITO REGULADOR:
         A     K
    ─────►|Z─────           Vin ──[Rs]──┬── Vout = Vz
                                        │
                                       [Dz] (Zener)
                                        │
                                       GND
    
    Condição: Vin > Vz (tensão Zener)
    Vout = Vz (constante, independe de Vin ou Iout, dentro dos limites)
    
    Rs = (Vin - Vz) / (Iz + IL_max)
    Pz_max = Vz × Iz_max   (nunca ultrapassar!)
    
    Valores comerciais: 2,7V, 3,3V, 3,9V, 4,7V, 5,1V, 6,2V, 8,2V, 12V...
    Potências: 0,5W, 1W, 3W, 5W
    
    EXEMPLO: Regular 5V a partir de 9V (Iz=10mA, IL=20mA):
    Rs = (9 - 5) / (0,010 + 0,020) = 4 / 0,030 = 133 Ω → usar 120 Ω
    Prs = (Vin-Vz)²/Rs = 16/120 = 133 mW → usar resistor 1/4W
```

#### 9.3.2 LED (Light Emitting Diode)

O **LED** é um diodo que emite luz quando polarizado diretamente. Cada cor tem uma tensão direta (Vf) diferente:

```
    SÍMBOLO DO LED:
    
         A ──►|─── K
               ↑↑
               luz

    CORES E TENSÕES TÍPICAS:
    ┌──────────┬──────────┬──────────────────────┐
    │  Cor     │  Vf (V)  │  Material            │
    ├──────────┼──────────┼──────────────────────┤
    │ Infraverm│ 1,2–1,5  │  GaAs                │
    │ Vermelho │ 1,8–2,2  │  GaAsP / AlGaInP     │
    │ Laranja  │ 2,0–2,2  │  AlGaInP             │
    │ Amarelo  │ 2,0–2,5  │  AlGaInP             │
    │ Verde    │ 2,0–3,5  │  GaP / InGaN         │
    │ Azul     │ 3,0–3,5  │  InGaN               │
    │ Branco   │ 3,0–3,5  │  InGaN + fósforo     │
    │ UV       │ 3,5–4,0  │  GaN                 │
    └──────────┴──────────┴──────────────────────┘
```

**Calculando o resistor limitador de corrente:**
```
    VCC ──[Rs]──[LED]── GND
    
    Rs = (VCC - Vf) / If
    
    EXEMPLO: LED vermelho (Vf=2V, If=20mA) em VCC=5V:
    Rs = (5 - 2) / 0,020 = 150 Ω
    
    EXEMPLO: LED branco (Vf=3,3V, If=20mA) em VCC=5V:
    Rs = (5 - 3,3) / 0,020 = 85 Ω → usar 82 Ω ou 100 Ω
    
    LED RGB: 3 LEDs internos (R, G, B) com 4 terminais (ânodo ou cátodo comum)
```

#### 9.3.3 Diodo Schottky

Diodo de **barreira metálica**, sem camada de lacunas — extremamente rápido e baixa queda de tensão:

```
    Características:
    Vf = 0,2–0,3 V  (vs 0,6–0,7 V do Si normal)
    Velocidade de comutação: < 1 ns (muito rápido)
    Sem armazenamento de carga → sem recuperação reversa
    
    Usos: retificadores de fontes chaveadas, proteção reversa de bateria,
          detector de RF, lógica Schottky TTL
    
    Modelos: 1N5817 (1A/20V), 1N5819 (1A/40V), BAT43 (200mA sinal)
```

#### 9.3.4 Diodo Varicap (Varactor)

Capacitância variável controlada por tensão reversa — usado em sintonizadores de FM/TV e PLL:

```
    Ct = C0 / (1 + V_rev/Vj)^n
    
    Quanto maior a tensão reversa → maior zona de depleção → menor capacitância
    Controle eletrônico de frequência (VCO)
```

### 9.4 Tabela Resumo dos Tipos de Diodos

| Tipo | Símbolo | Vf | Corrente | Aplicação Principal |
|------|---------|-----|---------|---------------------|
| Retificador | ►| | 0,6–0,7 V | A – kA | Fontes de alimentação |
| Schottky | ►| (barra dobrada) | 0,2–0,3 V | mA – A | Fontes chaveadas, RF |
| Zener | ►|Z | — (reverso) | mA – A | Regulação de tensão |
| LED | ►|▲ | 1,5–4,0 V | mA – A | Iluminação, indicação |
| Fotodiodo | ►| ↓ | — | µA | Sensor de luz, receptor |
| Varicap | ►|▻ | — (reverso) | µA | Sintonia, VCO, PLL |
| Túnel | ►| | < 0 | mA | Osciladores µW, digital |

### 🎬 Vídeos Recomendados — Diodos

- 📺 [**Make it Extreme BR** — Fonte de alimentação com diodos e capacitores](https://www.youtube.com/watch?v=9kgMNhqVNnw)
- 📺 [**Desbravando a Eletrônica** — Diodo LED: como calcular resistor](https://www.youtube.com/watch?v=J2D7q7H4t8U)
- 📺 [**Professor Yuri Martins** — Diodo Zener e regulação de tensão](https://www.youtube.com/watch?v=_PfgDlfuJIk)
- 📺 [**Eletrônica Total** — Ponte retificadora na prática](https://www.youtube.com/watch?v=mJivMnXkjWE)

### 🎯 Exercícios do Capítulo 9

**1.** Projete uma fonte de alimentação simples com as seguintes especificações:
   - Entrada: 127 V CA / 60 Hz
   - Saída: 12 V CC / 500 mA
   - Use: transformador, ponte de diodos, capacitor filtro
   - Calcule o ripple com o capacitor escolhido.

**2.** Calcule o resistor limitador para 3 LEDs vermelhos (Vf=2V, If=20mA) em **série** alimentados por 12 V.

**3.** Um diodo Zener 5V1 (5,1V/1W) é usado para regular a saída. Calcule:
   - a) A corrente máxima no Zener
   - b) O resistor série para Vin=12V com Iz_mín=5mA e IL=50mA

> 📝 **Gabarito:**  
> 2) Vf_total = 3×2 = 6V; Rs = (12-6)/0,020 = 300 Ω  
> 3a) Iz_max = Pz/Vz = 1/5,1 = 196 mA  
> 3b) Rs = (12-5,1)/(0,005+0,050) = 6,9/0,055 = 125 Ω → usar 120 Ω (verificar: P_Rs = 6,9²/120 = 397 mW → usar 1/2 W)

---

<a name="cap10"></a>
## 📗 Capítulo 10 — Transistores BJT e MOSFET

### 10.1 O Transistor BJT (Bipolar Junction Transistor)

O **transistor BJT** é um dispositivo semicondutor com **três terminais** e **duas junções P-N**. É controlado por **corrente**.

```
    TIPOS:

    TRANSISTOR NPN:              TRANSISTOR PNP:

        C (Coletor)                   C (Coletor)
        │                             │
    B──┤                         B──┤
    (Base) NPN                   (Base) PNP
        │                             │
        E (Emissor)                   E (Emissor)

    Símbolo NPN:     Símbolo PNP:
    
       C                C
       │                │
    ───┤                ├───
    B  │►               │◄  B
       │                │
       E                E
    (seta saindo)    (seta entrando)
```

#### 10.1.1 Funcionamento do BJT NPN

```
    REGIÕES DE OPERAÇÃO:

    1. CORTE (chave aberta):
       Vbe < 0,6V → Ic ≈ 0 (transistor não conduz)
       → Usado para DESLIGAR cargas

    2. ATIVA (amplificação):
       Vbe ≈ 0,6V → Ic = hFE × Ib
       hFE (ganho de corrente) = 50 a 500 típico
       → Usado para AMPLIFICAR sinais

    3. SATURAÇÃO (chave fechada):
       Ib grande → Ic = Vcc/Rc (máximo de corrente)
       Vce_sat ≈ 0,2V → Transistor totalmente ligado
       → Usado para LIGAR cargas (chave digital)

    Relação fundamental:
    Ic = hFE × Ib
    Ie = Ib + Ic = (hFE + 1) × Ib ≈ hFE × Ib
```

#### 10.1.2 Transistor como Chave (Driver Digital)

```
    Circuito de chave com BJT NPN:

    VCC (+12V)
      │
    [Carga: motor, LED, relé]
      │
      C (Coletor)
      │
    B─┤  NPN
      │
      E (Emissor)
      │
     GND

    [Rb]──── Base (B)
     │
    Sinal de controle (µC 3,3V ou 5V)

    Cálculo do resistor de base (Rb):
    
    Ib_min = Ic / hFE_min      (corrente de base mínima para saturar)
    Ib_real = 5 × Ib_min       (overdrive de base, garantia de saturação)
    Rb = (V_controle - Vbe) / Ib_real
    
    EXEMPLO: Motor 12V/200mA, µC 5V, BC547 (hFE_min=110):
    Ib_min = 0,200 / 110 = 1,8 mA
    Ib_real = 5 × 1,8 = 9 mA (overdrive 5x)
    Rb = (5 - 0,6) / 0,009 = 489 Ω → usar 470 Ω
    
    DIODO DE RODA LIVRE (flyback): SEMPRE colocar em paralelo com cargas indutivas!
    ┌──[Motor]──┐
    │    ↑↑↑    │  ← Diodo 1N4007 (ânodo para GND, cátodo para VCC)
    │  (bobina) │     protege o transistor contra pico de tensão
    └───────────┘
```

#### 10.1.3 Transistor como Amplificador

```
    AMPLIFICADOR COM EMISSOR COMUM:

    VCC (+12V)
      │
    [Rc = 2,2kΩ]
      │
      C (Coletor)──── Saída (Vout)
      │
    B─┤  BC547
      │
      E (Emissor)──── GND
      │
    [Re = 470Ω] (degeneração, estabilidade)

    Ganho de tensão: Av = -Rc / Re = -2200/470 ≈ -4,7×
    (negativo = inversão de fase)
    
    Ponto Q (quiescente): Ic_Q ≈ VCC/2 = 6V/Rc → operação linear
```

### 10.2 Transistor MOSFET

O **MOSFET** (Metal-Oxide-Semiconductor Field-Effect Transistor) é controlado por **tensão** na porta (Gate). Consome muito menos corrente de controle que o BJT.

```
    TIPOS DE MOSFET:

    N-CHANNEL (modo enriquecimento):    P-CHANNEL:
    
         D (Dreno)                          D (Dreno)
         │                                  │
    G───┤                              G───┤
    (Gate) NMOS ↑                      (Gate) PMOS ↓
         │                                  │
         S (Source)                         S (Source)

    Símbolo NMOS:        Símbolo PMOS:
    
        D                   D
        │                   │
    ───┤│                ├│───
    G  │                 │  G
       │                 │
        S                   S
    (seta entrando)     (seta saindo)
```

#### 10.2.1 Funcionamento do MOSFET N-Channel

```
    OPERAÇÃO:

    Vgs < Vth (threshold): MOSFET DESLIGADO
    Vgs > Vth: MOSFET LIGADO (canal formado entre D e S)
    
    REGIÃO ÔHMICA (triodo):
    Vds < Vgs - Vth → MOSFET como resistor variável (RDS_on)
    RDS_on × Id = Vds_sat (muito pequena!)
    
    REGIÃO DE SATURAÇÃO (pinch-off):
    Vds > Vgs - Vth → MOSFET como fonte de corrente
    
    VANTAGENS do MOSFET vs BJT:
    ✅ Controlado por tensão (impedância de entrada alta, gate corrente ≈ 0)
    ✅ RDS_on muito baixo (mΩ em MOSFETs de potência modernos)
    ✅ Sem corrente de armazenamento → comutação mais rápida
    ✅ Paralelismo fácil (mais estável termicamente)
    ✅ Sem offset de Vbe (pode operar com Vgs de 3,3V em MOSFETs lógicos)
```

#### 10.2.2 MOSFET de Potência em Aplicações Práticas

```
    CONTROLE DE MOTOR CC COM MOSFET (IRLZ44N):

    +12V
      │
    [Motor CC]
      │
      D (Dreno)
      │
    G─┤  IRLZ44N  ← Vgs_th = 1V, RDS_on = 28mΩ
      │
      S (Source)
      │
     GND

    Arduino Pin──[Rg=100Ω]──Gate  (R gate limita oscilações)
    
    Cálculo de dissipação térmica:
    P_dissipada = Id² × RDS_on = 5² × 0,028 = 0,7 W
    Temperatura da junção: Tj = Ta + P × Rθja = 25 + 0,7 × 62 = 68°C ✅

    COMPARATIVO BJT vs MOSFET para chaveamento:
    ┌─────────────────┬──────────┬──────────┐
    │ Parâmetro       │  BJT     │  MOSFET  │
    ├─────────────────┼──────────┼──────────┤
    │ Controle        │ Corrente │ Tensão   │
    │ Vce/Vds_sat     │ 0,2 V    │ mV–10s   │
    │ Velocidade      │ Médio    │ Rápido   │
    │ Corrente gate   │ mA (Ib)  │ ≈ 0 (CC) │
    │ RDS_on          │ N/A      │ mΩ–Ω    │
    │ Custo           │ Baixo    │ Médio    │
    │ Uso típico      │ Sinal    │ Potência │
    └─────────────────┴──────────┴──────────┘
```

### 10.3 IGBT — Para Aplicações de Alta Potência

O **IGBT** (Insulated Gate Bipolar Transistor) combina a facilidade de controle do MOSFET com a capacidade de corrente do BJT:

```
    IGBT = MOSFET (gate) + BJT (potência)
    
    Vantagens:
    - Gate controlado por tensão (como MOSFET)
    - Condução bipolar (como BJT) → maior densidade de corrente
    - Tensões de até 6,5 kV, correntes de kA
    - Frequência: até 20-50 kHz (inversores industriais)
    
    Aplicações: inversores solares, drives de motor (WEG CFW), UPS,
                carregadores EV rápidos, ar-condicionado inverter
```

### 🎬 Vídeos Recomendados — Transistores

- 📺 [**Canal do Técnico** — BJT como chave e amplificador](https://www.youtube.com/watch?v=ABXhXuCZbBQ)
- 📺 [**Filipe Flop** — MOSFET: teoria e aplicações práticas](https://www.youtube.com/watch?v=FcoU5Jh-RNI)
- 📺 [**Eletrogate** — Controlando motores com transistor e Arduino](https://www.youtube.com/watch?v=_nkIJ5RmUE4)
- 📺 [**WR Kits** — Simulação de transistor no Proteus](https://www.youtube.com/watch?v=vBF2jWrGpR4)

### 🎯 Exercícios do Capítulo 10

**1.** Um LED de alto brilho (If=50mA) precisa ser acionado por um Arduino (saída máx. 40mA). Projete o circuito com BJT BC548 (hFE=200), alimentação 5V, calculando Rb.

**2.** Qual é a vantagem de usar um MOSFET IRLZ44N ao invés de um BJT BD135 para controlar um motor de 3A? Calcule a potência dissipada em cada caso (Vce_sat do BD135 = 1V; RDS_on do IRLZ44N = 28mΩ).

**3.** Por que é necessário colocar um diodo flyback em paralelo com uma bobina de relé controlada por transistor?

> 📝 **Gabarito:**  
> 1) Ib_min = 50mA/200 = 0,25mA; Ib_real = 5×0,25 = 1,25mA; Rb = (5-0,6)/0,00125 = 3,52kΩ → usar 3,3kΩ  
> 2) BD135: P = Vce×Ic = 1×3 = **3W** (necessita heatsink!); IRLZ44N: P = RDS_on×I² = 0,028×9 = **0,25W** (sem heatsink!). MOSFET é ≈12× mais eficiente.  
> 3) Quando o transistor desliga, a bobina do relé reage contra a queda de corrente, gerando uma tensão reversa alta (V = L×dI/dt) que pode destruir o transistor. O diodo flyback conduz essa corrente de volta para a bobina, protegendo o transistor.


---

<a name="cap11"></a>
## 📗 Capítulo 11 — Amplificadores Operacionais (Op-Amps)

### 11.1 O Que é um Amplificador Operacional?

O **Amplificador Operacional** (op-amp) é um CI analógico de altíssimo ganho com duas entradas e uma saída. É o componente mais versátil da eletrônica analógica.

```
    SÍMBOLO DO OP-AMP:

        Vin+ ──────┐
                   │
               +   │
    V+ supply ─┤  >├──── Vout
    V- supply ─┤   │
               -   │
                   │
        Vin- ──────┘

    Simplificado:
         (+)
          ├──►
    ─────(+)  \
               >──── Vout
    ─────(-)  /
          ├──►
         (-)
    
    Entradas:
    (+) = entrada não-inversora
    (-) = entrada inversora
    
    Parâmetros ideais (modelo simplificado):
    • Ganho de malha aberta: A_OL = ∞ (real: 10⁵ a 10⁷)
    • Impedância de entrada: Rin = ∞ (real: MΩ a GΩ)
    • Impedância de saída: Rout = 0 (real: < 100 Ω)
    • Banda de frequência: ∞ (real: limitado pelo GBW)
    • Tensão de offset: 0 (real: µV a mV)
```

### 11.2 Regras de Ouro do Op-Amp Ideal (Malha Fechada)

```
    REGRA 1: V(+) = V(-)   [as entradas ficam no mesmo potencial]
    REGRA 2: Iin(+) = Iin(-) = 0   [nenhuma corrente entra nas entradas]
    
    Estas regras valem APENAS com realimentação negativa!
```

### 11.3 Configurações Fundamentais

#### 11.3.1 Amplificador Inversor

```
    Vin ──[Rin]──┬── (-) ──[Rf]──── Vout
                 │
                GND ──── (+)

    Ganho: Av = -Rf / Rin
    
    O sinal de saída é INVERTIDO (negativo)
    A entrada (+) fica em GND (ou referência)
    
    EXEMPLO: Rin=10kΩ, Rf=100kΩ
    Av = -100k/10k = -10
    Vin = 0,5V → Vout = -5V
    
    Impedância de entrada: Zin = Rin
```

#### 11.3.2 Amplificador Não-Inversor

```
    Vin ──────────────── (+)
                          │
    GND ──[R1]──┬── (-) ──┘
                │
               [Rf]
                │
               Vout

    Ganho: Av = 1 + Rf/R1
    
    O sinal de saída mantém a MESMA fase
    
    EXEMPLO: R1=10kΩ, Rf=90kΩ
    Av = 1 + 90k/10k = 10
    Vin = 0,5V → Vout = 5V
    
    Impedância de entrada: Zin ≈ ∞ (muito alta)
```

#### 11.3.3 Seguidor de Tensão (Buffer)

```
                ┌──────────────────┐
                │                  │
    Vin ──────── (+)               │
                    >──── Vout ────┘
               (-) /

    Ganho: Av = 1 (tensão de saída = tensão de entrada)
    
    Aplicação: isolamento de impedâncias (buffering)
    Zin alta → Zout baixa
    
    Exemplo: sensor com alta impedância de saída
    driving um ADC ou display com baixa impedância de entrada
```

#### 11.3.4 Amplificador Diferencial

```
    V1 ──[R1]──── (-)
                     >──── Vout = (V2-V1) × Rf/R1
    V2 ──[R1]──── (+)
                   │
                  [Rf]── GND

    Ganho: Av = Rf / R1
    
    Amplifica a DIFERENÇA entre duas tensões
    Rejeita tensão de modo comum (CMR)
    
    Aplicações: amplificação de sinais de sensores (ponte Wheatstone,
    célula de carga, termopares), ECG, instrumentação
```

#### 11.3.5 Comparador

```
    V_ref ──── (+)
                  >──── Vout = +Vcc ou -Vcc
    V_in  ──── (-)
    
    Sem realimentação → op-amp satura
    Se Vin > Vref → Vout = -Vcc (saída baixa)
    Se Vin < Vref → Vout = +Vcc (saída alta)
    
    DETECTOR DE NÍVEL:
    Vref = 2,5V (divisor resistivo)
    Vin = sensor temperatura (NTC)
    → Aciona alarme quando temperatura supera limiar
    
    Obs: Para comparadores rápidos, usar CI dedicado (LM393, LM311)
```

### 11.4 Filtros Ativos com Op-Amp

Os filtros ativos usam op-amps + resistores + capacitores para filtrar frequências de forma precisa:

```
    FILTRO PASSA-BAIXA (Low Pass):
    Vin ──[R]──┬── (-) ──[Rf]──── Vout
               │
              [C]── GND

    Frequência de corte: fc = 1 / (2π × R × C)
    Acima de fc: ganho cai 20 dB/decade

    FILTRO PASSA-ALTA (High Pass):
    Vin ──[C]──┬── (-) ──[Rf]──── Vout
               │
              [R]── GND

    FILTRO PASSA-FAIXA (Band Pass):
    Combinação de passa-baixa + passa-alta
    
    EXEMPLO — EQ de áudio (equalizador de 3 bandas):
    Graves: passa-baixa  fc = 300 Hz
    Médios: passa-faixa  300 Hz – 3 kHz
    Agudos: passa-alta   fc = 3 kHz
```

### 11.5 Op-Amps Populares no Brasil

| CI | Alimentação | GBW | Slew Rate | Corrente | Uso principal |
|----|------------|-----|-----------|---------|--------------|
| **LM741** | ±5–18V | 1 MHz | 0,5 V/µs | 50 mA | Clássico educacional |
| **LM358** | 3–32V | 1 MHz | 0,6 V/µs | 45 mA | Single supply, geral |
| **NE5532** | ±5–15V | 10 MHz | 9 V/µs | 50 mA | Áudio HiFi profissional |
| **TL071** | ±5–18V | 3 MHz | 13 V/µs | 18 mA | Áudio, instrumentação |
| **LM393** | 2–36V | — | — | 50 mA | Comparador (saída OC) |
| **INA128** | ±2,25–18V | 1,3 MHz | 4 V/µs | 5 mA | Amp. instrumentação CMRR=120dB |

### 🎬 Vídeos Recomendados — Op-Amps

- 📺 [**Canal Filipe Flop** — Op-Amp: as 5 configurações mais usadas](https://www.youtube.com/watch?v=aYpC8i6mRbM)
- 📺 [**Dicas de Eletrônica** — LM358 na prática: projetos reais](https://www.youtube.com/watch?v=pGvnTZVi5dA)
- 📺 [**Mundo dos Makers** — Filtros ativos com TL072](https://www.youtube.com/watch?v=VTjPEGn0vhM)
- 📺 [**Henrique Cuzziol** — Amplificadores operacionais para iniciantes](https://www.youtube.com/watch?v=kAjFbKK4DhM)

### 🎯 Exercícios do Capítulo 11

**1.** Projete um amplificador inversor com ganho de -20 usando o LM358, alimentado em +5V/GND (single supply). Use R1 = 10 kΩ.

**2.** Um sensor de pressão fornece tensão de 0 a 100 mV. Você precisa converter para 0 a 5V para um ADC. Qual configuração de op-amp usar? Qual o ganho necessário? Projete o circuito.

**3.** Calcule a frequência de corte de um filtro passa-baixa com R = 15 kΩ e C = 10 nF.

> 📝 **Gabarito:**  
> 1) Rf = 20 × R1 = 20 × 10k = 200 kΩ (usar 220 kΩ padrão). Vref(+) = 2,5V (R_ref igual ao paralelo R1||Rf = 10k||220k ≈ 9,6kΩ, usar 10kΩ para minimizar offset).  
> 2) Amplificador não-inversor. Av = 5V/0,1V = 50. Rf = (50-1) × R1 = 49 × 10k = 490kΩ → usar 470kΩ ou 499kΩ (1%).  
> 3) fc = 1/(2π × 15×10³ × 10×10⁻⁹) = 1/(2π × 150×10⁻⁶) = 1/0,000942 ≈ **1.061 Hz ≈ 1 kHz**

---

<a name="cap12"></a>
## 📗 Capítulo 12 — Eletrônica Digital e Portas Lógicas

### 12.1 O Mundo Digital vs Analógico

```
    MUNDO ANALÓGICO:           MUNDO DIGITAL:
    
    Tensão (V)                 Tensão (V)
        5 |  /\   /\               5 | ‾‾‾|    |‾‾‾|
        3 | /  \ /  \              3 |    |    |   |
        1 |/    V    \             1 |    |    |   |
        0 └────────────           0 └────|____|───
          tempo                     tempo
    
    Infinitos valores possíveis   Apenas 2 estados:
    Ex: 2,37 V; 0,5 V...          0 (baixo) ou 1 (alto)
    
    Problema: suscetível a ruído  Vantagem: imune a ruído!
    
    Famílias lógicas — níveis de tensão:
    ┌─────────┬──────────┬──────────┬──────────┐
    │ Família │ Vcc      │ V_LOW    │ V_HIGH   │
    ├─────────┼──────────┼──────────┼──────────┤
    │ TTL 74xx│ 5 V      │ 0–0,8 V  │ 2,4–5 V  │
    │ CMOS    │ 3–18 V   │ 0–1/3Vcc │ 2/3–Vcc  │
    │ 3,3V    │ 3,3 V    │ 0–0,8 V  │ 2,0–3,3V │
    │ Arduino │ 5 V      │ 0–1,5 V  │ 3,0–5 V  │
    └─────────┴──────────┴──────────┴──────────┘
```

### 12.2 Sistemas de Numeração

#### 12.2.1 Binário, Decimal, Hexadecimal

```
    DECIMAL (base 10): 0 1 2 3 4 5 6 7 8 9
    BINÁRIO (base 2):  0 1
    HEXADECIMAL (base 16): 0-9 A B C D E F

    TABELA DE CONVERSÃO:
    ┌────────┬────────┬──────┬────────┐
    │Decimal │Binário │Hexa  │Octal   │
    ├────────┼────────┼──────┼────────┤
    │   0    │  0000  │  0   │   0    │
    │   1    │  0001  │  1   │   1    │
    │   2    │  0010  │  2   │   2    │
    │   3    │  0011  │  3   │   3    │
    │   4    │  0100  │  4   │   4    │
    │   5    │  0101  │  5   │   5    │
    │   6    │  0110  │  6   │   6    │
    │   7    │  0111  │  7   │   7    │
    │   8    │  1000  │  8   │  10    │
    │   9    │  1001  │  9   │  11    │
    │  10    │  1010  │  A   │  12    │
    │  11    │  1011  │  B   │  13    │
    │  12    │  1100  │  C   │  14    │
    │  13    │  1101  │  D   │  15    │
    │  14    │  1110  │  E   │  16    │
    │  15    │  1111  │  F   │  17    │
    │  16    │ 10000  │  10  │  20    │
    │ 255    │11111111│  FF  │  377   │
    └────────┴────────┴──────┴────────┘

    CONVERSÃO BINÁRIO → DECIMAL:
    1011₂ = 1×2³ + 0×2² + 1×2¹ + 1×2⁰
           = 8   +  0   +  2   +  1
           = 11₁₀
    
    CONVERSÃO DECIMAL → BINÁRIO (divisões sucessivas por 2):
    45 ÷ 2 = 22 resto 1   ↑
    22 ÷ 2 = 11 resto 0   ↑  Leia de baixo
    11 ÷ 2 =  5 resto 1   ↑  para cima:
     5 ÷ 2 =  2 resto 1   ↑  101101₂
     2 ÷ 2 =  1 resto 0   ↑
     1 ÷ 2 =  0 resto 1   ↑
```

### 12.3 Portas Lógicas Fundamentais

As **portas lógicas** são os blocos de construção de toda a eletrônica digital. Elas realizam operações da **Álgebra Booleana**.

#### 12.3.1 Porta AND (E)

```
    Símbolo:           Tabela Verdade:
                       A │ B │ S
    A ─┐              ──┼───┼──
       │)──── S = A·B  0 │ 0 │ 0
    B ─┘              0 │ 1 │ 0
                       1 │ 0 │ 0
    "S = 1 somente     1 │ 1 │ 1  ← apenas aqui!
     quando A E B = 1"
    
    CI: 74HC08 (quad 2-input AND)
    Analogia: duas chaves em SÉRIE
```

#### 12.3.2 Porta OR (OU)

```
    Símbolo:           Tabela Verdade:
                       A │ B │ S
    A ─┐              ──┼───┼──
       ├)──── S = A+B  0 │ 0 │ 0  ← apenas aqui!
    B ─┘              0 │ 1 │ 1
                       1 │ 0 │ 1
    "S = 1 quando      1 │ 1 │ 1
     A OU B = 1"
    
    CI: 74HC32 (quad 2-input OR)
    Analogia: duas chaves em PARALELO
```

#### 12.3.3 Porta NOT (NÃO / Inversor)

```
    Símbolo:           Tabela Verdade:
                       A │ S
    A ──[>o]──── S=Ā  ──┼──
                       0 │ 1
    "S é o inverso     1 │ 0
     de A"
    
    CI: 74HC04 (hex inverter)
    Mais simples e poderosa — base da memória (flip-flop SR)
```

#### 12.3.4 Porta NAND (NÃO-E)

```
    Símbolo:           Tabela Verdade:
                       A │ B │ S
    A ─┐              ──┼───┼──
       │)o──── S=A·B̄  0 │ 0 │ 1
    B ─┘              0 │ 1 │ 1
                       1 │ 0 │ 1
    NAND = AND + NOT   1 │ 1 │ 0  ← apenas aqui!
    
    CI: 74HC00 (quad 2-input NAND)
    ★ PORTA UNIVERSAL — qualquer função booleana pode ser implementada
      somente com NANDs!
```

#### 12.3.5 Porta NOR (NÃO-OU)

```
    Símbolo:           Tabela Verdade:
                       A │ B │ S
    A ─┐              ──┼───┼──
       ├)o──── S=A+B̄  0 │ 0 │ 1  ← apenas aqui!
    B ─┘              0 │ 1 │ 0
                       1 │ 0 │ 0
    NOR = OR + NOT     1 │ 1 │ 0
    
    CI: 74HC02 (quad 2-input NOR)
    ★ TAMBÉM PORTA UNIVERSAL!
```

#### 12.3.6 Porta XOR (OU Exclusivo)

```
    Símbolo:           Tabela Verdade:
                       A │ B │ S
    A ─┐              ──┼───┼──
       ├=)──── S=A⊕B  0 │ 0 │ 0
    B ─┘              0 │ 1 │ 1
                       1 │ 0 │ 1
    "S = 1 quando A    1 │ 1 │ 0  ← diferente de OR!
     e B são DIFERENTES"
    
    CI: 74HC86 (quad 2-input XOR)
    Usado em: somadores binários, detecção de paridade, criptografia
```

### 12.4 Circuitos Combinacionais

#### 12.4.1 Meio Somador (Half Adder)

```
    Soma de 2 bits binários:

    A ─┬──[XOR]──── Soma (S)
       │
    B ─┴──[AND]──── Carry (C)

    A │ B │ S │ C
    ──┼───┼───┼──
    0 │ 0 │ 0 │ 0
    0 │ 1 │ 1 │ 0
    1 │ 0 │ 1 │ 0
    1 │ 1 │ 0 │ 1  ← 1+1 = 10 em binário (soma=0, carry=1)
```

#### 12.4.2 Multiplexador (MUX)

```
    MUX 4:1 — escolhe 1 de 4 entradas:

    D0 ─┐
    D1 ─┤            S1 │ S0 │ Saída
    D2 ─┤ MUX 4:1 ───  ──┼───┼──────
    D3 ─┘            0  │  0 │ D0
          │           0  │  1 │ D1
         S0,S1        1  │  0 │ D2
    (seleção)         1  │  1 │ D3

    Aplicação: roteamento de sinais, conversão paralelo-série
```

### 12.5 Flip-Flops: Memória Digital de 1 Bit

O **flip-flop** é o elemento básico de memória digital — armazena 1 bit:

```
    FLIP-FLOP SR (Set-Reset):

    S ──┬──[NAND]──┬── Q
        │         │
    R ──┴──[NAND]──┴── Q̄

    S │ R │ Q │ Estado
    ──┼───┼───┼────────
    0 │ 0 │ Q │ Memória (mantém)
    1 │ 0 │ 1 │ SET (lembra 1)
    0 │ 1 │ 0 │ RESET (lembra 0)
    1 │ 1 │ ? │ Proibido!

    FLIP-FLOP D (Data/Delay):
    A transição do clock (↑) "captura" o valor de D em Q.
    Base de registradores, memórias SRAM e flip-flops de todos os CIs.
    
    Contador de 4 bits com 4 flip-flops D em cascata:
    → Conta de 0 a 15 (0000₂ a 1111₂)
    → Frequência de saída = f_clock / 16
```

### 12.6 CIs Digitais — Família 74HC

```
    FAMÍLIA 74HC (High-speed CMOS):
    Vcc: 2–6 V  |  Velocidade: 20–50 MHz  |  Potência: muito baixa
    
    CÓDIGO: 74HC[função]
    
    74HC00  → 4× NAND 2 entradas
    74HC04  → 6× Inversor (NOT)
    74HC08  → 4× AND 2 entradas
    74HC32  → 4× OR 2 entradas
    74HC74  → 2× Flip-Flop D
    74HC86  → 4× XOR 2 entradas
    74HC138 → Decoder 3-para-8
    74HC245 → Buffer de barramento bidirecional 8 bits
    74HC595 → Registrador de deslocamento 8 bits (SPI → GPIO)
    
    Exemplo de uso do 74HC595 com Arduino:
    3 pinos do Arduino → 8 saídas digitais
    (expansão de portas via SPI)
```

### 🎬 Vídeos Recomendados — Eletrônica Digital

- 📺 [**Curso em Vídeo** — Lógica Digital completa (Gustavo Guanabara)](https://www.youtube.com/watch?v=Uvp8aT21hk4)
- 📺 [**Diolinux** — Sistemas de numeração binário e hexadecimal](https://www.youtube.com/watch?v=AKMX-oJKq3E)
- 📺 [**Canal do Técnico** — Portas lógicas: montagem na protoboard](https://www.youtube.com/watch?v=6Z8MH5OIhh8)
- 📺 [**IFSC Digital** — Flip-Flops e circuitos sequenciais](https://www.youtube.com/watch?v=pFi9UNkw8Yc)
- 📺 [**Ben Eater** (leg. PT) — Construindo um computador do zero](https://www.youtube.com/watch?v=HyznrdDSSGM)

### 🎯 Exercícios do Capítulo 12

**1.** Converta os seguintes números:
   - a) 10110011₂ para decimal
   - b) 175₁₀ para binário
   - c) 0xAB para decimal e binário

**2.** Monte a tabela verdade para a expressão: S = (A AND B) OR (NOT A AND C)

**3.** Um sistema de segurança aciona o alarme (S=1) quando: a porta está aberta (A=1) E o sensor de movimento detectou presença (M=1) E o sistema está armado (AR=1). Escreva a expressão booleana e monte com portas lógicas.

**4.** Quantos flip-flops D em cascata são necessários para dividir uma frequência de 1 MHz por 256?

> 📝 **Gabarito:**  
> 1a) 128+32+16+2+1 = **179₁₀** | 1b) 10101111₂ | 1c) 10×16+11=171₁₀ = 10101011₂  
> 3) S = A AND M AND AR  
> 4) 8 flip-flops (2⁸ = 256)

---

<a name="referencias"></a>
## 📗 Capítulo 13 — Referências, Recursos e Links YouTube

### 13.1 🎬 Canais do YouTube — Eletrônica em Português

#### Iniciantes / Geral
| Canal | Foco | Link |
|-------|------|------|
| **WR Kits** | Projetos práticos, Arduino, eletrônica básica | [youtube.com/@WRKits](https://www.youtube.com/@WRKits) |
| **Brincando com Ideias** | Arduino, automação, IoT | [youtube.com/@BrincandocomIdeias](https://www.youtube.com/@BrincandocomIdeias) |
| **FilipeFlop** | Componentes, módulos, projetos | [youtube.com/@FilipeFlop](https://www.youtube.com/@FilipeFlop) |
| **Eletrogate** | Arduino, eletrônica, robótica | [youtube.com/@Eletrogate](https://www.youtube.com/@Eletrogate) |
| **Eletrônica Fácil** | Teoria + prática para iniciantes | [youtube.com/@ElectronicaFacil](https://www.youtube.com/@ElectronicaFacil) |
| **Curso em Vídeo** | Computação, lógica digital | [youtube.com/@CursoemVideo](https://www.youtube.com/@CursoemVideo) |

#### Técnico / Intermediário
| Canal | Foco | Link |
|-------|------|------|
| **Canal do Técnico** | Curso técnico eletrônica completo | [youtube.com/@CanalDoTecnico](https://www.youtube.com/@CanalDoTecnico) |
| **Dicas de Eletrônica** | Op-amps, fontes, CIs | [youtube.com/@DicasDeEletronica](https://www.youtube.com/@DicasDeEletronica) |
| **Mundo dos Makers** | ESP32, sensores, projetos avançados | [youtube.com/@MundodosMakers](https://www.youtube.com/@MundodosMakers) |
| **Henrique Cuzziol** | Fundamentos teóricos, cálculos | [youtube.com/@HenriqueCuzziol](https://www.youtube.com/@HenriqueCuzziol) |
| **Baba de Robô** | Robótica, controle, CNC | [youtube.com/@BabadeRobo](https://www.youtube.com/@BabadeRobo) |

#### Avançado / Profissional
| Canal | Foco | Link |
|-------|------|------|
| **LAFEPE — UFMG** | Eletrônica universitária | [youtube.com/@LAFEPE](https://www.youtube.com/@LAFEPE) |
| **Prof. Edson Borin** | Sistemas digitais, VHDL | [youtube.com/@EdsonBorin](https://www.youtube.com/@EdsonBorin) |
| **Eletrogate Academy** | Cursos completos pagos | [academy.eletrogate.com](https://academy.eletrogate.com) |

#### Em Inglês (com legendas em PT)
| Canal | Foco |
|-------|------|
| [**EEVblog** (Dave Jones)](https://www.youtube.com/@EEVblog) | Reviews, teoria, osciloscópio |
| [**Ben Eater**](https://www.youtube.com/@BenEater) | Computadores do zero, lógica digital |
| [**Andreas Spiess**](https://www.youtube.com/@AndreasSpiess) | IoT, ESP32, sensores |
| [**GreatScott!**](https://www.youtube.com/@greatscottlab) | Projetos práticos profissionais |
| [**Afrotechmods**](https://www.youtube.com/@Afrotechmods) | Fundamentos de circuitos, PCB |
| [**Robert Feranec**](https://www.youtube.com/@RobertFeranec) | PCB design profissional |

### 13.2 📚 Livros Técnicos Recomendados

| Título | Autor | Nível | Observações |
|--------|-------|-------|------------|
| **Eletrônica** (Vol. 1 e 2) | Albert Paul Malvino | Iniciante/Médio | Referência clássica brasileira |
| **Fundamentos de Eletrônica** | William H. Hayt | Médio | Muito didático, teoria sólida |
| **Arte da Eletrônica** | Horowitz & Hill | Avançado | A bíblia da eletrônica profissional |
| **Eletrônica Digital** | Floyd | Médio | Lógica digital completa |
| **Microeletrônica** | Sedra & Smith | Avançado | Transistores, amplificadores, CIs |
| **Fundamentos de Sistemas Digitais** | Tocci & Widmer | Médio | Digital e VHDL |
| **Eletrônica de Potência** | Ned Mohan | Avançado | Conversores, inversores, drives |

### 13.3 🌐 Sites e Ferramentas Online Gratuitas

| Recurso | Tipo | URL |
|---------|------|-----|
| **Falstad Circuit** | Simulador de circuitos online | [falstad.com/circuit](https://www.falstad.com/circuit) |
| **Tinkercad Circuits** | Simulador + Arduino online | [tinkercad.com/circuits](https://www.tinkercad.com/circuits) |
| **Wokwi** | Simulador Arduino/ESP32 | [wokwi.com](https://wokwi.com) |
| **EasyEDA** | PCB design online gratuito | [easyeda.com](https://easyeda.com) |
| **KiCad** | PCB design open-source | [kicad.org](https://www.kicad.org) |
| **Fritzing** | Diagrama de protoboard | [fritzing.org](https://fritzing.org) |
| **LTSPICE** | SPICE simulador (Analog Devices) | [analog.com/ltspice](https://www.analog.com/en/design-center/design-tools-and-calculators/ltspice-simulator.html) |
| **Resistor Calculator** | Calculadora código de cores | [resistorguide.com](https://www.resistorguide.com/resistor-color-code-calculator/) |
| **All About Circuits** | Referência técnica completa | [allaboutcircuits.com](https://www.allaboutcircuits.com) |
| **Datasheets.com** | Banco de datasheets | [datasheets.com](https://www.datasheets.com) |

### 13.4 🛒 Onde Comprar Componentes no Brasil

| Loja | Tipo | Diferencial |
|------|------|------------|
| **FilipeFlop** | Online | Grande variedade, tutoriais próprios |
| **Eletrogate** | Online | Arduino, módulos, IoT |
| **Baú da Eletrônica** | Físico + Online (SP) | Componentes discretos, mercado a granel |
| **Mouser Electronics** | Online (importação) | Catálogo completo, original |
| **Digi-Key** | Online (importação) | Muito completo, amostras grátis |
| **LCSC** | Online (importação) | SMD a preço baixo, aliado ao EasyEDA |
| **Aliexpress** | Online (importação) | Módulos e kits baratos |

### 13.5 📋 Normas e Regulamentações no Brasil

| Norma | Órgão | Assunto |
|-------|-------|---------|
| **ABNT NBR 5410** | ABNT | Instalações elétricas de baixa tensão |
| **ABNT NBR 14039** | ABNT | Instalações elétricas de média tensão |
| **ABNT NBR IEC 61131** | ABNT | Controladores programáveis (PLC) |
| **ABNT NBR IEC 61800** | ABNT | Acionamentos elétricos de potência variável |
| **INMETRO Portaria 563/14** | INMETRO | Eficiência energética de fontes externas |
| **Resolução ANEEL 414/10** | ANEEL | Condições gerais de fornecimento de energia |
| **Resolução ANEEL 482/12** | ANEEL | Geração distribuída (solar fotovoltaica) |

### 13.6 🔬 Playlists do YouTube — Cursos Completos

| Playlist | Canal | Tópicos |
|----------|-------|---------|
| [Eletrônica Básica — Iniciantes](https://www.youtube.com/watch?v=BHj4q8rU1BI&list=PLx4x_zx8csUgB-y0OIWL8ZvKFUFZXWrJZ) | Canal do Técnico | Ohm, componentes, simulação |
| [Arduino do Zero ao Avançado](https://www.youtube.com/watch?v=P6tVEZwwbQg&list=PLZ8dBTV2_5HTGGtrPxDB7zx33J5y2U5tE) | Brincando com Ideias | Arduino completo |
| [Física — Eletromagnetismo](https://pt.khanacademy.org/science/ap-physics-2) | Khan Academy PT | Teoria elétrica completa |
| [Digital Logic](https://www.youtube.com/watch?v=M0mx8S05v60&list=PLBlnK6fEyqRjMH3mWf6kwqiTbT798eAOm) | Neso Academy (leg) | Digital completo |
| [MOOC Eletrônica para Makers](https://www.coursera.org/learn/electronics) | Coursera | Prático com projetos |

---

## 🧪 Apêndice A — Guia de Medição com Multímetro

```
    MULTÍMETRO DIGITAL (DMM) — Guia Rápido:

    ┌─────────────────────────────────────────────────────┐
    │                ESCALA × MEDIÇÃO                      │
    ├─────────────┬───────────────────────────────────────┤
    │ DCV / VDC   │ Tensão contínua (bateria, fonte DC)   │
    │ ACV / VAC   │ Tensão alternada (tomada 127/220V)    │
    │ DCA / ADC   │ Corrente contínua (em série no circuito) │
    │ Ω           │ Resistência (circuito DESLIGADO!)     │
    │ ))) ou diodo│ Teste de continuidade / diodo         │
    │ hFE         │ Ganho de transistor BJT               │
    │ Hz          │ Frequência de sinal                   │
    │ µF          │ Capacitância                          │
    └─────────────┴───────────────────────────────────────┘

    DICAS DE SEGURANÇA:
    ✅ Nunca meça corrente em tomadas (AC) — faixa de tensão!
    ✅ Nunca meça resistência com circuito energizado
    ✅ Comece sempre pela escala MAIOR para evitar danos
    ✅ Verifique as ponteiras: V/Ω/Hz no terminal COM e V/Ω
    ✅ Para corrente: ponteiras COM e mA (ou A para alta corrente)
    ⚠️ Alerta: Escala errada → queima o fusível interno do multímetro
```

---

## 🧪 Apêndice B — Tabela de Resistores Comerciais (E24)

| Ω | Ω | kΩ | kΩ | MΩ |
|---|---|----|----|----|
| 10 | 12 | 10 | 12 | 1,0 |
| 11 | 13 | 11 | 13 | 1,1 |
| 12 | 15 | 12 | 15 | 1,2 |
| 13 | 16 | 13 | 16 | 1,5 |
| 15 | 18 | 15 | 18 | 1,8 |
| 16 | 20 | 16 | 20 | 2,2 |
| 18 | 22 | 18 | 22 | 2,7 |
| 20 | 24 | 20 | 24 | 3,3 |
| 22 | 27 | 22 | 27 | 3,9 |
| 24 | 30 | 24 | 30 | 4,7 |
| 27 | 33 | 27 | 33 | 5,6 |
| 30 | 36 | 30 | 36 | 6,8 |
| 33 | 39 | 33 | 39 | 8,2 |
| 36 | 43 | 36 | 43 | 10,0 |
| 39 | 47 | 39 | 47 | — |
| 43 | 51 | 43 | 51 | — |
| 47 | 56 | 47 | 56 | — |
| 51 | 62 | 51 | 62 | — |
| 56 | 68 | 56 | 68 | — |
| 62 | 75 | 62 | 75 | — |
| 68 | 82 | 68 | 82 | — |
| 75 | 91 | 75 | 91 | — |
| 82 | 100| 82 | 100| — |
| 91 | — | 91 | — | — |

---

## 🧪 Apêndice C — Fórmulas Essenciais

```
    ┌──────────────────────────────────────────────────────────┐
    │               FÓRMULAS DE REFERÊNCIA RÁPIDA              │
    ├────────────────────────┬─────────────────────────────────┤
    │ Lei de Ohm             │ V = R × I                       │
    │ Potência               │ P = V × I = I²R = V²/R         │
    │ Energia                │ E = P × t (Wh = W × h)         │
    │ Resistores Série       │ Rt = R1+R2+R3+...               │
    │ Resistores Paralelo    │ 1/Rt = 1/R1+1/R2+1/R3+...      │
    │ Divisor Tensão         │ Vout = Vin×R2/(R1+R2)          │
    │ Capacitância           │ Q = C×V; E = ½CV²               │
    │ Cap. Série             │ 1/Ct = 1/C1+1/C2+...            │
    │ Cap. Paralelo          │ Ct = C1+C2+...                   │
    │ Indutância             │ V = L×dI/dt; E = ½LI²           │
    │ Ind. Série             │ Lt = L1+L2+...                   │
    │ Transformador          │ V1/V2 = N1/N2 = I2/I1           │
    │ Freq. RC               │ fc = 1/(2π×R×C)                 │
    │ Freq. LC               │ f0 = 1/(2π√LC)                  │
    │ Constante tempo RC     │ τ = R×C                         │
    │ Constante tempo RL     │ τ = L/R                         │
    │ Ganho inv. op-amp      │ Av = -Rf/Rin                    │
    │ Ganho n-inv. op-amp    │ Av = 1+Rf/R1                    │
    │ Diodo LED (resistor)   │ Rs = (Vcc-Vf)/If                │
    │ Diodo Zener            │ Rs = (Vin-Vz)/(Iz+IL)           │
    │ BJT (saturação)        │ Ib = Ic/(hFE×overdrive)         │
    └────────────────────────┴─────────────────────────────────┘
```

---

## 📝 Notas Finais

Esta apostila é um documento **vivo** — será continuamente atualizada com novos capítulos:

- [ ] **Cap. 14** — Sensores e Transdutores (temperatura, pressão, luz, ultrassom)
- [ ] **Cap. 15** — Microcontroladores: Arduino e ESP32
- [ ] **Cap. 16** — Comunicação Serial: UART, SPI, I²C, 1-Wire
- [ ] **Cap. 17** — Fontes de Alimentação: Linear e Chaveada
- [ ] **Cap. 18** — PCB Design: do Esquemático ao Circuito Impresso
- [ ] **Cap. 19** — Soldagem e Montagem de Circuitos
- [ ] **Cap. 20** — Projetos Integrados: da Ideia ao Produto

---

> 📌 **Elaborado para o Curso Técnico em Eletrônica**  
> Normas: ABNT NBR 5410 | IEC 61131 | IEC 61800 | INMETRO  
> Versão 1.0 — Português do Brasil  
> Contribuições e correções são bem-vindas via Issues e Pull Requests.

