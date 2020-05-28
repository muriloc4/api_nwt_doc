# NWT - API

### Endpoitn 

BASE_URL = http://api.nwt.net.br



Como exemplo, pode usar meu cpf : 17980781716 



**Bem-vindo a API Pública da NWT :coffee: :smile:**



## Whatsapp  





### Financeiro

---



***POST*** {{ base_url  }}/wpp/billetList/:cpf

Irá listar os boletos do cliente. Mas caso ele tenha mais de um contrato, essa rota irá retorar: 

```json
{
  "messager": [
    "Verifiquei que você tem mais de um contrato. A qual deles se refere ?\n",
    "Contrato: 5. Endereço: Rua Valadares, 124, Cariacica, ES. [ 1_MEGA_RESIDENCIAL ]",
    "Contrato: 32. Endereço: AV COSTA BRANDAO, 151, Cariacica, ES. [ 50_MEGA_RESIDENCIAL ]",
    "Contrato: 93. Endereço: , , , . [ 50_MEGA_RESIDENCIAL ]",
    "Contrato: 110. Endereço: Rua Valadares, 124, Cariacica, ES. [ 1_MEGA_RESIDENCIAL ]"
  ]
}
```

Para pegar o boleto do contrato, informe o nº do Contrato via *body* da *request*



##### Header

Content-Type:multipart/form-data

##### Body

contrato = {{ nº do contrato }}



```json
{
  "messager": [
    "Boleto: 3\nReferente ao mês: *04* \nvalor R$ \nSegunda Via : https:\/\/pagamentos.nwt.net.br\/santander\/boleto\/3\nLinha digitavel: 03393775500000002009589193012345678901230101"
  ]
}
```

### Lista Contratos

***POST*** {{base_url}} wpp/contractsList/:cpf



**Retorno** - *200*

```json
{
  "status": true,
  "data": {
    "id": "2011420",
    "nome": "ANDRÉ SOUZA DE OLIVEIRA JUNIOR",
    "cpf": "17980781716",
    "email": "ajjunior33@gmail.com",
    "telefone": "27988864790",
    "celular": "27988864790",
    "contacts": [
      {
        "id": "9215",
        "endereco": "Rua Valadares",
        "bairro": "Presidente Médici",
        "cidade": "Cariacica",
        "plano": "PLANO_CORPORATIVO_CUSTOMIZADO",
        "estado": "ES"
      },
      {
        "id": "9274",
        "endereco": "Rua Principal",
        "bairro": "Porto de Santana",
        "cidade": "Cariacica",
        "plano": "100_MEGA_RESIDENCIAL",
        "estado": "ES"
      }
    ]
  }
}
```



*400* Bad Request

```json
{
  "status": false,
  "messager": "Não consegui encontrar o responsavel pelo CPF 232"
}
```



### Lista de Boletos

***POST*** {{base_url}} wpp/billetListContract/:cpf/:id_contrato



**Retorno ** *200*

```json
{
  "status": true,
  "billets": [
    {
      "id": "359693",
      "vencimento": "25\/05\/2020",
      "valor": "12.00",
      "linhadigitavel": "03399057134660200507935969301015682660000001200",
      "url_pagamento": "https:\/\/pagamentos.nwt.net.br\/santander\/boleto\/359693"
    },
    {
      "id": "360036",
      "vencimento": "07\/05\/2020",
      "valor": "1.21",
      "linhadigitavel": "03399057134660200507936003601014582480000000121",
      "url_pagamento": "https:\/\/pagamentos.nwt.net.br\/santander\/boleto\/360036"
    }
  ]
}
```



**Retorno** *400* Bad Request (CPF INVALIDO)

```json
{
  "status": false,
  "messager": "Não consegui encontrar o responsavel pelo CPF 132"
}
```

**Retorno** *400* Bad Request (CONTRATO INVALIDO)

```json
{
  "status": false,
  "messager": "Esse contrato não pertence a esse cliente."
}
```



<div align="center">
    Create by André Junior - 2020
</div>

