# NWT - API

### Endpoitn 

BASE_URL = http://api.nwt.net.br





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



<div align="center">
    Create by André Junior - 2020
</div>

