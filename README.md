# MeuPrimeiroEmprego

Aplicação web voltada a quem busca a primeira oportunidade em tecnologia. O projeto compara um currículo com uma descrição de vaga, apresenta pontos de compatibilidade e ajuda a organizar uma versão do currículo com foco em clareza e leitura por sistemas de recrutamento.

A proposta é melhorar a apresentação das informações existentes, sem inventar experiências, qualificações ou resultados.

## Aplicação publicada

- Aplicação: [INSERIR URL PÚBLICA]
- Repositório: [INSERIR URL DO REPOSITÓRIO]

## O problema

Quem busca a primeira vaga em tecnologia pode ter conhecimentos relevantes adquiridos em cursos, projetos acadêmicos e laboratórios, mas encontrar dificuldade para apresentar essas experiências de forma alinhada à vaga.

O MeuPrimeiroEmprego foi criado para ajudar esse público a:

- Comparar os requisitos de uma vaga com o próprio currículo.
- Identificar conhecimentos já demonstrados.
- Perceber requisitos que ainda não aparecem no documento.
- Reorganizar o currículo sem transformar estudos ou projetos em experiência profissional.

## Público-alvo

- Estudantes de cursos técnicos e graduação em tecnologia.
- Pessoas em transição de carreira.
- Candidatos a estágio ou vagas de nível júnior.
- Profissionais buscando a primeira oportunidade em TI.

## Funcionalidades

> Antes de publicar este README, marque somente o que foi testado e está funcionando.

- [x] Tela inicial com apresentação da proposta.
- [x] Formulário para inserir a descrição da vaga e o currículo.
- [ ] Validação dos campos e dos limites mínimos de caracteres.
- [ ] Análise de compatibilidade.
- [ ] Exibição de palavras-chave encontradas.
- [ ] Exibição de palavras-chave ausentes.
- [ ] Recomendações de melhoria.
- [ ] Geração do currículo ajustado.
- [ ] Cópia do currículo gerado.
- [ ] Exportação em PDF.
- [ ] Layout validado em dispositivos móveis.

## Como funciona

### 1. Inserção da vaga

A pessoa cola a descrição da vaga, incluindo responsabilidades, requisitos e diferenciais.

### 2. Inserção do currículo

Em seguida, cola o conteúdo do currículo atual.

Para quem ainda não trabalhou na área, o documento pode apresentar formação, cursos, projetos pessoais, atividades acadêmicas e laboratórios.

### 3. Análise de compatibilidade

A aplicação compara os textos e apresenta os resultados conforme os critérios implementados no projeto.

Descrição da implementação:

[EXPLICAR AQUI COMO A COMPARAÇÃO REALMENTE FUNCIONA: extração de termos, normalização do texto, lista de palavras-chave, uso de IA ou outra abordagem.]

### 4. Apresentação do diagnóstico

O resultado reúne os pontos de alinhamento e os requisitos não identificados no currículo.

Um requisito ausente significa que ele não foi identificado no texto analisado, e não necessariamente que a pessoa não possui aquele conhecimento.

### 5. Ajuste do currículo

A versão ajustada deve reorganizar e destacar informações já presentes no currículo original.

Conhecimentos adquiridos em laboratório devem continuar identificados como laboratório. Projetos acadêmicos não devem ser apresentados como empregos.

### 6. Revisão e exportação

A pessoa revisa o conteúdo antes de copiar, exportar ou utilizar o currículo em uma candidatura.

## Como interpretar o score

O score representa uma estimativa de compatibilidade produzida pelos critérios desta aplicação.

Ele não representa:

- Uma nota emitida pelo sistema de recrutamento de uma empresa.
- Uma probabilidade de contratação.
- Uma garantia de aprovação em processos seletivos.
- Uma avaliação completa da capacidade profissional do candidato.

### Critério de cálculo

[DESCREVER A FÓRMULA REAL IMPLEMENTADA E SE EXISTEM PESOS PARA REQUISITOS OBRIGATÓRIOS E DIFERENCIAIS.]

