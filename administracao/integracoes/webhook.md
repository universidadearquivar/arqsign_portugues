# 🟪 Webhook

{% hint style="success" %}
<mark style="color:green;">É uma tecnologia que permite a comunicação entre aplicações, enviando dados automaticamente entre elas via HTTP. Os webhooks são ativados por eventos específicos (gatilhos).</mark>

<mark style="color:green;">Os webhooks são úteis para: Automatizar processos, Melhorar o fluxo de trabalho, Economizar recursos e custos do servidor, Integrar com serviços de terceiros e outras APIs externas.</mark>&#x20;

<mark style="color:green;">Os webhooks são semelhantes as APIs, que permitem a comunicação entre aplicativos, mas funcionam de forma diferente. Uma API é um conjunto de protocolos e rotinas para construir e interagir com aplicativos de software, enquanto um webhook é uma forma de um aplicativo notificar outro quando ocorre um evento específico.</mark>&#x20;
{% endhint %}

Este menu permite ao cliente configurar Webhooks para acompanhar o andamento dos seus processos de assinaturas de documentos.

<figure><img src="../../.gitbook/assets/image (295).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Conforme a configuração de Webhook realizada, o cliente recebe os dados de execução dos processos de assinatura por meio dos eventos/gatilhos.

{% hint style="info" %}
<mark style="color:blue;">Este menu é exibido aos usuários com perfil de</mark> <mark style="color:blue;"></mark><mark style="color:blue;">**Administrador Global**</mark> <mark style="color:blue;"></mark><mark style="color:blue;">com devida</mark> <mark style="color:blue;"></mark><mark style="color:blue;">**permissão definida**</mark> <mark style="color:blue;"></mark><mark style="color:blue;">na plataforma e com</mark> <mark style="color:blue;"></mark><mark style="color:blue;">**plano de assinatura vigente**</mark> <mark style="color:blue;"></mark><mark style="color:blue;">ou seja com</mark> <mark style="color:blue;"></mark><mark style="color:blue;">**conta de status Ativo**</mark><mark style="color:blue;">.</mark>
{% endhint %}

Clicando em Webhook, é apresentado o GRID com as configurações de Webhook da conta do usuário logado, ordenados alfabeticamente pela coluna "Nome".

<figure><img src="../../.gitbook/assets/image (297).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

**Adicionar:** Utilize para incluir uma nova configuração. Ao clicar no ícone "Adicionar", a aplicação verifica o status da conta e a quantidade de configurações que a conta possui.&#x20;

{% hint style="warning" %}
<mark style="color:orange;">Somente</mark> <mark style="color:orange;"></mark><mark style="color:orange;">**conta com status Ativo**</mark> <mark style="color:orange;"></mark><mark style="color:orange;">pode adicionar configuração de Webhook,</mark> <mark style="color:orange;"></mark><mark style="color:orange;">**limitados a 25 configurações**</mark><mark style="color:orange;">.</mark>

<mark style="color:orange;">Se Conta Ativa e</mark> <mark style="color:orange;"></mark><mark style="color:orange;">**possui 25 configurações de webhook**</mark><mark style="color:orange;">, a aplicação exibe a mensagem:</mark> <mark style="color:orange;"></mark><mark style="color:orange;">**"A conta atingiu o limite máximo de X configurações de webhook."**</mark>

<mark style="color:orange;">Se</mark> <mark style="color:orange;"></mark><mark style="color:orange;">**Conta bloqueada,**</mark> <mark style="color:orange;"></mark><mark style="color:orange;">a aplicação exibe a mensagem:</mark> <mark style="color:orange;"></mark><mark style="color:orange;">**"A conta está bloqueada. Somente conta com status Ativo pode adicionar configuração de webhook."**</mark> <mark style="color:orange;"></mark><mark style="color:orange;">.</mark>
{% endhint %}

**Excluir:** Utilize para excluir uma configuração. O ícone de exclui é habilitado somente após selecionar uma ou mais configurações de webhook com **status inativo** e que **não esteja em edição por outro usuário**.

