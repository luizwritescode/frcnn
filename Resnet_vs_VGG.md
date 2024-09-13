**Relatório Técnico: Comparação de Backbones ResNet e VGG para Detecção de Objetos com Faster R-CNN**

**1. Introdução:**
A detecção de objetos é uma tarefa fundamental em visão computacional, com aplicações que vão desde vigilância até direção autônoma. O Faster R-CNN é uma arquitetura popular para detecção de objetos, conhecida por sua precisão e eficiência. Neste relatório, comparamos o desempenho de modelos Faster R-CNN usando backbones ResNet e VGG em um conjunto de dados de teste.

**2. Configuração Experimental:**
Treinamos dois modelos Faster R-CNN, um com um backbone ResNet e outro com um backbone VGG, usando os mesmos dados de treinamento e hiperparâmetros. Após o treinamento, avaliamos os modelos em um conjunto de dados de teste e analisamos seu desempenho.

**3. Métricas de Desempenho:**
Utilizamos várias métricas de desempenho para avaliar os modelos:

- **IoU Médio (Intersection over Union):** Mede a sobreposição entre as caixas delimitadoras previstas e as caixas delimitadoras verdadeiras. Um IoU mais alto indica uma melhor precisão na localização. O valor "1.0" indica que as caixas são identicas, enquanto "0" indica que não há interseção.
- **GIoU Médio (Generalized IoU):** Uma variante do IoU que considera a área de interseção e união entre as caixas. O GIoU é mais robusto a erros de localização pois quando não há intersecção, a IoU sempre vai ser 0, enquanto a GIoU mostra um valor negativo. O valor "0" indica que as caixas são identicas.
- **Precisão:** Razão entre as predições verdadeiras positivas e o total de predições positivas. Mede a precisão das predições positivas.
- **Recall:** Razão entre as predições verdadeiras positivas e o total de verdadeiros positivos. Mede a completude das predições positivas.

**4. Resultados:**

**Backbone ResNet:**
- IoU Médio de predições corretas: 0.8288
- GIoU Médio de predições corretas: -0.1711
- Precisão: [Burr: 1.0, Crack: 0.732, Pit: 0.571,  Unpolished: 0.962, No_defect: 1.0]
- Recall: [Burr: 1.0, Crack: 0.75, Pit: 0.889, Unpolished: 0.735, No_Defect: 0.9375]

**Backbone VGG:**
- IoU Médio de predições corretas: 0.8296
- GIoU Médio de predições corretas: -0.1703
- Precisão: [Burr: 1.0, Crack: 0.854, Pit: 0.571, Unpolished: 0.962, No_Defect 0.978]
- Recall: [Burr: 1.0, Crack: 0.814, Pit: 0.941, Unpolished: 0.758, No_Defect 0.936]

**5. Análise:**
- **IoU Médio e GIoU Médio:** Ambos os modelos alcançam valores de IoU médio e GIoU médio similares, indicando precisão de localização comparável e robustez a erros de localização.
- **Precisão e Recall:** O modelo com backbone VGG apresenta ligeiramente maior precisão e recall para a maioria das classes em comparação com o modelo com backbone ResNet. Isso sugere que o backbone VGG pode ser melhor tanto na detecção quanto na localização precisa de objetos. Porém, ao observar o modelo em execução, percebe-se muito mais falso positivos do que o modelo Resnet.
- **Eficiência Computacional:** Embora não seja medida diretamente neste relatório, vale ressaltar que o ResNet geralmente oferece tempos de treinamento e inferência mais rápidos em comparação com o VGG devido à sua arquitetura mais eficiente.

**6. Conclusão:**
Nesta comparação entre modelos Faster R-CNN com backbones ResNet e VGG, ambos os modelos demonstram desempenho geral semelhante em termos de precisão de localização e robustez a erros de localização. No entanto, o modelo com backbone VGG apresenta ligeiramente melhor precisão e recall, indicando capacidades superiores de detecção de objetos. Isso porque, estamos comparando caixa verdade com a inferencia que tem o melhor IoU, ignorando as outras. Na prática, a rede VGG pode estar gerando mais predições do que necessário, muitas delas falso positivas, o que não é ideal.Experimentos e análises adicionais podem ser necessários para explorar a eficiência computacional e a escalabilidade de cada modelo para conjuntos de dados maiores e aplicações do mundo real.