---
description: >-
  O objetivo do método é permitir aos Clientes, via API, enviar processos com um
  ou mais documentos para assinar.
---

# ✔️ POST/api/v2/processo/enviar-documento-para-assinar

Diferente da aplicação ArqSign, que permite agrupar os arquivos do processo, neste serviço quando enviado o processo com mais de um documento, o serviço considera como **uma coleção de arquivos e estes não serão agrupados em um único arquivo**. Ou seja, não é possível agrupar arquivos pelo serviço de envio de processo de documentos para assinar.&#x20;

O usuário deve informar os dados do processo e dos destinatários participantes do processo de assinatura.

## Autenticações e permissões

1. Para autenticar na API da ArqSign, o usuário deve informar a AppKey, válida, da conta que está enviando os documentos para assinaturas.
2. Somente conta com **status Ativo** e com **permissão de Integração ArqSign** pode enviar processos via integração ArqSign.
3. A conta deve possuir créditos de Envios, SMS e/ou WhatsApp, conforme necessidade.
4.  Caso a conta não possua crédito, o sistema retorna a mensagem:

    "Saldo de créditos de Envios ou WhatsApp ou SMS insuficiente"

## Requisição: Parâmetros

**Orientações:**

Quando campo requerido estiver como “Sim” = Sempre requerido

Quando campo requerido estiver como “Não” = Informação Opcional

Quando campo requerido estiver como “Talvez” = Em alguns casos ele será requerido. Para saber estes casos, consultar a descrição do tópico, conforme o número de referência da linha na tabela.

Quando campo requerido estiver como “Não” = Informação Opcional

<figure><img src="../../../../.gitbook/assets/Pastel Simple Important points to build an attractive personal website infographic (1).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

### **Exemplo de Body Request**

```
{
   "idResponsavel": "guid",
   "nomeProcesso": "varchar(250)",
    "idPasta": "guid",
    "configuracoesAvancadas": {
        "tempoExpiracaoDocumentoDias": "smallint",
        "avisoAntesExpiracaoDocumentoDias": "smallint",
        "frequenciaLembretesDias": "smallint",
        "gerarQrCode": "bit",
        "obrigarLeitura": "bit"
    },
    "renovacaoMeses": "tinyint",
    "mensagemPadrao": {
        "titulo": "varchar(150)",
        "texto": "varchar(max)"
    },
    "usarOrdemAssinatura": "bit",
    "usarPosicaoAssinaturaAutomatica": "bit",
    "destinatarios": [
        {
            "idTipoAcao": "tinyint",
            "ordemAssinatura": "tinyint",
            "nome": "varchar(150)",
            "email": "varchar(150)",
            "telefone": "varchar(20)",
            "assinarOnline": {
                "assinarComo": "tinyint",
                "papelPessoaFisica": [
                    "varchar(50)",
                    "varchar(50)",
                    "varchar(50)"
                ],
                "papelPessoaJuridica": [
                    "varchar(50)"
                ],
                "seguranca": {
                    "codigoSeguranca": "char(4)",
                    "idMeioEnvio": "tinyint",
                    "codigoSegurancaEmail": "varchar(150)",
                    "codigoSegurancaTelefone": "varchar(20)",
                    "reenviarCodigo": "bit"
                },
                "mensagemPersonalizada": {
                    "titulo": "VarChar(150)",
                    "texto": "VarChar(max)"
                },
                "anexos": [
                    {
                        "anexoDocumentoNome": "VarChar(75)",
                        "anexoObrigatorio": "bit",
                        "anexoExibirTodosDestinatarios": "bit"
                    }
                ],
                "definirPosicaoAssinaturaManual": [
                    {
                        "documentoDeOrdem": "tinyint",
                        "pessoaFisica": {
                            "pagina": "int",
                            "altura": "decimal",
                            "largura": "decimal",
                            "posicaoX": "decimal",
                            "posicaoY": "decimal"
                        },
                        "pessoaJuridica": {
                            "pagina": "int",
                            "altura": "decimal",
                            "largura": "decimal",
                            "posicaoX": "decimal",
                            "posicaoY": "decimal"
                        }
                    }

                ],
                "idTipoAssinatura": "tinyint",
                "assinaturaEletronica": {
                    "obrigarSignatarioInformarNome": "bit",
                    "obrigarSignatarioInformarNumeroDocumento": "bit",
                    "tipoDocumentoAInformar": "tinyint",
                    "configuracaoDocumentoOutro": {
                        "nomeDocumento": "VarChar(50)",
                        "formatoDadosDocumento": "tinyint",
                        "qtdeCaracteresDocumento": "tinyint"
                    },
                    "obrigarSignatarioInformarNomeEmpresa": "bit",
                    "obrigarSignatarioInformarNumeroDocumentoEmpresa": "bit",
                    "tipoDocumentoEmpresaAInformar": "tinyint",
                    "configuracaoDocumentoEmpresaOutro": {
                        "nomeDocumento": "VarChar(50)",
                        "formatoDadosDocumento": "tinyint",
                        "qtdeCaracteresDocumento": "tinyint"
                    }
                }
            }
        }
    ],
    "documentos": [//somente pdf
        {
            "ordemDocumento": "tinyint",
            "nomeComExtensao": "varchar(150)",
            "arquivo": "String Base64"
        },
        {
            "ordemDocumento": "tinyint",
            "nomeComExtensao": "varchar(150)",
            "arquivo": "String Base64"
        }
    ]
}


```

