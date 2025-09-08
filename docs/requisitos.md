# Documento de Requisitos do Sistema Apita Aí

## 1. Introdução

### 1.1 Propósito
Este documento especifica os requisitos funcionais e não funcionais do sistema **Apita Aí**, que tem como objetivo oferecer uma solução prática e eficiente para gestores de campeonatos de futebol.

### 1.2 Escopo
O sistema permite o cadastro e a organização de times, campeonatos, rodadas e partidas, além de oferecer uma tabela de classificação automática e diversas funcionalidades para acompanhar o desempenho dos times.

### 1.3 Definições, Acrônimos e Abreviações
Lista de termos utilizados.  
- **SIGAA**: Sistema Integrado de Gestão de Atividades Acadêmicas.  
- **Usuário**: Aluno, professor ou administrador.

### 1.4 Referências
Lista de documentos ou links usados como base.  
- IEEE 830 – Padrão para especificação de requisitos de software.  
- Manual da organização.  

---

## 2. Descrição Geral

### 2.1 Perspectiva do Produto
O Software vai se dividir em duas grandes partes (Front e Back) que se comunicam através de requisições HTTP. Entretanto, se comportam como apenas um produto. 
 

### 2.2 Funções do Produto
- Cadastrar, consultar e listar times.  
- Criar campeonatos e associar times.  
- Criar rodadas e partidas.  
- Registrar resultados.  
- Gerar automaticamente a tabela de classificação.   

### 2.3 Características dos Usuários
- **Gestores**: Pessoas que organizam campeonatos, com conhecimento básico de informática.  
- **Interessados no campeonato** (uso indireto): Jogadores, técnicos ou torcedores que podem visualizar informações.  

### 2.4 Restrições
O sistema pode não estar otimizado para o uso em tablets.  

### 2.5 Suposições e Dependências
- Assume-se que o usuário final terá conhecimentos básicos de operação em sistemas computacionais.  
- Usuário terá acesso à internet. 

---

## 3. Requisitos Funcionais

| ID | Requisito | Prioridade | Descrição |
|----|-----------|------------|-----------|
| RF01 | Cadastro de Usuário | Alta | O sistema deve permitir o cadastro de novos usuários. |
| RF02 | Login | Alta | O sistema deve permitir autenticação com email e senha. |
| RF03 | Cadastro de Times | Alta | O sistema deve permitir consultar os detalhes de um time cadastrado. |
| RF04 | Consulta de Dados de Times | Alta | O sistema deve permitir consultar os detalhes de um time cadastrado. |
| RF05 | Listagem de Times | Alta | O sistema deve exibir a lista de todos os times cadastrados no campeonato. |
| RF06 | Cadastro de Campeonatos | Alta | O sistema deve permitir criar campeonatos com nome, local, datas e tipo (mata-mata ou pontos corridos). |
| RF07 | Associação de Times ao Campeonato | Alta | O sistema deve permitir associar times a um campeonato. |
| RF08 | Cadastro de Rodadas e Partidas | Alta | O sistema deve permitir criar rodadas e partidas entre times, com data, hora e local. |
| RF09 | Registro de Resultados| Alta| O sistema deve permitir registrar os resultados das partidas. |
| RF10 | Geração de Tabela de Classificação  | Alta | O sistema deve exibir a tabela de classificação com base nos resultados das partidas. |





---

## 4. Requisitos Não Funcionais

| ID | Requisito | Categoria | Descrição |
|----|-----------|-----------|-----------|
| RNF01 | Desempenho     | Performance  | O sistema deve processar as atualizações em menos de 2 segundos. |
| RNF02 | Usabilidade    | UX | O sistema deve possuir interface simples e intuitiva em linha de comando. |
| RNF03 | Portabilidade  | Software     | O sistema deve ser compatível com Windows, Linux e MacOS. |
| RNF04 | Segurança      | Dados        | O sistema deve evitar inconsistências, como cadastro duplicado de times. |
| RNF05 | Manutenibilidade | Código     | O código deve seguir boas práticas de programação orientada a objetos. |

---

## 5. Casos de Uso

### 5.1 Caso de Uso: Cadastro de Time
- **Ator Principal:** Gestor  
- **Pré-condições:** O time não deve estar previamente cadastrado.  
- **Fluxo Principal:**  
  1. O gestor acessa a funcionalidade de cadastro de time.  
  2. Informa nome, estado, técnico e elenco.  
  3. O sistema valida os dados e salva o time.  
