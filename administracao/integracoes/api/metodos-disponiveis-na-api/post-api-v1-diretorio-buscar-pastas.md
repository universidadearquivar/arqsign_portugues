# ✔️ POST api/v1/diretorio/buscar-pastas

Este serviço permite buscar os dados das pastas da conta.

O usuário terá a possibilidade de buscar por:

* Caminho completo de uma ou mais pastas;
* Os filhos de uma pasta;
* Pasta raiz e seus primeiros filhos.

## Requisição

**Orientações:**

Quando campo requerido estiver como “Sim” = Sempre requerido

Quando campo requerido estiver como “Não” = Informação Opcional

Quando campo requerido estiver como “Talvez” = Em alguns casos ele será requerido. Para saber estes casos, consultar a descrição do tópico das validações específicas.

<figure><img src="../../../../.gitbook/assets/image (317).png" alt=""><figcaption><p>Clique na imagem para ampliar</p></figcaption></figure>

### Exemplo Body Request

```json
{
   "buscarPor": "tinyint",//1 - Caminho Completo, 2 = Filhos, 3 = Pasta Raiz 
   "ativas": "bit",//1 – true, 0 = false
   "pastas": [
    "guid",
    "guid",
    "guid",
    "guid"
     ]
}
```

## Validações

### Validações especificas

**buscarPor**

> **Descrição:** Parâmetro obrigatório informando o tipo de busca que será executado.
>
> **Formato:** Bit: 1 - Caminho Completo, 2 = Filhos, 3 = Pasta Raiz
>
> **Requerido: **<mark style="color:red;">**Sim**</mark>
>
> **Validação:**
>
> a- Somente é permitido valores iguais a 1, 2 ou 3.

**ativas**

> **Descrição:** Parâmetro informando se a busca deve retornar somente as pastas ativas ou todas as pastas.
>
> **Formato:** Bit: 1 - True, 0 = False
>
> **Requerido: **<mark style="color:blue;">**Não**</mark>
>
> **Validação:**
>
> a- Quando este parâmetro for enviado como **true**, o sistema retorna **somente pastas ativas**, considerando os demais parâmetros de busca.
>
> b- Quando este parâmetro for enviado como **false**, o sistema retorna **as pastas ativas e excluídas logicamente**, considerando os demais parâmetros de busca.
>
> c- Quando este parâmetro **não** for enviado ou enviado como **null**, o sistema considera como **false** e retornar **as pastas ativas e excluídas logicamente**, considerando os demais parâmetros de busca.

**pastas**

> Nesta parte do json o usuário poderá informar um ou mais id’s de pastas para consultar, conforme demais parâmetros.
>
> **Descrição:** Parâmetro informando as pastas que serão consultadas. Esta informação é necessária quando estiver buscando pelo caminho completo de uma ou mais pastas ou quando estiver buscado pelos filhos de uma pasta.
>
> **Formato:** Guid
>
> **Requerido: **<mark style="color:red;">**Sim, quando buscarPor for igual a 1 ou 2**</mark>
>
> **Validação:**
>
> a- Não é obrigatório informar pastas quando **buscarPor** for igual 3.
>
> O sistema desconsidera a informação desse parâmetro quando **buscarPor** for igual 3.
>
> b- O sistema exige id de pasta quando **buscarPor** for igual 1 ou 2.
>
> c- É permitido informar somente um id de pasta quando **buscarPor** for igual 2.
>
> d- É permitido informar um ou mais id’s de pastas quando **buscarPor** for igual 1.
>
> e- Quando for informado id de pasta, o sistema valida se o **idPasta** pertence a conta.

### Validações gerais

1- O usuário deve informar a  AppKey da conta que está buscando os dados das pastas.

2- Somente conta com status Ativo pode buscar dados das pastas da conta via integração ArqSign.

## Retorno validações

### Erro: 400 - Bad Request

&#x20;Este erro é retornado quando não for possível interpretar a requisição e/ou o servidor tenta processar a solicitação, mas algum parâmetro da solicitação não é válido, por exemplo, um recurso formatado incorretamente ou uma tentativa de requisição com dados faltantes. As informações sobre a solicitação são fornecidas no corpo da resposta e incluem um código de erro e uma mensagem de erro.

&#x20;**a- Item obrigatório:** Esta mensagem é exibida no singular ou plural quando um ou mais itens obrigatórios não tiver sido enviado na chamada da API.

> **Mensagem:** O(s) item(ns) listado(s) é(são) obrigatório(s): “nome dos itens separados por vírgula”.

**b- Formato incorreto:** Esta mensagem é exibida no singular ou plural quando um ou mais itens estiverem sido enviados com formato incorreto.

> **Mensagem:** O(s) item(ns) listado(s) está(ão) com o formato incorreto: “nome dos itens separados por vírgula”.

**c- Ids inexistente:** Esta mensagem é exibida no singular ou plural quando um ou mais Id enviado não existir.

> **Mensagem:** O(s) id(s) listado(s) não existe(m): “nome dos itens que são Ids de tabela, separados por vírgula”.

**d- Algum parâmetro está incorreto ou é inexistente:** Esta mensagem é exibida quando a chamada é feita com algum parâmetro escrito errado ou quando é enviado uma informação que não existe no método.

> **Mensagem:** Algum parâmetro está incorreto ou é inexistente.

### &#x20;Erro: 401 – Unauthorized

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

<figure><img src="../../../../.gitbook/assets/image (318).png" alt=""><figcaption><p>Clique na imagem para ampliar</p></figcaption></figure>

### Dados da Pasta

**1 - id**

O sistema retorna o id da pasta.

**2 - nome**

O sistema retorna o nome da pasta.     &#x20;

**3 - caminhoCompleto**

O sistema **retorna o caminho completo das pastas informadas.**

Ex.:    Arquivar|Administração|Contratos

**4 - status**

O sistema retorna o status da pasta “**Ativa**” ou “**Excluída**”

**Ativa** = Pasta não excluída logicamente.

**Excluída** = Pasta excluída logicamente.

**5 - filhos**

Quando **o parâmetro buscarPor for igual a 1 (Caminho Completo)**, o sistema **não retorna os filhos das pastas informadas.**

&#x20;Quando **o parâmetro buscarPor for igual a 2 (Filhos)**, o sistema **retorna os filhos da pasta informada**, ordenadas alfabeticamente pelo nome.

&#x20;Quando **o parâmetro buscarPor for igual a 3 (Pasta Raiz)**, o sistema **retorna os dados da pasta raiz e seus primeiros filhos**, ordenados alfabeticamente pelo nome.

**5.1 - id**

O sistema retorna o id da pasta filha.

**5.2 - nome**

O sistema retorna o nome da pasta filha.

**5.3 - caminhoCompleto**

O sistema retorna o caminho completo da pasta filha.

Ex.: Arquivar|Administração|Contratos

**5.4 - status**

O sistema retorna o status da pasta filha “**Ativa**” ou “**Excluída**”

**Ativa** = Pasta não excluída logicamente.

**Excluída** = Pasta excluída logicamente.

**5.5 - possuiFilhos**

O sistema retorna  se o filho da pasta possui filho ou não.

### Retorno - Exemplo Body Response
