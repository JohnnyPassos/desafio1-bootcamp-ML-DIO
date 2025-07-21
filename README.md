# Desafio de Projeto: Classificação de Imagens de Cães e Gatos com Transfer Learning

![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-%23D00000.svg?style=for-the-badge&logo=Keras&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

## 📖 Sobre o Projeto

Este projeto foi desenvolvido como parte do desafio "Treinamento de Redes Neurais com Transfer Learning" do bootcamp **Baires Dev - Machine Learning Training**[cite: 6]. O objetivo é aplicar os conceitos de Deep Learning para construir um modelo de classificação de imagens capaz de diferenciar entre fotos de cães e gatos.

A abordagem central utilizada foi o **Transfer Learning**, uma técnica poderosa que consiste em aproveitar o conhecimento de uma rede neural já pré-treinada em um grande dataset (como o ImageNet) e adaptá-la para uma nova tarefa específica.

## 🛠️ Tecnologias Utilizadas

* **Python 3:** Linguagem principal do projeto.
* **TensorFlow e Keras:** Frameworks para construção e treinamento da rede neural.
* **Google Colab:** Ambiente de desenvolvimento em nuvem com acesso a GPUs.
* **NumPy:** Para manipulação de dados numéricos.
* **Matplotlib:** Para visualização de gráficos (não utilizado na versão final, mas parte do ecossistema).
* **OS, shutil, zipfile:** Bibliotecas padrão do Python para manipulação de arquivos e diretórios.

## 🎯 Metodologia

O desenvolvimento do projeto seguiu um pipeline estruturado, comum em problemas de visão computacional:

### 1. Aquisição e Extração dos Dados
O dataset utilizado foi o "Cats and Dogs" da Kaggle, disponibilizado pela Microsoft. O download e a extração dos arquivos foram feitos diretamente no ambiente do Google Colab.
link de descrição dos dados usados : https://www.tensorflow.org/datasets/catalog/cats_vs_dogs?hl=pt-br 
link de download dos dados (que estavam no tipo ZIP) : https://www.microsoft.com/en-us/download/details.aspx?id=54765

### 2. Pré-processamento e Estruturação de Dados
Esta foi uma etapa crucial para garantir que o Keras pudesse ler os dados corretamente. O processo envolveu:
* Criação de uma estrutura de diretórios organizada, separando o dataset em duas pastas principais: `train` (treino) e `validation` (validação).
* Dentro de cada uma dessas pastas, foram criadas subpastas para cada classe: `cats` e `dogs`.
* As imagens foram movidas dos diretórios originais para essa nova estrutura, garantindo uma divisão clara entre os dados que seriam usados para treinar o modelo e os dados para validar sua performance.

### 3. Construção do Modelo com Transfer Learning
A estratégia de Transfer Learning foi implementada da seguinte forma:
* **Carregamento do Modelo Base:** Foi utilizada a arquitetura **VGG16**, pré-treinada no dataset ImageNet. O modelo foi carregado sem suas camadas de topo (`include_top=False`), mantendo apenas a base convolucional responsável pela extração de características das imagens.
* **Congelamento da Base:** As camadas do modelo VGG16 foram "congeladas" (`trainable = False`). Isso impede que seus pesos, que já contêm um vasto conhecimento sobre características visuais, sejam alterados durante o treinamento inicial, otimizando o processo e evitando a perda de informações valiosas.
* **Adição de um Novo Classificador:** Um novo topo de modelo (classificador) foi adicionado sobre a base congelada. Esse topo é composto por camadas `Flatten` (para achatar os dados), `Dense` (camadas neurais totalmente conectadas) e `Dropout` (para regularização e combate ao overfitting). A camada final possui um único neurônio com ativação `sigmoid`, ideal para classificação binária.

### 4. Compilação e Treinamento
* O modelo foi compilado utilizando o otimizador `Adam`, a função de perda `binary_crossentropy` (adequada para problemas de classificação binária) e a métrica `accuracy` para monitorar o desempenho.
* O treinamento foi executado utilizando os dados preparados, e o modelo aprendeu com sucesso a diferenciar as imagens de cães e gatos, atingindo o objetivo principal do desafio.

## 🚀 Como Executar

1.  Clone este repositório:
    ```bash
    git clone [https://github.com/seu-usuario/seu-repositorio.git](https://github.com/seu-usuario/seu-repositorio.git)
    ```
2.  Abra o arquivo `.ipynb` no Google Colab ou em um ambiente Jupyter com as dependências instaladas.
3.  Certifique-se de que o ambiente de execução do Colab esteja configurado para usar **GPU** para um treinamento mais rápido.
4.  Execute as células em ordem para baixar os dados, estruturar as pastas e treinar o modelo.

## ✅ Resultados e Conclusão

O modelo foi treinado com sucesso, demonstrando a eficácia da técnica de Transfer Learning. O projeto cumpriu todos os requisitos do desafio proposto, resultando em um classificador funcional e validando a aplicação prática dos conceitos estudados no bootcamp.

## 🔮 Melhorias Futuras

Embora o objetivo principal tenha sido alcançado, o projeto pode ser expandido com as seguintes melhorias:

* **Fine-Tuning:** Como próximo passo, seria possível "descongelar" as últimas camadas do modelo base (VGG16) e continuar o treinamento com uma taxa de aprendizado muito baixa. Isso poderia aprimorar a performance do modelo, ajustando-o ainda mais para a especificidade do dataset.
* **Data Augmentation Avançada:** Explorar técnicas mais robustas de aumento de dados para criar um dataset de treino ainda mais variado e reduzir o overfitting.
* **Experimentação com Outras Arquiteturas:** Testar outras arquiteturas pré-treinadas, como `Xception`, `ResNet` ou `EfficientNet`, para comparar a performance.

## 👨‍💻 Autor

**Johnny Passos Galdino**

* **LinkedIn:** https://www.linkedin.com/in/johnny-passos-1aa06359/
* **GitHub:** https://github.com/JohnnyPassos
