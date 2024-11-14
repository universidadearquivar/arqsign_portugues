# ✔️ GET api/v1/processo/{idArquivoProcesso}/registro-assinaturas

Este serviço permite buscar o base64 do registro de assinatura de um arquivo processo.

## Validações

### Validações gerais

&#x20;1- O usuário deve informar AppKey e SubscriptionKey (SubscriptionKey1 ou SubscriptionKey2) da conta.

&#x20;2- Somente conta com status Ativo pode permitir buscar o registro de assinatura de um ArquivoProcesso via integração ArqSign.

&#x20;3- O sistema retorna o registro de assinatura somente para **processos com status diferente de criado.**

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

### &#x20;Erro: 500 - Server Error

Este erro é retornado quando:

* Ocorre um erro interno no servidor;
* Ocorre uma falha na plataforma ArqSign;
* Formato do JSON incorreto.

## Retorno de sucesso

Status 200 - Success

&#x20;O sistema retorna o arquivo em formato base64 do registro de assinatura para o idArquivoProcesso informado.

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption><p>Clique na imagem para ampliar</p></figcaption></figure>

### Dados do registro de assinaturas

**1 - id**

O sistema retorna o id do arquivo processo a que se refere o registro de assinatura.

**2 - nome**

O sistema retorna o nome do documento a que se refere o registro de assinatura + a palavra “Registro de Assinaturas”. Exemplo: “Contrato\_Registro de Assinaturas.pdf”

**3 - base64**

O sistema retorna o base64 do registro de assinatura.

### Retorno - Exemplo Body Response

```json
{
  "idArquivoProcesso": "guid",
  "nome": "string",
  "base64": "base64",
}
```