## Descrição dos parâmetros do JSON

### idResponsavel

Parâmetro **obrigatório** informando o Id do responsável do processo. Esta informação será considerada como o responsável pelo cadastro e pelo processo, ou seja, “remetente” do processo. Desta forma, se o usuário informado autenticar na aplicação ele visualizará todos os documentos no menu “Enviados”.

Deve-se informar o id de um usuário ativo que pertence a conta.

### nomeProcesso

Parâmetro **obrigatório** informando o Nome do processo, permitindo até 250 caracteres.

### idPasta

Parâmetro obrigatório informando Id da pasta do processo.\
Deve-se informar um id de pasta que pertence a conta.

### configuracoesAvancada

Nesta parte do JSON, o usuário pode enviar as configurações avançadas para o processo em relação a tempo de expiração, aviso de expiração, frequência deste aviso, geração do QRCode e obrigatoriedade de leitura dos documentos do processo.

As configurações avançadas são **opcionais** e **caso se não sejam enviadas** ou enviadas como nula, o sistema **salva o processo com as configurações da conta em questão.**

#### **tempoExpiracaoDocumentoDias**

Parâmetro **opcional** informando o tempo em que o processo ficará disponível para assinatura, até que todos os signatários assinem e o processo seja concluído.\
São permitidos valores entre {1} e {999}

Quando este parâmetro não é enviado ou enviado como nulo ou 0, o sistema considera as configurações da conta.

#### **avisoAntesExpiracaoDocumentoDias**

Parâmetro **opcional** informando o tempo para a aplicação iniciar o aviso antes que o documento expire.\
São permitidos valores entre {1} e {99}

Quando este parâmetro não é enviado ou enviado como nulo ou 0, o sistema considera as configurações da conta.

#### **frequenciaLembretesDias:**

Parâmetro **opcional** informando o tempo para avisos de assinatura.\
São permitidos valores entre {1} e {999}

Quando este parâmetro não é enviado ou enviado como nulo ou 0, o sistema considera as configurações da conta.

#### **gerarQrCode**

Parâmetro **opcional** informando se deve gerar o QRCode  do documento assinado ou não no momento da conclusão do processo.\
Quando para o processo possuir mais de um  documento para assinatura, o QRCode será gerado por documento. Cada documento terá seu QRCode e sua página de assinatura.

É permitido informar 1 = true ou 0 = false.

Quando este parâmetro não é enviado ou enviado como nulo ou 0, o sistema considera as configurações da conta.

#### **obrigarLeitura**

Parâmetro **opcional** informando a obrigatoriedade de leitura dos documentos ao assinar.\
Quando o processo em questão possuir mais de um documento a assinar, esta informação será usada para obrigar ou não o signatário a clicar em cada documento antes do botão “Assinar” ser habilitado.\
Caso o processo possua somente um arquivo para assinar, esta informação não será necessária para o processo de assinatura.\
É permitido informar 1 = true ou 0 = false.

Quando este parâmetro não é enviado ou enviado como nulo ou 0, o sistema considera as configurações da conta.

### renovacaoMeses

Parâmetro **opcional** informando o tempo, em meses, para definir quando o processo em questão precisa ser renovado.

### mensagemPadrao

Parâmetro **opcional** informando a mensagem padrão que será enviada para todos os destinatários definidos como signatários do processo.\
Se a coleção de dados **“mensagemPadrao”** **não for enviada**, o sistema envia as notificações com os valores default:\
**Título =** ArqSign: \[Nome do documento informado no parâmento "nome"]\
**Texto =** Você recebeu o(s) documento(s): \[Nome do documento informado no paramento "nome"] para assinaturas.

#### titulo

Parâmetro **opcional** informando o Título da mensagem a ser enviada para os signatários.

**texto**

Parâmetro **opcional** informando o Texto da mensagem a ser enviada para os signatários.

### usarOrdemAssinatura

Parâmetro **obrigatório** informando se será usada ou não ordem de assinatura para os signatários.\
É permitido informar 1 = true ou 0 = false

a. Quando o parâmetro **usarOrdemAssinatura** for enviado como **false**, sistema desconsidera o valor informado no parâmetro **“ordemAssinatura”** de todos os destinatários com ação de Assinar Online e envia o processo para todos os destinatários considerando como ordem 1.

