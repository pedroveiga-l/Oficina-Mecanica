# Sistema de Gerenciamento de Oficina Mecânica

Trabalho Final da disciplina de **Programação Orientada por Objetos**, do curso de Análise e Desenvolvimento de Sistemas (noturno) da PUC Minas, Campus Betim, 2º semestre de 2026. Professor: Jardell Fillipe da Silva.

## Integrantes

- João Paulo Diniz Junior
- Luan Carlos Silva Carvalho
- Pedro Paulo Veiga Lima
- Renan Guerra Gonçalves

## Descrição do sistema

O sistema controla o dia a dia de uma oficina mecânica de pequeno porte. Ele serve ao atendente e ao gerente, que hoje fazem esse controle de forma manual.

Principais funcionalidades:

- cadastro de clientes e de seus veículos;
- cadastro de funcionários (mecânicos e atendentes);
- controle de estoque de peças;
- abertura de ordens de serviço, com serviços executados e peças utilizadas;
- cálculo do valor final da ordem e acompanhamento do status (aberta, em andamento, concluída, cancelada);
- cálculo do salário dos funcionários, incluindo a comissão dos mecânicos.

## Modelagem

| Classe | Tipo | Responsabilidade |
|---|---|---|
| Pessoa | abstrata | Dados comuns: nome, CPF, telefone |
| Cliente | filha de Pessoa | Guarda a lista de veículos do cliente |
| Funcionario | abstrata, filha de Pessoa | Salário base e contrato de `CalcularSalario()` |
| Mecanico | filha de Funcionario | Especialidade e comissão sobre serviços concluídos |
| Atendente | filha de Funcionario | Bônus fixo por atendimento |
| Veiculo | concreta | Placa, modelo, ano e quilometragem |
| Peca | concreta | Nome, preço e quantidade em estoque |
| Servico | abstrata | Descrição, valor base e contrato de `CalcularValor()` |
| Revisao | filha de Servico | Valor varia conforme a quilometragem |
| TrocaDeOleo | filha de Servico | Valor varia conforme litros e tipo de óleo |
| Alinhamento | filha de Servico | Valor fixo, com adicional para veículos grandes |
| IPagavel | interface | Contrato `CalcularTotal()` |
| OrdemServico | concreta | Liga cliente, veículo, mecânico, serviços e peças; controla o status |
| Orcamento | concreta | Estimativa de valor antes da abertura da ordem |
| Oficina | concreta | Classe de controle: guarda as listas, cadastros e buscas |

## Os quatro pilares no projeto

- **Abstração:** `Pessoa`, `Funcionario` e `Servico` são classes abstratas; `IPagavel` é uma interface implementada por `OrdemServico` e `Orcamento`.
- **Encapsulamento:** atributos privados com propriedades que validam os dados (CPF, placa, ano, quilometragem, salário, preço, estoque e status da ordem).
- **Herança:** `Pessoa` → `Cliente` e `Funcionario` → `Mecanico` e `Atendente`; `Servico` → `Revisao`, `TrocaDeOleo` e `Alinhamento`.
- **Polimorfismo:** `CalcularValor()` em cada tipo de serviço, `CalcularSalario()` em cada tipo de funcionário e `CalcularTotal()` em cada item `IPagavel`.

## Tecnologias

- Linguagem: C#
- Aplicação de console

## Status

Em desenvolvimento. Esta é a fase de entrega parcial (modelagem do sistema); o código será adicionado nas próximas etapas.
