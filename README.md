# Primeiro Emprego TI

Aplicação web voltada a quem busca a primeira oportunidade em tecnologia. O projeto compara um currículo com uma descrição de vaga, apresenta pontos de compatibilidade e ajuda a organizar uma versão do currículo com foco em clareza e leitura por sistemas de recrutamento.

A proposta é melhorar a apresentação das informações existentes, sem inventar experiências, qualificações ou resultados.

## Aplicação publicada

- Aplicação: [primeiroempregoti.lovable.app]


## O problema

Quem busca a primeira vaga em tecnologia pode ter conhecimentos relevantes adquiridos em cursos, projetos acadêmicos e laboratórios, mas encontram dificuldade para apresentar essas experiências de forma alinhada à vaga.

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
- [x] Validação dos campos e dos limites mínimos de caracteres.
- [x] Análise de compatibilidade.
- [x] Exibição de palavras-chave encontradas.
- [x] Exibição de palavras-chave ausentes.
- [x] Recomendações de melhoria.
- [x] Geração do currículo ajustado.
- [x] Cópia do currículo gerado.
- [x] Exportação em PDF.
- [x] Layout validado em dispositivos móveis.

## Como funciona

### 1. Inserção da vaga

O candidato cola a descrição da vaga, incluindo responsabilidades, requisitos e diferenciais.

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

### Como funciona

O MeuPrimeiroEmprego realiza uma análise de compatibilidade determinística e 100% local no navegador (src/lib/analyzer.ts). O motor confronta o texto da vaga contra um dicionário fixo de 53 tecnologias e competências com suporte a sinônimos e correspondências parciais, calculando um índice de compatibilidade de 0 a 100% com base nos termos encontrados. Em seguida, o currículo fornecido é reorganizado em seções padronizadas para leitura por ATS, priorizando na seção de habilidades os termos já declarados pelo candidato que coincidem com a vaga. Nenhuma informação nova é inventada ou adicionada ao currículo, não há uso de inteligência artificial generativa e nenhum dado é transmitido para servidores externos, permanecendo restrito à memória de sessão do navegador.

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
<summary># Mega Prompt — [MeuPrimeiroEmprego]

## 1. Contexto
Você é um desenvolvedor front-end sênior. Crie um aplicativo web chamado
**[MeuPrimeiroEmprego]** usando React, TypeScript, Tailwind CSS e shadcn/ui.

O app ajuda pessoas a adaptar o currículo a uma vaga antes de se candidatarem destinada apenas para o publico de tecnologia.
Ele compara o currículo com a descrição da vaga, identifica alinhamentos e
lacunas e gera uma versão ATS friendly.

## 2. Regra inegociável
O app NUNCA deve inventar experiência, emprego, certificação, formação,
tecnologia, data ou conquista.

Ele pode apenas:
- Reorganizar informações existentes;
- Destacar experiências relevantes para a vaga;
- Sugerir substituições de termos quando houver equivalência real;
- Recomendar que o usuário adicione manualmente uma informação verdadeira.

Exiba este aviso em local visível:
“Este app melhora a apresentação do seu currículo, mas nunca inventa
experiência ou qualificação.”

## 3. Escopo do MVP
Construa apenas:
- Tela inicial;
- Formulário de análise;
- Tela de resultado;
- Geração do currículo ajustado;
- Exportação em PDF.

Não implemente login, banco de dados, histórico, integrações externas,
pagamento ou painel administrativo.

## 4. Telas

### Tela 1 — Início
Objetivo: explicar o app em 10 segundos e levar o usuário à análise.

Elementos:
- Header com logotipo textual “[Nome]” e botão “Analisar currículo”;
- Hero com título “[sua promessa principal]”;
- Subtítulo explicando entrada: vaga + currículo;
- Três cards: “Cole a vaga”, “Cole o currículo”, “Receba a versão ATS”;
- Aviso sobre não invenção de experiência;
- CTA principal: “Começar análise”.

### Tela 2 — Análise
Objetivo: coletar os dois textos.

Elementos:
- Campo 1: “Descrição da vaga” — textarea grande;
- Campo 2: “Seu currículo atual” — textarea grande;
- Contador de caracteres para ambos;
- Botão “Analisar compatibilidade”, desabilitado até os dois campos
  terem conteúdo mínimo;
- Botão “Limpar”;
- Estado de carregamento durante a análise.

Validações:
- Vaga: mínimo de [200] caracteres;
- Currículo: mínimo de [500] caracteres;
- Mensagens de erro claras em português.

### Tela 3 — Resultado
Objetivo: mostrar o diagnóstico antes do currículo final.

Seções:
1. **Score de compatibilidade**
   - Percentual de 0 a 100;
   - Explicação curta do resultado;
   - Barra de progresso.

2. **Palavras-chave encontradas**
   - Badges com termos presentes na vaga e no currículo.

3. **Palavras-chave ausentes ou fracas**
   - Badges com termos relevantes da vaga que não aparecem no currículo;
   - Para cada termo, uma sugestão honesta: onde poderia existir evidência
     real ou se deve ser ignorado.

4. **Recomendações**
   - Lista de 3 a 7 ajustes práticos;
   - Cada item deve indicar o motivo e não pedir invenção de conteúdo.

