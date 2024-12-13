---
icon: rectangle-history
---

# Histórico de alterações da API

## 2024



<details>

<summary>2.2.0 - 04/09/2024</summary>

Criada a versão dois (V2) do método:

* [PATCH api/v2/processo/reenviar-processo/{idProcesso}](api/metodos-disponiveis-na-api/patch-api-v2-processo-idprocesso-reenviar-processo.md)

Esta versão foi totalmente reestruturada permitindo que além do reenvio simples e direto de um processo, seja possível também editar dados como o tipo de envio e-mail ou WhatsApp se a conta ou tipo de assinatura assim permitir, alterar a forma de envio do código de segurança, nome do signatário, dados de assinaturas obrigatórios ou usados para validação ou preenchimento automático.

</details>

<details>

<summary>06/09/2024</summary>

Criada de nova rota para a API ArqSign.

A rota [https://api.arqsign.com/](https://api.arqsign.com/) será descontinuada a partir do dia 31/10/2024, devendo todos que usam a API ArqSIGN alterar as chamadas para a nova rota: [https://api-rest.arqsign.com/](https://restapi.arqsign.com/)

A documentação oficial da API do ArqSIGN agora está na URL: [https://developers.arqsign.com/](https://developers.arqsign.com/)

Para mais detalhes clique aqui.

</details>

<details>

<summary>2.3.0 - 31/10/2024</summary>

Foi criado em [Integrações o menu Webhoo](webhook.md)k. Seu objetivo é possibilitar ao cliente acompanhar o andamento dos processos de assinaturas dos documentos. Conforme a configuração de webhook, o usuário receberá os dados de execução dos processos por meio dos eventos/gatilhos.

</details>

<details>

<summary>2.3.1 - 11/11/2024</summary>

Foi realizada a descontinuidade da versão 1 (V1) dos métodos:

* POST/api/v1/processo/enviar-documento-para-assinar
* GET/api/v1/processo/{idprocesso}
* PATCH/api/v1/processo/{idProcesso}/reenviar-processo

Para mais detalhes, [clique aqui](api/metodos-disponiveis-na-api/).

</details>

<details>

<summary>2.4.0 - 13/11/2024</summary>

**Foi realizado um ajuste da API de buscar dados do processo.**

* [GET/api/v2/processo/{idProcesso}](https://arquivar.gitbook.io/manual-arqsign/~/changes/kWiQBotJ7NkdrQc7NWAg/administracao/integracoes/api/metodos-disponiveis-na-api/1.-processo/1.1.get-api-v2-processo-idprocesso)
  * Este serviço permite aos Clientes, via API, buscar um processo, com seus respectivos dados do processo, signatários e documentos do processo.

**Foram também disponibilizados novos métodos:**

* [POST/api/v1/processo/{idProcesso}/buscar-anexos-signatarios](https://arquivar.gitbook.io/manual-arqsign/~/changes/kWiQBotJ7NkdrQc7NWAg/administracao/integracoes/api/metodos-disponiveis-na-api/1.-processo/1.7.post-api-v1-processo-idprocesso-buscar-anexos-signatarios)
  * Este serviço permite buscar os anexos dos signatários, informando um ou mais signatários específicos do processo.

- [GET/api/v1/processo/{idArquivoProcesso}/registro-assinaturas](https://arquivar.gitbook.io/manual-arqsign/~/changes/kWiQBotJ7NkdrQc7NWAg/administracao/integracoes/api/metodos-disponiveis-na-api/1.-processo/1.8.get-api-v1-processo-idarquivoprocesso-registro-assinaturas)
  * Este serviço permite buscar o base64 do registro de assinatura de um arquivo processo.

* [POST/api/v1/diretorio/buscar-pastas](https://arquivar.gitbook.io/manual-arqsign/~/changes/kWiQBotJ7NkdrQc7NWAg/administracao/integracoes/api/metodos-disponiveis-na-api/2.-diretorios/2.1.post-api-v1-diretorio-buscar-pastas)
  * Este serviço permite buscar os dados das pastas da conta.

- [POST/api/v1/usuarios/buscar-usuarios](https://arquivar.gitbook.io/manual-arqsign/~/changes/kWiQBotJ7NkdrQc7NWAg/administracao/integracoes/api/metodos-disponiveis-na-api/3.-usuarios/3.1.post-api-v1-usuarios-buscar-usuarios)
  * Este serviço permite buscar dados dos usuários da conta.

* [GET/api/v1/conta/papeis-signatarios](https://arquivar.gitbook.io/manual-arqsign/~/changes/kWiQBotJ7NkdrQc7NWAg/administracao/integracoes/api/metodos-disponiveis-na-api/4.-conta/4.1.get-api-v1-conta-papeis-signatarios)
  * Este serviço permite buscar os papéis de signatário da conta.

- [POST/api/v1/conta/buscar-consumo-itens-assinatura](https://arquivar.gitbook.io/manual-arqsign/~/changes/kWiQBotJ7NkdrQc7NWAg/administracao/integracoes/api/metodos-disponiveis-na-api/4.-conta/4.2.post-api-v1-conta-buscar-consumo-itens-assinatura)
  * Este serviço permite buscar a quantidade do item de envios (Envios, WhatsApp, SMS) que a conta usou em determinado período.

* [GET/api/v1/conta/dados-assinatura](https://arquivar.gitbook.io/manual-arqsign/~/changes/kWiQBotJ7NkdrQc7NWAg/administracao/integracoes/api/metodos-disponiveis-na-api/4.-conta/4.3.get-api-v1-conta-dados-assinatura)
  * Este serviço permite buscar os dados de uma conta ArqSIGN.

- [PATCH/api/v1/confwebhook/{idConfWebHook}/alterar-status](https://arquivar.gitbook.io/manual-arqsign/~/changes/kWiQBotJ7NkdrQc7NWAg/administracao/integracoes/api/metodos-disponiveis-na-api/5.-webhook/5.1.patch-api-v1-confwebhook-idconfwebhook-alterar-status)
  * Este serviço permite alterar o status das configurações de webhook.

* [POST/api/v1/confwebhook](https://arquivar.gitbook.io/manual-arqsign/~/changes/kWiQBotJ7NkdrQc7NWAg/administracao/integracoes/api/metodos-disponiveis-na-api/5.-webhook/5.2.post-api-v1-confwebhook)
  * Este serviço permite cadastrar uma configuração de webhooks.

</details>

<details>

<summary>2.0.0 - 18/07/2024</summary>

Criada a versão dois (V2) dos seguintes métodos:

* [POST api/v2/processo/enviar-documento-para-assinar](https://manual.arquivar.com/manual-arqsign/administracao/integracoes/api/metodos-disponiveis-na-api/1.-processo/1.1.post-api-v2-processo-enviar-documento-para-assinar)

Nesta versão foram incluídos os parâmetros **gerarQrCode** e **obrigarLeitura**, além da opção de enviar mais de um documento no formato .pdf no processo.

* [GET /api/v2/processo/{idProcesso](https://manual.arquivar.com/manual-arqsign/administracao/integracoes/api/metodos-disponiveis-na-api/1.-processo/1.2.get-api-v2-processo-idprocesso)}

A nova versão do serviço de buscar o processo permite retornar todos os documentos do processo informado, o que não é possível com a utilização da versão 1 do serviço.

</details>
