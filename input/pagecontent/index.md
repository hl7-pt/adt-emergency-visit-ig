<blockquote class="stu-note">
    <p>A especificação aqui documentada é, por enquanto, uma especificação de prova de conceito e não pode ser usada para fins de implementação. 
    Nenhuma responsabilidade pode ser inferida do uso ou mau uso desta especificação, ou de suas consequências.</p>
  </blockquote>

### Ambito

O presente guia de implementação (IG) foi desenvolvido com o objetivo de uniformizar a definição, utilização e partilha de informações entre diferentes sistemas de informação de saúde, assegurando uma interoperabilidade eficaz entre diferentes entidades e profissionais de saúde.

Este guia fornece especificações técnicas utilizando o FHIR Versão R4, e funcionais e pressupõe que o leitor esteja familiarizado com a especificação funcional e com esta versão do FHIR.


### Introdução

Em Portugal começam a existir várias implemetações em FHIR que mapeaiam as implementações de mensagens HL7v2.x para mensagens HL7 FHIR. Este IG pretende dar suporte a integrações em FHIR que implementam o paradigma de *FHIR Messaging*, fazendo a ponte entre as implementações que já existem em HL7v2.x e mensagens HL7 FHIR.
Tem como base o perfil [Patient Administration Management](https://profiles.ihe.net/ITI/TF/Volume1/ch-14.html#14) da Estrutura Técnica de Infraestrutura de TI do IHE para a abordagem em HL7v2.x e que tem como atores *"Patient Encounter Supplier"* e *"Patient Encounter Consumer"*.

O paradigma de mensagem FHIR permite manter a comunicação assáncrona de mensagens e evoluir a comunicação para o Standard FHIR e ao mesmo tempo, usando ferramentas de conversão, manter a comunicação com os sistemas que mantém as integrações em HL7 v2 (Fig.1).

<br>
<img src="messageParadigmSchema.png" alt="Arquitetura de Paradigma de Messaging"/>
<br>



Fig.1 -Fhir Messaging Paradigm Schema



O perfil IHE Patient Administration Managament apresenta duas transações: *Patient Identity Management* e *Patient Encounter Management*. O âmbito desta IG é focado na transação *Patient Encounter Management* (Fig.2) o qual inclui as operações que permitem fazer a gestão dos episódios dos utentes.

<br>
<img src="domainsAdt.png" alt="Dominios do ADT"/>
<br>

Fig.2 - Atores da trasanção Gestão da Episódios do Utente



O termo “episódios do utente” refere-se aos dados dos episódios do utente de contexto administrativo e clinico, incluindo informações administrativas do utente e do episódio dados adminsitrativos do espisódio, entidade responsável, bem como dados clinicos relativos ao episodio clinico do utente. Esta IG foca-se no contexto da Urgencia hospitalar.

A transação *Patient Encounter Management* transmite dados relativos aos episódios e contém eventos para gestão de episódios de urgencia. No entando pode ser estendida para ser usada nos vários contextos como internamento, e todos aqueles que recebem um leito na unidade de saúde, ou urgência, consulta externa, hospital de dia, ambulatório e outros que não têm atribuído um leito na unidade de saúde.

Em Hl7v2, as mensagens que suportam as ações necessárias estão especificadas no profile IHE mencionado anteriormente prevendo a toca de mensagens com eventos especificos já defenidos pelo standard HL7 v2:


| Category of event                   | Insert Code | Insert Message  | Cancel Code | Cancel Message  |
|-------------------------------------|-------------|-----------------|----------|-----------------|
| New Emergency Referral Request *    | S01         | REF^S01^REF_S01 | S04      | REF^S04^REF_S01 |
| Update Emergency Referral Request * | S03         | REF^S03^REF_S01 |          |                 |
| Register outpatient                 | A04         | ADT^A04^ADT_A01 | A11      | ADT^A11^ADT_A09 |
| Discharge patient                   | A03         | ADT^A03^ADT_A03 | A13      | ADT^A13^ADT_A01 |
| Update patient visit                | A08         | ADT^A08^ADT_A05 |          |                 |
| Change patient class to outpatient  | A07         | ADT^A07^ADT_A06 |          |                 |
| Transfer patient                    | A02         | ADT^A02^ADT_A02 | A12      | ADT^A12^ADT_A12 |


Tabela 1 - Subconjunto de mensagens obrigatórias para gestão de episódios de urgencia (fonte IHE). 

Nesta tabela foram adicionados os eventos de referenciação à urgencia (REF^S01, REF^S01 e REF^S04) que fazem parte do fluxo de informação no contexto de gestão de episódios de urgencia em Portugal.

Em FHIR não existe a definição de eventos para dar suporte a mensagens orientadas a eventos tal como no HL7 v2, mas o FHIR está preparado para isso. Torna-se assim necessário definir uma sistema de codificação para estes eventos de forma a tormar uniforme os codigos dos eventos a enviar nas mensagens entre os diferentes sistemas, comum às diferentes implementações deste tipo. A IG de Gestão de Identidade do Utente já faz referencia a este sistema de codificação de eventos das mensagens FHIR. 


### Autores e contribuidores 

<table>
<thead>
<tr class="header">
<th>Papel</th>
<th>Nome</th>
<th>Organização</th>
<th>Contacto</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Autor</td>
<td>zzz</td>
<td>xxxx</td>
<td>yyyy</td>
</tr><tr class="even">
<td>Autor</td>
<td>xxx</td>
<td></td>
<td>dssd</td>
</tr><tr class="odd">
<td>Autor</td>
<td>asdasd</td>
<td>asdasd</td>
<td>asdas</td>
</tr><tr class="even">
<td>Autor</td>
<td>asdasd</td>
<td></td>
<td>dasda</td>
</tr></tbody>
</table>
