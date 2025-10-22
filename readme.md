# Circuito RC / Prática

Para essa atividade, vamos trabalhar com um circuito resistor-capacitor na prática. O objetivo é fazer um circuito RC com chave para que possa carregar um capacitor, monitorar o monitor serial com os outputs da carga do capacitor (etapa 1) e plotar em um gráfico utilizando python (etapa 2)

### Parte 1: Carregamento do capacitor  

Seguindo as etapas da atividade ponderada da Crishna, utlizando a lista de materiais a seguir, faça um circuito RC capaz de carregar um capacitor na plataforma tinkercad. Verifique sua funcionalidade com base no output da seção do _monitor serial_

lista de materiais:

1. 1 Arduino Uno R3

2. 1 Protoboard

3. 8 Jumpers

4. 1 Interruptor deslizante

5. 1 Capacitor polarizado 10μF / 25V

6. 1 Resistor de 20MΩ

7. 1 Resistor de 100Ω

⚠️ **Entrega Parte 1**: em seu GitHub pessoal (usando sua conta com email Inteli), inserir screenshots de sua tela na plataforma Tinkercad e seu código, além de uma fotografia que demonstre seu Arduino ligado no computador e o seu led aceso. Você também poderá enviar um vídeo que evidencie esse funcionamento.

<br>

### Entrega - Parte 01

📸 **Screenshot do Tinkercad**: 

<div style="text-align: center;">
<img title="Código na IDE" src="assets\tinkercad.png"  style="width: 100%;">
</div>

<br>

🔌 **Código do Tinkercad**: 

```C
int pinoNoRC=0;
int valorLido = 0;
float tensaoCapacitor = 0, tensaoResistor;
unsigned long time;
void setup() {
  Serial.begin(9600);
}
void loop() {
  time = millis();
  valorLido = analogRead(pinoNoRC);
  tensaoResistor = (valorLido * 5.0/1023); // 5V / 1023 degraus = 0.049
  tensaoCapacitor = abs(5.0 - tensaoResistor);
  Serial.print(time); // imprime conteúdo de time no MONITOR GERAL
  Serial.print(" ");
  	Serial.print(tensaoResistor);
 	Serial.print(" ");
    Serial.println(tensaoCapacitor);
 	delay(400);
}
```

<br>

📸 **Vídeo de funcionamento do Arduino**:

`Se demorar para carregar, apenas espere o gif ou acesse ele diretamente da pasta assets: Capacitor.gif`

<div style="text-align: center;">
<img title="Código na IDE" src="assets\Capacitor.gif"  style="width: 100%;">
</div>

<br>

🤖 **Output do monitor serial**:

901 4.57 0.43
1803 4.17 0.83
2706 3.81 1.19
3608 3.48 1.52
4510 3.19 1.81
5412 2.91 2.09
6315 2.66 2.34
7217 2.43 2.57
8120 2.22 2.78
9022 2.03 2.97
9924 1.85 3.15
10826 1.69 3.31
11729 1.55 3.45
12632 1.41 3.59
13534 1.29 3.71
14436 1.18 3.82
15339 1.08 3.92
16241 0.99 4.01
17143 0.90 4.10
18046 0.82 4.18
18949 0.75 4.25
19851 0.69 4.31
20753 0.63 4.37
21656 0.57 4.43
22558 0.52 4.48
23460 0.48 4.52
24364 0.44 4.56
25266 0.40 4.60
26168 0.37 4.63
27070 0.33 4.67
27973 0.30 4.70
28875 0.28 4.72
29777 0.25 4.75
30681 0.23 4.77
31583 0.22 4.78
32485 0.20 4.80
33387 0.18 4.82
34290 0.16 4.84
35192 0.15 4.85
36094 0.14 4.86
36998 0.12 4.88
37900 0.11 4.89
38802 0.10 4.90
39705 0.09 4.91
40607 0.09 4.91
41509 0.08 4.92
42412 0.07 4.93
43315 0.07 4.93
44217 0.06 4.94
45119 0.05 4.95
46022 0.05 4.95
46924 0.04 4.96
47826 0.04 4.96
48729 0.04 4.96
49632 0.03 4.97
50534 0.03 4.97
51436 0.03 4.97
52339 0.03 4.97
53241 0.02 4.98

<br>
<br>

### Parte 2: Simulando Blink Externo

Agora que se tem o output do _monitor serial_ na parte 01, vamos plotar isso em um gráfico na linguagem python com o código a seguir. Espera-se para essa etapa, o código python do gráfico, bem como o output do gráfico dos dados do capacitor da parte 01.

- Código Python do gráfico:

```python
import matplotlib.pyplot as plt
# Seus dados
dados = [
    (0, 5.00, 0.00),
    (401, 4.80, 0.20),
    (803, 4.61, 0.39),
 mantenha esse formato e adicione seus dados do MONITOR SERIAL
]
# Separando os dados
x = [item[0] for item in dados]
y1 = [item[1] for item in dados]
y2 = [item[2] for item in dados]
# Criando o gráfico
plt.figure(figsize=(10, 6))
plt.plot(x, y1, label='Y1')
plt.plot(x, y2, label='Y2')
# Configurando rótulos e título
plt.xlabel('X')
plt.ylabel('Valores')
plt.title('Gráfico de Dispersão')
plt.legend()
# Exibindo o gráfico
plt.grid(True)
plt.show()
```

<br>

📊 **Gráfico**: 

<div style="text-align: center;">
<img title="Código na IDE" src="assets\grafico.png"  style="width: 100%;">
</div>