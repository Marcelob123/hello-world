# Agenda Salão — Etapa 5: recebimentos e clientes

Interface mobile preservada. Esta versão acrescenta confirmação de recebimento ao finalizar, quantidade e perfil financeiro dos clientes, e lista compacta no Início. Mantém vários serviços, agenda verde, mensagens editáveis e relatórios.

## 1. Atualizar no Visual Studio Code

1. Extraia o ZIP.
2. Copie **todo o conteúdo** da pasta `app-salao-etapa-5-recebimentos` para a pasta em que você já trabalha. Substitua os arquivos anteriores e inclua os novos `js/core.js` e `js/finance.js`.
3. Abra a pasta atual no VS Code e execute `index.html` com Live Server.
4. Continue usando o **mesmo navegador, endereço e porta** da versão anterior. `localhost` e `127.0.0.1` são armazenamentos diferentes; trocar a porta também muda o armazenamento.
5. Pressione Ctrl + F5.

Não apague os dados do navegador. O banco continua `AgendaSalaoDB`, versão 1. Agendamentos das Etapas 2 e 3 são lidos normalmente. A atualização preserva seus serviços, preços combinados, clientes e pagamentos. Um agendamento antigo com preço negociado mantém esse preço, mesmo se o cadastro do serviço tiver outro valor.

## Novidades da Etapa 5

### Finalizar o procedimento e dar baixa no pagamento

Abra o atendimento pelo Início, Agenda ou Financeiro e toque em **Concluir atendimento**. Aparece a pergunta **Você recebeu o valor total?**, sem uma resposta pré-selecionada.

1. **Sim, recebi o total:** registra o total como pago, zera o saldo daquele atendimento e marca o procedimento como concluído. Confira a forma de pagamento antes de confirmar.
2. **Não, ainda falta receber:** informe o total já recebido (pode ser zero). O procedimento é concluído, mas o saldo real permanece em aberto.
3. **Ainda preciso conferir:** conclui o procedimento e mantém o pagamento já registrado. Se não havia informação, continua como pagamento a conferir. Essa opção não apaga um recebimento parcial anterior.

Toque em **Confirmar e finalizar** para gravar. **Voltar sem finalizar** não muda nada. Nenhuma escolha grava automaticamente.

A mesma confirmação aparece se você escolher “Concluído” no formulário de um atendimento novo ou ainda não concluído. Se cancelar, o formulário fica preenchido e você pode continuar editando. O atendimento só é gravado ao confirmar a finalização. Para revisar um atendimento antigo já concluído, abra suas opções e clique novamente em concluir.

Quando confirmar pagamento total, **Início, Agenda, Clientes, Financeiro, relatório e próximas mensagens** passam a mostrar o valor recebido e saldo zerado. A baixa é do procedimento escolhido: outros atendimentos do mesmo cliente continuam com seus próprios valores e saldos. O cliente permanece cadastrado e o histórico é preservado.

### Quantidade de clientes e perfil financeiro

Em **Clientes**, os cartões mostram o total de **clientes cadastrados** e a quantidade em cada perfil. Esse total conta cada cadastro uma vez, mesmo que a pessoa tenha vários agendamentos.

- **Bom histórico:** há pelo menos um atendimento concluído; todos os concluídos têm pagamento informado e saldo zerado.
- **Precisa de atenção:** existe saldo conhecido pendente em atendimento concluído. O relatório mostra o valor.
- **Pagamento a conferir:** há atendimento concluído sem informação de pagamento, ou pagamento acima do total que precisa ser conferido.
- **Sem histórico:** ainda não há atendimento concluído registrado.

Se houver saldo pendente e também pagamento desconhecido, o perfil fica em “Precisa de atenção”; os pagamentos desconhecidos continuam detalhados no financeiro. Um atendimento futuro sem pagamento não torna o cliente “ruim”: os perfis usam somente procedimentos concluídos.

Essa classificação é sobre os dados financeiros, não sobre a pessoa. Ela não mede pontualidade, faltas, respeito ou reclamações, pois esses dados não estão registrados no aplicativo.

Use **Filtrar perfil dos clientes**, a busca por nome/telefone e o botão **▤** para abrir o relatório. Nele aparece o perfil e o motivo, sempre calculados pelo histórico completo, independentemente do período escolhido para os valores. Ao acertar um saldo, a classificação muda automaticamente.

**Exportar todos os clientes** baixa um CSV da base inteira, incluindo clientes sem atendimento. O arquivo contém nome, contato, perfil, motivo, procedimentos concluídos, recebimentos em concluídos, saldo pendente e última visita. A exportação inclui todos os cadastros, mesmo se a lista na tela estiver filtrada.

O perfil é uma informação interna do salão: ele não aparece no relatório financeiro em texto/PDF destinado ao cliente, nem nas mensagens de WhatsApp. O CSV de perfis é um relatório interno separado.

### Lista compacta no Início

Hoje, Mês e Geral mostram cada atendimento em uma linha com **nome do cliente, data e horário**. Toque na linha para ver serviços, preços, desconto, pedido, pagamento, saldo e as opções de ação. As informações continuam salvas; somente a apresentação da lista ficou mais compacta.

