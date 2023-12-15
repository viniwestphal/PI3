Acesse a página da [Wiki](https://github.com/viniwestphal/PI3/wiki) para ver a documentação completa do projeto.

Veja também o [resumo expandido](https://github.com/viniwestphal/PI3/blob/main/Resumo_Expandido_Vinicius.pdf).

# Proposta de Tema de PI3
Título: Câmera de Filmagem Inteligente para Contagem e Detecção de Veículos

Aluno(s): Vinicius Westphal de Paula

Orientador: Prof. Ênio dos Santos Silva

# Objetivo geral
Implementar uma câmera baseada em microcontroladores capaz de detectar veículos em tempo real.

# Objetivos específicos
- Pesquisa de microcontroladores com suporte à câmera de filmagem;
- Pesquisa de modelos de detecção de objetos para dispositivo de baixa potência;
- Treinar um modelo capaz de detecção de veículos automóveis;
- Implementar e testar o modelo em um microcontrolador;


# Metodologia
Este capítulo trata das ferramentas utilizadas para desenvolvimento do projeto. Em ordem cronológica, foi realizada uma revisão de literatura abordando os conceitos de sistemas embarcados, o uso de módulos de câmera integrados a microcontroladores, os conceitos básicos de aprendizado de máquina voltado à visão computacional para detecção de objetos, e como a implementação de aprendizado de máquina em sistemas embarcados pode ser feita através de TinyML. Em seguida é feita uma análise dos principais modelos de detecção de objetos e suas principais limitações para sistemas embarcados. Por fim busca-se um modelo que tenha uma implementação viável para detecção de veículos a fim de testar seu funcionamento rodando diretamente em um microcontrolador utilizando uma câmera integrada. 

### Sistemas embarcados
Sistemas embarcados são sistemas computacionais especializados, projetados incluindo uma combinação de hardware eletrônico e partes mecânicas junto a software para desempenhar uma função específica. Sistemas embarcados modernos são geralmente baseados em microcontroladores, o que acarreta em restrições em termos de poder de processamento, memória e armazenamento. São otimizados para eficiência e possuem recursos limitados em comparação à sistemas computacionais de uso geral. 

### Microcontroladores
De maneira geral, microcontroladores são circuitos integrados compactos que funcionam como um pequeno computador em um único chip semicondutor. São projetados para uso em aplicações embarcadas, em contraste com os microprocessadores usados em computadores pessoais ou em outra aplicação de propósito geral composta por vários chips discretos. Operam de maneira eficiente com um consumo de potência mínimo, o que os torna ideal para dispositivos alimentados por bateria ou sistemas onde a eficiência de energia é crucial.

Existem diversos microcontroladores disponíveis no mercado que suportam interface à câmera para aplicações diversas. Os mais populares incluem:

- ESP32-CAM: é um microcontrolador que possui uma câmera de vídeo integrada e um leitor para cartão microSD para armazenamento, além de possuir Wi-Fi e Bluetooth integrados. 

- Raspberry Pi: apesar de não ser estritamente um microcontrolador, as placas Raspberry Pi são computadores de placa única (single-board computers) que suportam módulos de câmera, sendo capazes de gerenciar tarefas de processamento de imagem, ainda permitindo uma configuração embarcada. Assim como o ESP32-CAM, também incluem Wi-Fi e leitor para cartão microSD.

- Arduino: o popular microcontrolador Arduino não possui suporte nativo à câmeras, porém existem "shields" para serem usados para interface de câmeras. Entretanto o Arduino também não possui suporte nativo a Wi-Fi e leitor de cartão microSD, o que o torna uma opção menos atrativa em comparação aos demais microcontroladores que já possuem essas funções.

### Aprendizado de máquina
Aprendizado de máquina é um subcampo da Inteligência Artificial (IA) que envolve a criação de algoritmos e modelos que permitem computadores aprender e fazer previsões ou decisões baseado em dados, sem programação explícita. O objetivo primário do aprendizado de máquina é desenvolver algoritmos que possam aprender automaticamente e melhorar a partir de experiência ou informações. Existem vários tipos de aprendizado de máquina, cada um com abordagens distintas para a construção de modelos e a realização de tarefas específicas, com destaque para Aprendizado Supervisionado, Aprendizado Não Supervisionado, Aprendizado Semi-Supervisionado, Aprendizado por Reforço e Aprendizado Profundo.

### Aprendizado Profundo
Aprendizado Profundo (Deep Learning) é uma subárea do aprendizado de máquina baseada em redes neurais artificiais compostas por várias camadas de nós interconectados, também conhecidos como neurônios, organizados da seguinte forma: uma camada de entrada (input layer), uma ou várias camadas ocultas (hidden layers) e uma camada de saída (output layer). A capacidade dessas redes são capazes de aprender padrões complexos e representações a partir de dados brutos têm possibilitado sucesso em tarefas de visão computacional.

### Transferência de Aprendizado
Um dos componentes chave do Aprendizado Profundo inclui a técnica de Transferência de Aprendizado (Transfer Learning). Essa técnica envolve a utilização de modelos pré treinados em grandes bancos de dados e ajustá-los (fine-tuning) para tarefas específicas, ao invés de iniciar o processo de treinamento do zero. Isso poupa recursos computacionais e tempo, permitindo o trabalho com um conjunto de dados menor.
A transferência de aprendizado pode ser feita de diferentes maneiras:

- **Extração de características**: nas camadas iniciais de um modelo pré-treinado, que capturam características gerais, pode-se utilizar um extrator de características fixo. Os pesos dessas camadas são congelados, e apenas as camadas finais são retreinadas no novo conjunto de dados para a tarefa específica. Este método é eficaz quando o novo conjunto de dados é relativamente pequeno ou similar ao conjunto de dados original.

- **Ajuste fino (fine-tuning)**: ao invés de manter as camadas pré-treinadas fixas, os pesos de algumas ou de todas as camadas são ajustados ou refinados usando o novo conjunto de dados. O ajuste fino permite que o modelo se adapte aos detalhes da nova tarefa, ao mesmo tempo em que aproveita o conhecimento adquirido do modelo pré-treinado.

### Computação de borda
Computação de borda é um conceito na computação que envolve processamento de informação mais próximo de onde é realizada a geração dos dados, ao invés de depender de um servidor centralizado baseado em nuvem. O modelo busca trazer poder computacional e armazenamento mais próximos de onde as informações são geradas, tipicamente dentro ou perto da "borda" da rede de informações, reduzindo latência e uso de largura de banda enquanto permite tempos de resposta mais rápidos e um processamento de dados mais eficiente.

### Aprendizado de máquina minúsculo (TinyML)
Aprendizado de máquina minúsculo (do inglês Tiny Machine Learning) se refere ao campo de Aprendizado de Máquina que foca em executar modelos diretamente em dispositivos com recursos limitados como microcontroladores.
Esse conceito está fortemente atrelado ao conceito de computação de borda, onde combinando as tecnologias busca-se a implementação de modelos de aprendizado de máquina diretamente nos dispositivos de borda, aumentando ainda mais sua capacidades para análise, automação e tomada de decisões local, sem depender fortemente de uma infraestrutura centralizada de nuvem. 

Entretanto, desenvolver modelos TinyML requer otimização e criação de algoritmos leves para que possam executar de maneira eficiente dentro das restrições desses dispositivos. Técnicas como quantização de modelo, poda e arquiteturas especializadas são usadas para reduzir o tamanho dos modelos ainda mantendo uma precisão aceitável.

### Detecção de Objetos
Detecção de objetos é uma técnica de visão computacional usada para identificar e localizar objetos dentro de imagens ou vídeos. Envolve a detecção de instâncias de objetos dentro de uma imagem, determinar sua classe ou categoria específica, assim como sua localização específica dentro da imagem.

### Modelos de detecção de objetos
Existem diversas abordagens para detecção de objetos, alguns dos métodos mais populares incluem o uso de abordagens baseadas em Aprendizado Profundo que utilizam redes neurais profundas, como Redes Neurais Convolucionais (CNNs).

YOLO: uma arquitetura proeminente para detecção de objetos é YOLO (You Only Look Once), um sistema de detecção de objetos em tempo real que divide uma imagem em grades e prevê caixas delimitadoras (bounding boxes) e probabilidade de classes partindo diretamente das células da grade.
Entretanto, executar YOLO em dispositivos embarcados pode apresentar várias limitações devido às restrições de recursos e requisitos computacionais do algoritmo, como alcançar desempenho satisfatório em tempo real alcançando 30 quadros por segundo, por exemplo. Taxas de quadros mais baixas podem afetar a usabilidade em aplicações que exigem processamento em tempo real. A otimização do YOLO para dispositivos embarcados requer técnicas especializadas, como quantização de modelo, poda ou o uso de variantes mais leves do modelo (como Tiny YOLO), sacrificando precisão em troca de uma velocidade de inferência mais rápida e menos requisitos computacionais, e ainda não há garantia que o modelo terá um desempenho satisfatório nesses dispositivos.

FOMO: (Faster Objects, Moving Objects) é um modelo que implementa uma versão simplificada de detecção de objetos, chamada também de detecção constrita de objetos, para casos onde o tamanho do objeto não é relevante, apenas sua posição na imagem. Ao invés de utilizar caixas delimitadoras, é feita uma detecção baseada nos centróides dos objetos, sendo uma abordagem que foi pensada especificamente para executar detecção de objetos em microcontroladores.

FOMO divide uma imagem de entrada em uma grade e executa o equivalente a classificação de imagem em todas as células da grade de forma independente e em paralelo. Por padrão, o tamanho da grade é de 8x8 pixels, o que significa que para uma imagem de 96x96, a saída será de 12x12.
Em outras palavras, FOMO executa a detecção de objetos em cada uma das células e determina a probabilidade de um objeto estar presente naquela célula. 
Para um resolução de entrada de 96x96, observa-se na figura abaixo (contendo parafusos) que o tamanho das células das grades é de 1/8 da resolução de entrada e em um formato quadrado. 

![](https://github.com/viniwestphal/PI3/blob/main/Figuras/96x96_fomo_inference.png)

Para determinar o centroide de um objeto, é então escolhida a célula com maior probabilidade de conter determinado objeto, enquanto as células adjacentes com probabilidade menor de conter o mesmo objeto são ignoradas. 

![](https://github.com/viniwestphal/PI3/blob/main/Figuras/96x96_fomo_inference_done.png)

Com essas observações nota-se que o cenário ideal para utilização do modelo FOMO envolve objetos que sejam todos de tamanho similar, e ocupem pelo menos uma grade por completo. Também é importante que objetos distintos não estejam tão próximos uns dos outros, pois se objetos diferentes ocuparem a mesma célula da grade, apenas o objeto de maior probabilidade será considerado. Uma maneira de contornar essa limitação seria aumentando a resolução da imagem como na figura abaixo (320x320), aumentando assim o número de células, porém exigindo mais poder computacional do dispositivo embarcado.

![](https://github.com/viniwestphal/PI3/blob/main/Figuras/320x320_fomo.png)

Dada essas limitações percebe-se que FOMO é melhor aplicado em situações onde a posição da câmera é fixa, para objetos de tamanho similar e que estejam a uma mesma distância da câmera. 

A resolução da imagem pode ainda ser ajustada dependendo da situação de uso, é possível treinar o modelo em uma resolução menor, e redimensioná-la durante a inferência, isso permite adaptar um modelo já existente para diferentes dispositivos embarcados.
Devido a natureza totalmente convolucional do modelo FOMO, apenas a proporção da imagem é fixa e é possível usá-lo como complemento para qualquer rede convolucional de imagens (incluindo modelos de transferência de aprendizado).

De acordo com seus desenvolvedores, o modelo FOMO pode ter um desempenho muito melhor em um maior número de objetos pequenos do que YOLOv5.
Isso torna FOMO um modelo bastante atrativo para implementar detecção de objetos a um microcontrolador, tendo em vista que já foi projetado para essa função.

### Fluxo de trabalho para treinamento de um modelo para detecção de objetos

* Coletar dados
* Rotular dados
* Treinar o modelo
* Avaliar o modelo
* Executar o modelo

### Edge Impulse
Edge Impulse é uma plataforma projetada para gerenciar modelos de aprendizado de máquina em dispositivos de borda, sem a necessidade de um conhecimento extenso em ciência de dados ou sistemas embarcados. A plataforma simplifica todo o fluxo de trabalho, simplificando o processo de aquisição de dados, treinamento, e implementação, permitindo desenvolvedores criar e executar modelos de aprendizado de máquina para dispositivos de borda de maneira eficiente.

Uma das vantagens da utilização da plataforma Edge Impulse é que seus desenvolvedores são os mesmos do modelo FOMO, permitindo a implementação a diversos dispositivos embarcados de maneira facilitada.

# Cronograma
Clique [aqui]() para acessar o cronograma.

# Lista de materiaisr

| Item | Descrição | Unidade | Valor Unitário | Quantidade | Total |
| ---- | ------------- | --- | ------------- | ------------- | ------------- |
|  01  | Módulo ESP32-CAM | 1 | R$ 65,00 | 1 | R$ 65,00 |
|  02  | Computador com Windows 10| 1 | - | 1 | -|
|  03  | Cabo Micro-USB | 1 | | R$ 15,00 | 1 | R$ 15,00 |
|    |  |   |  |  | **R$ 80,00** |

# Unidades curriculares envolvidas
- Microcontroladores;
- Programação;
- Introdução a aprendizado de máquina.
