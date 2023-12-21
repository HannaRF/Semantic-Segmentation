# Semantic-Segmentation

![image](https://github.com/HannaRF/Semantic-Segmentation/assets/85463854/d3845a35-805d-4d58-a2b4-76ebf4701596)

**Objetivo:**
- Implementar uma Rede U-Net para realizar segmentação semântica em imagens.

**Conjunto de Dados:**
- Utiliza imagens fornecidas [Image_Train.tif e Reference_Train.tif](https://drive.google.com/file/d/1TU2nTVGS2932hRs1u-ma4r3vmgqHRbMO/view?usp=sharing).
- Avalia o modelo treinado nas imagens Image_Test.tif e Reference_Test.tif.
- Um jupyter notebook com funções básicas está disponível.

**Protocolo Experimental:**
1. **Carregar dados de entrada:**
   - Usa a função `load_tiff_image(image)` para carregar imagens do conjunto de dados 2D Semantic Labeling-Vaihingen.
   - Normaliza os dados para o intervalo [0,1] usando a função `normalization(image)`.

2. **Treinar o modelo U-Net:**
   - Extrai patches de tamanho w-by-w-by-c pixels de Image_Train e patches de tamanho w-by-w de Reference_Train.
   - Divide aleatoriamente os patches de treinamento em conjuntos de Treinamento (80%) e Validação (20%).
   - Converte patches de Reference em codificação one-hot com base no número de classes usando `tf.keras.utils.to_categorical`.
   - Implementa o modelo U-Net com skip connections.
   - Usa weighted_categorical_crossentropy como função de perda.
   - Treina o modelo com a função `Train_model()`, incorporando early stopping com paciência 10.

3. **Testar o modelo:**
   - Extrai patches das imagens de teste e avalia o modelo usando `Test(model, patch_test)`.

4. **Reconstruir a previsão (imagem de teste completa):**
   - Apresenta os resultados de classificação como imagens de rótulos.
   - Relata métricas de precisão, incluindo precisão geral e média, e pontuação F1.
   - Compara os resultados com diferentes tamanhos de patches (32x32, 64x64, 128x128).

Este projeto é uma implementação prática de um pipeline de aprendizado profundo para a tarefa específica de segmentação semântica, usando a arquitetura U-Net e técnicas associadas.