## 2. Mais de um serviço no agendamento

1. Toque no botão central **+** e escolha o cliente.
2. Em **Adicionar serviço**, escolha o serviço e toque em **+ Adicionar**.
3. Repita para incluir outros serviços. Um mesmo serviço não é adicionado duas vezes.
4. Se necessário, ajuste o **preço combinado** e a **duração** de cada serviço na lista.
5. Use **×** para retirar um serviço.
6. Informe um desconto, se houver. O desconto não pode superar a soma dos serviços.
7. Informe data, horário, pedido do cliente, valor pago e forma do pagamento.
8. Salve.

O total e a duração são calculados automaticamente. Exemplo: Corte R$ 50 / 45 min + Escova R$ 45 / 45 min, desconto R$ 5 → total R$ 90 / 90 min. Se recebeu R$ 20, o saldo é R$ 70. Ao concluir, o app pergunta se recebeu o total, se há saldo pendente ou se precisa conferir. Só registra novo recebimento quando você confirma o valor.

Cada agendamento guarda uma cópia dos nomes, preços e durações escolhidos. Alterar depois o preço no cadastro do serviço não muda o histórico. O app avisa se o horário coincide com outro atendimento, considerando a duração total; você decide se mantém a coincidência.

## 3. Datas verdes na Agenda

Na parte superior há uma faixa horizontal de quadrados com dia da semana, número do dia e quantidade agendada.

- **Verde:** existe pelo menos um atendimento naquela data, inclusive atendimentos já concluídos.
- **Contorno rosa:** data selecionada.
- Toque num quadrado para abrir o dia.
- Deslize a faixa para ver mais datas.
- Use **Ir para hoje**, as setas ou o seletor de data para ir a qualquer data.

A faixa mostra 61 dias ao redor da região selecionada e é reconstruída ao escolher uma data fora dela. Datas distantes continuam acessíveis pelo seletor. Ao criar ou excluir agendamentos, as marcações e quantidades são recalculadas.

## 4. Mensagens prontas, contato e edições salvas

Abra **Agenda → ••• → Mensagem para o cliente**.

Há cinco tipos: resumo do agendamento, lembrete, aviso, agradecimento e resumo de pagamento. O tipo sugerido considera a situação: pendente → aviso; confirmado → lembrete; concluído → agradecimento. Você pode trocar o tipo.

- Um agradecimento antes do atendimento agradece pelo agendamento; após a conclusão, agradece pela visita.
- Um lembrete de um atendimento já concluído identifica que ele foi concluído. Se o horário passou e não foi concluído, orienta a conferir a situação.
- Todas as mensagens detalham os serviços e preços, desconto, pedido, data, horário, duração, situação do atendimento, total, pago e saldo.
- Observações internas não entram nas mensagens.

Edite **WhatsApp deste agendamento** e o texto. Toque em **Salvar mensagem e contato**. Cada tipo tem sua edição salva separadamente para aquele agendamento. Se marcar **Atualizar também o telefone no cadastro do cliente**, o telefone do cliente será atualizado junto, na mesma gravação.

O telefone do cadastro é usado quando não existe contato específico salvo. O campo permite números brasileiros com DDD, com ou sem +55. Você pode salvar uma mensagem sem telefone para copiar o texto; abrir o WhatsApp exige um número válido.

Use **Abrir conversa no WhatsApp** para abrir a mensagem no contato que está no campo, ou **Copiar mensagem** para colar em outro aplicativo. O envio é confirmado por você. Abrir o WhatsApp não comprova envio, entrega ou leitura e não salva automaticamente as edições; use o botão de salvar.

Se data, valores, serviços, nome do cliente ou modelo mudarem após salvar uma edição, o app gera um texto atualizado e mostra um aviso. A edição anterior permanece disponível em **Carregar edição salva anterior**; confira seus valores e datas antes de usar. **Gerar novamente** substitui a prévia pelos dados atuais.

### Personalizar modelos para próximos clientes

Na mesma janela, abra **Personalizar modelo deste tipo**. Edite o modelo usando:

`{cliente}`, `{salao}`, `{servicos}`, `{data}`, `{horario}`, `{total}`, `{pago}`, `{saldo}`, `{pedido}`, `{status}`.

Exemplo: `Olá, {cliente}! Lembramos do seu horário no {salao}, em {data}, às {horario}.`

Clique em **Salvar modelo**. Ele será usado ao gerar novos textos desse tipo. O detalhamento de serviços e pagamentos é acrescentado automaticamente. Para usar o modelo novo na prévia atual, clique em **Gerar novamente**. **Voltar ao modelo pronto** restaura o modelo padrão.

Os textos próprios de corte, escova, manicure e demais serviços continuam disponíveis em **Menu → Serviços → Editar → Mensagem para este serviço**.

## 5. Resumo Hoje, Mês e Geral

O Início tem três períodos:

- **Hoje:** data atual do aparelho.
- **Mês:** todos os atendimentos do mês atual.
- **Geral:** histórico inteiro, incluindo atendimentos futuros.