b. Quando o parâmetro **usarOrdemAssinatura** for enviado como **true**, sistema valida o parâmetro **“ordemAssinatura”** de todos os destinatários com ação de Assinar Online. Ou seja, o parâmetro **“ordemAssinatura”** dos destinatários não pode ser zero ou null.

Caso o processo tenha ordem de assinatura, o sistema envia o processo somente para os destinatários de ordem 1.

### usarPosicaoAssinaturaAutomatica

Parâmetro **obrigatório** para indicar à aplicação se o processo em questão terá a página de assinatura ao final de cada arquivo. Nesta página a aplicação escolhe automaticamente onde cada assinatura será posicionada.\
É permitido valores informar 1 = true ou 0 = false

a. Quando o parâmetro **“usarPosicaoAssinaturaAutomatica”** for **true**, então a aplicação irá **incluir uma página no final de cada arquivo, com a posição da assinatura de cada destinatário com ação de Assinar Online**, considerando o tipo de pessoa para cada signatário conforme descrito abaixo:

* Para os signatários com o parâmetro **assinarComo** = 1 (Pessoa física), significa que a aplicação ArqSign irá incluir uma página no final do arquivo com a definição automática da posição da assinatura do tipo **Pessoa Física** (PF).
* Para os signatários com o parâmetro **assinarComo** = 2 (Pessoa jurídica), significa a aplicação ArqSign irá incluir uma página no final do arquivo com a definição automática da posição da assinatura do tipo **Pessoa Jurídica** (PJ).
* Para os signatários com o parâmetro **assinarComo** = 3 (Pessoa física e jurídica), significa a aplicação ArqSign irá incluir uma página no final do arquivo com a definição automática da posição para duas assinaturas, uma do tipo **Pessoa Física** (PF) e uma do tipo **Pessoa Jurídica** (PJ).

Quando o parâmetro **“usarPosicaoAssinaturaAutomatica”** for **enviado como true** não é necessário enviar os parâmetros **definirPosicaoAssinaturaManual**. Mas se no JSON for enviado para algum signatário o parâmetro **definirPosicaoAssinaturaManual**, **a informação será ignorada neste caso.**

b. Quando o parâmetro **usarPosicaoAssinaturaAutomatica** for enviado como **false**, significa que o posicionamento das assinaturas **para cada signatário** deverá ser informado manualmente **para cada arquivo do processo** em questão. Sendo obrigatório enviar os dados do parâmetro **definirPosicaoAssinaturaManual.**

{% hint style="danger" %}
<mark style="color:red;">**Importante**</mark><mark style="color:red;">: No JSON todos os destinatários com ação de assinar online precisam ter o posicionamento da representação visual de forma automática pela aplicação ou o posicionamento para todos devem ser enviados manualmente no JSON. Não pode haver no mesmo processo alguns destinatários com posicionamento automático e outros sem posicionamento automático.</mark>
{% endhint %}

### destinatários

#### idTipoAcao

Parâmetro **obrigatório** que define a ação do destinatário para com o documento. Atualmente existem duas opções **1 - Assinar Online** ou **2 - Receber uma cópia.**\
É permitido informar 1 - Assinar Online ou 2 - Receber uma cópia.

&#x20;a. É obrigatório informar para o processo de assinaturas, ao menos um destinatário com ação de **“Assinar Online”.**

#### ordemAssinatura

Parâmetro que define a ordem de assinatura do signatário em questão.\
\
**a.** Quando o parâmetro **“usarOrdemDeAssinatura”** estiver sendo enviado como **True = 1** e o destinatário em questão possuir o parâmetro **idTipoAcao = 1 (Assinar Online)**, então esta informação é obrigatória.

A **ordemAssinatura** não deve ser enviada no JSON ou será desconsiderada quando:\
\- **idTipoAcao = 2 (Receber uma cópia).**\
\- **usarOrdemDeAssinatura = 0 (fase)** e signatários com **idTipoAcao = 1 (AssinarOnline).**

**b.** A aplicação **não permite mesmo destinatário na mesma ordem de assinatura.** Para verificar se o destinatário é o mesmo, verifica se o email ou o telefone usado como forma de envio para o documento se repetem na mesma ordem de assinatura.

#### nome

Parâmetro **obrigatório** informando o nome do destinatário que assinará o documento ou receberá uma cópia.

**a.** O sistema valida a obrigatoriedade e o tamanho do nome do signatário.

#### email

Parâmetro informando o email onde o destinatário receberá o documento.

**Formato**: Varchar(150)\
**Requerido: Email ou Telefone são obrigatórios**

**Validação**:

**a.** O sistema valida a **obrigatoriedade** do e-mail ou telefone. \
Quando não for enviado nenhum e-mail ou telefone a aplicação valida os dados exibindo a mensagem: O parâmetro **email** ou **telefone** é obrigatório.

