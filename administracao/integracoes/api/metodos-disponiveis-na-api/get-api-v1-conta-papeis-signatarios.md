# ✔️ 4.1.GET/api/v1/conta/papeis-signatarios

Este serviço permite buscar os papéis de signatário da conta.

## Requisição

A Requisição não se aplica pois a validação é feita pela AppKey.

## Validações

### &#x20;Validações gerais

&#x20;1- Para autenticar na API da ArqSign, o usuário deve informar a  AppKey da conta que está buscando os dados dos papeis de signatários.

&#x20;2- Somente conta com status Ativo pode buscar dados dos papeis de signatários da conta via integração ArqSign.

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

## Retorno de sucesso

Status 200 - Success

&#x20;O sistema retorna os papeis de signatários da conta.

<figure><img src="../../../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption><p>Clique na imagem para ampliar</p></figcaption></figure>

### Dados dos Papeis do signatário

&#x20;**1 - id**

O sistema retorna o id do papel signatário.

&#x20; **2 - nome**

O sistema retorna o nome do papel signatário.

&#x20; **3 - padrao**

O sistema retorna informação se o papel signatário é padrão ou não (true ou false).

### &#x20;Retorno - Exemplo Body Response

```json
[
   {
     "id": "guid",
     "nome": "string",
     "padrao": "booleano",
   }
]
```

