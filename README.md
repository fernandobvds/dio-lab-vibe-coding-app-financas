# 💸 App de Organização de Finanças Pessoais com Vibe Coding - Feranando Batista

```
==================================================
1. FINALIDADE DESTE DOCUMENTO
==================================================

Este PRD define a visão, o escopo, os requisitos e os critérios
de aceite do MVP do Organiza.

É a referência consolidada do produto, não uma autorização
para implementar todas as funcionalidades de uma só vez.

Se utilizado em um projeto existente:
- Inspecionar a implementação antes de propor alterações.
- Preservar dados e funcionalidades corretas.
- Não reconstruir o aplicativo.
- Não substituir o backend sem autorização.
- Não executar migrações destrutivas.
- Implementar somente a etapa expressamente autorizada.
- Não publicar automaticamente.
- Informar divergências entre o PRD e o código existente.
- Não considerar requisitos descritos como funcionalidades
  já implementadas ou validadas.

==================================================
2. VISÃO DO PRODUTO
==================================================

Criar um aplicativo que ajude pessoas a registrar, compreender
e acompanhar suas finanças pessoais por meio de conversas simples.

O usuário deve poder informar receitas e despesas em linguagem
natural, revisar a interpretação e confirmar antes de salvar.

O produto deve combinar:
- Conversa como caminho principal.
- Formulário guiado como alternativa equivalente.
- Resumos financeiros claros.
- Acompanhamento de metas.
- Orientações educativas baseadas nos registros.
- Desenho universal desde a concepção.

O aplicativo não acessa contas bancárias nem movimenta dinheiro
no MVP.

==================================================
3. PROBLEMA E HIPÓTESES
==================================================

Problema a investigar:
Pessoas iniciantes podem encontrar dificuldade para manter
um controle financeiro quando precisam preencher muitos campos,
interpretar termos técnicos ou manter planilhas.

Hipóteses:
- Registrar por conversa pode reduzir o esforço de entrada.
- Revisar uma prévia pode aumentar a confiança nos registros.
- Resumos simples podem facilitar a compreensão dos gastos.
- Orientações contextualizadas podem incentivar o uso contínuo.
- Alternativas ao chat podem ampliar a acessibilidade.

Essas hipóteses devem ser validadas com usuários.
Não apresentá-las como resultados já comprovados.

==================================================
4. PÚBLICO-ALVO
==================================================

Pessoas adultas iniciantes em organização financeira.

Considerar diferentes cenários de uso:
- Baixa familiaridade com tecnologia.
- Diferentes níveis de compreensão financeira.
- Pessoas idosas.
- Pessoas com deficiência visual, motora ou cognitiva.
- Uso por teclado, leitor de tela ou ampliação.
- Dispositivos pequenos.
- Conexão limitada ou instável.

Não exigir coleta de características pessoais para oferecer
uma experiência acessível.

==================================================
5. OBJETIVOS
==================================================

- Facilitar o registro de receitas e despesas.
- Permitir revisão, correção e cancelamento.
- Classificar transações com sugestões corrigíveis.
- Mostrar receitas, despesas e resultado do período.
- Apresentar despesas por categoria.
- Acompanhar metas com valores informados pelo usuário.
- Explicar os números com linguagem educativa e não julgadora.
- Oferecer alternativas de interação equivalentes ao chat.
- Proteger os dados e isolar as contas.

==================================================
6. PRINCIPAIS TELAS
==================================================

1. Acesso:
   Cadastro, login e recuperação de acesso.

2. Introdução:
   Explicação do funcionamento, exemplos e aviso sobre IA.

3. Conversa:
   Registro por linguagem natural, prévias e orientações.

4. Transações:
   Listagem, filtros, consulta, edição e exclusão.

5. Resumo:
   Receitas, despesas, resultado e categorias por período.

6. Metas:
   Cadastro e acompanhamento de objetivos financeiros.

7. Configurações:
   Preferências, privacidade e gestão de dados.

Todas as telas devem ter estados aplicáveis de:
- Carregamento.
- Ausência de dados.
- Sucesso.
- Erro.
- Falha de conexão.
- Sessão expirada.

==================================================
7. AUTENTICAÇÃO E PERFIL
==================================================

Implementar:
- Cadastro por e-mail e senha.
- Login.
- Logout.
- Recuperação de acesso.
- Tratamento de sessão expirada.
- Proteção das áreas privadas.

Preferências:
- Fuso horário.
- Idioma.
- Moeda.
- Ocultar valores na interface.

Regras:
- Usar o provedor de autenticação adotado pelo projeto.
- Não criar mecanismo próprio de armazenamento de senhas.
- Não expor credenciais privilegiadas no frontend.
- Permitir colagem e gerenciadores de senha.
- Identificar o usuário pela sessão autenticada.
- Não confiar em user_id enviado pelo navegador como autorização.
- Não confundir conta do usuário com perfil público.

==================================================
8. REGISTRO POR CONVERSA
==================================================

Interpretar:
- Intenção.
- Tipo: receita ou despesa.
- Valor.
- Data.
- Descrição, quando disponível.
- Categoria sugerida.

Exemplo:
"Gastei 42,90 no almoço ontem."

Fluxo:
1. Receber a mensagem.
2. Identificar intenção e extrair campos.
3. Perguntar quando faltar informação obrigatória.
4. Apresentar prévia.
5. Permitir confirmar, corrigir ou cancelar.
6. Validar no backend.
7. Salvar após confirmação.
8. Atualizar a interface após sucesso.

Regras:
- Valor e tipo são obrigatórios.
- Valor deve ser maior que zero.
- Nunca inventar valor.
- Não inventar estabelecimento ou descrição.
- Quando faltar data, sugerir hoje e exibir a data completa.
- Resolver datas relativas conforme o fuso do perfil.
- Esclarecer datas ambíguas.
- Fazer perguntas curtas, preferencialmente uma por vez.
- Usar categorias padrão ou do próprio usuário.
- Se não houver categoria adequada, sugerir Outros.
- Permitir corrigir a categoria.
- Mensagens hipotéticas não geram registros.
- Perguntas educativas não geram registros.
- Intenções mistas ou ambíguas exigem esclarecimento.
- Não interpretar automaticamente situações fora do escopo,
  como parcelamentos ou transferências ambíguas.

Mensagens com várias transações:
- Apresentar cada transação para revisão.
- Confirmar explicitamente o conjunto.
- Evitar gravação parcial sem tratamento claro.

==================================================
9. PRÉVIA, CONFIRMAÇÃO E IDEMPOTÊNCIA
==================================================

A prévia deve mostrar:
- Tipo.
- Valor em BRL.
- Data completa.
- Descrição, quando disponível.
- Categoria sugerida.

Ações:
- Confirmar.
- Corrigir.
- Cancelar.

Regras:
- Não persistir a transação antes da confirmação.
- Vincular a confirmação à versão exata da prévia.
- Alterar a prévia invalida a confirmação anterior.
- Revalidar sessão, campos e categoria ao confirmar.
- Uma mesma operação reenviada não pode gerar duplicata.
- Garantir idempotência no backend/banco.
- Não depender somente de desabilitar o botão.
- Transações semelhantes podem gerar aviso, não bloqueio automático.
- Exibir sucesso somente após confirmação do backend.
- Em falha de gravação ambígua, verificar o estado da operação
  antes de reenviar.
- Cancelar não cria transação.

==================================================
10. FORMULÁRIO GUIADO E TRANSAÇÕES
==================================================

Oferecer alternativa acessível ao chat.

Campos:
- Tipo.
- Valor.
- Data.
- Descrição opcional.
- Categoria.

Permitir:
- Criar.
- Consultar.
- Filtrar.
- Editar.
- Excluir com confirmação.

Regras:
- Preservar os dados digitados em falhas recuperáveis.
- Não apresentar sucesso falso.
- Manter o formulário independente da cota de IA.
- Não prometer funcionamento durante indisponibilidade
  de rede, sessão ou backend.
- Não armazenar rascunhos financeiros persistentemente
  no navegador sem uma decisão explícita de privacidade



- Prints ou pequenos vídeos das interações com a IA;  
- Um resumo do que o seu **App de Finanças Pessoais** faz;  
- Uma breve **reflexão sobre o processo**:
  - O que funcionou bem?  
  - O que não funcionou como o esperado?  
  - O que aprendeu sobre conversar com IAs?
 
==================================================
11. CATEGORIAS
==================================================

Oferecer categorias padrão e personalizadas.

Categorias padrão sugeridas:
Receitas:
- Salário.
- Freelance.
- Rendimentos.
- Outros.

Despesas:
- Alimentação.
- Moradia.
- Transporte.
- Saúde.
- Educação.
- Lazer.
- Assinaturas.
- Compras.
- Outros.

Regras:
- Categorias padrão são somente leitura para usuários comuns.
- Categorias personalizadas pertencem ao criador.
- Não permitir vincular categoria privada de outra pessoa.
- Agrupar por identificador, não apenas pelo nome.
- Renomear categoria preserva suas relações.
- Não excluir silenciosamente categoria em uso.
- Exigir reclassificação ou aplicar outra regra segura
  explicitamente definida.

==================================================
12. RESUMOS FINANCEIROS
==================================================

Exibir:
- Total de receitas.
- Total de despesas.
- Resultado: receitas menos despesas.
- Despesas por categoria.
- Participação percentual de cada categoria.

Períodos:
- Mês atual, como padrão.
- Mês anterior.
- Personalizado.

Regras:
- Filtrar pela data da transação.
- Incluir início e fim do intervalo.
- Impedir início posterior ao fim.
- Usar o fuso do perfil para determinar hoje e mês atual.
- Tratar colunas DATE como datas civis, sem mudar o dia por UTC.
- Considerar todos os registros autorizados do período.
- Não limitar totais à página carregada da listagem.
- Incluir registros de chat e formulário sem duplicação.
- Excluir registros removidos.
- Não incluir prévias, rascunhos ou falhas.
- Não incluir metas como receitas ou despesas.
- Agrupar transações sem categoria em "Sem categoria".
- Tratar divisão por zero.
- Arredondar percentuais somente para apresentação.
- Ordenar categorias por despesa, do maior para o menor.
- Não usar dados demonstrativos em contas reais.

Exibir:
"Este resumo considera apenas os registros adicionados ao aplicativo."

Não chamar o resultado de:
- Saldo bancário.
- Dinheiro disponível.
- Valor confirmado em conta.

Falhas:
- Erro de consulta não pode aparecer como valor zerado.
- Diferenciar período vazio de falha do backend.
- Oferecer nova tentativa.
- Não apresentar dados de um período como se fossem de outro.

==================================================
13. METAS
==================================================

Campos:
- Nome.
- Valor-alvo.
- Valor informado como reservado.
- Prazo opcional.

Exibir:
- Valor-alvo.
- Reservado.
- Valor restante.
- Progresso percentual.
- Excedente.
- Prazo e estado.

Cálculos:
- Restante = máximo entre alvo - reservado e zero.
- Progresso = reservado / alvo × 100.

Regras:
- Alvo maior que zero.
- Reservado não negativo.
- Permitir reservado acima do alvo.
- Mostrar "Meta atingida" quando aplicável.
- Mostrar excedente.
- Barra visual pode parar em 100%.
- Texto preserva o progresso real acima de 100%.
- Prazo vencido não impede atualização.
- Não movimentar dinheiro.
- Não criar transação automática.
- Não afirmar que o valor foi verificado em conta.

Usar:
"Valor informado como reservado".

Contribuição mensal sugerida permanece fora do MVP inicial.

==================================================
14. AGENTE FINANCEIRO EDUCATIVO
==================================================

Oferecer acesso "Entender meus números".

Ações sugeridas:
- Explique meu resumo.
- Onde estão minhas maiores despesas?
- Quais possibilidades de economia aparecem nos registros?
- Explique minhas metas.

Mostrar o período utilizado.

O agente deve:
- Usar dados autorizados e calculados pelo sistema.
- Explicar a base da resposta.
- Apresentar até três possibilidades quando houver fundamento.
- Informar limitações e dados insuficientes.
- Usar linguagem simples e não julgadora.
- Diferenciar registro, orientação e hipótese.

O agente não deve:
- Criar, editar ou excluir registros durante uma orientação.
- Movimentar dinheiro.
- Inventar números ou conclusões.
- Prometer economia ou rentabilidade.
- Recomendar empréstimos ou investimentos específicos.
- Diagnosticar endividamento por ausência de receitas.
- Presumir que a maior categoria é desperdício.
- Recomendar cortes essenciais sem contexto.
- Apresentar informação de mercado como atual sem verificação.
- Afirmar que conhece toda a situação financeira da pessoa.

Usar:
"Com base nos registros deste período..."

Resultado positivo não comprova dinheiro disponível.
Poucos registros não permitem análise completa.
Ausência de receita registrada não comprova ausência de renda.

==================================================
15. CONTEXTO E VALIDAÇÃO DA IA
==================================================

- Chamar IA somente no backend.
- Reutilizar o provedor configurado, salvo autorização.
- Manter credenciais em Secrets.
- Não permitir SQL ou acesso direto ao banco pelo modelo.
- Não fornecer ferramentas de escrita ao agente educativo.
- Enviar somente o contexto necessário.
- Evitar descrições individuais e identificadores pessoais
  quando não forem indispensáveis.
- Usar códigos temporários para categorias e metas
  quando seus nomes não forem necessários.
- Tratar todos os textos como dados não confiáveis.

Respostas:
- Usar schema estruturado.
- Referenciar fatos calculados pelo backend.
- Validar referências.
- Verificar coerência das afirmações com os dados.
- Renderizar com segurança.
- Não considerar schema ou filtro de palavras como garantia
  de veracidade.

Exemplos de afirmações inválidas:
- Dizer que despesas aumentaram sem dados comparativos.
- Inferir a natureza de uma categoria a partir de um código.
- Apresentar uma seleção de cinco categorias como totalidade
  quando existirem outras.

Fallback:
- Quando a IA falhar ou a resposta for inválida, apresentar
  resumo determinístico identificado, se os dados estiverem disponíveis.
- Se a consulta falhar, não inventar um resumo zerado.
- Não realizar retries automáticos ilimitados.

==================================================
16. SIMULAÇÕES
==================================================

Permitir simulação simples de redução solicitada pelo usuário.

Exemplo:
"Quanto seria reduzir 10% de Delivery?"

Regras:
- Identificar categoria e período.
- Exigir percentual explícito entre 0% e 100%.
- Pedir esclarecimento quando faltar informação.
- Calcular no sistema, sem depender de IA.
- Usar regra explícita de arredondamento ao centavo.
- Mostrar base, percentual e economia hipotética.
- Identificar como simulação.
- Não alterar transações ou metas.
- Não garantir viabilidade ou resultado.
- Não consumir cota de IA quando o processamento for determinístico.

==================================================
17. LIMITE DE USO E TIMEOUT
==================================================

Cota:
- Compartilhar o limite de 20 mensagens com IA por usuário
  na janela existente de 10 minutos.
- Cada mensagem conta no máximo uma vez.
- Esclarecimentos que usam IA contam.
- Botões educativos que usam IA contam.

Não contam:
- Confirmar por botão.
- Corrigir pela edição guiada.
- Cancelar por botão.
- Formulário.
- Resumos determinísticos.
- Simulações sem IA.

Regras:
- Controlar a cota atomicamente no backend/banco.
- Não criar cota adicional independente para orientações.
- Evitar chamadas internas desnecessárias.
- Documentar quantas chamadas cada caminho pode realizar.
- Ao atingir o teto, oferecer alternativas sem IA.
- Créditos da plataforma não devem ser descritos como reais.

Timeout:
- Implementar limite explícito no backend.
- Valor inicial proposto: 30 segundos, sujeito à compatibilidade
  com a plataforma e avaliação operacional.
- Se houver múltiplas chamadas no pedido, compartilhar o orçamento.
- Tentar cancelar upstream quando suportado.
- Descartar respostas tardias.
- Encerrar carregamento e apresentar alternativa clara.
- Não prometer que cancelamento elimina cobrança.
- Não confundir timeout de interpretação com timeout de gravação.

==================================================
18. ARQUITETURA E DADOS
==================================================

Reutilizar a arquitetura existente do projeto.

Entidades principais:
- Perfis.
- Transações.
- Categorias.
- Metas.
- Controle de operações/idempotência.
- Controle de uso de IA.

Princípios:
- Valores monetários em centavos inteiros.
- Evitar perda de precisão entre banco, backend e frontend.
- Data da transação separada do horário de criação.
- Dados pessoais associados ao usuário autenticado.
- Constraints e validação no backend/banco.
- Não adicionar persistência de conversa sem decisão explícita.
- Migrações devem preservar registros existentes.

==================================================
19. SEGURANÇA E ISOLAMENTO
==================================================

- Aplicar RLS às tabelas pessoais expostas.
- Autorizar leitura e escrita por usuário.
- Proteger totais, funções, views e endpoints.
- Não confiar apenas na interface.
- Preferir SECURITY INVOKER para novas funções quando aplicável.
- Verificar identidade, permissões e políticas em conjunto.
- Não criar SECURITY DEFINER sem necessidade justificada
  e autorização explícita.
- Não usar credencial privilegiada para contornar isolamento.
- Usuário sem sessão não recebe dados financeiros.

Cache e concorrência:
- Separar cache por usuário e filtros.
- Limpar dados pessoais no logout.
- Impedir dados da conta anterior na troca de sessão.
- Ignorar respostas antigas após mudança de usuário ou período.
- Não permitir que uma resposta atrasada sobrescreva estado atual.

==================================================
20. PRIVACIDADE E GESTÃO DE DADOS
==================================================

Antes do piloto externo:
- Definir responsável e canal de contato.
- Documentar finalidades e dados tratados.
- Revisar base legal de cada tratamento.
- Informar processamento por IA e fornecedores.
- Definir retenção e exclusão.
- Verificar configurações e condições do provedor.
- Documentar limites de backups e logs.
- Disponibilizar exportação dos registros do usuário.
- Disponibilizar fluxo de exclusão ou solicitação de exclusão
  de conta e dados.

Não:
- Prometer ausência de retenção sem verificação.
- Afirmar conformidade jurídica apenas por existir aviso.
- Considerar CSV, isoladamente, prova de cumprimento de todos
  os requisitos de portabilidade.
- Tratar exclusão de um lançamento como exclusão da conta inteira.

Esses itens fazem parte do fechamento do MVP.
Ainda precisam de implementação ou definição quando ausentes.

==================================================
21. DESENHO UNIVERSAL E ACESSIBILIDADE
==================================================

Aplicar:
- Uso equitativo.
- Flexibilidade.
- Simplicidade.
- Informação perceptível.
- Tolerância ao erro.
- Baixo esforço.
- Espaço adequado para interação.

Adotar WCAG 2.2 AA como referência de avaliação.

Requisitos:
- Chat não é o único caminho.
- Teclado sem aprisionamento de foco.
- Foco visível e não oculto.
- Labels e nomes acessíveis.
- Erros com orientação de correção.
- Contraste adequado.
- Informação não dependente apenas de cor.
- Ampliação de texto a 200%.
- Reflow conforme critérios aplicáveis.
- Controles de toque de 44 × 44 pixels CSS como padrão.
- Gráficos com tabela ou lista equivalente.
- Não depender de hover.
- Respeitar redução de movimento.
- Não animar respostas letra por letra.
- Não mover foco a cada mensagem.
- Anunciar atualizações sem reler toda a conversa.
- Não impor tempo curto para revisão.

Testes automatizados ou inspeção de atributos não substituem
avaliação manual com tecnologias assistivas.
```

