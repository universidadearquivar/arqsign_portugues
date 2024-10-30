# ✉️ Caixa de Entrada

Na Caixa de Entrada são listados todos os documentos nos quais o usuário participa do processo de assinatura como signatário, ou seja, como assinante por meio da Plataforma ArqSign.

O signatário de um processo de assinatura pode ser também o remetente do documento e neste caso o documento será exibido tanto na Caixa de Entrada quanto no [menu Enviados](enviados.md).

{% hint style="warning" %}
<mark style="color:orange;">**Não serão exibidos na Caixa de Entrada documentos que já tenham expirado, ou seja, cujo prazo para assinatura já tenha terminado.**</mark>
{% endhint %}

<figure><img src="../.gitbook/assets/caixa_entrada01.png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Ao clicar em um documento, será aberta a tela de visualização do documento, que apresenta o documento enviado, seus status e data de vencimento. No canto direito da tela são apresentadas informações dos signatários como dados pessoais, papel de signatário e status da assinatura.

<figure><img src="../.gitbook/assets/alteracao2.png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

***

## Colunas da tela principal - Caixa de Entrada

<figure><img src="../.gitbook/assets/caixa_entrada02.png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

**Coluna Nome do Documento:** Nesta coluna são exibidos o nome do documento e o nome do signatário. Se houver mais de um signatário será mostrado o nome do primeiro e a quantidade de outras pessoas que deverão assinar.&#x20;

**Coluna Responsável:** Nesta coluna são apresentados o nome e e-mail de quem enviou o documento (remetente).

**Coluna Status:** Os status possíveis para um documento são: “Aguardando” (nenhum participante assinou o documento até o momento), “Em processo” (um ou mais participantes já assinaram o documento, mas ainda faltam assinaturas) e “Concluído” (todos os participantes já assinaram o documento). Ao passar o mouse sobre o status são exibidas informações sobre quais signatários ainda estão com assinatura pendente e quais já concluíram, além dos dados desses signatários.

<figure><img src="../.gitbook/assets/caixa_entrada03.png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

**Coluna Tamanho:** Nesta coluna é exibido o tamanho do arquivo do documento.&#x20;

**Coluna Pasta:** Nesta coluna é exibida a pasta do diretório onde o documento está armazenado. Caso o usuário não tenha permissão de acesso à pasta, será exibido “Sem pasta”.

**Coluna Enviado:** Informações sobre a data e hora em que o documento foi enviado.

**Coluna Concluído:** Informações sobre a data e hora em que o processo de assinatura do documento foi concluído. Caso ainda não tenha sido concluído esta coluna ficará em branco.

**Coluna Ações:** Esta coluna exibe botões de ação sobre o documento. Esses botões serão exibidos de acordo com o perfil do usuário. Será sempre exibida nesse botão a ação prioritária de execução, de acordo com o perfil do usuário e status do documento.

**Barra de filtro:** É possível localizar um ou mais documentos utilizando-se os filtros disponíveis para busca. A busca pode ser feita pelo nome ou e-mail do responsável pelo envio, pelo nome de um dos signatários, pelo status do documento (na Caixa de Entrada só serão exibidos os documentos com status “Concluído”, Aguardando” e “Em processo”), pela pasta onde o documento está armazenado ou pela data de conclusão das assinaturas.

<figure><img src="../.gitbook/assets/caixa_entrada04.png" alt=""><figcaption></figcaption></figure>

***

## Ações individuais - Caixa de Entrada

<figure><img src="../.gitbook/assets/image (221).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

#### **Assinar**

Disponível somente se o documento ainda não tiver sido assinado pelo signatário e seja a sua vez de assinar de acordo com a ordem estabelecida pelo remetente, se houver. Ao clicar neste botão o usuário é direcionado para a [tela de assinatura do documento](../menu-superior/assinatura-de-documentos.md).

#### **Histórico**

&#x20;Aqui é possível visualizar o histórico do processo de assinatura e seus documentos. Selecione o botão de eventos para visualizar detalhadamente os dados. Nesta tela também é possível baixar os arquivos originais do processo.

Com o botão de eventos posicionado para a direita, observamos os dados do processo na tela.

<figure><img src="../.gitbook/assets/image (86).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Com o botão de eventos posicionado para a esquerda, é possível visualizar os Id's e Hash's dos documentos, no caso de um **processo com mais de um documento não agrupados**.

<figure><img src="../.gitbook/assets/image (87).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