**b.** Somente é permitido **e-mail válido.**

**c.** Somente **é permitido informar e-mail ou telefone.**\
Quando o usuário informar os dois campos, o sistema retorna a mensagem: Somente é possível enviar o processo para um e-mail ou telefone. Escolha uma forma de envio.

#### telefone

Parâmetro informando o telefone onde o destinatário receberá o documento. Enviando o número do telefone, significa que o documento será enviado por **WhatsApp.**

**a.** O sistema valida a **obrigatoriedade** do e-mail ou telefone.\
Quando não for enviado nenhum e-mail ou telefone a aplicação valida os dados exibindo a mensagem: O parâmetro **email ou telefone** é obrigatório.

**b.** Sistema **valida** o telefone informado.

**c.** Somente **é permitido informar e-mail ou telefone**.\
Quando o usuário informar os dois campos, o sistema retornar a mensagem: Somente é possível enviar o processo para um e-mail ou telefone. Escolha uma forma de envio.

**d.** Somente é possível enviar processo por WhatsApp, quando o destinatário atender a um dos requisitos abaixo:\
**1.** For assinar o documento eletronicamente idTipoAcao = **1 (Assinar Online) e idTipoAssinatura = 1 (Assinatura Eletrônica)**\
**2.** For receber uma cópia: **idTipoAcao = 2 (Receber uma cópia)**

### **assinarOnline**

Esta parte do JSON deve ser enviada somente para os destinatários com **idTipoAcao = 1 (Assinar Online).** Caso seja enviado para destinatário com o **idTipoAcao = 2 (Receber Cópia)**, estes dados serão ignorados.

#### **assinarComo**

Parâmetro **obrigatório** que indica se o signatário, com o **idTipoAcao = 1 (Assinar Online)**, assinará como pessoa física, pessoa jurídica ou ambos.\
É permitido informar 1 = Pessoa Física ou 2 = Pessoa Jurídica ou 3 = Pessoa Física e Jurídica.

#### papelPessoaFisica

Parâmetro **opcional** para enviar os papeis do signatário em relação a assinatura de pessoa física que ele realizará.

**a.** O parâmetro de **papelPessoaFisica é opcional**, mas quando informado o sistema verifica **se a conta possui o papel do signatário informado.**\
Usuário poderá informar null ou não informar este parâmetro no JSON.

Se o **papelPessoaFisica** for enviado para um signatário com o parâmetro **“assinarComo”** = 2 (Pessoa Jurídica), então esta informação é desconsiderada.

#### papelPessoaJurídica

Parâmetro **opcional** para enviar os papeis do signatário em relação a assinatura de pessoa jurídica que ele realizará.

**a.** O parâmetro de **papelPessoaJuridica é opcional,** mas quando informado o sistema verifica **se a conta possui o papel do signatário informado.**\
Usuário poderá informar null ou não informar estes parâmetros no JSON.

Se o **papelPessoaJuridica** for enviado para um signatário com o parâmetro **“assinarComo”** = 1 (Pessoa Física), então esta informação é desconsiderada.

#### seguranca

Esta parte do JSON é **opcional**, deverá ser enviada somente se houver a necessidade de exigir do signatário, em questão, um código de segurança para iniciar o processo de assinatura.

1. **codigoSeguranca**\
   Código de segurança a ser exigido ao signatário que irá assinar o documento. Esta informação precisa ser numérica com 4 caracteres.
2.  **idMeioEnvio**\
    Parâmetro para informar como o código de segurança será enviado ao signatário em questão.

    Este parâmetro somente será exigido caso seja enviado o parâmetro **codigoSeguranca** e somente é permitido valores iguais 1 = SMS (Somente Brasil), 2 = WhatsApp, 3 = Email ou 4 = Não enviar.&#x20;

    O sistema desconsidera a informação desse parâmetro caso o **codigoSeguranca** = null.
3.  **codigoSegurancaEmail**\
    Email onde o signatário deverá receber o código de segurança definido no parâmetro **codigoSeguranca.**&#x20;

    **a.** O parâmetro **codigoSegurancaEmail** é obrigatório quando o parâmetro **idMeioEnvio** for igual a **3.**

    **b.** A aplicação valida se a informação enviada é um e-mail.&#x20;

    Caso este parâmetro seja enviado quando idMeioEnvio <> 3, o sistema ignora a informação.

    O sistema desconsidera a informação desse parâmetro caso o **codigoSeguranca** = null.
4.  **codigoSegurancaTelefone**\
    Telefone onde o signatário deverá receber o código de segurança definido no parâmetro **codigoSeguranca.**

    **a.** O parâmetro **codigoSegurancaTelefone** é obrigatório quando o parâmetro **idMeioEnvio** for igual a **1** ou **2.**

    Quando idMeioEnvio = 1 (SMS), será aceito somente números do Brasil.

    Sistema valida o telefone informado.

    Caso este parâmetro seja enviado quando idMeioEnvio = 3 ou 4, o sistema ignora a informação.

    O sistema desconsidera a informação desse parâmetro caso o **codigoSeguranca** = null.
