# ✔️ PATCH api/v1/confwebhook/{idConfWebHook}/alterar-status

Este serviço permite alterar o status das configurações de webhook.

## Requisição

&#x20;**Orientações:**

* Quando campo requerido estiver como “Sim” = Sempre requerido
* Quando campo requerido estiver como “Não” = Informação Opcional
* Quando campo requerido estiver como “Talvez” = Em alguns casos ele será requerido. Para saber estes casos, consultar a descrição do tópico, conforme o número de referência da linha na tabela.

<figure><img src="../../../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Clique na imagem para ampliar</p></figcaption></figure>

### Exemplo Body Request

```json
{
    "status": "byte"
}
```

## Validações

Validações Específicas

**status**

> **Descrição:** Parâmetro informando o status que será alterado no Webhook.
>
> **Formato:** Byte - 1 = Ativo, 2 = Inativo
>
> **Requerido:** <mark style="color:red;">**Sim**</mark>
>
> **Validação:**
>
> a- Somente é permitido valores iguais a 1 ou 2.
>
> b- Ao ativar uma configuração de webhook, o sistema zera as quantidades de tentativas dos gatilhos, se houver.

**Validações Gerais**

Autenticação

1- Para autenticar na API da ArqSign, o usuário deve informar AppKey da conta que está alterando o status da configuração de webhook.

2- Somente conta com status Ativo pode alterar o status da configuração de Webhook via integração ArqSign.

3- O sistema valida se o **IdConfWebHook** informado pertence a conta da **AppKey**.

## Retorno Validações

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

Este erro é retornado quando

* A chave de autenticação da API ArqSign está incorreta ou não foi informada corretamente.
* Conta está com status diferente de Ativo.

### Erro: 404 - Not Found

Este erro é retornado quando o recurso solicitado ou o _endpoint_ não foi localizado.

### Erro: 500 - Server Error

Este erro é retornado quando:

* Ocorre um erro interno no servidor;
* Ocorre uma falha na plataforma ArqSign;
* Formato do parâmetro incorreto;
* Formato do JSON incorreto.

## Retorno Sucesso

&#x20;Ao executar a alteração do status da configuração de Webhook, o sistema retorna código 200 – OK.

&#x20;
