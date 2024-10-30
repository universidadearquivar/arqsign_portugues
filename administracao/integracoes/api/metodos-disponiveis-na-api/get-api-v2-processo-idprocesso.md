---
description: >-
  O objetivo do método é permitir aos clientes, via API, buscar um processo com
  seus respectivos dados, signatários e documentos.
---

# ✔️ GET/api/v2/processo/{idProcesso}

## Requisição

<figure><img src="../../../../.gitbook/assets/image (112).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

## Autenticações e Validações

1. Para autenticar na API da ArqSign, o usuário deve informar a AppKey, válida, da conta que está buscando p processo.
2. Somente conta com **status Ativo** e com **permissão de Integração ArqSign** pode buscar processos via integração ArqSign.
3. O sistema valida se o **IdProcesso** pertence a conta da **AppKey**.

## Retorno Validações

### Erro: 400 - Bad Request

Este erro é retornado quando não for possível interpretar a requisição e/ou o servidor tenta processar a solicitação, mas algum parâmetro da solicitação não é válido, por exemplo, um recurso formatado incorretamente ou uma tentativa de requisição com dados faltantes. As informações sobre a solicitação são fornecidas no corpo da resposta e incluem um código de erro e uma mensagem de erro.

**a. Item obrigatório:** Esta mensagem é exibida no singular ou plural quando um ou mais itens obrigatórios não tiver sido enviado na chamada da API.

**Mensagem: O(s) item(ns) listado(s) é(são) obrigatório(s): “nome dos itens separados por vírgula”.**

**b. Formato incorreto:** Esta mensagem é exibida no singular ou plural quando um ou mais itens estiverem sido enviados com formato incorreto.

**Mensagem: O(s) item(ns) listado(s) está(ão) com o formato incorreto: “nome dos itens separados por vírgula”.**

**c. Ids inexistente:** Esta mensagem é exibida no singular ou plural quando um ou mais Id enviado não existir.

**Mensagem: O(s) id(s) listado(s) não existe(m): “nome dos itens que são Ids de tabela, separados por vírgula”.**

**d. Documento excluído:** Esta mensagem será exibida quando o processo retornar estive excluído.

**Mensagem: Processo excluído.**

**e. Algum parâmetro está incorreto ou é inexistente:** Esta mensagem é exibida quando a chamada é feita com algum parâmetro escrito errado ou quando é enviado uma informação que não existe no método.

**Mensagem: Algum parâmetro está incorreto ou é inexistente.**

### Erro: 401 – Unauthorized

Este erro é retornado quando a chave de autenticação da API ArqSign está incorreta ou não foi informada corretamente.

### Erro: 404 - Not Found

Este erro é retornado quando o recurso solicitado ou o _endpoint_ não foi localizado.

### Erro: 422 - Unprocessable

Este erro é retornado quando a requisição foi recebida com sucesso, porém contém parâmetros inválidos.

### Erro: 500 - Server Error

Este erro é retornado quando:

* Ocorre um erro interno no servidor;
* Ocorre uma falha na plataforma ArqSign;
* Formato do JSON incorreto.

## Retorno de sucesso

Status 200 - Success

O sistema deve retornar os dados do processo, dados dos signatários, arquivo do processo e registro de assinatura.

* Dados do processo
* Dados dos signatários
* Documentos do processo com seu respectivo registro de assinatura.

<figure><img src="../../../../.gitbook/assets/GET v2 (1).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

### Dados do processo

Esta parte do JSON retorna os dados do processo de assinatura.

#### 1. nomeProcesso

O sistema retorna o nome do processo.

#### 2. idPasta

O sistema retorna o id da pasta do processo.

#### 3. caminhodaPasta

O sistema retorna o caminho da pasta do processo.\
Ex.:  Arquivar \\\Administração \\\ Contratos

#### 4. idResponsavel

O sistema retorna o id do responsável (remetente) do processo.

#### 5. nomeResponsavel

O sistema retorna o nome do responsável do processo.

#### 6. status

O sistema retorna o status do processo **(Criado, Aguardando, Em processo, Concluído ou Cancelado).**

#### 7. dataCadastro

O sistema retorna a data de cadastro do processo.

#### 8. dataEnvio

O sistema retorna a data de envio do processo. O processo terá data de envio **(dataEnvio)** quando o status for diferente de **Criado**.

#### 9. dataConclusao

O sistema retorna a data de conclusão do processo. O processo terá data de conclusão **(dataConclusao)** quando o status for igual a **Concluído**.

#### 10. dataRenovacao

