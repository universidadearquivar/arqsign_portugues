# ✔️ PATCH/api/v2/processo/{idProcesso}/reenviar-processo

Este serviço permite aos Clientes, via API, **reenviar o processo** para os **destinatários pendentes de assinatura** na ordem de assinatura atual, permitindo **editar dados os destinatários** pendentes de assinatura.

## Requisição - Orientações

Quando campo requerido estiver como “Sim” = Sempre requerido

Quando campo requerido estiver como “Não” = Informação Opcional

Quando campo requerido estiver como “Talvez” = Em alguns casos ele será requerido. Para saber estes casos, consultar a descrição do tópico, conforme o número de referência da linha na tabela.

<div align="left">

<figure><img src="../../../../.gitbook/assets/image (266).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

</div>

## Exemplo Body Request

**Exemplo Body - Sem edição**

```
[]

```

**Exemplo Body - Com edição**

```
[
    {
        "idProcessoDestinatario": "Guid",
        "idFormaEnvioProcesso": "bit",
        "nome": "string",
        "email": "string",
        "telefone": "string",
        "idMeioEnvioCodigoSeguranca": "bit",
        "emailSeguranca": "string",
        "telefoneSeguranca": "string",
        "permitirReenviarCodigo": "bit",
        "dadosAssinatura": {
            "signatario": {
                "nome": "string",
                "numeroDocumento": "string",
                "validar": "bit"
                "DescartarDadosAnteriores": "bit"
            },
            "empresa": {
                "nome": "string",
                "numeroDocumento": "string",
                "validar": "bit"
                "DescartarDadosAnteriores": "bit"
            }
        }
    }
]

```

## Validações

### Validações Gerais - Autenticação

Para autenticar na API da ArqSign deve-se informar a AppKey da conta que está reenviando o processo. Esta conta deve estar ativa e com a devida permissão para o uso da integração Arqsign.

### Validações Gerais - Descrição dos parâmetros JSON

**01. idProcessoDestinatario**

**Descrição:** Parâmetro informando o Id do destinatário que será reenviado o processo.

**Formato:** Guid

**Requerido:** <mark style="color:red;">Sim, quando houver dados para edição.</mark>

&#x20;**Validação:** O reenvio do processo é permitido somente para destinatários com ação de Assinar Online que estejam com ação de assinatura pendente nos documentos. Não é permitido o envio do processo para destinatários com ação de Receber Cópia.

***

**02. IdFormaEnvioProcesso**

**Descrição:** Parâmetro informando a forma de reenvio do processo

**Formato:** Bit - 1 - E-mail ou 2 - Whatsapp

**Requerido:** <mark style="color:blue;">Não</mark>

***

**03. nome**

**Descrição:** Parâmetro informando o nome do destinatário.

**Formato:** String

**Requerido:** <mark style="color:blue;">Não</mark>

***

**04. email**

**Descrição:** Parâmetro informando o e-mail para reenviar o processo.

**Formato:** String

**Requerido:** <mark style="color:red;">Sim, quando o parâmetro idFormaEnvio for igual a 1.</mark>

&#x20;**Validação:** O e-mail informado deve estar em um formato válido

***

**05. telefone**

**Descrição:** Parâmetro informando o telefone para reenviar o processo.

**Formato:** String

**Requerido:** <mark style="color:red;">Sim, quando o parâmetro idFormaEnvio for igual a 2.</mark>

&#x20;**Validação:** Somente é possível reenviar processo por WhatsApp (idFormaEnvioProcesso = 2) quando o tipo de assinatura destinatário for eletrônica.

***

**06. idMeioEnvioCodigoSeguranca**

**Descrição:** Os dados de Código de Segurança podem ser editados somente para destinatários que possuam a configuração de código de segurança, não permitindo inserir código de segurança para destinatários que não foram configurados inicialmente para usar o código de segurança. É permitido apenas alterar a forma de entrega do código de segurança para os destinatários que possuam esta configuração no processo.                     &#x20;

**Formato:** Bit, 1- SMS (Somente Brasil), 2 – Whatsapp, 3 – Email ou 4 - Não enviar

**Requerido:** <mark style="color:blue;">Não</mark>

***

**07. emailSeguranca**

**Descrição:** Parâmetro informando o e-mail para envio do código de segurança.

**Formato:** String

**Requerido:** <mark style="color:red;">Sim, quando o parâmetro idMeioEnvioCodigoSeguranca for igual a 3.</mark>

***

**08.** **telefoneSeguranca**

**Descrição:** Parâmetro informando o telefone para envio do código de segurança.

**Formato:** String

**Requerido:** <mark style="color:red;">Sim, quando o parâmetro idMeioEnvioCodigoSeguranca for igual a 1 ou 2.</mark>

***

**09. permitirReenviarCodigo**

**Descrição:** Permitir o reenvio do código de segurança

