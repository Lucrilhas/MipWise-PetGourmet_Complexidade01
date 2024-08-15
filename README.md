# Mip Procure

## Repository guide
- [docs](docs): Hosts documentation (in addition to readme files and docstrings)
  of the project.
- [mip_procure](mip_procure): Contains the Python package that solves the 
  problem.
  It contains scripts that define the input and the output data schemas, the 
  solution engine, and other auxiliary modules.
- [test_mip_procure](test_mip_procure): Hosts testing suits and testing data 
  sets used for testing the solution throughout the development process.
- `pyproject.toml` and `setup.cfg` are used to build the distribution files 
  of the package (more information [here](https://github.com/mipwise/mip-go/blob/main/6_deploy/1_distribution_package/README.md)).

# Complexidade número 01

* André Luiz
* Iago Nery
* Lucas Cruvinel
* Octavio Sobral

## Alterações dos alunos

Foram realizadas mudanças nos arquivos:

- `main.py`: Descomentada a linha 10, para permitir a execução da complexidade 1;
- `data_bridge.py`: Na linha 131, foram adicionadas as `tr_keys`, que são as chaves para as variáveis que indicam se houve ou não viagem de caminhão naquela semana.
  - Foi acordado que, como já havia a restrição de não poder transferir mais de 12.000, não seria possível ter mais de uma viagem por semana. Logo, a quantidade de viagens pode ser 0 ou 1, tornando-se um valor booleano.
- `test_local_execution.py`: Pequena alteração na biblioteca importada para conseguir executar corretamente o código. Pode ser necessário reverter:
  - Descomentar a linha 2 e comentar a linha 3.
- `opt_model`:
  - Linha 68: Foi declarada a variável `tr` do tipo booleano, que recebe as `tr_keys` já mencionadas.
  - Linha 76: Inicializada a variável `tr` dentro do pulp.
  - Linhas 182 até 209: Função que contempla a complexidade 01, adicionando as restrições necessárias.
  - Linhas 174 e 177: Criação de um novo custo para ser adicionado à função objetivo.

## Resultados:
- O principal resultado pode ser observado em `test_mip_procure\data\outputs\kpis.csv`, onde é possível encontrar o custo ótimo de transporte.
- No nosso caso, foi de 3500, significando que, das 12 semanas, em 10 foi necessário utilizar o caminhão.