#### **Alterar Pasta**

Esta opção só será exibida se o usuário tiver acesso à conta na qual o documento está armazenado. Ao clicar nesta opção ele poderá alterar a pasta do diretório onde o documento está armazenado.

<figure><img src="../.gitbook/assets/caixa_entrada05.png" alt=""><figcaption></figcaption></figure>

#### **Alterar Proprietário**

&#x20;Esta opção só será exibida se o usuário além de signatário for também o remetente do documento. Ao clicar nesta opção ele poderá alterar o proprietário do documento. Ao executar essa ação não será possível realizar outras atividades de gestão do documento.

{% hint style="warning" %}
&#x20;<mark style="color:orange;">**Só podem ser selecionados como novo proprietários usuários cadastrados na mesma conta do responsável.**</mark>&#x20;

<mark style="color:orange;">**O Administrador Global que não for o remetente do documento, poderá alterar a propriedade de documentos concluídos que estão listados na funcionalidade**</mark> [<mark style="color:orange;">**Diretórios**</mark>](broken-reference) <mark style="color:orange;">**ou quando for inativar usuário que possui documentos em sua propriedade.**</mark>
{% endhint %}

<figure><img src="../.gitbook/assets/caixa_entrada10.png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

#### **Baixar Arquivo**

Quando processo possuir um documento ou é um compartilhamento de apenas um documento do processo, **o sistema faz **_**download**_ do documento do **processo e do registro de assinaturas** em uma pasta.zip.

A pasta zip é nomeada com o nome do processo e o arquivo de registro de assinatura é nomeado como **NomeDocumento\_Registro** de assinatura.

<figure><img src="../.gitbook/assets/image (222).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Quando o processo **possuir mais de um documento**, o sistema exibe modal com os documentos do processo para o usuário selecionar quais documentos deseja baixar. Caso seja um compartilhamento, deve-se listar apenas os documentos que foram compartilhados.

<figure><img src="../.gitbook/assets/image (223).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

O Registro de Assinaturas exibe todas as informações sobre as assinaturas eletrônicas e digitais realizadas durante o processo, como nome dos signatários, data e hora da assinatura, localização, IP de onde foi realizada, dados dos certificados digitais utilizados etc.

<figure><img src="../.gitbook/assets/image (225).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (226).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

#### **Cancelar**

&#x20;Esta opção só será exibida se o usuário além de signatário for também o remetente do documento. Ao clicar nesta opção o documento é cancelado e o processo de assinaturas é interrompido. Essa opção não será exibida se o status do documento for “Concluído”.

#### **Compartilhar**

&#x20;Essa opção permite que o usuário crie um link de acesso a um ou mais documento do processo que poderá ser compartilhado com outras pessoas que não sejam participantes do processo de assinatura. Esse link pode ter prazo de validade determinado ou indeterminado e o usuário pode definir se deseja permitir que as pessoas que acessarem visualizem também os anexos enviados pelos signatários.

Quando o processo com mais de um documento não agrupados não possui compartilhamento de documentos, o sistema abre a _modal_ para o usuário selecionar os documentos do processo que deseja compartilhar.&#x20;

<figure><img src="../.gitbook/assets/image (73).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Quando o processo com mais de um documento possui compartilhamento de documentos, o sistema abre a modal com os links já compartilhados.

<figure><img src="../.gitbook/assets/image (74).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Ao expandir as ações do link de compartilhamento, é possível **visualizar** a tela de compartilhamento novamente ou e **excluir** o compartilhamento realizado.&#x20;

<figure><img src="../.gitbook/assets/image (230).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Ao compartilhar os documentos do processo, o usuário tem a possibilidade de enviá-los por e-mail clicando no botão "Enviar Link por e-mail".

<figure><img src="../.gitbook/assets/image (231).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Adicione no campo indicado todos os e-mails que devem receber a documentação compartilhada.&#x20;

<figure><img src="../.gitbook/assets/image (232).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

{% hint style="danger" %}
<mark style="color:red;">Ao compartilhar documentos de um processo, é importante ressaltar que o destinatário do compartilhamento poderá visualizar apenas os documentos selecionados para compartilhamento e não todos os documentos que compõem o processo de assinatura.</mark>
{% endhint %}

#### Visualização de documentos compartilhados

Quando realizado o compartilhamento de apenas um documento de um processo com mais de um documento não agrupado, ao abrir o documento, será apresentado somente o documento compartilhado com o usuário.