**Formato:** Bit, 1 = true ou 0 = False

**Requerido:** <mark style="color:blue;">Não</mark>

***

**10.dadosAssinatura**

Esta parte do JSON é opcional e **permite editar os dados de assinatura dos destinatários** com **idTipoAssinatura igual a 1 = eletrônica** que possuam estes dados configurados, que podem ser usados para preenchimento de campos ou validação do documento no momento que o destinatário assinar os documentos do processo como pessoa física e/ou jurídica.

Quando forem enviados dados de assinatura para **destinatários que não foram configurados inicialmente com estes dados,** estes serão desconsiderados.

**10.1 Signatário:** Parâmetros para editar nome e documento do signatário que serão utilizados para preenchimento de campos na tela ou validação do documento do signatário.

**a. nome**

**Descrição:** Parâmetro informando o nome do signatário que será alterado ao reenviar o processo.

**Formato:** Varchar(250)

**Requerido:** <mark style="color:blue;">Não</mark>

**b. numeroDocumento**

**Descrição:** Parâmetro informando o documento do signatário que será alterado ao reenviar o processo.

**Formato:** String

**Requerido:** <mark style="color:blue;">Não</mark>

**c. validarDocumento**

**Descrição:** Parâmetro informando se o número do documento do destinatário alterado no parâmetro **numeroDocumento** do objeto **signatario** será utilizado para validação ou não.

**Formato:** Bit: 1 – True ou 0 - False

**Requerido:** <mark style="color:blue;">Não</mark>

&#x20;**Os dados informados neste parâmetro serão desconsiderados quando** o parâmetro **numeroDocumento** objeto **signatario**  for nulo ou não for enviado.

&#x20;**Quando este parâmetro não for enviado ou for enviado** com **null** ou **com valor 0**, significa que os dados informados no parâmetro **numeroDocumento** serão utilizados somente para **preenchimento automático** no momento da assinatura como pessoa física.

**Quando este parâmetro for enviado com valor 1**, significa que os dados informados no parâmetro **numeroDocumento** serão utilizados para **validação** no momento da assinatura como pessoa física.

**d. DescartarDadosAnteriores**

**Descrição:** Parâmetro informando se os dados não informados no objeto signatario serão descartados.

**Formato:** Bit: 1 – True ou 0 - False

**Requerido:** <mark style="color:blue;">Não</mark>

**Os dados informados neste parâmetro serão desconsiderados quando** os parâmetros **nome** e **numeroDocumento** do objeto **signatario**  forem enviados.

**Quando este parâmetro não for enviado** ou for enviado com **null** ou **com valor 0**, significa que nenhum parâmetro do objeto **signatario** será descartado.

**Quando este parâmetro for enviado com valor 1**, significa que os dados não informados do objeto **signatario** devem ser removidos do processo.

**10.2 empresa:** Parâmetros para editar nome e documento da empresa que serão utilizados para preenchimento de campos na tela ou validação do documento do signatário.

{% hint style="warning" %}
<mark style="color:orange;">**Atenção:**</mark> <mark style="color:orange;"></mark><mark style="color:orange;">Os</mark> <mark style="color:orange;"></mark><mark style="color:orange;">**dados de empresa**</mark> <mark style="color:orange;"></mark><mark style="color:orange;">serão</mark> <mark style="color:orange;"></mark><mark style="color:orange;">**desconsiderados**</mark> <mark style="color:orange;"></mark><mark style="color:orange;">quando o signatário estiver configurado para</mark> <mark style="color:orange;"></mark><mark style="color:orange;">**assinar somente como pessoa física.**</mark>
{% endhint %}

**a. nome**

**Descrição:** Parâmetro informando o nome da empresa que será alterado ao reenviar o processo.

**Formato:** Varchar(250)

**Requerido:** <mark style="color:blue;">Não</mark>

**b. numeroDocumento**

**Descrição:** Parâmetro informando o documento da empresa será alterado ao reenviar o processo.

**Formato:** String

**Requerido:** <mark style="color:blue;">Não</mark>

**Validação: Quando este parâmetro NÃO for informado ou for nulo** e o parâmetro **DescartarDadosAnteriores** for enviado **com valor 1**, a informação de documento será excluída do processo.

**c. validarDocumento**

**Descrição:** Parâmetro informando se o número do documento da empresa alterado no parâmetro numeroDocumento do objeto empresa será utilizado para validação ou não.

**Formato:** Bit: 1 – True ou 0 - False

**Requerido:** <mark style="color:blue;">Não</mark>

**Os dados informados neste parâmetro devem ser desconsiderados quando o** parâmetro **numeroDocumento** objeto **empresa**  for nulo

**Quando este parâmetro não for enviado** ou for enviado com **null** ou com **valor 0**, significa que os dados informados no parâmetro **numeroDocumento** serão utilizados somente para **preenchimento automático** no momento da assinatura como pessoa jurídica.