- **Fluxo Alternativo:**  
  - 3a. Se o time já existir, o sistema exibe uma mensagem de erro. 

### 5.2 Caso de Uso: Registro de Resultados
- **Ator Principal:** Gestor  
- **Pré-condições:** A partida deve estar cadastrada.  
- **Fluxo Principal:**  
  1. O gestor seleciona a partida.  
  2. Informa o resultado (gols de cada time).  
  3. O sistema permite que o gestor atualize o campeonato com o resultado de cada jogo. 
- **Fluxo Alternativo:**  
  - 3a. Caso os dados sejam inválidos, o sistema exibe mensagem de erro.  

### 5.3 Caso de Uso: Cadastro de Usuário
- **Ator Principal:** Usuário  
- **Pré-condições:** O usuário não deve ter cadastro no sistema.  
- **Fluxo Principal:**  
  1. O usuário acessa a funcionalidade de cadastro.  
  2. Informa nome, e-mail e senha.  
  3. O sistema valida os dados e cria a conta.  
- **Fluxo Alternativo:**  
   - 3a. Caso já exista uma conta com o mesmo e-mail, o sistema exibe mensagem de erro.  

### 5.4 Caso de Uso: Login
- **Ator Principal:** Usuário  
- **Pré-condições:** O usuário deve estar cadastrado.  
- **Fluxo Principal:**  
  1. O usuário acessa a tela de login.  
  2. Informa e-mail e senha.  
  3. O sistema valida os dados e permite o acesso.  
- **Fluxo Alternativo:**  
  - 3a. Caso as credenciais sejam inválidas, o sistema exibe mensagem de erro.  

### 5.5 Caso de Uso: Consulta de Dados de Times
- **Ator Principal:** Gestor  
- **Pré-condições:** O time deve estar cadastrado.  
- **Fluxo Principal:**  
  1. O gestor informa o nome do time desejado.  
  2. O sistema busca os dados e exibe as informações completas (nome, estado, técnico, elenco).  
- **Fluxo Alternativo:**  
  - 2a. Caso o time não exista, o sistema informa que não foi encontrado.  

### 5.6 Caso de Uso: Listagem de Times
- **Ator Principal:** Gestor  
- **Pré-condições:** Deve haver pelo menos um time cadastrado no campeonato.  
- **Fluxo Principal:**  
  1. O gestor acessa a funcionalidade de listagem de times do campeonato.  
  2. O sistema exibe a lista de todos os times cadastrados no campeonato.  
- **Fluxo Alternativo:**  
  
### 5.7 Caso de Uso: Cadastro de Campeonatos
- **Ator Principal:** Gestor  
- **Pré-condições:** O campeonato não deve estar previamente cadastrado.  
- **Fluxo Principal:**  
  1. O gestor acessa a funcionalidade de cadastro de campeonato.  
  2. Informa nome, local, data de início e término, e tipo (mata-mata ou pontos corridos).  
  3. O sistema valida os dados e cadastra o campeonato.  
- **Fluxo Alternativo:**  
  - 3a. Caso já exista um campeonato com as mesmas informações, o sistema exibe mensagem de erro.  

### 5.8 Caso de Uso: Associação de Times ao Campeonato
- **Ator Principal:** Gestor  
- **Pré-condições:** Deve existir um campeonato e times cadastrados.  
- **Fluxo Principal:**  
  1. O gestor acessa a funcionalidade de associação de times.  
  2. Seleciona um campeonato.  
  3. Seleciona os times participantes.  
  4. O sistema associa os times ao campeonato escolhido.  
- **Fluxo Alternativo:**  
  - 3a. Caso um time já esteja associado ao campeonato, o sistema emite aviso.  

### 5.9 Caso de Uso: Cadastro de Rodadas e Partidas
- **Ator Principal:** Gestor  
- **Pré-condições:** O campeonato deve existir e conter times associados.  
- **Fluxo Principal:**  
  1. O gestor seleciona um campeonato.  
  2. Cria uma rodada e define suas partidas.  
  3. Para cada partida, informa os dois times, data, horário e local.  
  4. O sistema salva as partidas.  
- **Fluxo Alternativo:**  
  - 3a. Caso o gestor selecione o mesmo time para os dois lados, o sistema emite erro.  
 

