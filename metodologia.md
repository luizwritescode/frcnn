# Metodologia

1. Preparação do banco de dados

Originalmente, o banco de dados continha anotações de classes que não são interessantes para pesquisa pois não propõem uma comparação justa entre humanos e máquianas. Por isso, foram feitas as seguintes adaptações:

- Adaptando o banco para humanos e maquinas

	- Foram *retiradas* do banco de dados **imagens com mais de 3 defeitos**, pois poderiam apresentar problemas para o teste com humanos, e para deixar a comparação "justa", também foram retiradas do banco de imagens para as máquinas

	- Foram *retiradas* do banco de dados **imagens com defeitos 5, 6 ( scratch, strain)** pois são dificeis de 
	serem reconhecidas, seu impacto seria mais relevante se forem usadas para avaliar a capacidade de generalização de ambos humanos e máquinas vendo como escolhem a classe que melhor representa 5 e 6 dentre as classes disponiveis

	- Foi *omitida* a **classe 1 (polished)**, pois ela ocorria muito em um caso estranho onde a peça tinha defeitos, mas também estava polida, o que poderia causar confusão. Outro motivo f,oi para dar espaço a uma classe mais compreensivel e generalista "sem defeito". Omitir a classe polished causou lacunas nas anotações. A solução foi reanotar imagens que ficaram sem anotações.

	- Os numeros de ID das classes foi ajustado para as novas classes

	original		adaptada
	0 burr -> 		0 rebarba
	2 pol&burr -> 	0 rebarba
	3 crack -> 		1 rachadura
	4 pit -> 		2 perfuração
	7 unpolished -> 3 não polida

	1 polished -> 	omitida

	5 scratch -> 	retirada
	6 strain -> 	retirada

	**4 sem defeito** -> adicionada


- Reanotação

	- Foi criado um aplicativo web utilizando html e javascript puro para uso interno, que posteriormente vai ser atualizado para efetuar testes com humanos.

	- Após a reclassificação e omissão de classes as imagens que ficaram com arquivos de texto correspondentes vazios podem ser consideradas sem defeitos e vão ser reanotadas uma por uma utilizando o aplicativo.



- Configuração de treino

	- Tamanho da imagem:

	- Tamanho dos anchors

	- Fator de escala do anchors

	- Normalização (Zero-center by mean pixel)

		- Calculando Channel mean pixel


- Segundo Treino 
	
	- O modelo foi retreinado usando tamanho de imagem original (640px) para tentar melhorar o posicionamento das caixas. 

		Resultados: melhora significativa no posicionamento, mas o modelo tem acurácia levemente reduzida

Modificações pendentes:

- Introduzir nova métrica de posicionamento das ancoras

	IoU (inferencia/gt) / IoU (gt/inferencia)

	Generalized IoU

- Introduzir nova estratégia de normalização

	Zero-based mean pixel [-144,144] -> [0,1]
 
- Terceiro Treino
	
	- Implementar Resnet como nova rede backbone

Entender mAP@k Mean Average Precision


Relátorio comparando métricas VGG e Resnet

- Quarto Treino

	- Transformada de Fourier, cada imagem vira N analises na frequencia dependendo do numero de fases
