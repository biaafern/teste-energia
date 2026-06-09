# Dimensionamento Energético - MicroMouse

Este documento apresenta o levantamento de carga e o cálculo de autonomia da bateria para o primeiro plano de controle do MicroMouse.

## 1. Especificação dos Componentes
| Componente | especifição | Quantidade | Corrente (mA) | Tensão | Cálculo da energia consumida por componentes |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Microcontrolador | ESP32 WROOM 32E, 38 pinos | 1 | 80 | 3,3V | E = 475,2J |
| Buck converter | LM2596 | 1 | 25 | 7,4V | E = 333J |
| Sensores IR | TCRT5000 | 3 | 20 | 3,3V | E = 475,2J |
| ponte H | TB6612FNG | 1 | 5 | 3,3V | E = 29,7J |
| Motor N20 + Encoder |  | 2 | 600 | 6V | E = 6480J |

### Cálculo da Corrente Total ($I_{total}$):
Somando o consumo de todos os componentes operando simultaneamente (considerando os 2 motores do robô):

$$I_{total} = I_{esp32} + I_{buck} + (4 \times I_{ir}) + I_{ponteH}  + (2 \times I_{motor})$$
$$I_{\text{total}} = 80 + 25 + 60 + 5 + 1200$$
$$I_{total} = 1370\text{ mA}$$

---

## 2. Dados da Bateria Selecionada
* **Tipo:** LiPo (Lítio-Polímero) em configuração 2S
* **Tensão:** 7.4 V (Duas células de 3.7V em série)
* **Capacidade ($C_{bat}$):** 1200 mAh

---

## 3. Cálculo de Autonomia

Considerando um fator de segurança de 20% (utilização de apenas 80% da capacidade nominal para preservação e aumento da vida útil da bateria LiPo), o tempo de uso contínuo estimado é dado por:

$$\text{Autonomia} = \frac{C_{bat}}{I_{total}} \times 0.8$$

$$\text{Autonomia} = \frac{1200\text{ mAh}}{1370\text{ mA}} \times 0.8$$

$$\text{Autonomia} \approx 0.876 \times 0.8 \approx 0.701\text{ horas}$$

Convertendo para minutos:
$$\text{Autonomia} \approx 0.701 \times 60 \approx \mathbf{42\text{ minutos}}$$

## Conclusão
Com o consumo total de **1370 mA**, é estimado para o arranjo de baterias de 1200 mAh uma autonomia de aproximadamente **42 minutos** de funcionamento contínuo para o Micromouse. Considerando também que a bateria escolhida é recarregável e pode ser recarregada completamente em um período de até duas horas.