O sistema retorna a data de renovação do processo. O processo terá data de renovação **(dataRenovacao)** quando houver configuração de renovação e o documento estiver com status **Concluído**.

&#x20;O sistema deve calcular a data de renovação conforme a configuração de renovação e a data de conclusão do documento. **(dataRenovacao = dataConclusao + renovacaoMeses)**

#### 11. dataCancelamento

O sistema retorna a data de cancelamento do processo. O processo terá data de cancelamento **(dataCancelamento)** quando o status for igual a **Cancelado**.

#### 12. usuarioCancelamento

O sistema retorna o nome do usuário quem cancelou o processo. O documento terá o nome do usuário quem cancelou o documento **(usuarioCancelamento)** quando houver data de cancelamento **(dataCancelamento)** e o status for igual a **Cancelado**.

#### 13. dataReenvio

O sistema retorna a data de reenvio do processo. O processo terá data de reenvio quando o remetente reenviar o processo para os signatários pendentes de assinaturas.

#### 14. dataExpiracao:

O sistema retorna a data de expiração do processo.

O sistema deve calcular a data de expiração conforme a configuração e a data de envio/reenvio do documento.\
Se **dataReenvio** for igual a null, então **dataExpiracao = dataEnvio + ExpiracaoDias.**\
Se **dataReenvio** for diferente de null, então **dataExpiracao = dataReenvio + expiracaoDias.**

#### 15. expiracaoDias

O sistema retorna os dias de expiração do processo.

#### 16. avisoExpiracaoDias

O sistema retorna os dias para aviso de expiração do processo.

#### 17. lembrete:

O sistema retorna o dado informando se o processo possui lembre de assinatura.

&#x20;O parâmetro **(lembrete)** informa se o processo possui lembrete de assinatura ou não.\
1 - true = possui lembrete de assinatura.\
0 - false = não possui lembrete de assinatura.

#### &#x20;18. frequenciaLembrete

O sistema retorna a frequência de lembrete de assinatura do(s) documento(s) do processo.



### Dados dos Signatários

Esta parte do JSON retorna os dados dos signatários participantes do processo de assinatura.

#### 19. signatarios

#### 19.1. ordemAssinatura

O sistema retorna a ordem de assinatura do signatário, em questão.&#x20;

**19.2. id**

O sistema retorna o id do processo destinatário.

**19.3. nome**

O sistema retorna o nome do signatário.

**19.4. email**

O sistema retorna o e-mail do signatário quando o processo foi enviado por **e-mail.**

**19.5. telefone**

O sistema retorna o telefone do signatário quando o processo foi enviado por **WhatsApp**.

**19.6. aguardandoEnvio**

O sistema retorna informação de aguardando envio do processo que pode ser true ou false. Este parâmetro terá valor true quando o processo de assinatura possuir ordem de assinaturas e o signatário antecessor ao signatário, em questão, não concluiu a assinatura. Assim o signatário está aguardando o envio do documento para assinatura.

**19.7. falhaEnvio**

O sistema retorna informação de falha no envio do processo que pode ser true ou false. Este parâmetro terá valor true quando ocorrer falha no envio do processo para o destinatário, em questão.

**19.8. tipoAcao**

O sistema retorna o tipo de ação do signatário no processo que pode ser **Assina Online** ou **Receber uma cópia.**

**19.9. copiaEnviada**

O sistema retorna informação de cópia enviada quando o signatário possuir ação de **Receber uma cópia**. Este parâmetro terá valor true quando teve a cópia do processo enviada ou false quando não teve cópia enviada.

**19.10. remetente**

O sistema retorna informação se o signatário é, também, o remetente do processo. Este parâmetro terá valor true quando teve o signatário é o remetente do processo ou false o signatário não é remetente do processo.\
Obs.: O remetente do processo também pode participar do processo de assinatura como signatário.

**19.11. assinaturaRecusada**

O sistema retorna informação de assinatura recusada quando um signatário recusar a assinatura do(s) documento(s). Este parâmetro terá valor true quando o signatário recusou a assinatura do(s) documento(s) ou false quando o signatário não recusou a assinatura do(s) documento(s) do processo.

**19.12. motivoRecusa**

O sistema retorna informação de motivo da recusa da assinatura do(s) documento(s) do processo. Quando o parâmetro **assinaturaRecusada** for igual a **true**, o parâmetro **motivoRecusa** deve conter o motivo da recusa informado pelo signatário e o status do processo deve ser **“Cancelado”.**

**19.13. seguranca**