{% hint style="warning" %}
<mark style="color:orange;">Não é permitido excluir configuração, inativo, de webhook que estejam em edição por outro usuário.</mark>
{% endhint %}

**Filtrar:** Utilize para filtrar configurações específicas. O sistema permite ao usuário filtrar por dados contidos no resultado da consulta do GRID e não somente na página, em questão.

* Nome: permite filtrar pelo nome do webhook.
* Status: permite filtrar pelo status do webhook. O sistema lista as opções "**Ativo**", "**Inativo**" e "**Inativo por falhas**".

<figure><img src="../../.gitbook/assets/image (299).png" alt=""><figcaption></figcaption></figure>

**Coluna Id:** Exibe o Id do Webhook no sistema.

**Coluna Nome:** Exibe o nome do Webhook no sistema. Quando o webhook estiver em edição, o sistema sinaliza com a informação <mark style="color:red;">**"Em edição com: \[Nome do usuário que está editando o webhook]".**</mark>

**Coluna Status:** Exibe o status do webhook: **Ativo**, **Inativo** ou **Inativo por falhas.**

Quando o status for "**Ativo**", ele pode ter as seguintes flags:

* **Gatilho Inativo:** Quando pelo menos um gatilho da configuração está inativo por falhas recorrentes.
* **Falha em Gatilho:** Quando não existem gatilhos inativos na configuração, mas pelo menos um gatilho tem a quantidade de falhas maior do que zero.

**Coluna Ações:** Este botão é exibido:

* Desabilitado para configurações de webhook com flag "Em edição" com outro usuário.
* Habilitado para\* configurações de webhook sem flag "Em edição" com o usuário logado.

Quando habilitado, o sistema lista as ações, conforme status do webhook: Ativar, Editar, Excluir , Inativar.

* **Ativar:** somente para configuração de webhook com status Inativo.
* **Editar:** listada para todos os webhooks.
* **Excluir:** somente para configuração de webhook com status Inativo.
* **Inativar:** somente para configuração de webhook com status Ativo.

***

## Configurações de Webhook

Ao clicar em Adicionar "+", é apresentada a tela para configuração de webhook.

<figure><img src="../../.gitbook/assets/image (300).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

### Dados Gerais

Os dados gerais do webhook devem ser informados nesta área:

<figure><img src="../../.gitbook/assets/image (301).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

**Status:** São exibidas na lista as opções "Ativo" e "Inativo", sendo exibida por padrão o preenchimento da opção "Ativo".

{% hint style="info" %}
<mark style="color:blue;">Na visualização/edição de um webhook já criado, caso seu status seja "Inativo por falhas", ele irá abrir na tela de configurações com o status "Inativo".</mark>
{% endhint %}

&#x20;**Nome:** Informe o nome do webhook. Trata-se de um campo de preenchimento obrigatório. O sistema não permite webhooks com mesmo nome na mesma conta.

**URL para publicar:** Informe a URL que será chamada para receber os dados do processo de assinatura dos documentos. Trata-se de um campo de preenchimento obrigatório.

**Aguardar retorno:** Defina se o webhook deve aguardar um retorno. Trata-se de um campo de preenchimento opcional.

{% hint style="info" %}
<mark style="color:blue;">A marcação desse campo fará com que o webhook aguarde uma confirmação do seu listener (URL para publicar) após enviar uma mensagem. O webhook registra uma transferência de mensagens bem-sucedida quando o listener retorna um código de status HTTP 200. Se esta opção não é marcada e o webhook não receber um código de status HTTP 200, a aplicação não considerará isso como falha.</mark>
{% endhint %}

### Executar o webhook quando

Nesta área devem ser definidos os pré-requisitos para a execução do webhook.

<figure><img src="../../.gitbook/assets/image (302).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

#### **Adicionar Grupos e Usuários**&#x20;