5. **Currículo ATS friendly**
   - Texto gerado em seções claras;
   - Botão “Copiar texto”;
   - Botão “Exportar PDF”.

## 5. Fluxo da análise

1. Usuário cola a descrição da vaga.
2. Usuário cola o currículo.
3. Usuário clica em “Analisar compatibilidade”.
4. O sistema extrai termos relevantes da vaga: hard skills, ferramentas,
   responsabilidades, requisitos e diferenciais.
5. O sistema compara esses termos com o currículo.
6. O sistema calcula um score de compatibilidade.
7. O sistema classifica termos como:
   - Encontrado;
   - Parcialmente encontrado;
   - Ausente.
8. O sistema gera recomendações apenas com base em informações reais do currículo.
9. O sistema reescreve o currículo em formato ATS friendly.
10. O usuário revisa, copia ou exporta em PDF.

## 6. Regras do currículo ATS friendly

- Usar títulos de seção padrão: Resumo, Experiência, Formação, Habilidades;
- Manter ordem cronológica inversa;
- Usar linguagem objetiva e verbos de ação;
- Priorizar palavras-chave reais da vaga quando houver correspondência no currículo;
- Não usar tabelas, colunas, ícones, gráficos ou elementos que prejudiquem leitura por ATS;
- Preservar datas, empresas, cargos e conquistas originais;
- Não acrescentar nenhuma informação nova que não esteja no currículo original.

## 7. Design system

Use shadcn/ui com Tailwind CSS.

Paleta:
- Branco: fundo principal, `#FFFFFF`;
- Azul primário: `#1D4ED8`;
- Azul escuro: `#1E3A8A`;
- Azul claro: `#DBEAFE`;
- Cinza neutro: `#F8FAFC`;
- Texto principal: `#0F172A`;
- Texto secundário: `#475569`;
- Sucesso: `#16A34A`;
- Alerta: `#D97706`;
- Erro: `#DC2626`.

Aplicação:
- `--background`: branco;
- `--foreground`: texto principal;
- `--primary`: azul primário;
- `--primary-foreground`: branco;
- `--muted`: cinza neutro;
- `--muted-foreground`: texto secundário;
- `--border`: cinza claro;
- `--ring`: azul primário.

Componentes shadcn/ui:
- Button para ações principais;
- Card para blocos de conteúdo;
- Textarea para vaga e currículo;
- Badge para palavras-chave;
- Progress para o score;
- Alert para avisos e erros;
- Tabs para alternar entre “Diagnóstico” e “Currículo ajustado”;
- Sonner para feedback de cópia e exportação.

Tipografia:
- Fonte: Inter;
- Títulos: semibold;
- Corpo: regular;
- Espaçamento generoso e hierarquia visual clara.

Estilo:
- Interface limpa, profissional e minimalista;
- Muito espaço em branco;
- Bordas arredondadas;
- Sem gradientes chamativos;
- Design responsivo para desktop e mobile.

## 8. Estados da interface

Implemente:
- Estado vazio;
- Estado de carregamento;
- Estado de erro;
- Estado de sucesso;
- Botões desabilitados quando obrigatório;
- Feedback após copiar e exportar.

## 9. Ordem de construção

1. Layout base e design system;
2. Tela inicial;
3. Formulário de análise;
4. Tela de resultado;
5. Lógica de comparação e score;
6. Geração do currículo;
7. Exportação em PDF;
8. Revisão de responsividade e acessibilidade.


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

## Evidências de funcionamento

<img width="577" height="429" alt="{7DD6EB4A-1F1F-4071-97AD-F807F15CA7AE}" src="https://github.com/user-attachments/assets/72552ea8-2998-4e75-892c-66bfc5963958" />
<img width="570" height="453" alt="{660F771B-122A-4121-AD68-A47D9A258A70}" src="https://github.com/user-attachments/assets/d4538319-b5d2-4bc5-ba76-030d3a82036e" />


## Privacidade e tratamento dos dados

Envio externo: Nenhum. Não há chamadas de rede (fetch, axios), nem APIs de terceiros, nem funções no servidor. O processamento é 100% executado no browser pelo runtime do JavaScript.

Armazenamento: Ocorre exclusivamente no sessionStorage do navegador.

Não há banco de dados, nem armazenamento persistente de longo prazo (localStorage), nem cookies. Ao fechar a aba, os dados são descartados.

## Limitações

- O resultado depende da qualidade dos textos fornecidos.
- A ausência de um termo não comprova a ausência de uma competência.
- O score não reproduz necessariamente os critérios de sistemas de recrutamento.
- O currículo ajustado exige revisão humana antes do envio.
- A aplicação não garante entrevistas, aprovação ou contratação.
- [ACRESCENTAR LIMITAÇÕES ESPECÍFICAS DA IMPLEMENTAÇÃO.]

## Possíveis evoluções

- Exportação em `.docx`.
- Histórico de análises.
- Autenticação.
- Comparação entre versões do currículo.
- Suporte a outros idiomas.
- Explicação mais detalhada dos critérios de compatibilidade.

Esses itens são possibilidades futuras e não funcionalidades disponíveis.


## Autor

Fernando Batista Vieira da Silva

- GitHub: [INSERIR PERFIL]
- LinkedIn: [INSERIR PERFIL, SE DESEJAR]