O Organiza é um aplicativo de organização financeira pessoal que facilita o controle de receitas, despesas e metas.

Suas principais funções são:

Registrar receitas e despesas por conversa, com revisão e confirmação antes de salvar.

Oferecer um formulário guiado como alternativa ao chat.

Sugerir categorias e permitir consultar, editar e excluir lançamentos.

Mostrar resumos por período, com receitas, despesas, resultado e gastos por categoria.

Acompanhar metas, incluindo valor-alvo, valor informado como reservado, progresso e prazo.

Explicar os números com um agente de IA educativo, sem julgamentos ou promessas de resultado.

Simular possíveis economias sem alterar os registros.


Site:

<img width="333" height="405" alt="{EDFEC6BF-6060-4ABC-8EDF-D48C730FD751}" src="https://github.com/user-attachments/assets/d51c6175-9149-43f4-9df3-b0c7e41edf0c" />

<img width="675" height="804" alt="image" src="https://github.com/user-attachments/assets/986e5ab0-6936-4a0e-9949-09cd4628924f" />

<img width="383" height="417" alt="{16B25540-16D9-4713-B1CB-68CC1087ED11}" src="https://github.com/user-attachments/assets/6085055f-5439-4a0e-a34c-6d3ddd103ec8" />

<img width="379" height="404" alt="{B9967CFC-7BE7-4806-9BAA-4C6462736FD4}" src="https://github.com/user-attachments/assets/871b10d8-8530-4f58-9e3b-8d7a5f3151fe" />

