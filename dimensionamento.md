# Dimensionamento Energético - MicroMouse

Este documento apresenta o levantamento de carga e o cálculo de autonomia da bateria para o primeiro plano de controle do MicroMouse.

## 1. Especificação dos Componentes
| Componente | especifição | Quantidade | Corrente (mA) | Tensão | Cálculo da energia consumida por componentes |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Microcontrolador | ESP32 DevKit V1, 30 pinos | 1 | 80 | 3,3V | E = 475,2J |
| Buck converter | LM2596 | 1 | 25 | 7,4V | E = 333J |
| Sensores IR | TCRT5000 | 4 | 25 | 3,3V | E = 475,2J |
| Oonte H | TB6612FNG | 1 | 5 | 3,3V | E = 29,7J |
| Expansor| Shield ESP32, 30 pinos | 1 | 5 | 5V | E = 45J |
| Motor N20 + Encoder |  | 2 | 600 | 6V | E = 6480J |

### Cálculo da Corrente Total ($I_{total}$):
Somando o consumo de todos os componentes operando simultaneamente (considerando os 2 motores do robô):

$$I_{total} = I_{esp32} + I_{buck} + (4 \times I_{ir}) + I_{ponteH} + I_{expansor} + (2 \times I_{motor})$$

$$I_{total} = 80 + 25 + (4 \times 25) + 5 + 5 + (2 \times 600)$$

$$I_{total} = 80 + 25 + 100 + 5 + 5 + 1200 = 1415\text{ mA}$$

---

## 2. Dados da Bateria Selecionada
* **Tipo:** LiPo (Lítio-Polímero) em configuração 2S
* **Tensão:** 7.4 V (Duas células de 3.7V em série)
* **Capacidade ($C_{bat}$):** 1200 mAh

---

## 3. Cálculo de Autonomia

Considerando um fator de segurança de 20% (utilização de apenas 80% da capacidade nominal para preservação e aumento da vida útil da bateria LiPo), o tempo de uso contínuo estimado é dado por:

$$\text{Autonomia} = \frac{C_{bat}}{I_{total}} \times 0.8$$

$$\text{Autonomia} = \frac{1200\text{ mAh}}{1415\text{ mA}} \times 0.8$$

$$\text{Autonomia} \approx 0.848 \times 0.8 \approx 0.678\text{ horas}$$

Convertendo para minutos:
$$\text{Autonomia} \approx 0.678 \times 60 \approx \mathbf{40\text{ minutos}}$$

## Conclusão
Com o consumo total de **1415 mA**, é estimado para o arranjo de baterias de 1200 mAh uma autonomia de aproximadamente **40 minutos** de funcionamento contínuo pro micromouse. Considerando também que a bateria escolhida é recarregável e pode ser recarregada completamnete em um período de até duas horas.