**Quando este parâmetro for enviado com valor 1**, significa que os dados informados no parâmetro **numeroDocumento** serão utilizados para **validação** no momento da assinatura como pessoa física.

**d. DescartarDadosAnteriores**

**Descrição:** Parâmetro informando se os dados não informados no objeto empresa serão descartados.

**Formato:** Bit: 1 – True ou 0 - False

**Requerido:** <mark style="color:blue;">Não</mark>

**Os dados informados neste parâmetro serão desconsiderados quando os** parâmetros **nome** e **numeroDocumento** do objeto **empresa**  forem enviados.

**Quando este parâmetro não for enviado** ou for enviado com **null** ou **com valor 0**, significa que nenhum parâmetro do objeto **empresa** será descartado.

**Quando este parâmetro for enviado com valor 1**, significa que os dados não informados do objeto **empresa** serão removidos do processo.

***

## Retorno Validações

### Erro: 400 - Bad Request

Este erro é retornado quando não for possível interpretar a requisição e/ou o servidor tenta processar a solicitação, mas algum parâmetro da solicitação não é válido, por exemplo, um recurso formatado incorretamente ou uma tentativa de requisição com dados faltantes. As informações sobre a solicitação são fornecidas no corpo da resposta e incluem um código de erro e uma mensagem de erro.&#x20;

**a. Item obrigatório:** Esta mensagem será exibida no singular ou plural quando um ou mais itens obrigatórios não estiverem sido enviados na chamada da API: **O(s) item(ns) listado(s) é(são) obrigatório(s): “nome dos itens separados por vírgula”.**

&#x20;**b. Formato incorreto:** Esta mensagem será exibida no singular ou plural quando um ou mais itens estiverem sido enviados com formato incorreto: **O(s) item(ns) listado(s) está(ão) com o formato incorreto: “nome dos itens separados por vírgula”.**

**c. Ids inexistente:** Esta mensagem será exibida no singular ou plural quando um ou mais Id enviados não existirem: **O(s) id(s) listado(s) não existe(m): “nome dos itens que são Ids de tabela, separados por vírgula”.**

**d. Algum parâmetro está incorreto ou é inexistente:** Esta mensagem será exibida quando a chamada for feita com algum parâmetro escrito errado ou quando é enviado uma informação que não existe no método: **Algum parâmetro está incorreto ou é inexistente.**

### Erro: 401 – Unauthorized

Este erro é retornado quando:

• A chave de autenticação da API ArqSign está incorreta ou não foi informada corretamente.

• Conta está com status diferente de Ativo.

### Erro: 404 - Not Found

Este erro é retornado quando o recurso solicitado ou o _endpoint_ não foi localizado.

### Erro: 422 - Unprocessable

Este erro é retornado quando a requisição foi recebida com sucesso, porém contém parâmetros inválidos.

### Erro: 500 - Server Error

Este erro é retornado quando:

• Ocorre um erro interno no servidor.

• Ocorre uma falha na plataforma ArqSign.

• Formato do parâmetro incorreto.

• Formato do JSON incorreto.

***

## Retorno Sucesso

**Code 200** – OK

Ao executar o reenvio do processo com sucesso, o sistema **retornará os dados dos participantes do processo pendentes de assinatura dos documentos.**

{% hint style="warning" %}
<mark style="color:orange;">**Atenção: Mesmo que o destinatário não tenha sido informado para reenvio, os dados deste também retornará se estiver pendente de assinatura.**</mark>
{% endhint %}

**Por exemplo:**

Em um processo que possui 3 signatários pendentes de assinatura.

Ao reenviar o processo sem editar dados, retornará os dados dos 3 signatários pendentes de assinatura.

Ao reenviar o processo editando dados de um signatário, retornará os dados dos 3 signatários pendentes de assinatura.

### &#x20;Retorno - Exemplo Body Response

```
[
    {
        "idProcessoDestinatario": "guid",
        "ordem": 1, //numérico  
        "formaEnvioProcesso": "string",
        "nome": "string",
        "anexos": [
            {
                "idConfiguracaoAnexo": "guid",
                "nomeAnexo": "string"
            }
        ]
    },
    {
        "idProcessoDestinatario": "guid",
        "ordem": 1, //numérico  
        "formaEnvioProcesso": "string",
        "nome": "string",
        "anexos": null
    }
]

```

**a. idProcessoDestinatario**&#x20;

A API retorna o id do processo destinatário

**b. ordem**

API retorna a ordem de assinatura do destinatário.

**c. formaEnvioProcesso**

&#x20;A API retorna a forma de envio do processo para o destinatário, e-mail ou telefone do destinatário, em questão.

&#x20;**d. Nome**

&#x20;A API retorna o nome do destinatário.

&#x20;**e. Anexo**&#x20;

A API retorna as configurações de anexo do destinatário, se houver.
