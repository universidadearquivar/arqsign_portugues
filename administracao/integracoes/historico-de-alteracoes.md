# 🔳 Histórico de alterações

## 2024

<details>

<summary>2.3.0 - 31/10/2024</summary>

Foi criado em [**Integrações o menu Webhook**](webhook.md). Seu objetivo é possibilitar ao cliente acompanhar o andamento dos processos de assinaturas dos documentos. Conforme a configuração de webhook, o usuário receberá os dados de execução dos processos por meio dos eventos/gatilhos.

</details>

<details>

<summary>06/09/2024</summary>

Criada de nova rota para a API ArqSign.

A rota [https://api.arqsign.com/](https://api.arqsign.com/) será descontinuada a partir do dia **31/10/2024**, devendo todos que usam a API ArqSIGN alterar as chamadas para a nova rota: [https://api-rest.arqsign.com/](https://restapi.arqsign.com/)

**A documentação oficial da API do ArqSIGN agora está na URL:** [**https://developers.arqsign.com/**](https://developers.arqsign.com/)&#x20;

Para mais detalhes [**clique aqui.**](api/url-da-api-arqsign.md#nova-rota-https-api-rest.arqsign.com)

</details>

<details>

<summary>2.2.0 - 04/09/2024</summary>

Criada a versão dois (V2) do método:

* [**PATCH api/v2/processo/reenviar-processo/{idProcesso}**](api/metodos-disponiveis-na-api/patch-api-v2-processo-idprocesso-reenviar-processo.md)

Esta versão foi totalmente reestruturada permitindo que além do reenvio simples e direto de um processo, seja possível também editar dados como o tipo de envio e-mail ou WhatsApp se a conta ou tipo de assinatura assim permitir, alterar a forma de envio do código de segurança, nome do signatário, dados de assinaturas obrigatórios ou usados para validação ou preenchimento automático.

</details>

<details>

<summary>2.1.0 - 05/08/2024</summary>

Foi criado em [**Integrações o menu API**](api/). Seu objetivo é disponibilizar ao cliente a(s) chave(s) de acesso que será(ão) utilizada(s) para gerenciamento e controle das requisições via API.

</details>

<details>

<summary>2.0.0 - 18/07/2024</summary>

Criada a versão dois (V2) dos seguintes métodos:

* [**POST api/v2/processo/enviar-documento-para-assinar** ](https://arquivar.gitbook.io/manual-arqsign-2.0.0/administracao/integracoes/metodos-disponiveis-na-api/post-api-v2-processo-enviar-documento-para-assinar)

Nesta versão foram incluídos os parâmetros **gerarQrCode** e **obrigarLeitura**, além da opção de enviar mais de um documento no formato .pdf. Agora é possível enviar até 25 arquivos por processo.

* [**GET /api/v2/processo/{idProcesso}** ](https://arquivar.gitbook.io/manual-arqsign-2.0.0/administracao/integracoes/metodos-disponiveis-na-api/get-api-v2-processo-idprocesso)

A nova versão do serviço de buscar o processo permite retornar todos os documentos do processo informado, o que não é possível com a utilização da versão 1 do serviço.&#x20;

</details>

<details>

<summary>1.17.0 - 07/02/2024</summary>

Assinar Documento: Sistema apresentava erro ao tentar assinar documento que foi enviado pela API.

O sistema plotava a representação visual em posicionamento incorreta em documentos enviados pela API com posição manual.&#x20;

</details>

***

## 2023

<details>

<summary>1.15.6 - 13/12/2023</summary>

Na tela do menu Integrações da Plataforma ArqSign:

1. Removido o link: Treinamento
2. Alterado a palavra "Manual do Usuário" para "Documentação API"
3. Alterado o link de "Documentação API" para o link: https://arquivar.gitbook.io/manual-arqsign/administracao/integracoes.

</details>

<details>

<summary>1.15.3 - 13/11/2023</summary>

API > Validar Email CTG: Sistema retornava erro 404 para alguns domínios.

</details>

<details>

<summary>1.15.2 - 02/11/2023</summary>

API e-commerce - Comprar Créditos: Ajustado o serviço e comprar créditos (/api/v1/compras/comprar-creditos) para receber os dados fiscais e endereço da conta.

</details>

<details>

<summary>1.14.0 - 03/10/2023</summary>

API > Enviar Documento para Assinar: Sistema não desconsiderava posição manual quando informado valor no parâmetro de página automática.

</details>

<details>

<summary>1.13.5 - 19/09/2023</summary>

O sistema exibia a senha do certificado no payload do endpoint api/v1/certificados/validar-certificado-selecionado.

</details>

<details>

<summary>1.13.4 - 18/08/2023</summary>

API ArqSign > Dados do Processo: Sistema apresentava informação de recusa da assinatura para todos os signatários. O correto é apresentar a informação nos dados do signatário quem recusou a assinatura do documento.

</details>

<details>

<summary>1.13.3 - 02/08/2023</summary>

API > Notificação: Aplicação estava apresentando o nome da conta no lugar do nome do documento, na notificação enviada para assinatura do documento.

</details>

<details>

<summary>1.13.0 - 27/06/2023</summary>

Integrações : Incluídos os links do manual e de treinamento da API ArqSign.

</details>

<details>

<summary>1.12.3 - 26/05/2023</summary>

API > Enviar Documento para Assinar: Sistema não enviava o documento com definição e página automática.

</details>

<details>

<summary>1.12.2 - 25/05/2023</summary>

API: Sistema não aplica representação visual no documento para destinatários que deveriam ter representação em página automática.

</details>

<details>

<summary>1.11.1 - 02/05/2023</summary>

API > Enviar documento para assinar: Sistema enviava documento pela API quando não existe representação visual do tipo PJ e existe configuração de Razão Social e Documento PJ como obrigatório.&#x20;

API > Enviar documento para assinar: Sistema validava posição de assinatura para destinatário com ação de receber uma cópia.&#x20;

API > Enviar documento para assinar: Sistema gerava marcação para assinatura na página automática para destinatário com ação de receber uma cópia.

</details>

<details>

<summary>1.9.8 - 04/04/2023</summary>

Correção das descrições dos serviços API.

</details>

<details>

<summary>1.9.7 - 30/03/2023</summary>

\[API] Enviar documento para assinar: Aplicação não valida quando são enviados parâmetros para posição automática e manual para representação visual, retornando status 200.

Assinar documento: Ao assinar um documento pelo Whatsapp, que foi enviado pela API, o sistema plota informação incorreta juntamente com a representação visual, apresentando o número de telefone do signatário no campo e-mail.

Assinar documento: Ao assinar um documento com assinatura eletrônica, que foi enviado pela API, o sistema não plota informação do certificado vinculado a assinatura.

</details>

<details>

<summary>1.9.4 - 14/03/2023</summary>

Assinar documento: Correção no loop gerado durante a assinatura, com Certificado Digital, de um documento enviado via API.

</details>

<details>

<summary>1.9.3 - 23/02/2023</summary>

API para enviar documento para assinar: não estava sendo validado a forma de envio para salvar o contato do signatário.

</details>

***

## 2022

<details>

<summary>1.8.1 - 16/11/2022</summary>

API > Enviar documento: Sistema permitia envia documento o mesmo e-mail na mesma ordem de assinatura.

</details>

<details>

<summary>1.6.4 - 03/06/2022</summary>

Ajuste na API de Compra: No recebimento dos dados de compra, vindos do e-commerce, quando o país era diferente do Brasil, o sistema obrigava que Tipo Pessoa, CPF/CNPJ e CEP fossem informados. Após o ajuste, estes dados não são mais obrigatórios quando país for diferente do Brasil.

</details>

<details>

<summary>1.3.0 - 04/01/2022</summary>

Incluímos mais validações de segurança na API que o e-commerce chama no ArqSign.

</details>
