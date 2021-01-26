.. PedePronto documentation , created by
   Paulo Henrique on Thu Jan 21 16:55:16 2021.


Autenticação
---------------------------------------

Todas as requisições abaixo devem ser autenticadas. A autenticação deve ser fornecida através do envio do token da company através do header HTTP Authorization.
O token da company pode ser fornecido diretamente pela Onyo ou pode ser obtido através das chamadas de login e company acima.
Por exemplo, caso a integração esteja configurada para trabalhar com o Amor os Pedaços do Shopping Mooca Plaza, então todas as chamadas devem ter o seguinte header:

``Authorization: Basic Mzg5OjM4OQ==``


Cadastro de produtos (product-list)
---------------------------------------

**Endpoint:** PUT /v1/{:PARTNER_SLUG}/product-list

**Descrição:** Essa chamada é utilizada para que o PDV cadastre ou atualize os produtos de uma determinada loja através da API. 
Quando um produto é cadastrado através da API ele não é disponibilizado automaticamente para os consumidores no aplicativo. Sempre que um cadastro de um produto novo é feito o time de cardápio da Onyo recebe uma notificação e verifica se as alterações podem ser publicadas.

Exemplo de payload:

.. code-block:: python

   {
   "products":[
      {
         "interfaceName":"Strogonoff",
         "description":"Strogonoff de carne",
         "type":"menu-item",
         "minimumChoices":0,
         "maximumChoices":1,
         "posReference":"pdv@678",
         "price":"24.50",
         "hidden":false,
         "prices":[
            {
               "price":"25.50",
               "hidden":false,
               "unavailable":false,
               "companyPosReference":"pdv@1"
            }
         ]
      }
   ]}

Exemplo de resposta:

.. code-block:: python

   {
   "products":[
      {
         "maximumChoices":1,
         "numericalId":72216,
         "description":"Strogonoff de carne",
         "posReference":"eatsforyou@678",
         "preparationTimeMinimum":null,
         "id":"/v1/product/72216",
         "price":null,
         "billName":"Strogonoff",
         "preparationTimeMaximum":null,
         "posSubproducts":[
            
         ],
         "subProducts":[
            
         ],
         "prices":[
            {
               "price":"25.50",
               "hidden":false,
               "unavailable":false,
               "companyPosReference":"eatsforyou@pdv@1"
            }
         ],
         "hidden":false,
         "type":"menu-item",
         "minimumChoices":0,
         "interfaceName":null
      }
   ]}
   
Listagem de produtos (company-product-list)
-----------------------------------------------

**Endpoint:** GET /v1/{:PARTNER_SLUG}/company/product-list

**Descrição:** Essa chamada é utilizada para que o PDV liste os produtos vendidos na loja.

Exemplo de resposta:

.. code-block:: python

   {
   "pagination":{
      "previous":null,
      "total":1,
      "page":1,
      "next":null
   },
   "data":[
      {
         "numericalId":22535,
         "sequence":1,
         "image":[
            
         ],
         "rewardable":false,
         "currency":null,
         "operator":"and",
         "shortDescription":"Refrigerante",
         "id":"http://api-staging.cloud.onyo.com/v1/mobile/product/22535",
         "category":{
            "name":"Bebidas",
            "id":326
         },
         "layout":"vertical",
         "unavailable":false,
         "minimumChoices":0,
         "redeemPoints":6,
         "subsidy":null,
         "recommended":false,
         "preparationTimeMaximum":null,
         "hidden":false,
         "type":"menu-item",
         "price":"15.90",
         "maximumChoices":1,
         "offer":true,
         "preparationTimeMinimum":null,
         "rewardPoints":null,
         "timeRule":null,
         "name":"Refrigerante",
         "fullDescription":"Refrigerante",
         "products":[
            "http://api-staging.cloud.onyo.com/v1/mobile/product/24102"
         ],
         "redeemable":true,
         "isMenuException":false
      },
      {
         "numericalId":24102,
         "sequence":1,
         "image":[
            
         ],
         "rewardable":false,
         "currency":null,
         "operator":"and",
         "shortDescription":"Escolha o sabor",
         "id":"http://api-staging.cloud.onyo.com/v1/mobile/product/24102",
         "category":null,
         "layout":"vertical",
         "unavailable":false,
         "minimumChoices":0,
         "redeemPoints":null,
         "subsidy":null,
         "recommended":false,
         "preparationTimeMaximum":null,
         "hidden":false,
         "type":"choosable",
         "price":"19.90",
         "maximumChoices":1,
         "offer":true,
         "preparationTimeMinimum":null,
         "rewardPoints":null,
         "timeRule":{
            
         },
         "name":"Escolha o sabor",
         "fullDescription":"Escolha o sabor",
         "products":[
            
         ],
         "redeemable":false,
         "isMenuException":false
      },
      {
         "numericalId":24103,
         "sequence":1,
         "image":[
            
         ],
         "rewardable":false,
         "currency":null,
         "operator":"and",
         "shortDescription":"Coca-Cola",
         "id":"http://api-staging.cloud.onyo.com/v1/mobile/product/24103",
         "category":null,
         "layout":"vertical",
         "unavailable":false,
         "minimumChoices":0,
         "redeemPoints":null,
         "subsidy":null,
         "recommended":false,
         "preparationTimeMaximum":null,
         "hidden":false,
         "type":"simple",
         "price":"19.90",
         "maximumChoices":1,
         "offer":true,
         "preparationTimeMinimum":null,
         "rewardPoints":null,
         "timeRule":{
            
         },
         "name":"Coca-Cola",
         "fullDescription":"Coca-Cola",
         "products":[
            
         ],
         "redeemable":false,
         "isMenuException":false
      }
   ]}

Alteração de disponibilidade de produtos (product-unavailable)
----------------------------------------------------------------

**Endpoint:** PUT /v1/{:PARTNER_SLUG}/product/unavailable

**Descrição:** Essa chamada é utilizada para o PDV marcar um produto como disponível ou indisponível.
Note que o valor true na chave “unavaiable” significa que o produto está indisponível.

Exemplo de payload:

.. code-block:: python

   {"items": [{"product": 35775, "unavailable": true}]}

Exemplo de resposta:

.. code-block:: python

   {"items": [{"product": 35775, "unavailable": true}]}

