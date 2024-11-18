# 🟪 API

No menu API o cliente tem acesso as chaves necessárias para o gerenciamento e controle das requisições realizadas via API de integração.

<figure><img src="../../../.gitbook/assets/image (256).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

### **AppKey**

Para realizar a integração da plataforma a outras ferramentas via API é necessária uma Chave de Acesso,  que o usuário pode obter clicando em “Gerar Chave”. A chave gerada será apresentada no campo “API AppKey”.

{% hint style="danger" %}
<mark style="color:red;">**Sempre que gerada uma nova chave de acesso, todas as integrações feitas utilizando a chave anterior serão desconfiguradas. Sugerimos cautela ao criar novas chaves de acesso.**</mark>
{% endhint %}

### **SubscriptionKey**

Trata-se de chaves de acesso, criadas para trazer mais segurança na troca de informações entre plataformas externas e a ArqSign. &#x20;

**Chave 1:** Quando o cliente ainda não possui chave gerada o campo é apresentado em branco, quando o cliente já tem chave gerada é apresentada a chave 1 que foi gerada automaticamente pelo sistema.

**Chave 2:** Quando o cliente ainda não possui chave gerada o campo é apresentado em branco, quando o cliente já tem chave gerada é apresentada a chave 2 que foi gerada automaticamente pelo sistema.

Por **padrão** o sistema vai gerar sempre um **"par"** de **chaves**, então o cliente poderá utilizar **uma ou outra** ou **poderão ser usadas de forma rotacionada**, ou seja, a cada chamada o usuário poderá usar uma, ou ainda em casos em que a integração ocorre com terceiros, **o cliente utiliza uma e o terceiro a outra**.

Uma vez que a chave é gerada, ela deve ser incluída no HEADER das requisições para que estas sejam autorizadas.

Ao clicar em "Gerar Par de Chaves", é exibida uma mensagem na tela de validação da ação.

<figure><img src="../../../.gitbook/assets/image (257).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
<mark style="color:red;">Se após regerar as chaves, o usuário não atualizá-las nos parâmetros de pesquisa da integração já existente, as chamadas na API da ArqSign deixarão de funcionar</mark>
{% endhint %}

Para **regerar o par de chaves**, utilize o botão **"Gerar Par de Chaves".** Para **regerar apenas uma das chaves, utilize o** ícone de **"Regerar Chave"** considerando a chave 1 ou a 2.

<figure><img src="../../../.gitbook/assets/image (258).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

### Como passar a AppKey e a SubscriptionKey

Considerando a rota: [https://api-rest.arqsign.com/](https://api-rest.arqsign.com), é necessário enviar no “Headers” além da “AppKey” a “SubscriptionKey” conforme figura abaixo:

<figure><img src="../../../.gitbook/assets/image (25).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

***

### Serviços de Integração ArqSign

<figure><img src="../../../.gitbook/assets/image (52).png" alt=""><figcaption><p>Clique na imagem para ampliar.</p></figcaption></figure>

Ao clicar neste link, a aplicação irá abrir a página [**api.arqsign.com**](https://api.arqsign.com/index.html) com os métodos disponíveis até o momento.

***

### Documentação API

<figure><img src="../../../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

Ao clicar neste link, a aplicação irá abrir a página [**de detalhamento da API.**](../)

***

### Download lista de Id's usuários

<figure><img src="../../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

Ao clicar neste link a aplicação irá fazer o download de um arquivo .csv com a lista de todos os usuários ativos na conta e seu respectivo ID.

{% hint style="success" %}
<mark style="color:green;">A busca pelos usuários ativos da conta também pode ser realizada por API, para mais informações acesse o detalhamento do método:</mark> [<mark style="color:green;">POST/api/v1/usuarios/buscar-usuarios</mark>](https://arquivar.gitbook.io/manual-arqsign/\~/changes/kWiQBotJ7NkdrQc7NWAg/administracao/integracoes/api/metodos-disponiveis-na-api/3.-usuarios/3.1.post-api-v1-usuarios-buscar-usuarios)
{% endhint %}

***

### Download lista de Id's pastas

<figure><img src="../../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

Ao clicar neste link a aplicação irá fazer o download de um arquivo .csv com a lista de todas as pastas não excluídas da conta e seu respectivo ID.

{% hint style="success" %}
<mark style="color:green;">A busca pelas pastas não excluídas da conta também pode ser realizada por API, para mais informações acesse o detalhamento do método:</mark> [<mark style="color:green;">POST/api/v1/diretorio/buscar-pastas</mark>](https://arquivar.gitbook.io/manual-arqsign/\~/changes/kWiQBotJ7NkdrQc7NWAg/administracao/integracoes/api/metodos-disponiveis-na-api/2.-diretorios/2.1.post-api-v1-diretorio-buscar-pastas)
{% endhint %}