O sistema retorna dados de código de segurança somente se o signatário possuir estas configurações para acessar o(s) documento(s) do processo.

**19.13.1. codigoSeguranca**

&#x20;O sistema retorna o código de segurança gerado ao enviar o processo par assinaturas.

**19.13.2. codigoSegurancaEmail**

O sistema retorna o e-mail quando o código de segurança foi enviado por **e-mail.**

**19.13.3. codigoSegurancaTelefone**

O sistema retorna o telefone quando o código de segurança foi enviado por **WhatsApp** ou **SMS**.

**19.14. papelSignatario**

O sistema retorna o(s) papel(is) somente se o signatário possuir estas configurações.

**19.14.1. pessoaFisica**

O sistema retorna esta informação quando o signatário possui papel(is) como pessoa física.

**19.14.2. pessoaJuridica**

O sistema retorna esta informação quando o signatário possui papel(is) como pessoa jurídica.

**19.15. dadosAssinatura**

O sistema retorna dados de assinatura do signatário.

**19.15.1. tipoAssinatura**

O sistema retorna o tipo de assinatura que o signatário executou ou executará. Este parâmetro pode ter o valor: **Assinatura Eletrônica** ou **Certificado Digital - ICP Brasil,** ou **Certificado Digital – Outros.**\
Quando o **tipo de ação** do signatário for igual a **Receber uma cópia**, o parâmetro **tipoAssinatura** será **null**.

**19.15.2. dataAssinatura**

O sistema retorna a data que o signatário assinou o documento. Este parâmetro terá valor null quando o signatário não assinou o(s) documento(s) do processo.

**19.15.3. ip**

O sistema retorna o IP do signatário que assinou o documento. Este parâmetro terá valor null quando o signatário não assinou o(s) documento(s) do processo.

**19.15.5. geoLocalizacao**

O sistema retorna a geolocalização do signatário que assinou o documento. Este parâmetro terá valor null quando o signatário não assinou o(s) documento(s) do processo ou quando o signatário não permitiu capturar a sua localização.

**19.16. dadosCertificado**

O sistema retorna os dados do certificado utilizado para assinatura do(s) documento(s) do processo. Estes parâmetros terão valor null quando o signatário não assinou o(s) documento(s) do processo.

**19.16.1. nome**

O sistema retorna o nome do certificado.

**19.16.2. emissor**

O sistema retorna o emissor do certificado.

**19.16.3. validadeInicio**

O sistema retorna o início da validade do certificado.

**19.16.4. validadeFim**

O sistema retorna o final da validade do certificado.

**19.17. dadosPessoaFisica**

Estes dados serão retornados quando signatários com tipo de assinatura eletrônica informar os dados de pessoa física. Estes parâmetros terão valor null quando:

* O tipo de assinatura for com cerificado digital (ICP-Brasil ou Outros), ou
* O tipo de assinatura eletrônica e o signatário não informou os dados de pessoa física, ou
* Signatário não assinou o(s) documento(s) do processo.

**19.17.1. nomePessoaFisica**

O sistema retorna o nome informado pelo signatário ao assinar o(s) documento(s) do processo.

**19.17.2. tipoDocumentoPessoaFisica**

O sistema retorna o tipo do documento de pessoa física do signatário. Este terá o valor definido no envio documento que pode ser **CPF, CNH, RG** ou **Outro**.\
Quando o tipo do documento de pessoa física for definido como **Outro**, o sistema deve exibir o nome do tipo do documento definido pelo usuário/remetente do processo.

**19.17.3. numeroDocumetoPessoaFisica**

O sistema retorna o número do documento de pessoa física informado pelo signatário ao assinar o(s) documento(s) do processo.

**19.18. dadosPessoaJuridica**

Estes dados serão retornados quando signatários com tipo de assinatura eletrônica informar os dados de pessoa jurídica. Estes parâmetros terão valor null quando:

* O tipo de assinatura for com cerificado digital (ICP-Brasil ou Outros), ou
* O tipo de assinatura eletrônica e o signatário não informou os dados de pessoa jurídica, ou
* Signatário não assinou o(s) documento(s) do processo.

**19.18.1.nomeEmpresa**

O sistema retorna o nome da empresa informado pelo signatário.

**19.18.2. tipoDocumentoEmpresa**

O sistema retorna o tipo do documento de pessoa jurídica do signatário ao assinar o(s) documento(s) do processo. Este terá o valor definido no envio documento que pode ser **CNPJ** ou **Outro**. Quando o tipo do documento de pessoa jurídica for definido como **Outro**, o sistema deve exibir o nome do tipo do documento definido pelo usuário.

