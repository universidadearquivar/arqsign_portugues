# 🟪 Segurança

A Arquivar tem mais de trinta e um anos de experiência na prestação de serviços de gerenciamento de documentos, processos e informações em conformidade com a legislação brasileira e com as normas do Conselho Nacional de Arquivos (CONARQ).&#x20;

Nossas soluções atendem a mais de 2.500 clientes e 20.000 usuários.&#x20;

A partir desse know-how, a Arquivar desenvolveu a ArqSign – uma plataforma que permite a assinatura eletrônica e digital de documentos, em total conformidade com a legislação brasileira, portanto com 100% de validade jurídica.

<details>

<summary>Esse tipo de serviço já está homologado pela LGPD?</summary>

O objetivo da ArqSign é proteger os direitos de seus clientes, assegurando total segurança aos seus dados. Todas as informações coletadas ou processadas pela ArqSign seguem estritamente as disposições legais da Lei Geral de Proteção de Dados (LGPD).

</details>

<details>

<summary>Como fica um documento assinado por meio da Plataforma ArqSign?</summary>

No Painel de Assinaturas do Adobe Reader é possível verificar:&#x20;

1. A Arquivar como certificadora do processo de assinatura, no início da trilha de assinatura;&#x20;
2. Um certificado digital identificando cada ação de assinatura (no exemplo abaixo temos 2 signatários).&#x20;
3. A Arquivar finalizando o fluxo de assinatura e bloqueando o arquivo para impossibilitar alterações.&#x20;

![](<../.gitbook/assets/image (160).png>)

![](<../.gitbook/assets/image (161).png>)

</details>

<details>

<summary>Qual o tipo de criptografia é utilizado na Plataforma ArqSign?</summary>

Para garantir a segurança dos dados que estão sendo trafegados entre Cliente e Servidor, os [dados são criptografados](https://arquivar.com.br/politica-de-privacidade/) por meio de certificado SSL de SHA256.&#x20;

Utilizamos criptografia de comunicações e processos de operação – protocolos de transporte padrão da indústria entre os dispositivos do usuário e os datacenters da Microsoft Azure, bem como dentro dos próprios datacenters.&#x20;

Para dados em repouso, nosso Servidor, o Azure oferece uma ampla gama de recursos de criptografia até AES-256; &#x20;

* Proteção de redes – infraestrutura necessária para conectar máquinas virtuais com segurança umas às outras e para conectar datacenters locais às VMs do Azure. O Azure bloqueia tráfego não autorizado para datacenters da Microsoft ou dentro deles, usando diversas tecnologias. A Rede Virtual do Azure estende-se à sua rede local para a nuvem por meio de VPN site a site; &#x20;
* Gerenciamento de ameaças – Microsoft Antimalware para serviços de nuvem e máquinas virtuais. A Microsoft também emprega detecção de intrusão, prevenção de ataques DDoS (ataque de negação de serviço distribuído), testes de penetração regulares e ferramentas de análises de dados e aprendizado de máquina para ajudar a atenuar as ameaças contra a plataforma Azure. &#x20;

</details>

<details>

<summary>Onde ficam armazenados os dados e documentos inseridos na Plataforma ArqSign?</summary>

Os dados e documentos são armazenados no datacenter Microsoft Azure, líder mundial em estabelecer requisitos de privacidade e de segurança. &#x20;

O Microsoft Azure cumpre uma ampla variedade de normas de conformidade internacionais e específicas do setor, como o GDPR (Regulamento Geral sobre a Proteção de Dados), a ISO 27001, o HIPAA, o FedRAMP, a SOC 1 e SOC 2, bem como normas específicas de certos países, incluindo o IRAP da Austrália, o G-Cloud do Reino Unido e o MTCS de Cingapura. Rigorosas auditorias de terceiros, tais como aquelas realizadas pelo British Standards Institute, confirmam a adesão do Azure aos rígidos controles de segurança exigidos por tais normas.&#x20;

A Microsoft aproveitou sua experiência na criação de proteções de software corporativo e na execução de alguns dos maiores serviços online do mundo a fim de criar tecnologias e práticas de segurança robustas. Elas ajudam a garantir que a infraestrutura do Azure seja resistente a ataques, protege o acesso do usuário ao ambiente do Azure e ajuda a manter os dados do cliente seguros por meio de comunicações criptografadas e pelo gerenciamento de ameaças e práticas de atenuação, incluindo testes de penetração regulares.&#x20;

[Clique aqui](https://youtu.be/yKNeahEQY8g) e assista ao vídeo explicativo.

</details>

<details>

<summary>Qual a base de normas é referência para o processo de assinatura da Plataforma ArqSign?</summary>

A plataforma ArqSign está baseada nos [REQUISITOS DAS POLÍTICAS DE ASSINATURA DIGITAL NA ICP-BRASIL do ITI (Instituto Nacional de Tecnologia da Informação)](https://www.gov.br/iti/pt-br/central-de-conteudo/doc-icp-15-03-requisitos-minimos-para-politicas-de-assinatura-pdf).&#x20;

Este documento estabelece os requisitos a serem obrigatoriamente observados pelas entidades criadoras de Políticas de Assinatura Digital no âmbito da Infraestrutura de Chaves Públicas Brasileira (ICP-Brasil), em conformidade com a estrutura proposta pelos padrões ETSI TR 102 272 \[1] e ETSI TR 102.038 \[2].&#x20;

</details>

<details>

<summary>Qual a diferença entre a assinatura ArqSign e a assinatura de outras plataformas do mercado?</summary>

A ArqSign garante que o arquivo assinado por todos os participantes do fluxo seja sempre o mesmo através de seu processo exclusivo de assinatura!&#x20;

Sempre que um signatário assina um documento sem seu próprio Certificado Digital, a Arqsign aplica um Certificado Digital da plataforma, capturando o _Hash_ (identificação única) do arquivo, verifica a integridade do arquivo e anexa ao Certificado a identificação do signatário.&#x20;

Quando o usuário já possui um certificado digital e deseja utilizá-lo para realizar a assinatura através da ArqSign, utilizamos este certificado para verificar a integridade e identificá-lo como signatário no documento. &#x20;

Aplicar um certificado digital ao documento para cada ato de assinatura é o único meio possível de assegurar o nível de segurança da assinatura avançada ou qualificada descritas na Lei nº 14.063, de 23 de setembro de 2020.

</details>

<details>

<summary>Quais são os itens de autenticação disponíveis na plataforma?</summary>

A ArqSign garante uma ampla variedade de tecnologias de autenticação, dentre as quais se encontram:&#x20;

* Certificados digitais ICP-Brasil ou de padrão internacional;
* Nome(s) do(s) signatário(s);
* Documentos cadastrais do signatário (CPF, CNPJ ou outro);
* Endereços de e-mail;
* Endereço(s) de IP do(s) signatário(s);
* Captura de geolocalização do signatário (se habilitado no equipamento);
* Termo de aceite para assinatura eletrônica.
* Código de acesso;
* Conta ArqSign;
* Representação visual da assinatura;
* Data e hora da assinatura;
* Histórico de movimentação (ou seja, quem enviou, visualizou, assinou etc.);
* Histórico de autenticação;
* Status de conclusão.

</details>
