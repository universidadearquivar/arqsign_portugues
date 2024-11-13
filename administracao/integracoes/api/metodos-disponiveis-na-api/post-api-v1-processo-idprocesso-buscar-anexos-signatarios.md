# ✔️ POST /api/v1/processo/{idProcesso}/buscar-anexos-signatarios

Este serviço permite buscar os **anexos dos signatários**, informando **um ou mais signatários específicos do processo**.

## Requisição

#### **Orientações:**

Quando campo requerido estiver como “Sim” = Sempre requerido

Quando campo requerido estiver como “Não” = Informação Opcional

Quando campo requerido estiver como “Talvez” = Em alguns casos ele será requerido. Para saber estes casos, consultar a descrição do tópico, conforme o número de referência da linha na tabela.

<figure><img src="../../../../.gitbook/assets/Screenshot_2 (2).png" alt=""><figcaption><p>Clique na imagem para ampliar</p></figcaption></figure>

#### Exemplo Body Request

```json
{
    "arquivoTipo": "byte",
    "signatarios": [
        "guid",
        "guid"
                ]
}

```

## Validações

### Validações especificas

O usuário deve informar o IdProcesso que deseja consultar os anexos dos signatários.

O sistema retorna os anexos dos signatários do processo no formato link para download ou base64 do arquivo.

#### **arquivoTipo**&#x20;

**Descrição:** Parâmetro obrigatório informando se é para retornar **o link para download ou base64 do anexo** do signatário.

**Formato:** Byte - 1 = base64, 2 = Link para download

**Requerido: **<mark style="color:red;">**Sim**</mark>

#### **Validação:**

a- Somente é permitido valores iguais a 1 ou 2.

* **Mensagem:** O parâmetro **arquivoTipo** permite somente valores 1 ou 2.
* Quando for enviado o **valor 1** no parâmetro **arquivoTipo** significa que o sistema retorna os anexos dos signatários do processo de assinaturas em **formato base64**
* Quando for enviado o **valor 2** no parâmetro **arquivoTipo** significa que o sistema **retorna o link para download dos anexos** dos signatários do processo de assinaturas.

