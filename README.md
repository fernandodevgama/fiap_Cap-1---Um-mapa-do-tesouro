# fiap_Cap-1---Um-mapa-do-tesouro

# FarmTech Solutions - Modelagem de Banco de Dados

## Descrição do Projeto
Este projeto foi desenvolvido pela equipe da FarmTech Solutions para a disciplina de Banco de Dados da FIAP. O objetivo é modelar um banco de dados relacional para gerenciar dados de sensores em uma plantação, otimizando a aplicação de água e nutrientes com base em leituras de umidade, pH e nutrientes (fósforo e potássio).

## Equipe
- [Nome do Aluno 1] (RM: [RM1])
- [Nome do Aluno 2] (RM: [RM2])
- [Nome do Aluno 3] (RM: [RM3])
- [Nome do Aluno 4] (RM: [RM4])
- [Nome do Aluno 5] (RM: [RM5])

## Modelo Entidade-Relacionamento (MER)

### Entidades e Atributos
1. **Cultura**
   - `id_cultura` (PK, INT): Identificador único.
   - `nome_cultura` (VARCHAR(50)): Nome da cultura.
   - `necessidade_agua` (DOUBLE): Quantidade ideal de água (litros).
   - `necessidade_pH_min` (DOUBLE): pH mínimo.
   - `necessidade_pH_max` (DOUBLE): pH máximo.
   - `necessidade_fosforo` (DOUBLE): Fósforo ideal (g/m²).
   - `necessidade_potassio` (DOUBLE): Potássio ideal (g/m²).

2. **Lote**
   - `id_lote` (PK, INT): Identificador único.
   - `tamanho_lote` (DOUBLE): Tamanho do lote (m²).
   - `id_cultura` (FK, INT): Cultura plantada.

3. **Sensor**
   - `id_sensor` (PK, INT): Identificador único.
   - `tipo_sensor` (VARCHAR(20)): Tipo ("Umidade", "pH", "Nutrientes").
   - `id_lote` (FK, INT): Lote associado.

4. **Leitura_Sensor**
   - `id_leitura` (PK, INT): Identificador único.
   - `id_sensor` (FK, INT): Sensor associado.
   - `data_hora` (DATETIME): Data e hora da leitura.
   - `valor_umidade` (DOUBLE): Umidade (%).
   - `valor_pH` (DOUBLE): pH.
   - `valor_fosforo` (DOUBLE): Fósforo (mg/kg).
   - `valor_potassio` (DOUBLE): Potássio (mg/kg).

5. **Ajuste**
   - `id_ajuste` (PK, INT): Identificador único.
   - `id_lote` (FK, INT): Lote associado.
   - `data_hora` (DATETIME): Data e hora do ajuste.
   - `quantidade_agua` (DOUBLE): Água aplicada (litros).
   - `quantidade_fosforo` (DOUBLE): Fósforo aplicado (g).
   - `quantidade_potassio` (DOUBLE): Potássio aplicado (g).

### Relacionamentos
- **Cultura → Lote** (1:N): Uma cultura pode estar em vários lotes.
- **Lote → Sensor** (1:N): Um lote pode ter vários sensores.
- **Sensor → Leitura_Sensor** (1:N): Um sensor gera várias leituras.
- **Lote → Ajuste** (1:N): Um lote pode ter vários ajustes.

## Diagrama Entidade-Relacionamento (DER)
![DER do Projeto](modelo_der.png)

## Arquivos do Projeto
- `FarmTech_Model.dmd`: Arquivo do modelo criado no SQL Developer Data Modeler.
- `modelo_der.png`: Imagem do DER exportada.

## Como Executar
1. Baixe o SQL Developer Data Modeler.
2. Abra o arquivo `FarmTech_Model.dmd` no software.
3. Visualize o modelo lógico e relacional.
4. Consulte a imagem `modelo_der.png` para referência.

## Regras de Negócio
- Cada lote está associado a uma única cultura.
- Sensores são instalados em lotes específicos e registram leituras em tempo real.
- Ajustes (água e nutrientes) são aplicados por lote com base nas leituras.
- O sistema armazena dados históricos para análises e previsões.

## Licença
Este projeto é apenas para fins educacionais e não deve ser utilizado comercialmente.