Observe que são apresentados na lista apenas os dados dos signatários:

<figure><img src="../.gitbook/assets/image (233).png" alt=""><figcaption><p>CLique na imagem para ampliar.</p></figcaption></figure>

Quando realizado o compartilhamento de mais documentos do processo, é apresentado na lista, além dos dados dos signatários, os demais documentos do processo:

<figure><img src="../.gitbook/assets/image (234).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

#### **Alterar Agendamento da Renovação**

&#x20;Esta opção só será exibida se o usuário além de signatário for também o remetente do documento. Utilizada para alterar ou incluir um prazo de renovação do documento estipulado anteriormente no menu [Novo Documento > Adicionar Documentos](../menu-superior/novo-documento.md#a.-adicionar-documentos).

<figure><img src="../.gitbook/assets/caixa_entrada14.png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

#### **Recusar Assinatura**

Disponível somente se o documento ainda não tiver sido assinado pelo signatário e seja a sua vez de assinar de acordo com a ordem estabelecida pelo remetente, se houver. Utilizado quando por algum motivo o signatário não deseja assinar o documento. Neste caso ele deve inserir uma justificativa para a recusa e clicar em “Recusar Assinatura”.

<figure><img src="../.gitbook/assets/caixa_entrada17.png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

#### **Reenviar**

Esta opção só será exibida se o usuário além de signatário for também o remetente do documento e se o documento estiver vencido, ou seja, o prazo de assinatura terminou antes que todos os signatários tenham assinado. Ao clicar neste botão serão exibidas as informações de ordem de envio para os destinatários, e-mail ou telefone para onde o documento foi enviado, código de segurança para acesso ao documento (se houver) e ícone “Editar”, que permite a edição das informações do destinatário.

<figure><img src="../.gitbook/assets/caixa_entrada18.png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

#### **Renomear**

&#x20;Esta opção só será exibida se o usuário além de signatário for também o remetente do documento.&#x20;

Quando o processo possui apenas um documento, o sistema permite alterar o nome do processo:

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Quando processo possui mais de um documento, o sistema permite alterar o nome do processo e o nome dos documentos do processo.

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

O campo “**Renomear documentos do processo**” é exibido, somente se o usuário logado for o remetente do processo e o processo possuir mais de um documento/arquivo.

Por padrão, este campo é exibido desmarcado e ao ser marcado, o sistema lista todos os documentos do processo habilitados para edição.

O usuário tem a possibilidade de mover os documentos, alterando a ordenação deles. Ao mover os documentos, o sistema atualiza a numeração na frente de cada documento.

**Excluir:** Utilizado para excluir o arquivo, que irá para a caixa [Excluídos](excluidos.md) .

<figure><img src="../.gitbook/assets/caixa_entrada15.png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

***

## Ações em lote - Caixa de Entrada

É possível selecionar mais de um documento marcando-se os checkbox ao lado do nome do arquivo e executar ações em lote. As ações em lote só poderão ser executadas em documentos em que o usuário for além de signatário o remetente do documento.

<figure><img src="../.gitbook/assets/caixa_entrada19.png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

#### **Mover  Processo (s)**

Ao clicar neste ícone será possível alterar a pasta onde os documentos selecionados estão armazenados. Só será possível executar essa ação em documentos em que o usuário for além de signatário o remetente do documento.   &#x20;

<figure><img src="../.gitbook/assets/caixa_entrada05.png" alt=""><figcaption></figcaption></figure>

#### **Reenviar**

Ao clicar neste ícone será possível reenviar os documentos selecionados para os destinatários que ainda não assinaram. Só será possível executar essa ação em documentos em que o usuário for além de signatário o remetente do documento e que não estejam com o status “Concluído”.

<figure><img src="../.gitbook/assets/caixa_entrada06.png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

#### **Cancelar Envio**

Ao clicar neste ícone será possível cancelar o envio dos documentos selecionados, interrompendo os processos de assinatura. Só será possível executar essa ação em documentos em que o usuário for além de signatário o remetente do documento e que não estejam com o status “Concluído”.

<figure><img src="../.gitbook/assets/caixa_entrada07.png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

#### **Excluir**

Ao clicar neste ícone será possível excluir os documentos selecionados. Só será possível executar essa ação em documentos em que o usuário for além de signatário o remetente do documento e que estejam com o status “Concluído”.

<figure><img src="../.gitbook/assets/caixa_entrada08.png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>