5.  **reenviarCodigo**\
    Informação que define se o signatário poderá reenviar o código de segurança para o seu telefone via SMS ou WhatsApp conforme definição no parâmetro idMeioEnvio.

    Quando não informado o parâmetro **reenviarCodigo** no JSON, o serviço considera como false.

    É permitido informar 1 = True ou 0 = False

    **a.** Este parâmetro somente é obrigatório quando o código de segurança for enviado por SMS ou WhatsApp.

    Caso este parâmetro seja enviado quando idMeioEnvio = 3 ou 4 ele é desconsiderado.

#### mensagemPersonalizada

Esta parte do JSON é **opcional** e deverá ser enviada somente se para o signatário em questão for necessário enviar uma mensagem personalizada. Se for enviado o título da mensagem será necessário enviar o texto e vice e versa.

1.  **titulo**\
    Título da mensagem personalizada a ser enviada para o signatário em questão. Os signatários com mensagem personalizada não recebem a **mensagemPadrao.**

    **a.** O parâmetro **mensagemPersonalizada** não é obrigatório, mas quando enviado o “titulo” a aplicação deve exigir o texto e vice e versa.
2.  **texto**\
    Título da mensagem personalizada a ser enviada para o signatário em questão. Os signatários com mensagem personalizada não recebem a **mensagemPadrao.**

    **a.** O parâmetro **mensagemPersonalizada** não é obrigatório, mas quando enviado o “titulo” a aplicação deve exigir o texto e vice e versa.

#### anexos

Esta parte do JSON é **opcional** e deverá ser enviada somente se para o signatário em questão for necessário solicitar o upload de algum arquivo no momento da assinatura. Se qualquer um dos parâmetros abaixo for enviado, será exigido os três.

Se qualquer um dos parâmetros, abaixo, for enviado, será exigido os três: **anexoDocumentoNome, anexoObrigatorio** e **anexoExibirTodosDestinatarios.**

1.  **anexoDocumentoNome**\
    Nome do anexo que será solicitado ao signatário no momento da assinatura dos documentos.

    É permitido informar até 75 caracteres.
2.  **anexoObrigatorio**\
    Informação para a aplicação exigir do signatário o upload do arquivo no ato da assinatura do documento.

    É permitido informar 1 = true ou 0 = false
3.  **anexoExibirTodosDestinatarios**\
    Informação para a aplicação **exibir o anexo que foi enviado pelo signatário para todos os outros destinatários com ação de assinar ou não.** Se o anexo a ser enviado exige um grau de sigilo, então esta informação deve ser enviada como false.

    É permitido informar 1 = true ou 0 = false

#### definirPosicaoAssinaturaManual

Esta parte do JSON é obrigatória somente se o parâmetro **usarPosicaoAssinaturaAutomatica** igual a **false**.\
Quando o parâmetro **usarPosicaoAssinaturaAutomatica** é enviado igual a **false**, significa que no JSON **deverá ser enviado o posicionamento manual das assinaturas de todos os destinatários com ação de Assinar Online em cada arquivo do processo.** Ou seja, é obrigatório definir a posição da assinatura manualmente **(definirPosicaoAssinaturaManual)** para cada destinatário em cada arquivo **(documentoDeOrdem)** conforme o valor definido no parâmetro **assinarComo** (1 = Pessoa Física ou 2 = Pessoa Jurídica ou 3 = Pessoa Física e Jurídica) \
\
Quando o parâmetro **usarPosicaoAssinaturaAutomatica** é enviado como **true**, as informações de posicionamento manual da assinatura de todos os signatários **serão desconsideradas**. Desta forma será incluída **uma página no final de cada documento com a posição da assinatura de cada destinatário com ação de Assinar Online.**\
\
O sistema valida se o posicionamento manual das assinaturas está no limite da página informada.\
O sistema valida as representações manuais informadas para os destinatários não permitindo a mesma representação manual por tipo de assinatura no mesmo documento **(parâmetro documentoDeOrdem)**.

#### documentoDeOrdem

Quando o **processo** de assinatura que está sendo enviado no JSON possuir mais de um arquivo para assinatura, este campo será usado para identificar o arquivo ao qual o posicionamento da assinatura que está sendo descrita nos parâmetros a seguir se referem.

Se o processo de assinatura possuir somente um arquivo a ser assinado, este campo se torna desnecessário e será desconsiderado quando enviado. \
**a.** Este parâmetro é obrigatório sempre que no processo existir mais de um arquivo a ser assinado.\
**b.** O sistema valida se existe o documento da ordem informada no parâmetro **“documentoDeOrdem”**

