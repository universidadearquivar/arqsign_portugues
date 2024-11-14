# ✔️ POST api/v1/conta/buscar-consumo-itens-assinatura

Este serviço permite buscar a quantidade do item de envios (Envios, WhatsApp, SMS) que a conta usou em determinado período.

## Requisição

Orientações:

* Quando campo requerido estiver como “Sim” = Sempre requerido
* Quando campo requerido estiver como “Não” = Informação Opcional
* Quando campo requerido estiver como “Talvez” = Em alguns casos ele será requerido. Para saber estes casos, consultar a descrição do tópico das validações específicas.

<figure><img src="../../../../.gitbook/assets/image (2).png" alt=""><figcaption><p>Clique na imagem para ampliar</p></figcaption></figure>

### Exemplo Body Request

```json
{
   "dataInicial": "date", 
   "dataFinal": "date",
   "item": "tinyint"
}
```

## Validações

### &#x20;Validações especificas

**dataInicial**

> **Descrição:** Parâmetro obrigatório informando a data inicial para a referência de uso de um item.
>
> **Formato:** date no padrão ISO <mark style="color:red;">(aaaa-mm-dd ou mm- dd-aaaa)</mark>
>
> **Requerido:** <mark style="color:red;">**Sim**</mark>
>
> **Validação:**
>
> a- O sistema não permite dataInicial maior que a dataFinal.

**dataFinal**

> **Descrição:** Parâmetro obrigatório informando a data final para a referência de uso de um item.
>
> **Formato:** date no padrão ISO <mark style="color:red;">(aaaa-mm-dd ou mm- dd-aaaa)</mark>
>
> **Requerido:** <mark style="color:red;">**Sim**</mark>
>
> **Validação:**
>
> a- O sistema não permite dataFinal menor que a dataInicial.

**item**

> **Descrição:** Parâmetro obrigatório informando o item desejado.
>
> **Formato:** tinyint - **0 = Todos os itens; 1 = Envio; 2 = WhatsApp; 3 = SMS**
>
> **Requerido: **<mark style="color:red;">**Sim**</mark>
>
> **Validação:**
>
> a- Somente serão aceitos os seguintes números:
>
> * 0 = para retornar todos os itens usados na conta (Envio, SMS e WhatsApp),
> * 1 = para retornar somente o uso do item Envio,
> * 2 = para retornar somente o uso do item WhatsApp,
> * 3 = para retornar somente o uso do item SMS.
>
> Caso o usuário envie um número diferente do esperado, retorna a menagem de “Ids inexistente”.

### Validações gerais

&#x20;1- O usuário deve informar AppKey e SubscriptionKey (SubscriptionKey1 ou SubscriptionKey2) da conta.

&#x20;2- Somente conta com status Ativo pode buscar dados de uso e consumo da conta via integração ArqSign.

&#x20;3- O sistema limita o período entre a **dataInicial** e **dataFinal**, permitindo até 1 ano.

## Retorno validações

### Erro: 400 - Bad Request

Este erro é retornado quando não for possível interpretar a requisição e/ou o servidor tenta processar a solicitação, mas algum parâmetro da solicitação não é válido, por exemplo, um recurso formatado incorretamente ou uma tentativa de requisição com dados faltantes. As informações sobre a solicitação são fornecidas no corpo da resposta e incluem um código de erro e uma mensagem de erro.

**a- Item obrigatório:** Esta mensagem é exibida no singular ou plural quando um ou mais itens obrigatórios não tiver sido enviado na chamada da API.

> **Mensagem:** O(s) item(ns) listado(s) é(são) obrigatório(s): “nome dos itens separados por vírgula”.

**b- Formato incorreto:** Esta mensagem é exibida no singular ou plural quando um ou mais itens estiverem sido enviados com formato incorreto.

> **Mensagem:** O(s) item(ns) listado(s) está(ão) com o formato incorreto: “nome dos itens separados por vírgula”.

**c- Ids inexistente:** Esta mensagem é exibida no singular ou plural quando um ou mais Id enviado não existir.

> **Mensagem:** O(s) id(s) listado(s) não existe(m): “nome dos itens que são Ids de tabela, separados por vírgula”.

**d- Algum parâmetro está incorreto ou é inexistente:** Esta mensagem é exibida quando a chamada é feita com algum parâmetro escrito errado ou quando é enviado uma informação que não existe no método.

> **Mensagem:** Algum parâmetro está incorreto ou é inexistente.

### Erro: 401 – Unauthorized

Este erro é retornado quando a chave de autenticação da API ArqSign está incorreta ou não foi informada corretamente.

### Erro: 404 - Not Found

Este erro é retornado quando o recurso solicitado ou o _endpoint_ não foi localizado.

### Erro: 500 - Server Error

Este erro é retornado quando:

* Ocorre um erro interno no servidor;
* Ocorre uma falha na plataforma ArqSign;
* Formato do JSON incorreto.

### Retorno de sucesso

&#x20;Status 200 - Success

<figure><img src="../../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>Clique na imagem para ampliar</p></figcaption></figure>

### Dados da Conta

&#x20;**1 - id**

O sistema retorna o id da conta.    &#x20;

**2 - nomeConta**

O sistema retorna o nome da conta.

**3 - itens**

> **id**
>
> O sistema retorna o id do item em questão. Somente são retornados os itens solicitados na requisição (parâmetro **item**):
>
> 1 = Envio
>
> 2 = Whatsapp
>
> 3 = SMS

> **nome**
>
> O sistema retorna o nome do item em questão, conforme idioma da conta.

> **quantidade**
>
> O sistema retorna a quantidade de uso para o item em questão no período informado na requisição.

### Retorno - Exemplo Body Response

```json
{
    "idConta": "guid",
    "nomeConta": "string",
    "itens": [
        {
            "id": "tinyint",
            "nome": "string",
            "quantidade": "int"
        }
    ]
}
```
