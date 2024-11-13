# ✔️ POST /api/v1/processo/{idProcesso}/buscar-anexos-signatarios

Este serviço permite buscar os **anexos dos signatários**, informando **um ou mais signatários específicos do processo**.

### Requisição

&#x20;

Orientações:

Quando campo requerido estiver como “Sim” = Sempre requerido

Quando campo requerido estiver como “Não” = Informação Opcional

Quando campo requerido estiver como “Talvez” = Em alguns casos ele será requerido. Para saber estes casos, consultar a descrição do tópico, conforme o número de referência da linha na tabela.

&#x20;

| <p> </p><p>Ref</p><p> </p> | <p> </p><p>Parâmetro</p><p> </p> | <p> </p><p>Formato</p><p> </p> | <p> </p><p>Requerido</p><p> </p> |
| -------------------------- | -------------------------------- | ------------------------------ | -------------------------------- |
| 1                          | "arquivoTipo"                    | "byte"                         | Sim                              |
| 2                          | “signatarios” \[]                | "guid"                         | Não                              |

&#x20;

#### 1.1.1       Exemplo Body Request