Esta opção é utilizada para configurar um ou mais grupos e/ou usuários como parâmetro de execução do webhook. Ou seja, o webhook somente será executado se o remetente do processo for um usuário selecionado ou  se fizer parte de um grupo configurado neste campo. Trata-se de um campo de preenchimento opcional.&#x20;

{% hint style="danger" %}
<mark style="color:red;">Caso um dos grupos listados tiver sido excluído posteriormente, ele será apresentado em vermelho.</mark>

<mark style="color:red;">Caso um dos usuários listados tiver sido inativado, bloqueado ou deixado de ser administrador global posteriormente, ele será apresentado em vermelho.</mark>
{% endhint %}

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Do lado direito da tela são apresentados os "Grupos" e os "Usuários" disponíveis para seleção. Do lado esquerdo da tela são apresentados os "Grupos" e os "Usuários" já selecionados.

<figure><img src="../../.gitbook/assets/image (305).png" alt=""><figcaption></figcaption></figure>

Utilize os botões disponíveis, clique sobre o nome do grupo ou nome do usuário que deseja mover e depois clique nos botões para "Adicionar", para envio de um por vez ou "Adicionar todos" para envio da lista completa. O mesmo deve ser feito para "Remover" itens da lista.

Concluída a seleção dos usuários e grupos, clique "Selecionar" para retornar a tela anterior.

<figure><img src="../../.gitbook/assets/image (307).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

{% hint style="success" %}
<mark style="color:green;">As definições realizadas serão apresentadas no campo "</mark><mark style="color:green;">**O processo tenha sido enviado por algum usuário do grupo ou usuário selecionado neste campo**</mark><mark style="color:green;">", que é verificado para "</mark><mark style="color:green;">**Execução do webhook**</mark><mark style="color:green;">".</mark>
{% endhint %}

#### Adicionar pastas

Esta opção é utilizada para configurar uma ou mais pastas como parâmetro de execução do webhook. Ou seja, o webhook somente será executado caso o processo tenha sido criado em alguma pasta contida neste campo. Neste campo serão exibidas as pastas selecionadas na modal "Pastas". Trata-se de um campo de preenchimento opcional.

<figure><img src="../../.gitbook/assets/image (308).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Selecione na árvore apresentada a pasta que deseja limitar a execução do webhook. No campo "Pastas selecionadas" serão listadas todas as pastas marcadas. Clique "Selecionar" para concluir a configuração.

{% hint style="danger" %}
<mark style="color:red;">Caso uma das pastas listadas tenha sido excluída posteriormente, ela será apresentada em vermelho.</mark>
{% endhint %}

<figure><img src="../../.gitbook/assets/image (309).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Leia com atenção a mensagem de validação do processo e clique para prosseguir.

<figure><img src="../../.gitbook/assets/image (310).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

{% hint style="success" %}
<mark style="color:green;">As definições realizadas serão apresentadas no campo "</mark><mark style="color:green;">**O processo tenha sido criado em uma das pastas selecionadas neste campo**</mark><mark style="color:green;">", que é verificado para "</mark><mark style="color:green;">**Execução do webhook**</mark><mark style="color:green;">".</mark>
{% endhint %}

### Gatilhos

Nesta área, é necessário definir um ou mais gatilhos de execução do webhook. Ou seja, aqui são definidos os momentos em que o webhook será executado, chamando a URL com os dados no JSON, conforme configuração de retorno.

<figure><img src="../../.gitbook/assets/image (314).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

É obrigatória a seleção de ao menos um gatilho para execução do webhook, são apresentadas as seguintes opções:&#x20;

1. &#x20;Processo enviado&#x20;
2. Processo com falha de envio
3. Processo assinado por algum signatário&#x20;
4. Processo recusado por algum signatário
5. Processo cancelado pelo remetente
6. Processo expirado
7. Processo reenviado
8. Processo assinado/concluído por todos os signatários&#x20;

### Retorno

Nesta área, são definidos os dados que serão retornados no JSON, além dos dados gerais.

