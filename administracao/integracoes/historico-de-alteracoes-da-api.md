# Histórico de alterações da API

## 2024

<details>

<summary>2.0.0 - 18/07/2024</summary>

Criada a versão dois (V2) dos seguintes métodos:

* [POST api/v2/processo/enviar-documento-para-assinar](https://manual.arquivar.com/manual-arqsign/administracao/integracoes/api/metodos-disponiveis-na-api/1.-processo/1.1.post-api-v2-processo-enviar-documento-para-assinar)

Nesta versão foram incluídos os parâmetros **gerarQrCode** e **obrigarLeitura**, além da opção de enviar mais de um documento no formato .pdf no processo.

* [GET /api/v2/processo/{idProcesso](https://manual.arquivar.com/manual-arqsign/administracao/integracoes/api/metodos-disponiveis-na-api/1.-processo/1.2.get-api-v2-processo-idprocesso)}

A nova versão do serviço de buscar o processo permite retornar todos os documentos do processo informado, o que não é possível com a utilização da versão 1 do serviço.

</details>