**19.18.3. numeroDocumentoEmpresa**

O sistema retorna o número do documento da empresa informado pelo signatário ao assinar o(s) documento(s) do processo.

**19.19. anexos**

O sistema retorna os dados de anexos quando o signatário que assinou o(s) documento(s) realizar upload de anexos, conforme a configuração do processo. Estes parâmetros terão valor null quando não houver anexos para o signatário.

**19.19.1. id**

O sistema retorna o id do anexo inserido pelo signatário.

**19.19.2. anexoDocumentoNome**

O sistema retorna o nome do anexo do signatário.

### Dados dos documentos do processo

Um processo de assinatura poder conter um ou mais documentos para serem assinados.

**20. documentos**

O sistema retorna o(s) documento(s) do processo de assinatura na ordem definida do parâmetro **"ordemDocumento"**, com seu respectivo registro de assinaturas.

**20.1. ordemDocumento**&#x20;

O sistema retorna a ordem do documento definida no momento que o processo foi enviado.

**20.2. nomeDocumento**

O sistema retorna o nome do documento.

**20.3. base64Documento**

O sistema retorna o base64 do arquivo.

**20.4. registroAssinaturas**

O sistema retorna, para cada documento do processo, o respectivo registro de assinaturas.

**20.4.1. nome**

O sistema retorna o nome do registro de assinaturas do documento. O nome do registro de assinatura deve conter o nome do documento mais a String “\_registro de assinaturas”.\
Exemplo.: Contrato de Aluguel\_Registro de assinaturas.pdf

**20.4.2. base64**

O sistema retorna o base64 do arquivo do registro de assinaturas do documento.

### Retorno - Exemplo Body Response

```

{
    "nomeProcesso": "string",
    "idPasta": "guid",
    "caminhoDaPasta": "string",
    "idResponsavel": "guid",
    "nomeResponsavel": "string",
    "status": "string",
    "dataCadastro": "datetime",
    "dataEnvio": "datetime",
    "dataConclusao": "datetime",
    "dataRenovacao": "datetime",
    "dataCancelamento": "datetime",
    "usuarioCancelamento": "string",
    "dataReenvio": "datetime",
    "dataExpiracao": "datetime",
    "expiracaoDias": "smallint",
    "avisoExpiracaoDias": "smallint",
    "lembrete": "true",
    "frequenciaLembrete": "smallint",
    "signatarios": [
        {
            "ordemAssinatura": "tinyint",
            "id": "guid",
            "nome": "string",
            "email": "string",
            "telefone": "string",
            "aguardandoEnvio": "string",
            "falhaEnvio": "string",
            "tipoAcao": "string",
            "papelSignatario": {
                "pessoaFisica": [
                    "varchar(50)",
                    "varchar(50)",
                    "varchar(50)"
                ],
                "pessoaJuridica": [
                    "varchar(50)"
                ]
            },
            "copiaEnviada": "string",
            "remetente": "string",
            "assinaturaRecusada": "string",
            "motivoRecusa": "string",
            "seguranca": {
                "codigoSeguranca": "string",
                "codigoSegurancaEmail": "string",
                "codigoSegurancaTelefone": "string"
            },
            "dadosAssinatura": {
                "tipoAssinatura": "string",
                "dataAssinatura": "datetime",
                "ip": "string",
                "geoLocalizacao": "string",
                "dadosCertificado": {
                    "nome": "string",
                    "emissor": "string",
                    "validadeInicio": "string",
                    "validadeFim": "string"
                },
                "dadosPessoaFisica": {
                    "nomePessoaFisica": "string",
                    "tipoDocumentoPessoaFisica": "string",
                    "numeroDocumetoPessoaFisica": "string"
                },
                "dadosPessoaJuridica": {
                    "nomeEmpresa": "string",
                    "tipoDocumentoEmpresa": "string",
                    "numeroDocumentoEmpresa": "string"
                },
                "anexos": [
                    {
                        "id": "guid",
                        "anexoDocumentoNome": "string"
                    }
                ]
            }
        }
    ],
    "documentos": [
        {
            "ordemDocumento": "tinyint",
            "nomeDocumento": "string",
            "base64Documento": "string base64",
            "registroAssinaturas": {
                "nome": "string",
                "base64": "string base64"
            }
        },
        {
            "ordemDocumento": "tinyint",
            "nomeDocumento": "string",
            "base64Documento": "string base64",
            "registroAssinaturas": {
                "nome": "string",
                "base64": "string base64"
            }
        }
    ]
}
```

