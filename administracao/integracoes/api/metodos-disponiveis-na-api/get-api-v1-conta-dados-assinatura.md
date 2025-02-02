# ✔️ 4.3.GET/api/v1/conta/dados-assinatura

Este serviço permite buscar os dados de uma conta ArqSIGN.

## Validações

### Validações gerais

O usuário deve informar AppKey e SubscriptionKey (SubscriptionKey1 ou SubscriptionKey2) da conta.

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

* Ocorre um erro interno no servidor,
* Ocorre uma falha na plataforma ArqSign,
* Formato do JSON incorreto.

## Retorno de sucesso

Status 200 - Success

O sistema deve retornar os dados da conta informada.

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption><p>Clique na imagem para ampliar</p></figcaption></figure>

### Dados da Conta

**Conta**

O sistema retorna os dados da conta identificado via AppKey.         &#x20;

> **id**
>
> O sistema retorna o id da conta da AppKey informada.
>
> &#x20;**nome**  &#x20;
>
> &#x20;O sistema retorna o nome da conta.
>
> **idStatus**
>
> O sistema deve retornar o id status da conta.
>
> 1 - Ativo
>
> 2 - Inativo
>
> 3 - Bloqueado
>
> 4 - Pendente.
>
> &#x20;**status**
>
> O sistema retorna o status da conta: Ativo, Inativo, Bloqueado e Pendente.
>
> &#x20;Retorna o status conforme o idioma da conta.

**plano**

O sistema retorna os dados do plano da última assinatura da conta.

> **id**
>
> O sistema retorna o id do plano da última assinatura da conta.       &#x20;
>
> **tipoPlano**
>
> O sistema retorna o tipo do plano da última assinatura da conta.
>
> C = Corporativo
>
> P = Profissional/Empresarial
>
> G = Grátis
>
> **nome**
>
> O sistema retorna o nome do plano da última assinatura da conta, conforme o idioma da conta.
>
> **periodo**
>
> O sistema retorna o período do plano da última assinatura da conta.
>
> **valor**
>
> O sistema retornaro valor do plano da última assinatura da conta.   &#x20;

**assinatura**

O sistema retorna a última assinatura da conta.

> **id**
>
> O sistema retorna o id da última assinatura da conta.   &#x20;
>
> **inicioVigencia**
>
> O sistema retorna o período inicial da última assinatura da conta.   &#x20;
>
> **fimVigencia**
>
> O sistema retorna o período final da última assinatura da conta.
>
> **trial**
>
> O sistema retorna se a última assinatura da conta está em período trial.
>
> **itens**
>
> O sistema retorna os itens da última assinatura da conta.
>
> > **id**
> >
> > O sistema retorna o id do item da última assinatura da conta.
> >
> > **nome**
> >
> > O sistema retorna o nome do item da última assinatura da conta.
> >
> > Retorna o nome conforme o idioma da conta.&#x20;
> >
> > **saldo**
> >
> > Retorna o saldo atual para o item em questão.
> >
> > Neste saldo está incluído saldo da assinatura vigente + saldo do item extra vigente.&#x20;
> >
> > Se a última assinatura da conta não estiver vigente, então retorna o saldo 0.
> >
> > **permiteExcedente**
> >
> > O sistema retorna se o item da última assinatura da conta permite excedente.

### Retorno - Exemplo Body Response

```json
{
    "Conta": {
        "id": "guid",
        "nome": "string",
        "idStatus": "tinyint",
        "status": "string"
        },
    "plano": {
        "id": "guid",
        "tipoPlano": "char(1)",
        "nome": "string",
        "periodo": "char",
        "valor": "decimal"
    },
    "assinatura": {
        "id": "guid",
        "inicioVigencia": "date",
        "fimVigencia": "date",
        "trial": "bit", // true ou false      
        "itens": [
            {
                "id": "tinyint",
                "nome": "string",
                "saldo": "int", 
                "permiteExcedente": "bit", // true ou false      
            },
            {
                "id": "tinyint",
                "nome": "string",
                "saldo": "int", 
                "permiteExcedente": "bit", // true ou false      
            }
        ]
    }
}
```