#### pessoaFisica

Os parâmetros abaixo indicarão o posicionamento da assinatura de pessoa física para o signatário em questão, no arquivo identificado em **documentoDeOrdem** e serão obrigatórios quando os parâmetros **usarPosicaoAssinaturaAutomatica** = **false** e **assinarComo** = **1 (PF) ou 3 (PF e PJ).**&#x20;

Quando o parâmetro **assinarComo = 2 (PJ)**, estes dados serão desconsiderados.\
Os parâmetros abaixo indicarão o posicionamento da assinatura de pessoa física para o signatário em questão, para o arquivo identificado em **documentoDeOrdem.**

1.  **pagina**\
    Esta informação é a página do arquivo onde a posição da assinatura será inserida. É **obrigatória** quando **usarPosicaoAssinaturaAutomatica** = **false** e **assinarComo = 1 (PF) ou 3 (PF e PJ).**

    **a.** Esta informação não pode ser zero nem nula.

    **b.** A aplicação valida se a página informada existe no arquivo em questão.
2.  **altura**\
    Altura em milímetros do tamanho da caixa onde a assinatura será aplicada. É **obrigatória** quando **usarPosicaoAssinaturaAutomatica** = **false** e **assinarComo** **= 1 (PF) ou 3 (PF e PJ).**

    É permitido informar valor decimal.

    **a.** Esta informação não pode nula.
3.  **largura**\
    Largura em milímetros do tamanho da caixa onde a assinatura será aplicada. É **obrigatória** quando **usarPosicaoAssinaturaAutomatica** **= false** e **assinarComo = 1 (PF) ou 3 (PF e PJ).**

    É permitido informar valor decimal.

    **a.** Esta informação não pode nula.
4.  **posicaoX**\
    **Descrição:** Posição em milímetros da borda esquerda da página até a borda esquerda da caixa de assinatura.

    É **obrigatória** quando **usarPosicaoAssinaturaAutomatica = false** e **assinarComo = 1 (PF) ou 3 (PF e PJ).**

    É permitido informar valor decimal.

    **a.** Esta informação não pode ser nula.
5.  **posicaoY**\
    **Descrição**: Posição em milímetros da borda superior da página até a borda superior da caixa de assinatura.

    É **obrigatória** quando **usarPosicaoAssinaturaAutomatica = false** e **assinarComo = 1 (PF) ou 3 (PF e PJ).**

    É permitido informar valor decimal.

    **a.** Esta informação não pode nula.

#### pessoaJuridica

Os parâmetros abaixo indicarão o posicionamento da assinatura de pessoa jurídica para o signatário em questão, no arquivo identificado em **documentoDeOrdem** e serão obrigatórios quando os parâmetros **usarPosicaoAssinaturaAutomatica = false** e **assinarComo =  2 (PJ) ou 3 (PF e PJ).**

Quando o parâmetro **assinarComo = 1 (PF)**, estes dados serão desconsiderados.

1.  **pagina**\
    Esta informação é a página do arquivo onde a posição da assinatura será inserida. É **obrigatória** quando **usarPosicaoAssinaturaAutomatica = false** e **assinarComo = 2 (PJ) ou 3 (PF e PJ)**.

    **a.** Esta informação não pode ser zero nem nula.

    **b.** A aplicação valida se a página informada existe no arquivo em questão.
2.  **altura**\
    Altura em milímetros do tamanho da caixa onde a assinatura será aplicada. É **obrigatória** quando **usarPosicaoAssinaturaAutomatica = false** e **assinarComo = 2 (PJ) ou 3 (PF e PJ).**

    É permitido informar valor decimal.

    **a.** Esta informação não pode ser zero nem nula.
3.  **largura**\
    Largura em milímetros do tamanho da caixa onde a assinatura será aplicada. É **obrigatória** quando **usarPosicaoAssinaturaAutomatica = false** e **assinarComo = 2 (PJ) ou 3 (PF e PJ).**

    É permitido informar valor decimal.

    **a**. Esta informação não pode ser zero nem nula.
4.  **posicaoX**\
    Posição em milímetros da borda esquerda da página até a borda esquerda da caixa de assinatura. É **obrigatória** quando **usarPosicaoAssinaturaAutomatica = false** e **assinarComo = 2 (PJ) ou 3 (PF e PJ).**

    É permitido informar valor decimal.

    **a**. Esta informação não pode ser zero nem nula.
5.  **posicaoY**\
    **Descrição:** Posição em milímetros da borda superior da página até a borda superior da caixa de assinatura. . É obrigatória quando **usarPosicaoAssinaturaAutomatica = false** e **assinarComo = 2 (PJ) ou 3 (PF e PJ).**

    É permitido informar valor decimal.

    **a.** Esta informação não pode ser zero nem nula.

#### idTipoAssinatura

