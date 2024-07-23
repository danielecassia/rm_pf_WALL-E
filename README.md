# Proposta de Projeto Final

![Foto do Projeto](https://colunaclaquete.com.br/wp-content/uploads/2021/01/Walle-pic-cropped-3.jpg)


## Sistema Multi-Robôs para Cobertura Eficiente de Ambientes Domésticos

### Contextualização

Uma aplicação relevante na área de robótica é a dos robôs aspiradores, que têm a função de percorrer o ambiente doméstico de forma autônoma, recolhendo detritos ao longo do caminho. Este projeto abordará o problema de cobertura no contexto de sistemas multi-robôs, com o objetivo de dividir a tarefa entre dois robôs. Um dos principais desafios nesta área é garantir que os robôs executem seu trajeto de forma eficiente, evitando a movimentação aleatória pelo espaço, como observado em robôs aspiradores convencionais, conforme demonstrado no vídeo da [Neato Robotics](https://www.youtube.com/watch?v=qHEJhJ_CuOQ).

Para superar esses desafios, utilizaremos nosso conhecimento em mapeamento, controle e algoritmos para desenvolver um sistema de multi-robôs que abordará o problema de cobertura do ambiente de forma eficaz, completa e, adicionalmente, enfrentaremos o desafio de implementar a colaboração entre os robôs. A implementação será realizada utilizando a linguagem Python e o simulador CoppeliaSim.

### Motivação

Abordar este problema é crucial para aumentar a eficiência energética e reduzir a pegada de carbono dos robôs aspiradores domésticos. Um planejamento adequado permite que esses robôs executem suas tarefas de maneira mais rápida e eficiente, contribuindo significativamente para a sustentabilidade ambiental. As principais aplicações incluem a limpeza autônoma em residências, escritórios e outros espaços fechados onde a manutenção regular é necessária.

### Descrição do Problema

O problema específico abordado é a ineficiência dos trajetos dos robôs aspiradores domésticos devido à ausência de um planejamento deliberativo de cobertura. Os desafios incluem a criação de um mapa da residência, a discretização do ambiente em uma grade, e a implementação de algoritmos de cobertura que permitam a coordenação eficiente de múltiplos robôs. O objetivo é desenvolver uma solução que possibilite aos robôs realizar trajetos otimizados e colaborativos, minimizando o tempo e a energia consumidos para limpar o ambiente completamente.

Em nossa implementação, consideraremos um ambiente com dois robôs que devem colaborar na limpeza de forma paralela. Além disso, vamos trabalhar partindo de um mapa pré-existente do ambiente, que teria sido obtido em uma fase anterior, no caso de uma implementação real.

### Trabalhos Relacionados

Implementações similares ao nosso projeto incluem os robôs da [Neato Robotics](https://neatorobotics.com). Esses robôs utilizam técnicas de mapeamento e navegação com base em visão computacional (bitvision) e empregam modelos treinados com florestas aleatórias para melhorar a eficiência da navegação e da cobertura do ambiente.

Diversos estudos abordam o problema de cobertura em sistemas multi-robôs. Um exemplo relevante é o artigo ["Exact and Heuristic Multi-Robot Dubins Coverage Path Planning for Known Environments"](https://www.mdpi.com/1424-8220/23/5/2560) publicado na revista Sensors. Este estudo apresenta métodos exatos e heurísticos para o planejamento de trajetórias de cobertura para múltiplos robôs em ambientes conhecidos. A pesquisa destaca a importância de criar trajetórias eficientes que minimizem o tempo e os recursos necessários para a cobertura completa do ambiente, focando em trajetórias do tipo Dubins, que são especialmente úteis para robôs com restrições de movimentação como os robôs aspiradores.

### Metodologia

Para resolver o problema, será utilizado o simulador CoppeliaSim juntamente com Python para modelar e testar o sistema multi-robôs. Iremos partir de um mapa da residência, uma imagem preto e branca e criaremos a discretização desse ambiente em um grid, onde cada célula será aproximadamente do tamanho do robô, que consegue limpá-la por completo. Em seguida, vamos utilizar a técnica deliberativa de Wavefront Planner para criar camadas do ambiente, antes de liberar os robôs. Com o mapeamento feito, iremos iniciar 2 robôs no ambiente, e atribuímos uma sequência de regiões para cada robô, para permitir que eles trabalhem em paralelo.

Para essa solução precisaremos eficientemente localizar o robô e converter suas coordenadas locais para globais. Além disso, precisamos de técnicas de controle para efetivamente mover os robôs entre as células desejadas, com o modelo cinemático do robô em questão. Finalmente, precisamos ser capaz de executar o algoritmo que dita os caminhos, decidir quais ladrilhos ainda restam ser limpos e saber quando a limpeza terminou, isso num planejamento que não permite que os caminhos dos robôs deem origem a trajetórias inválidas (que eles não se choquem).

### Referências

- Site Neato Robotics: [neatorobotics.com](https://neatorobotics.com/)
- Site iRobot: [irobot.com](https://www.irobot.com/)
- Trabalho relacionado na literatura: ["Exact and Heuristic Multi-Robot Dubins Coverage Path Planning for Known Environments"](https://www.mdpi.com/1424-8220/23/5/2560)