<figure><img src="../../.gitbook/assets/image (313).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Os possíveis dados são:

* **Processo:** Parte do JSON com os dados do processo;
* **Signatários:** Parte do JSON com os dados dos signatários;
* **Documentos:** Parte do JSON com os dados dos documentos do processo.&#x20;

{% hint style="danger" %}
<mark style="color:red;">Os dados gerais fazem parte do início do JSON e esta parte será enviada sempre, mesmo se não houver nenhum dado marcado de retorno para o JSON.</mark>
{% endhint %}

### Json

Nesta área, o sistema exibe o exemplo de retorno do JSON.

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

O dados de retornos configurados, são representados no campo JSON a medida que os campos são marcados.

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

* Ao marcar o campo "**Dados do processo**”,  o sistema exibe o exemplo dos dados do processo no campo "JSON".
* Ao marcar o campo "**Signatários**", o sistema exibe o exemplo dos dados dos signatários no campo "JSON".
* Ao marcar o campo "**Documentos**", o sistema marca checkbox "Arquivos do processo", "Link dos documentos compartilhados" e "Registro de assinatura".

"**Arquivos do processo**" e “**Registros de assinatura**"  podem ser retornados no formato Link para Download ou Base64. É necessário marcar uma opção de formado para os arquivos do processo e/ou registros de assinaturas

O "**Link dos documentos compartilhados**"  é o link  de compartilhamento dos documentos do processo. Estes links são disponibilizados somente na conclusão de processos que possui a configuração "**GerarQRCode**". Concluídas as configurações, clique "Salvar". Serão habilitadas novas abas para andamento das configurações.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

***

## HMAC

Toda configuração realizada na plataforma terá uma chave HMAC gerada. Para visualizar, clique na aba HMAC.

**HMAC** é uma forma de verificar a autenticidade e integridade das informações que estão sendo transmitidas por meio de uma chave secreta compartilhada entre as partes.

A cada webhook gerado na ArqSIGN, a aplicação irá gerar o “**Chave secreta HMAC**”. Esta chave será de conhecimento somente da ArqSIGN e da aplicação do cliente.

A “**Chave secreta HMAC**” e o body da requisição devem ser usados para o cálculo do SHA256 HMAC hash. Este hash será enviado no cabeçalho da requisição como “**HMAC**”.

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>



Utilizando os ícones disponíveis na tela, o usuário poderá:

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

**Visualizar:** Ao clicar no ícone, a chave HMAC é apresentada na tela.

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

**Copiar:** Após clicar no ícone de visualização, é habilitada a opção de "Copiar" a chave HMAC.

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

**Regerar Chave:** Ao clicar nesta opção, uma nova chave HMAC é gerada pelo sistema.&#x20;

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Valide a ação na tela para prosseguir.

***

## Gatilho

Nesta são listados os gatilhos configurados para o webhook, em questão, ordenados conforme evento de execução.

Uma configuração de webhook pode ater até 8 gatilhos:

1. Processo enviado
2. Processo com falha de envio
3. Processo assinado por algum signatário
4. Processo recusado por algum signatário
5. Processo cancelado pelo remetente
6. Processo expirado
7. Processo reenviado
8. Processo assinado/concluído por todos os signatários&#x20;

<figure><img src="../../.gitbook/assets/image (315).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

**Gatilhos do Webhook:** Traz o nome informado na tela de configuração para o processo.

**Coluna Gatilho:** Lista os gatilhos selecionados na tela de configuração.

**Coluna Quantidade de Falhas:** O sistema exibe a quantidade de falhas registradas para cada gatilho, quando houver.

**Coluna Status:** Mostra o status de cada gatilho.&#x20;

Para gatilhos com status "**inativo por falhas recorrentes"** e que não esteja em edição por outro usuário, o sistema exibe o botão "**Ativar**" habilitado, possibilitando ao usuário ativar o gatilho novamente.

Ao reativar o gatilho que está inativo por falhar recorrentes, o sistema zera a contagem de falhas.