Definição do tipo de assinatura que será exigida ao signatário que pode ser: **1 = Assinatura Eletrônica, 3 = Certificado Digital ICP Brasil** ou **4 = Certificado Digital Outros.**\
**a.** Esta informação é obrigatória para todos os signatários com parâmetro idTipoAcao = 1 (Assinar Online).\
**b.** A aplicação permite somente os valores 1,3 ou 4.

#### assinaturaEletronica

Esta parte do JSON somente é **obrigatória** para os signatários com **idTipoAssinatura = 1** (Assinatura Eletrônica).

*   **obrigarSignatarioInformarNome**\
    Informação para a aplicação obrigar o signatário em questão informar seu nome.

    É permitido informar 1 = True ou 0 = False.

    **a.** Esta informação é obrigatória para todos os signatários com idTipoAssinatura = 1 (Assinatura Eletrônica).
*   **obrigarSignatarioInformarNumeroDocumento**\
    Informação para a aplicação obrigar o signatário em questão informar o número de seu documento.

    É permitido informar 1 = True ou 0 = False.

    **a.** Esta informação é obrigatória para todos os signatários com idTipoAssinatura = 1 (Assinatura Eletrônica).
*   **tipoDocumentoAInformar**\
    Tipo de documento que o signatário deverá informar no momento da assinatura, permitindo os valores: **1 = CPF**, **2 = CNH**, **3 = RH** ou **4 = Outro**.

    **a.** Esta informação é obrigatória para todos os signatários com idTipoAssinatura = 1 (Assinatura Eletrônica).

    **b.** Quando informado, o sistema valida o parâmetro **tipoDocumentoAInformar** permitindo somente os valores:  1 = CPF, 2 = CNH, 3 = RH ou 4 = Outro.
* **configuracaoDocumentoOutro**\
  Esta parte do JSON somente **é obrigatória** quando o **tipoDocumentoAInformar** for igual a **4 = Outro**. Nesta parte é possível definir os parâmetros do documento que será solicitado ao signatário a informação, no ato da assinatura.
  1.  **nomeDocumento**\
      Nome do documento que será exibido ao signatário no momento da assinatura dos documentos.

      É permitido informar valores com até 50 caracteres
  2. **formatoDadosDocumento**\
     Formato de dados que será exigido no campo de documento, permitindo o valor 1 = Texto ou 2 = Numérico.
  3. **qtdeCaracteresDocumento**\
     Quantidade de caracteres que serão exigidos no campo documento.
*   **obrigarSignatarioInformarNomeEmpresa**\
    Informação para a aplicação obrigar o signatário em questão informar o nome da empresa (pessoa jurídica).

    É permitido informar 1 = True ou 0 = False.

    **a.** Esta informação é obrigatória para os signatários quando parâmetros idTipoAssinatura  = 1 (Assinatura Eletrônica) e assinarComo seja igual a 2 = Pessoa Jurídica ou 3 = Pessoa Física e Jurídica.
*   **obrigarSignatarioInformarNumeroDocumentoEmpresa**\
    Informação para a aplicação obrigar o signatário em questão informar o documento da empresa (pessoa jurídica).

    É permitido informar 1 = True ou 0 = False.

    **a.** Esta informação é obrigatória para os signatários quando parâmetros idTipoAssinatura  = 1 (Assinatura Eletrônica) e assinarComo seja igual a 2 = Pessoa Jurídica ou 3 = Pessoa Física e Jurídica.
*   **tipoDocumentoEmpresaAInformar**\
    Tipo de documento que o signatário deverá informar para a empresa.

    É permitido informar 4 = Outro ou 5 = CNPJ.

    **a.** Esta informação é obrigatória para os signatários quando parâmetros idTipoAssinatura  = 1 (Assinatura Eletrônica) e assinarComo seja igual a 2 = Pessoa Jurídica ou 3 = Pessoa Física e Jurídica.

    **b.** Quando informado, o sistema validr o parâmetro **tipoDocumentoEmpresaAInformar** permitindo somente os valores:  4 = Outro ou 5 = CNPJ.
*   **configuracaoDocumentoEmpresaOutro**\
    Esta parte do JSON somente é **obrigatória quando** o **tipoDocumentoEmpresaAInformar** **for igual a 4 = Outro.**

    Nesta parte é possível definir os parâmetros do documento que será solicitado ao signatário a informação, no ato da assinatura.

    1.  **nomeDocumento**\
        Nome do documento que será exibido ao signatário como documento da empresa, permitindo informar até 50 caracteres.

        **a.** Esta informação é obrigatória para todos os signatários com tipoDocumentoEmpresaAInformar = 4 (Outro).
    2.  **formatoDadosDocumento**\
        Formato de dados que será exigido no campo de documento da empresa, permitindo informar 1 = Texto ou 2 = Numérico

        a. Esta informação é obrigatória para todos os signatários com tipoDocumentoEmpresaAInformar = 4 (Outro).
    3.  **qtdeCaracteresDocumento**\
        Quantidade de caracteres que serão exigidos no campo documento.

        a. Esta informação é obrigatória para todos os signatários com tipoDocumentoEmpresaAInformar = 4 (Outro). &#x20;