[INFORMAR COMO O SISTEMA TRATA CORRESPONDÊNCIAS PARCIAIS, SINÔNIMOS E TERMOS NÃO IDENTIFICADOS, CASO ESSES RECURSOS EXISTAM.]

## Regra de integridade

A aplicação deve melhorar a apresentação do currículo sem acrescentar informações não fornecidas.

Não deve inventar:

- Empresas ou vínculos profissionais.
- Cargos.
- Datas.
- Certificações.
- Formação acadêmica.
- Conhecimentos técnicos.
- Resultados ou métricas.
- Níveis de domínio de ferramentas.

Exemplo de ajuste permitido:

> Reorganizar a descrição de um laboratório de redes para destacar os testes de conectividade já informados no currículo.

Exemplo de ajuste proibido:

> Transformar esse laboratório em experiência profissional de administração de redes corporativas.

## Interface e design

O projeto utiliza uma identidade visual simples, com azul e branco.

### Paleta de referência

| Uso | Cor |
|---|---|
| Fundo principal | `#FFFFFF` |
| Azul primário | `#1D4ED8` |
| Azul escuro | `#1E3A8A` |
| Azul claro | `#DBEAFE` |
| Superfície secundária | `#F8FAFC` |
| Texto principal | `#0F172A` |
| Texto secundário | `#475569` |

### Diretrizes

- Interface em português.
- Hierarquia visual clara.
- Formulários com rótulos e instruções.
- Feedback para ações e erros.
- Layout com foco em leitura e simplicidade.
- Componentes baseados em shadcn/ui, conforme a especificação inicial.

## Tecnologias

O projeto foi desenvolvido com auxílio do Lovable.

[CONFERIR O CÓDIGO E LISTAR AQUI SOMENTE AS TECNOLOGIAS REALMENTE UTILIZADAS.]

Exemplos de itens a verificar no repositório:

- Framework da interface.
- Linguagem.
- Biblioteca de estilos.
- Biblioteca de componentes.
- Biblioteca de exportação em PDF.
- Serviço ou modelo de IA, caso exista.

## Processo de construção

### 1. Definição do escopo

O escopo inicial priorizou o fluxo principal:

1. Colar a descrição da vaga.
2. Colar o currículo.
3. Executar a análise.
4. Consultar o diagnóstico.
5. Revisar o currículo ajustado.
6. Exportar o resultado.

Login, histórico e dashboard não foram priorizados na proposta do MVP.

### 2. Mega prompt utilizado

O prompt foi organizado em blocos:

- Contexto e objetivo.
- Público-alvo.
- Regra de não invenção de informações.
- Telas e navegação.
- Fluxo da análise.
- Regras do currículo ajustado.
- Design system.
- Estados da interface.
- Limites do MVP.

<details>
<summary>Ver o mega prompt utilizado</summary>

[COLAR AQUI O PROMPT EXATO ENVIADO AO LOVABLE.]

</details>

### 3. Evolução do prompt

[EXPLICAR O QUE MUDOU ENTRE A PRIMEIRA IDEIA E A VERSÃO UTILIZADA.]

| Etapa | Decisão ou mudança | Motivo |
|---|---|---|
| Definição do público | Foco na primeira oportunidade em tecnologia | Direcionar a linguagem e os cenários de uso |
| Identidade visual | Azul e branco | Manter uma apresentação simples e consistente |
| Escopo inicial | Priorizar análise e currículo ajustado | Reduzir a complexidade da primeira versão |
| [Outra etapa] | [Mudança realizada] | [Motivo] |

### 4. Refinamentos após a primeira geração

[REGISTRAR APENAS AJUSTES QUE VOCÊ REALMENTE PEDIU OU IMPLEMENTOU.]

| Ajuste | Problema observado | Resultado |
|---|---|---|
| [Ajuste realizado] | [Problema] | [Resultado validado] |

## Testes

Foram preparados cenários fictícios para avaliar a comparação e a preservação das informações do candidato.