As quantidades e os valores usam o mesmo período. **A atender** conta atendimentos ainda não concluídos, tanto pendentes de confirmação quanto confirmados. O resumo mostra agendamentos, concluídos, a atender, clientes, quantidade de serviços, total combinado, recebido e saldo conhecido.

Todos os resumos são recalculados após salvar, editar, concluir ou excluir atendimentos, e após mudanças de cadastro. Ao retornar ao app, os dados são relidos. Os valores são agrupados pela **data do atendimento**, e não pela data de entrada do dinheiro.

## 6. Financeiro fácil de conferir

Abra **Menu → Financeiro**.

Filtre por Hoje, Mês, Geral ou período escolhido. Também pode escolher um cliente, uma situação de pagamento e buscar nome ou serviço. **Limpar filtros** abre todo o histórico.

Os cartões explicam quatro valores:

- **Total combinado:** valor de todos os atendimentos do filtro, concluídos ou ainda agendados.
- **Recebido registrado:** soma dos valores pagos que você informou.
- **Ainda falta receber:** saldo dos atendimentos com pagamento conhecido.
- **Serviços concluídos:** valor combinado dos atendimentos concluídos; não significa que todos foram pagos.

Depois dos totais, veja o resumo **por cliente** e a lista detalhada dos atendimentos. Cada atendimento informa todos os serviços, preços, desconto, pedido, data, duração, situação, total, pago, saldo e forma de pagamento.

### Relatório individual

Toque em **Ver relatório completo** no cliente. Também há o botão **▤** ao lado do cliente em **Clientes**.

O relatório abre o **Histórico completo**, independentemente do filtro financeiro atual. Você pode escolher **Filtro financeiro** para mostrar somente os atendimentos que corresponderam aos filtros. Os totais acompanham a escolha. O histórico lista todos os serviços e valores de cada atendimento.

Você pode **Copiar relatório**, **Baixar relatório em texto**, **Imprimir / salvar PDF** (quando o navegador oferecer impressão) ou voltar a um atendimento para editar pagamento, serviço ou mensagem. As observações internas não entram nesses relatórios destinados ao cliente.

### Exportar relatório geral

**Exportar relatório CSV** exporta os atendimentos do filtro atual. Cada linha é um atendimento, com seus serviços detalhados, valores, data, pagamento e situação. Abra no Excel ou outro programa que leia CSV; o separador é `;` e os valores usam vírgula decimal. A exportação não altera o banco.

## 7. Como registrar os pagamentos

Informe o **total já recebido** naquele atendimento:

- Recebeu R$ 20 e depois R$ 30? Atualize para R$ 50.
- Informe **0** quando souber que não houve pagamento.
- Deixe em branco quando o pagamento não foi conferido.
- O valor pago não pode superar o total nem ser negativo.

Registros antigos que não tinham pagamento continuam como **Pagamento não informado**, mesmo se concluídos. Esses valores aparecem separados: não são presumidos como recebidos nem como dívida confirmada. Para conferir, abra **••• → Registrar / editar pagamento**.

Esta versão registra o total recebido e uma forma de pagamento por atendimento. Os relatórios são de atendimentos e recebimentos, agrupados pela data agendada; não são fluxo de caixa por data de cada parcela. Não registra despesas, estornos ou várias formas de pagamento num mesmo atendimento nesta etapa.

## 8. Arquivos completos

- `index.html` — telas e modais
- `css/style.css` — interface mobile preservada e novas áreas
- `js/database.js` — banco local e gravações atômicas de mensagem/contato
- `js/core.js` — regras de serviços, valores e filtros
- `js/messages.js` — textos prontos por situação e contato
- `js/finance.js` — financeiro, relatórios e exportações
- `js/app.js` — cadastros, agenda, edição e atualização das telas
- `README.md` — instruções completas

Sem dependências externas para executar o app. Nenhum APK foi gerado nesta entrega. Ao empacotar em WebView Android, o projeto Android precisará encaminhar links do WhatsApp, downloads e impressão para os recursos nativos adequados.

## 9. Validação realizada

Também verificamos nesta etapa: confirmação de pagamento total, parcial e manutenção do registro atual; cancelamento sem alterar dados; finalização pelo formulário; recálculo de saldos e perfis em todas as abas; contagem de cadastros; filtros e CSV de clientes; lista compacta com detalhes ao tocar; e persistência dos recebimentos ao recarregar.

Verificamos a abertura de um banco da Etapa 3 na Etapa 4; preservação de preços antigos e pagamentos desconhecidos; múltiplos serviços e descontos; soma de duração; edição, conclusão e exclusão com recálculo; datas verdes; mensagem por situação, texto e contato salvos; modelos com campos variáveis; dados persistentes após recarregar; filtros financeiros, relatórios individuais, exportações CSV/texto e layout de impressão; e oito telas nas larguras de 320, 360, 390, 460 e 1280 px, sem rolagem horizontal da página. O link de composição do WhatsApp foi verificado sem enviar mensagens.