**Coluna Ações:** Permite nova ativação de um gatilho inativado por falhas recorrentes, desde que não haja nenhum outro usuário realizando a edição do gatilho em questão.

### Execução

A cada evento na aplicação, conforme os gatilhos listados abaixo, o sistema executa o webhook, enviando atualizações (mensagens de evento) para a URL configurada em tempo real, ou seja, no ato da ocorrência do evento configurado.

1. **Processo enviado:** Ao enviar um processo pela aplicação ArqSign ou API, o sistema executa o webhook com este gatilho, enviando os dados, conforme a configuração de retorno, para a URL configurada.
2. **Processo com falha de envio:** Quando houver falha de envio do processo para algum destinatário e/ou falha de envio do código de segurança para algum destinatário.

{% hint style="danger" %}
<mark style="color:red;">O Retorno do JSON quando marcado para retornar os dados “Signatários” para este gatilho em específico, retornará somente os dados do signatário que teve a falha de envio do processo e/ou código de segurança.</mark>
{% endhint %}

3. **Processo assinado por algum signatário:** Assim que o processo é assinado por cada signatário. Desta forma, se o processo possuir 3 signatários, a cada assinatura concluída o webhook com esta configuração irá chamar a URL definida e ao final do processo de assinatura a URL terá sido chamada 3x.

{% hint style="danger" %}
<mark style="color:red;">O Retorno do JSON quando marcado para retornar os dados “Signatários” para este gatilho em específico, retornará somente os dados do signatário que assinou os documentos.</mark>
{% endhint %}

4. **Processo recusado por algum signatário:** Assim que algum signatário se recusar a assinar algum documento.
5. **Processo cancelado pelo remetente:** Assim que o remetente do processo cancelar o seu envio.
6. **Processo expirado:** Assim que o processo expirar, ou seja, ele vencer antes da conclusão total das assinaturas.
7. **Processo reenviado:** Assim que o processo for reenviado aos signatários pendentes de assinatura. O processo pode ser reenviado quando:

* O link de assinatura expira e se deseja atualizar o link para os signatários pendentes;
* Se deseja alterar algum signatário pendente de assinatura totalmente ou apenas a forma de envio para ele;
* Se deseja reenviar o link para algum signatário mesmo que este não esteja vencido.

8. **Processo assinado/concluído por todos os signatários:** Assim que o processo é totalmente assinado por todos os signatários.

### Falhas na Execução

Quando o envio dos dados não é bem-sucedido, a informação de falha é registrada no sistema para uma posterior tentativa de envio de forma manual ou automatizada. A aplicação considera uma entrega bem-sucedida ou não conforme alguns parâmetros:

#### **A. Webhook configurado COM a opção “Aguardar Retorno”:**

Com esta configuração, o webhook aguarda, por um período de 100 segundos, uma confirmação do seu listener (URL a publicar) após o envio da mensagem.

A confirmação esperada é um código de status <mark style="color:green;">**HTTP 200 - OK**</mark>.

1. Se o listener não responder no **tempo esperado**, **o sistema registra como falha (tratada)**. Ou seja, a **falta de retorno é considerada uma falha que é tratada.**
2. Se o listener **retornar um código diferente de HTTP 200**, o webhook **considera que houve falha na entrega.**

As transmissões com falhas na entrega são elegíveis para novas tentativas manuais ou automatizadas, exceto as falhas com os códigos abaixo:

* 401 – Não autorizado. Existem problemas nas credenciais para acessar o HTTP.
* 403 – Sem permissão de acesso ao servidor. O servidor atendeu à solicitação, mas se recusa a fazê-la.
* 404 – URL não existe.

#### B. Webhook é configurado SEM a opção “Aguardar Retorno”:

Sem esta configuração, o webhook deve aguardar, por um <mark style="color:red;">**período de 100 segundos**</mark>, uma confirmação do seu listener após o envio da mensagem.

A confirmação aguardada é um código de status <mark style="color:green;">**HTTP 200 – OK**</mark>.