### 5.10 Caso de Uso: Geração de Tabela de Classificação
- **Ator Principal:** Gestor  
- **Pré-condições:** Deve haver resultados registrados no campeonato.  
- **Fluxo Principal:**  
  1. O gestor acessa a funcionalidade de classificação.  
  2. O sistema gera e exibe a tabela de classificação com pontos, vitórias, empates, derrotas, saldo de gols e gols marcados.  
- **Fluxo Alternativo:**  
  - 2a. Caso não existam partidas finalizadas, o sistema exibe mensagem de que não há dados suficientes.  

---

## 6. Protótipos (Opcional)
Inserir imagens ou links para protótipos de tela.

---

## 7. Critérios de Aceitação
- O sistema deve permitir o cadastro de no mínimo 4 times em um campeonato.  
- O sistema deve permitir o usuário se cadastrar e logar em sua conta. 
- O sistema deve atualizar a tabela de classificação após cada resultado registrado.  
- O sistema deve impedir o cadastro de dois times com o mesmo nome. 
- O sistema deve permitir a criação de campeonatos nos formatos: mata-mata e pontos corridos. 
- O sistema deve validar que uma partida cadastrada tenha dois times distintos.
- O sistema deve permitir a consulta dos detalhes de qualquer time cadastrado (nome, estado, técnico e elenco).  
- O sistema deve aceitar apenas resultados válidos (gols ≥ 0).  
- O sistema deve ordenar a tabela de classificação corretamente em ordem decrescente de pontos e saldo de gols.  

---


## 8. Rastreabilidade


| Requisito | Caso de Uso | Critérios de Aceitação |
| - | - | - |
| **RF01 – Cadastro de Usuário** | CU 5.3 – Cadastro de Usuário | O sistema deve permitir o cadastro de novos usuários com nome, e-mail e senha; O sistema deve validar dados obrigatórios; O sistema deve impedir cadastro com e-mail duplicado. |
| **RF02 – Login** | CU 5.4 – Login | O sistema deve autenticar usuários cadastrados; O sistema deve exibir erro em caso de credenciais inválidas; O sistema deve permitir apenas acesso com e-mail e senha corretos. |
| **RF03 – Cadastro de Times** | CU 5.1 – Cadastro de Time | O sistema deve permitir cadastrar times com nome, estado, técnico e elenco; O sistema deve validar se o time já existe; O sistema deve impedir cadastros duplicados. |
| **RF04 – Consulta de Dados de Times** | CU 5.5 – Consulta de Dados de Times | O sistema deve permitir consultar os dados de um time cadastrado; O sistema deve exibir mensagem se o time não for encontrado. |
| **RF05 – Listagem de Times** | CU 5.6 – Listagem de Times | O sistema deve exibir a lista completa de times cadastrados; O sistema deve ordenar a lista alfabeticamente (ou por critério definido). |
| **RF06 – Cadastro de Campeonatos** | CU 5.7 – Cadastro de Campeonatos | O sistema deve permitir cadastrar campeonatos com nome, local, data de início, término e tipo; O sistema deve impedir campeonatos duplicados; O sistema deve validar as datas. |
| **RF07 – Associação de Times ao Campeonato** | CU 5.8 – Associação de Times ao Campeonato | O sistema deve permitir associar múltiplos times a um campeonato; O sistema deve impedir associação duplicada de times; O sistema deve validar que existem times e campeonato cadastrados. |
| **RF08 – Cadastro de Rodadas e Partidas** | CU 5.9 – Cadastro de Rodadas e Partidas | O sistema deve permitir cadastrar rodadas vinculadas a um campeonato; O sistema deve registrar partidas com data, horário, local e times; O sistema deve impedir partidas com o mesmo time em ambos os lados. |
| **RF09 – Registro de Resultados** | CU 5.2 – Registro de Resultados | O sistema deve permitir registrar gols de cada time; O sistema deve validar que a partida existe e está cadastrada; O sistema deve atualizar automaticamente as estatísticas do campeonato. |
| **RF10 – Geração de Tabela de Classificação** | CU 5.10 – Geração de Tabela de Classificação | O sistema deve exibir classificação com pontos, vitórias, empates, derrotas, saldo de gols e gols marcados; O sistema deve ordenar os times conforme regras do campeonato; O sistema deve exibir mensagem se não houver resultados cadastrados. |


---

## 9. Anexos
Incluir diagramas UML, wireframes, ou qualquer material adicional.

| Versão | Autor |Descrição | Data |
| - | - | - | - |
| 1.0 | Luana Medeiros | Criação do documento | 07/09/2025 |