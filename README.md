# Sistema Hospitalar – Banco de Dados

Este projeto representa a modelagem e a construção de um sistema de banco de dados completo para um hospital. Ele abrange desde o cadastro de pacientes e médicos até a gestão de exames, internações, receitas, leitos e pagamentos.

## 📄 Descrição Geral

O banco de dados simula um ambiente hospitalar realista, onde é possível armazenar, consultar e relacionar informações médicas e administrativas de maneira organizada. Utiliza a linguagem SQL (MySQL) com o objetivo de estruturar a base de dados de um hospital.

## 🧱 Estrutura de Tabelas

### 🏥 Paciente
Armazena dados pessoais dos pacientes.

- `id_paciente` (PK)
- `nome`, `data_nascimento`, `endereco`, `telefone`, `email`, `sexo`, `tipo_sanguineo`

### 🧑‍⚕️ Médico
Contém informações dos médicos, ligados às especialidades.

- `id_medico` (PK)
- `nome`, `crm`, `telefone`, `email`, `sexo`, `id_especialidade` (FK)

### 🩺 Especialidade
Lista das especialidades médicas disponíveis.

- `id_especialidade` (PK)
- `nome`

### 👷 Funcionário
Registra colaboradores do hospital.

- `id_funcionario` (PK)
- `nome`, `cargo`, `sexo`, `telefone`, `email`, `salario`

### 📋 Consulta
Relaciona pacientes com médicos e suas consultas.

- `id_consulta` (PK)
- `id_paciente`, `id_medico` (FKs)
- `data_consulta`, `diagnostico`, `id_receita`

### 🛏️ Internação
Controla dados sobre internações hospitalares.

- `id_internacao` (PK)
- `id_paciente`, `id_leito` (FKs)
- `data_entrada`, `data_saida`, `diagnostico`

### 🛌 Leito
Tabela de leitos hospitalares.

- `id_leito` (PK)
- `numero_leito`, `andar`, `tipo`, `disponivel`

### 🧪 Exame
Armazena os exames realizados pelos pacientes.

- `id_exame` (PK)
- `id_paciente` (FK), `tipo_exame`, `data_exame`, `resultado`, `observacoes`

### 💊 Receita
Prescrições médicas emitidas.

- `id_receita` (PK)
- `id_medico`, `id_paciente` (FKs), `data_receita`, `descricao`

### 💳 Pagamento
Registros financeiros dos pacientes.

- `id_pagamento` (PK)
- `id_paciente` (FK), `data_pagamento`, `valor`, `metodo_pagamento`, `status`

## 🔍 Exemplos de Consultas

```sql
-- Selecionar pacientes do sexo masculino com sangue O+
SELECT * FROM PACIENTE
WHERE SEXO = 'M' AND TIPO_SANGUINEO = 'O+';

-- Filtrar médicas da especialidade 1
SELECT * FROM MEDICO WHERE SEXO = 'F' AND id_especialidade = 1;

-- Pacientes com nome contendo "Almeida"
SELECT * FROM PACIENTE WHERE NOME LIKE '%ALMEIDA%';

-- Consultar funcionários com salário acima de R$100
SELECT AVG(SALARIO) FROM FUNCIONARIO WHERE SALARIO > 100.00;
🛠️ Tecnologias Recomendadas
Banco de Dados: MySQL

Ambiente de execução: MySQL Workbench, DBeaver, PHPMyAdmin

Futuras expansões: Pode ser integrado com aplicações web ou desktop

📦 Possibilidades de Expansão
Interface gráfica para gerenciamento dos dados

Relatórios estatísticos sobre pacientes, exames e internações

Controle de estoque de medicamentos

Integração com sistemas de prontuário eletrônico

👨‍💻 Colaboradores
Nome do autor: Leandro

Projeto: Acadêmico

📋 Licença
Este projeto é de uso educacional. Sinta-se livre para usar, modificar e compartilhar com fins não comerciais.