### documentos

**a.** Esta parte do JSON é **obrigatória, sendo necessário enviar pelo menos um arquivo.**

**b.** É permitido enviar até 25 arquivos por processo.

**c.** A soma do tamanho destes arquivos não pode ultrapassar a **100MB**.

**d.** Somente é permitido arquivo do tipo PDF.

#### ordemDocumento

Quando estiver sendo enviado mais de um arquivo no processo, será necessário definir a ordem com que estes arquivos serão listados na tela para o signatário assinar. Esta ordem também será usada para relacionar o posicionamento da assinatura do signatário no arquivo em questão. Ver parâmetro **documentoDeOrdem.**\
**a.** Para processo com mais de um arquivo o parâmetro **ordemDocumento** é obrigatório em cada documento.\
**b.** Não é permitido arquivos com mesma ordem.\
**c.** Quando estiver sendo enviado mais de um arquivo, eles serão considerados como uma coleção de arquivos para o processo em questão, **não serão mergeados,** ou seja, agrupados em um único arquivo.\
Não é possível agrupar arquivos pelo serviço de envio de processo de documentos para assinar.

#### nomeComExtensao

Parâmetro **obrigatório** para informar o Nome do arquivo com sua extensão, permitindo até 150 caracteres.\
**a.** A aplicação **não permite** arquivos com nomes iguais em um mesmo processo.

#### arquivo

Parâmetro **obrigatório** para informar o arquivo PDF no formato base64.\
**a.** É obrigatório enviar pelo menos um arquivo. Ele precisa ser enviado no formato PDF.



## Retorno Validações

### Erro: 400 - Bad Request

Este erro é retornado quando não for possível interpretar a requisição e/ou o servidor tenta processar a solicitação, mas algum parâmetro da solicitação não é válido, por exemplo, um recurso formatado incorretamente ou uma tentativa de requisição com dados faltantes. As informações sobre a solicitação são fornecidas no corpo da resposta e incluem um código de erro e uma mensagem de erro.

**a.** **Item obrigatório**: Esta mensagem é exibida no singular ou plural quando um ou mais itens obrigatórios não tiver sido enviado na chamada da API.

**O(s) item(ns) listado(s) é(são) obrigatório(s): “nome dos itens separados por vírgula”.**

**b. Formato incorreto:** Esta mensagem é exibida no singular ou plural quando um ou mais itens estiverem sido enviados com formato incorreto.

&#x20;**O(s) item(ns) listado(s) está(ão) com o formato incorreto: “nome dos itens separados por vírgula”.**

**c. Ids inexistente:** Esta mensagem é exibida no singular ou plural quando um ou mais Id enviado não existir.

&#x20;**O(s) id(s) listado(s) não existe(m): “nome dos itens que são Ids de tabela, separados por vírgula”.**

**d. Algum parâmetro está incorreto ou é inexistente:** Esta mensagem é exibida quando a chamada é feita com algum parâmetro escrito errado ou quando é enviado uma informação que não existe no método.

**Algum parâmetro está incorreto ou é inexistente.**

### Erro:  401 - Unauthorized

Este erro é retornado quando

* A chave de autenticação da API ArqSign está incorreta ou não foi informada corretamente.
* Conta está com status diferente de Ativo.

### Erro: 404 - Not Found

Este erro é retornado quando o recurso solicitado ou o _endpoint_ não foi localizado.

### Erro: 422 - Unprocessable

Este erro é retornado quando a requisição foi recebida com sucesso, porém contém parâmetros inválidos.

### Erro: 500 - Server Error

Este erro é retornado quando:

* Ocorre um erro interno no servidor.
* Ocorre uma falha na plataforma ArqSign.
* Formato do parâmetro incorreto.        &#x20;
* Formato do JSON incorreto.



## Retorno Sucesso

Ao executar o envio do processo com sucesso, o sistema retorna o id do processo e o(s) id(s) do(s) documento(s) do processo.

Code 200 – OK

### Retorno - Exemplo Body Response

```
{
    "IdProcesso": "guid",
    "documentos": [
        {
            "id": "guid",
            "nome": "string"
        },
        {
            "id": "guid",
            "nome": "string"
        }
    ]
}

```

#### idProcesso

O sistema retorna o id do processo criado.

#### documentos

Neste objeto o sistema retorna os  id’s e o nomes dos documentos do processo.\
Um processo por ter uma ou mais documentos.

#### idDocumento

O sistema retorna o id do documento do processo.

#### nomeDocumento

O sistema retorna o nome do documento do processo criado.
