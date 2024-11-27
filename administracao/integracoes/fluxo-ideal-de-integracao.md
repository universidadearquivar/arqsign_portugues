---
icon: arrow-progress
---

# Fluxo Ideal de Integração

O fluxo ideal de integração ArqSIGN deve combinar o uso da API ArqSIGN + Webhook ArqSIGN. &#x20;

Desta forma, para a melhor automatização possível, é importante configurar dois Webhooks, um para acompanhamento e outro para conclusão:&#x20;

## Webhook de Acompanhamento&#x20;

O objetivo do webhook de acompanhamento é manter o seu sistema atualizado quanto as principais ações relacionadas ao documento além de indicar momentos importantes para se chamar outras APIs ArqSIGN. &#x20;

Observe abaixo, que no retorno do webhook de acompanhamento sugerimos não incluir nenhum dado de documento, porque enquanto o processo não é concluído, é desnecessário ficar trafegando arquivos que podem ser muito grandes. &#x20;

### Gatilhos

* Processo assinado por algum signatário&#x20;
* Processo com falha de envio&#x20;
* Processo recusado por algum signatário&#x20;
* Processo cancelado pelo remetente&#x20;
* Processo expirado&#x20;

### Retorno

* Dados do processo
* Signatários

## Webhook de Conclusão&#x20;

O objetivo do webhook de conclusão é enviar ao seu sistema o arquivo assinado por todos os signatários. Neste momento pode ser enviado o Base64 ou o link tanto do arquivo assinado quanto do seu registro de assinatura. O mundo ideal é o webhook enviar ao seu endpoint a URL destes arquivos, e a sua aplicação manipular esta URL para realizar o download. Mas se isso não for possível, o webhook pode ser configurado para enviar o Base64.&#x20;

### Gatilhos

* Processo assinado/concluído por todos os signatários&#x20;

### Retorno

* Dados do processo&#x20;
* Signatários&#x20;
* Documentos&#x20;
  * Arquivos do processo: Link para baixar arquivo&#x20;
  * Link dos documentos compartilhados&#x20;
  * Registro de assinatura: Link para baixar o arquivo&#x20;

Com os dois Webhooks acima configurados, será possível implementar o fluxo de integração abaixo:

<figure><img src="../../.gitbook/assets/Fluxo Ideal de Integração ArqSIGN + Webhook.png" alt=""><figcaption><p>Clique na imagem para ampliar</p></figcaption></figure>

## Detalhamento do fluxo

1. **Envio de Documento aos Signatários**&#x20;

Nesta fase o Cliente deverá implementar a chamada do método POST responsável por enviar o documento a ser assinado na Plataforma ArqSIGN.&#x20;

**Método:**&#x20;

> **Nome:** Enviar processo de assinaturas V2.&#x20;
>
> **URL:** POST [https://api-rest.arqsign.com/api/v2/processo/enviar-documento-para-assinar](https://api-rest.arqsign.com/api/v2/processo/enviar-documento-para-assinar)&#x20;
>
> **Documentação:** [https://developers.arqsign.com/api-details#api=api-rest-arqsign\&operation=6734bb1a4640eeaf71857525](https://developers.arqsign.com/api-details#api=api-rest-arqsign\&operation=6734bb1a4640eeaf71857525)&#x20;

2. **Acompanhamento: Falha**&#x20;

Quando houver alguma falha na entrega dos documentos a serem assinados para algum signatário, a aplicação ArqSIGN acionará o Webhook que irá chamar o serviço (URL) do Cliente conforme configurado.&#x20;

Após este retorno do Webhook o Cliente poderá implementar a chamada do método PATCH responsável por reenviar o processo. Este método pode ser usado para editar a forma de envio para os signatários que tiveram falha na entrega.&#x20;

**Método:**&#x20;

> **Nome:** Editar e Reenviar o processo para os destinatários pendentes de assinaturas V2.&#x20;
>
> **URL:** PATCH [https://api-rest.arqsign.com/api/v2/processo/{idProcesso}/reenviar-processo](https://api-rest.arqsign.com/api/v2/processo/%7BidProcesso%7D/reenviar-processo)&#x20;
>
> **Documentação:** [https://developers.arqsign.com/api-details#api=api-rest-arqsign\&operation=6734bb1a21b37c983bbe8bbe](https://developers.arqsign.com/api-details#api=api-rest-arqsign\&operation=6734bb1a21b37c983bbe8bbe)&#x20;

3. **Acompanhamento: assinado por algum signatário**&#x20;

Quando algum signatário assinar o documento, a aplicação ArqSIGN acionará o Webhook que irá chamar o serviço (URL) do Cliente conforme configurado.&#x20;

O Cliente poderá com os dados retornados pelo Webhook atualizar seu sistema para manter seus dados atualizados.&#x20;

4. **Acompanhamento: recusa ou cancelamento**&#x20;

O cancelamento do processo pode ocorrer de três formas:&#x20;

* Quando algum signatário se recusa a assinar o documento;&#x20;
* Quando o responsável pelo envio do documento, cancela o processo via aplicação ArqSIGN;&#x20;
* Quando o cliente chama o método de API PATCH Processo/Cancelar-Processo para cancelar o processo.&#x20;

Quando o cancelamento ocorrer, o Webhook irá chamar o endpoint do Cliente conforme confirmado com a informação: se o processo foi cancelado ou se algum signatário se recusou a assinar. Quando o signatário se recusa assinar, a aplicação obriga que ele informe uma justificativa, esta justificativa também é enviada pelo Webhook.&#x20;

A partir deste ponto, o Cliente poderá tratar o retorno e decidir se deve iniciar o processo novamente com a chamada do POST para enviar um novo documento para assinar (Passo 1).&#x20;

5. **Acompanhamento: Expiração**&#x20;

Quando o documento expirar, a aplicação ArqSIGN acionará o Webhook que irá chamar o endpoint do Cliente conforme configurado.&#x20;

Após este retorno do Webhook o Cliente poderá implementar a chamada do método POST responsável por reenviar o processo. Este método irá atualizar o token de assinatura para os signatários que ainda não assinaram o documento. &#x20;

**Método:**&#x20;

> **Nome:** Editar e Reenviar o processo para os destinatários pendentes de assinaturas V2.&#x20;
>
> **URL:** PATCH [https://api-rest.arqsign.com/api/v2/processo/{idProcesso}/reenviar-processo](https://api-rest.arqsign.com/api/v2/processo/%7BidProcesso%7D/reenviar-processo)&#x20;
>
> **Documentação:** [https://developers.arqsign.com/api-details#api=api-rest-arqsign\&operation=6734bb1a21b37c983bbe8bbe](https://developers.arqsign.com/api-details#api=api-rest-arqsign\&operation=6734bb1a21b37c983bbe8bbe)&#x20;

6. **Conclusão**&#x20;

Quando o último signatário assinar o documento, a aplicação ArqSIGN acionará o Webhook que irá chamar o endpoint do Cliente conforme configurado.&#x20;

Após este retorno do Webhook o Cliente poderá armazenar em seu sistema o documento assinado juntamente com seu registro de assinatura.&#x20;

Observe que configurando dois webhooks conforme nossa sugestão, o documento assinado e concluído será trafegado somente neste momento, pelo Webhook de Conclusão.

&#x20;
