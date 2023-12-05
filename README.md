> toda proposta de tema de projeto de PI3 deve seguir o padrão abaixo.

# Proposta de Tema de PI3
Título: Câmera de Filmagem Inteligente para Contagem e Detecção de Veículos

Aluno(s): Vinicius Westphal de Paula

Orientador: Prof. Ênio dos Santos Silva

# Objetivo geral
>

Implementar uma câmera baseada em microcontroladores capaz de detectar veículos em tempo real.

# Objetivos específicos
> os objetivos específicos são as diferentes ações a serem tomadas durante o desenvolvimento visando concretizar o objetivo geral

- Pesquisa de microcontroladores com suporte à câmera de filmagem;
- Pesquisa de modelos de detecção de objetos para dispositivo de baixa potência;
- Treinar um modelo capaz de detecção de veículos automóveis;
- Implementar e testar o modelo em um microcontrolador;


# Metodologia
> descreva a metodologia de desenvolvimento destacando quais são as etapas

## Embedded Systems



## Edge Computing

Edge computing is a paradigm in computing that involves processing data closer to the source of data generation rather than relying on a centralized cloud-based server. It aims to bring computational power and storage closer to where data is produced, typically at or near the "edge" of the network.  This approach brings computational power and data storage closer to where it's generated, reducing latency and bandwidth usage while enabling faster response times and more efficient data processing.

Edge computing, when combined with technologies like TinyML (Tiny Machine Learning), enables the deployment of machine learning models and AI algorithms directly on edge devices, further enhancing their capabilities for local decision-making, analysis, and automation without heavy reliance on centralized cloud infrastructure.

## Microcontrollers

Microcontrollers are compact integrated circuits (ICs) that function as a small computer on a single semiconductor chip. They are designed to execute specific tasks in embedded systems, ranging from simple to complex functions.
They are used in a wide range of applications such as embedded systems, IoT devices, robotics, consumer electronics, automotive systems, medical devices, and more.

Microcontrollers execute pre-programmed instructions and perform tasks based on the input received from sensors, switches, or other external signals. 

Microcontrollers are programmed using specialized software and code tells the microcontroller how to perform its tasks, programming languages include C, C++, Python, or specific assembly languages.

Microcontrollers often excel at real-time processing, making them suitable for applications that require quick responses or precise timing.

They are designed to operate efficiently with minimal power consumption, which makes them ideal for battery-powered devices or systems where power efficiency is crucial.

### Camera Support

There are several microcontrollers available in the market that support camera interfacing for various applications. Some of the popular microcontrollers that can be used with cameras include:

Raspberry Pi: While not strictly a microcontroller, Raspberry Pi boards like the Raspberry Pi Camera Module can interface with cameras. These boards are powerful single-board computers that support camera modules and can handle image processing tasks.

ESP32: The ESP32 microcontroller has built-in Wi-Fi and Bluetooth capabilities and can be used with camera modules via its camera interface. There are specific ESP32-CAM modules available that integrate the ESP32 chip with a camera module.

Arduino: Arduino itself doesn’t have native camera support, but there are shields or modules available that can be used to interface with cameras, such as OV7670 or OV2640 camera modules.

#### ESP32-CAM

The ESP32-CAM is a development board based on the ESP32 system-on-chip (SoC) with an integrated camera module. It's designed for IoT projects that require camera functionality along with the powerful capabilities of the ESP32 microcontroller.

Programming the ESP32-CAM involves using the Arduino IDE or the ESP-IDF (Espressif IoT Development Framework) and libraries designed for camera support to access the camera module and perform various tasks like capturing images or video, streaming video over Wi-Fi, or implementing machine learning applications for image recognition.

Typical projects using the ESP32-CAM include security cameras, video streaming, motion detection systems, and other applications requiring image processing or visual data.

## Machine Learning

Machine learning is a subset of artificial intelligence that involves creating algorithms and models that enable computers to learn and make predictions or decisions based on data without explicit programming. The primary goal of machine learning is to develop algorithms that can automatically learn and improve from experience or data.

## TinyML

TinyML refers to the field of machine learning and artificial intelligence that focuses on running models on resource-constrained devices with low power, memory, and processing capabilities, such as microcontrollers (MCUs), rather than relying on powerful servers or cloud-based solutions.

The goal of TinyML is to deploy machine learning models directly on edge devices like sensors, wearables, IoT devices, and other embedded systems, enabling them to perform tasks locally without relying on a constant connection to the internet or sending data to remote servers. This has several advantages, including reduced latency, enhanced privacy and security, and lower power consumption.

Developing TinyML models involves optimizing and creating lightweight algorithms that can operate efficiently within the constraints of these devices. Techniques such as model quantization, pruning, and specialized architectures are used to reduce the size of the models while maintaining acceptable accuracy.


## Edge Impulse
Edge Impulse is a platform designed for developing, deploying, and managing machine learning models on edge devices, such as microcontrollers, without extensive expertise in data science or embedded systems. It simplifies the process of collecting data, training machine learning models, and deploying them to various edge devices.
Edge Impulse is particularly valuable for IoT (Internet of Things) applications, where real-time processing and inference on low-power devices are necessary. It simplifies the entire workflow, from data acquisition to deployment, and allows developers to create and deploy machine learning models for edge computing efficiently.

### Workflow
Collect images
Label Images
Train Model
Export Model
Run Model



FOMO
Basics on how FOMO works


Exporting to Arduino Library
Loading to ESP32-CAM
Importing the Arduino Library

EloquentESP32CAM Library
Using the ESP32-CAM to capture images




# Cronograma
> crie um projeto no GitHub discriminando as ações e o período em que as mesmas serão realizadas
> coloque dentro do parênteses abaixo o link para o projeto criado

Clique [aqui]() para acessar o cronograma.

# Lista de materiais
> crie uma lista dos materiais que serão necessários para a execução do projeto
> 
> utilize preço médio do mercado mesmo que não seja necessário comprar

| Item | Descrição | Unidade | Valor Unitário | Quantidade | Total |
| ---- | ------------- | --- | ------------- | ------------- | ------------- |
|  01  | Módulo ESP32-CAM | 1 | R$ 65,00 | 1 | R$ 65,00 |

|    |  |   |  |  | **R$ 65,00** |

# Unidades curriculares envolvidas
> liste as unidades curriculares envolvidas com o tema escolhido
- Microcontroladores;
- Programação;
- Introdução a aprendizado de máquina.
