# CDE-Simulation-Project-International-Patients-Treatment-Management

## Authors :

<table>
  <tr>
      <td>
        <a href="https://github.com/DRoy7"><td>Deep Roy</td></a>
        </td>
      <td>
        <a href="https://github.com/sriharish252"><td>Sri Harish</td></a>
        </td>
      <td>
        <a href="https://github.com/Kamalesh8"><td>Kamalesh R</td></a>
        </td>
      <td>
        <a href="https://github.com/Megha0699"><td>Megha S</td></a>
        </td>
      <td>
        <a href="https://github.com/greninja199"><td>Praduman Kumar</td></a>
        </td>
    </tr>
</table>

## Modules::

### Authorizatiion-Microservice :
This module is used for doing the **Authentication** and **Authorization** part of our project. 
This microsevice provides the endpoints for authentication and authorization

#### --Endpoints : 
<table>
    <thead>
        <th>Method</th>
        <th>Endpoint Path</th>
        <th>Returns</th>
    </thead>
    <tbody>
        <tr>
            <td>POST</td>
            <td>/authenticate</td>
            <td>ResponseEntity</td>
        </tr>
        <tr>
            <td>POST</td>
            <td>/authorize</td>
            <td>boolean</td>
        </tr>
        <tr>
            <td>POST</td>
            <td>/authorize-role</td>
            <td>boolean</td>
        </tr>
    </tbody>
</table>

#### --Application Properties Toggle :<br/>
spring.application.name=Authorizatiion-Microservice<br/>
server.port=8400<br/>
server.servlet.context-path=/auth<br/>
User Database : H2(In-Memory)<br/>

### InsuranceClaim-Microservice :
This module is used for doing the **Insurance Claim** part after the registration of a patient. 
This microsevice provides the endpoints for getting the Insurance related details and storing insurer details.

#### --Endpoints : 
<table>
    <thead>
        <th>Method</th>
        <th>Endpoint Path</th>
        <th>Returns</th>
    </thead>
    <tbody>
        <tr>
            <td>GET</td>
            <td>/getAllInsurerDetail</td>
            <td>List of "InsurerDetail"</td>
        </tr>
        <tr>
            <td>GET</td>
            <td>/getInsurerByPackageName/{packageName}</td>
            <td>"InsurerDetail"</td>
        </tr>
        <tr>
            <td>POST</td>
            <td>/initiateClaim</td>
            <td>double</td>
        </tr>
    </tbody>
</table>

#### --Dependencies on Other microsevices : **Authorizatiion-Microservice**, **IPTreatment-MicroService**

#### --Application Properties Toggle :<br/>
spring.application.name=InsuranceClaim<br/>
server.port=8300<br/>
server.servlet.context-path=/insure<br/>
auth.URL=http://localhost:8400/auth<br/>
iptreatment.URL=http://localhost:8200/ipTreatment<br/>
User Database : H2(In-Memory)<br/>


### IPTreatmentOffering-Microservice :
This module is used for doing the **IPTreatmentOffering services**. 
This microsevice provides the endpoints for viewing and modifying the treatment packages and the specialists.

#### --Endpoints : 
<table>
    <thead>
        <th>Method</th>
        <th>Endpoint Path</th>
        <th>Returns</th>
    </thead>
    <tbody>
        <tr>
            <td>GET</td>
            <td>/ipTreatmentPackages</td>
            <td>List<IPTreatmentPackage></td>
        </tr>
        <tr>
            <td>GET</td>
            <td>/ipTreatmentPackageByName/{ailment}/{packageName}</td>
            <td>List<IPTreatmentPackage></td>
        </tr>
        <tr>
            <td>GET</td>
            <td>/specialists</td>
            <td>List<SpecialistDetail></td>
        </tr>
        <tr>
            <td>POST</td>
            <td>/addSpecialist</td>
            <td>ResponseEntity<String></td>
        </tr>
        <tr>
            <td>DELETE</td>
            <td>/deleteSpecialist/{specialistId}</td>
            <td>ResponseEntity<String></td>
        </tr>
        <tr>
            <td>PUT</td>
            <td>/updatePackage/{pid}/{treatmentPackageName}</td>
            <td>ResponseEntity<String></td>
        </tr>
        <tr>
            <td>GET</td>
            <td>/countPid/{pid}</td>
            <td>boolean</td>
        </tr>
    </tbody>
</table>

#### --Application Properties Toggle : <br/>
spring.application.name=IPTreatmentOffering-service<br/>
server.port=8100<br/>
server.servlet.context-path=/ipTreatmentOffering<br/>
User Database : H2(In-Memory)<br/>



