# TRT4 • FCC Trainer

Banco de questões e simulador de provas para o **concurso do Tribunal Regional do Trabalho da 4ª Região (TRT4, Edital nº 01/2026, banca FCC)**. As provas estão previstas para **31/01/2027**, em Porto Alegre/RS.

O banco tem 305 questões de múltipla escolha com cinco alternativas, no estilo FCC. Todas trazem gabarito comentado e base legal. As 174 questões de Direito também têm uma **dica de prova**, com mnemônicos e pegadinhas comuns da banca.

O app inteiro é um único arquivo HTML: não precisa de servidor, instalação nem cadastro.

## Como usar

1. Baixe o arquivo [`Simulado TRT 4.html`](Simulado%20TRT%204.html).
2. Abra-o no navegador (Chrome, Edge, Firefox ou Safari, no computador ou no celular).
3. Escolha o seu **perfil de estudo** no topo do Painel e comece a treinar.

O visual usa Bootstrap e Bootstrap Icons via CDN, então é preciso estar conectado à internet. O progresso fica salvo no próprio navegador (`localStorage`) e nada é enviado a servidor algum.

## Funcionalidades

### Painel
- Questões vistas, acertos, erros e percentual geral.
- **Meta diária** ajustável, **sequência de dias** estudados (atual e recorde) e mapa de calor dos últimos 28 dias.
- Progresso e taxa de acerto **por disciplina**.
- Atalhos para Treino livre, Revisão do dia, Só as erradas, Marcadas e Simulado.

### Treinar
- Uma questão por vez, em card, com correção ao clicar ou só depois de confirmar.
- Depois de responder, aparecem o **gabarito comentado** e, nas questões de Direito, a **Dica de prova**.
- Filtros por disciplina e por situação, e busca por texto, artigo ou tema.
- **Revisão inteligente** (repetição espaçada): cada questão fica numa "caixa" de 0 a 4. Quem acerta sobe de caixa e vê a questão de novo em 1, 3, 7 ou 15 dias; quem erra volta para a caixa 0.
- Opção de embaralhar as alternativas e de marcar questões para revisão.

### Simulado
- **Simulado do cargo**: 30 questões de Conhecimentos Gerais e 30 de Específicos, com cronômetro de 4 horas, como no edital.
- **Simulado personalizado**: você escolhe o número de questões, o tempo e as disciplinas, e pode limitar a questões ainda não respondidas.
- Não há feedback durante a prova. No fim aparecem a nota, o gabarito comentado e a opção de revisar só as erradas.

### Desempenho
- Tabela de acertos e erros por disciplina.
- Lista das questões em que você tem mais dificuldade.
- Histórico dos simulados feitos, com data, duração e nota.

### Banco
- Consulta de todas as questões, com filtro por disciplina e busca.
- **Cadastro manual** de questões próprias e **importação em lote** via JSON.
- Exportação do banco e **backup e restauração do progresso** em arquivo `.json`, útil para trocar de navegador ou de aparelho.

### Perfis de estudo
O conteúdo programático muda conforme o cargo, então o banco pode ser filtrado por perfil:

| Perfil | O que inclui |
|---|---|
| Área Administrativa (03 + 19) | Tudo, exceto TI |
| Técnico Judiciário, Área Administrativa (19) | Conhecimentos Gerais + Constitucional, Administrativo, Administração Pública, Gestão de Pessoas, Lei 8.112/11.416, CLT e Processo do Trabalho (sem AFO) |
| Analista Judiciário, Área Administrativa (03) | Conhecimentos Gerais + Constitucional, Administrativo, Administração Pública, AFO, Gestão de Pessoas e Lei 8.112/11.416 (sem CLT e Processo do Trabalho) |
| Banco completo | Todas as disciplinas, inclusive TI (códigos 14 e 22) |

### Atalhos de teclado
| Tecla | Ação |
|---|---|
| `A`–`E` ou `1`–`5` | Escolher alternativa |
| `Enter` | Confirmar / próxima |
| `←` `→` | Questão anterior / próxima |
| `F` | Marcar para revisão |
| `G` | Revelar o gabarito (no treino) |
| `T` | Alternar tema claro/escuro |
| `?` | Abrir a ajuda |

## Conteúdo do banco

| Disciplina | Questões |
|---|---:|
| Direito do Trabalho (CLT) | 53 |
| Direito Administrativo (inclui Lei 14.133/2021, LAI e LGPD) | 32 |
| Lei 8.112/1990 e Carreiras do PJU (Lei 11.416/2006) | 27 |
| Direito Constitucional | 22 |
| Administração Pública e Geral | 20 |
| Processo do Trabalho | 19 |
| Legislação Institucional (CNJ, CSJT e TRT4) | 18 |
| Gestão de Pessoas | 18 |
| Língua Portuguesa | 16 |
| Edital TRT4 e regras da FCC | 16 |
| Orçamento Público / AFO | 14 |
| Raciocínio Lógico e Estatística | 13 |
| Direitos Humanos | 11 |
| Informática (Conhecimentos Gerais) | 10 |
| TI (Analista e Técnico) | 10 |
| Atualizações 2025/2026 (EC 141/2026, cotas, AQ do PJU) | 6 |
| **Total** | **305** |

## Formato das questões

Cada questão é um objeto com os campos abaixo. É o mesmo formato aceito pela importação em lote:

```json
{
  "i": "DT14",
  "d": "DT",
  "t": "CLT, art. 73",
  "q": "Sobre o trabalho noturno urbano, assinale a alternativa correta.",
  "a": ["Alternativa A", "Alternativa B", "Alternativa C", "Alternativa D", "Alternativa E"],
  "c": 1,
  "e": "Comentário com a base legal.",
  "k": "Dica de prova (opcional)."
}
```

| Campo | Significado |
|---|---|
| `i` | Identificador único (sigla da disciplina + número) |
| `d` | Disciplina: `DT`, `PT`, `CO`, `AD`, `RJ`, `DH`, `LP`, `RL`, `IN`, `TI`, `ED`, `AT`, `AP`, `GP`, `OR`, `LG` |
| `t` | Tema ou dispositivo legal |
| `q` | Enunciado |
| `a` | Exatamente 5 alternativas |
| `c` | Índice da alternativa correta (0 = A … 4 = E) |
| `e` | Comentário do gabarito |
| `k` | Dica de prova (opcional) |

## Estrutura do arquivo

O app está todo em `Simulado TRT 4.html`, organizado em três blocos:

1. **Estilos**: CSS próprio sobre o Bootstrap 5.3, com tema claro e escuro.
2. **Script principal**: disciplinas (`DISC`), banco nativo (`BANK`), persistência em `localStorage` e as telas de Painel, Treino, Simulado, Desempenho e Banco, além dos atalhos.
3. **Pacote administrativo** (segundo `<script>`): disciplinas extras (Administração Pública, Gestão de Pessoas, AFO e Legislação Institucional), as questões do `PACK` e os perfis de estudo por cargo.

## Aviso

As questões foram feitas com base no edital e na legislação vigente até novembro de 2026, mas **não substituem a leitura do edital oficial e da lei seca**. Normas recentes, como a EC 141/2026, as resoluções do CNJ e do CSJT e o Regimento Interno do TRT4, podem mudar. Confira sempre o texto atualizado no Planalto, no CNJ e nos sites do TRT4 e da FCC. Se encontrar algum erro, abra uma *issue*.