Os dados de teste não representam pessoas ou empresas reais.

### Cenários

| Cenário | O que verificar |
|---|---|
| Candidato a suporte júnior com conhecimentos parciais | Identificação de competências presentes e lacunas |
| Mesmo candidato com laboratórios adicionais | Reconhecimento das novas evidências |
| Candidata de front-end concorrendo à vaga de suporte | Diferenciação entre os perfis técnicos |
| Repetição das mesmas entradas | Consistência do resultado |
| Campos vazios ou abaixo do mínimo | Validação e mensagens claras |
| Currículo ajustado | Ausência de experiências inventadas |
| Exportação em PDF | Integridade do texto e da formatação |

### Resultados registrados

[EXECUTAR OS TESTES E PREENCHER A TABELA.]

| Teste | Resultado observado | Status |
|---|---|---|
| Compatibilidade parcial | [Preencher] | Pendente |
| Inclusão de laboratórios | [Preencher] | Pendente |
| Perfil diferente da vaga | [Preencher] | Pendente |
| Consistência da análise | [Preencher] | Pendente |
| Validação dos campos | [Preencher] | Pendente |
| Preservação das informações | [Preencher] | Pendente |
| Exportação em PDF | [Preencher] | Pendente |

## Evidências de funcionamento

[ADICIONAR CAPTURAS REAIS DA APLICAÇÃO NESTA SEÇÃO.]

Sugestões de evidências:

1. Tela inicial.
2. Formulário preenchido com dados fictícios.
3. Diagnóstico de compatibilidade.
4. Currículo ajustado.
5. PDF exportado.

Incluir somente imagens e arquivos que realmente estejam disponíveis no repositório.

## Privacidade e tratamento dos dados

[DESCREVER O COMPORTAMENTO REAL DA IMPLEMENTAÇÃO.]

Informar:

- Se o processamento ocorre no navegador ou em um servidor.
- Se algum texto é enviado a um serviço de IA.
- Se há armazenamento dos dados.
- Como os dados podem ser removidos, caso sejam armazenados.

Não afirmar que os dados permanecem no navegador sem verificar o código e as requisições da aplicação.

Para demonstrações públicas e testes, utilizar dados fictícios.

## Limitações

- O resultado depende da qualidade dos textos fornecidos.
- A ausência de um termo não comprova a ausência de uma competência.
- O score não reproduz necessariamente os critérios de sistemas de recrutamento.
- O currículo ajustado exige revisão humana antes do envio.
- A aplicação não garante entrevistas, aprovação ou contratação.
- [ACRESCENTAR LIMITAÇÕES ESPECÍFICAS DA IMPLEMENTAÇÃO.]

## Executar localmente

[ADICIONAR OS PRÉ-REQUISITOS E OS COMANDOS REAIS APÓS CONFERIR OS ARQUIVOS DO PROJETO.]

Documentar:

1. Como clonar o repositório.
2. Como instalar as dependências.
3. Como configurar variáveis de ambiente, se necessário.
4. Como iniciar o ambiente de desenvolvimento.

Nunca incluir chaves, tokens ou senhas neste README ou no código versionado.

## Possíveis evoluções

- Exportação em `.docx`.
- Histórico de análises.
- Autenticação.
- Comparação entre versões do currículo.
- Suporte a outros idiomas.
- Explicação mais detalhada dos critérios de compatibilidade.

Esses itens são possibilidades futuras e não funcionalidades disponíveis.

## Aprendizados

[PREENCHER COM A SUA EXPERIÊNCIA NO PROJETO.]

Pontos que podem ser abordados:

- Como a especificação influenciou a primeira versão.
- Quais resultados exigiram revisão.
- Como foram testadas as regras de não invenção.
- Quais decisões ajudaram a manter o MVP simples.
- O que você faria diferente em uma próxima versão.

## Autor

Fernando Batista Vieira da Silva

- GitHub: [INSERIR PERFIL]
- LinkedIn: [INSERIR PERFIL, SE DESEJAR]