1. Se o listener não responder **no tempo esperado**, **o sistema não registra como falha. Ou seja, a falta de retorno não é considerada uma falha.**
2. Se o listener **retornar um código diferente de HTTP 200**, o webhook **considera que houve falha na entrega.**

As transmissões com falhas na entrega são elegíveis para novas tentativas manuais ou automatizadas, exceto as falhas com os códigos abaixo:

* 401 – Não autorizado. Existem problemas nas credenciais para acessar o HTTP.
* 403 – Sem permissão de acesso ao servidor. O servidor atendeu a solicitação, mas se recusa a fazê-la.
* 404 – URL não existe.

### Retransmissão em caso de falhas

As falhas de comunicação elegíveis para retransmissão poderão ocorrer de forma manual, via solicitação do usuário na aplicação ou de forma automática conforme a periodicidade abaixo:

* 1ª Tentativa: no ato do evento
* 2ª Tentativa: 05 minutos após a primeira tentativa
* 3ª Tentativa: 15 minutos após a primeira tentativa
* 4ª Tentativa: 30 minutos após a primeira tentativa
* 5ª Tentativa: 01 hora após a primeira tentativa
* 6ª Tentativa: 02 horas após a primeira tentativa
* 7ª Tentativa: 04 horas após a primeira tentativa
* 8ª Tentativa: 08 horas após a primeira tentativa
* 9ª Tentativa: 16 horas após a primeira tentativa
* 10ª Tentativa: 1º dia após a primeira tentativa
* 11ª Tentativa: 2º dia após a primeira tentativa
* 12ª Tentativa: 3º dia após a primeira tentativa
* 13ª Tentativa: 4º dia após a primeira tentativa
* 14ª Tentativa: 5º dia após a primeira tentativa, se neste dia o webhook ainda apresentar falha, então ele será inativado **(Inativo por falhas recorrentes)**.

{% hint style="info" %}
<mark style="color:blue;">Cada evento configurado no webhook que houver falha, terá no máximo 14 tentativas, contando com a primeira tentativa que ocorre no ato do evento.</mark>
{% endhint %}

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

### Inativação automática do webhook por falhas

Sempre que o webhook receber do listener (URL do cliente) os códigos de erros abaixo, este webhook será inativado imediatamente para evitar chamadas desnecessárias, recebendo o status “**Inativo por falhas**”.

Os códigos de erros são:

* 401 – Não autorizado. Existem problemas nas credenciais para acessar o HTTP.
* 403 – Sem permissão de acesso ao servidor. O servidor atendeu à solicitação, mas se recusa a fazê-la.
* 404 – URL não existe.

&#x20;Sempre que o webhook outros erros, <mark style="color:red;">**após 5º dia**</mark> de erros consecutivos, o gatilho com estas falhas será inativado, recebendo o status “**Inativo por falhas recorrentes**”.

Os webhooks inativados pela aplicação por falhas, receberão os status “**Inativo por falhas**” e deixarão de enviar mensagens ao listener (URL do cliente), mas poderão ser editados e ativados novamente.

***

## Logs de falha

Nesta aba é possível acompanhar os logs de falha do webhook.&#x20;

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Nesta tela também é possível reenviar os dados manualmente clicando no botão "Reenviar". Este botão ficará habilitado apenas se o registro não tiver atingido a 14ª tentativa.

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Se o Webhook estiver inativo ou estiver em edição por outro usuário, todos os registros do GRID terão o botão "Reenviar" desabilitado.

Ao acionar o botão \[Reenviar] o sistema executa a tentativa de envio da mensagem.

Em todos os casos, se um reenvio tiver sucesso, o registro é removido do GRID e a quantidade de tentativas do gatilho deve ser zerada.

Na coluna "Falha", é apresenta a mensagem da falha ocorrido. Ao clicar no ícone uma nova janela é aberta.

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Na nova janela, além da mensagem de detalhamento da falha, são apresentados outros dados do processo.&#x20;
