.. PedePronto documentation , created by
   Paulo Henrique on Thu Jan 21 16:55:16 2021.


Autenticação
--------------------------------------

Todas as requisições abaixo devem ser autenticadas. A autenticação deve ser fornecida através do envio do token da company através do header HTTP Authorization.
O token da company pode ser fornecido diretamente pela Onyo ou pode ser obtido através das chamadas de login e company acima.
Por exemplo, caso a integração esteja configurada para trabalhar com o Amor aos Pedaços do Shopping Mooca Plaza, então todas as chamadas devem ter o seguinte header:

``Authorization: Basic Mzg5OjM4OQ==``


Listagem de pedidos (order-list)
--------------------------------------

**Endpoint:** GET /v1/{:PARTNER_SLUG}/order

**Descrição:** Essa chamada retorna uma lista de pedidos da loja autenticada na requisição.
Por padrão essa chamada executa um filtro pelos pedidos nos status 2 e 3 (payment-authorized e pos-received) que são os pedidos que o PDV precisa aprovar ou reprovar.
Caso algum filtro de status seja feito o filtro padrão será sobrescrito.

**Parâmetros na url:**

.. csv-table::
   :header: "Campo", "Tipo", "Obrigatório", "Comentário"
   :widths: 20, 20, 20, 40

   "email",	"String ou lista", "Não", "Status ou lista de status dos pedidos. Por padrão os pedidos são filtrados pelos status 2 e 3 caso nenhum filtro de status seja informado. Ex: status=3 ou status=3,4,5"
   "since", "String", "Não", "iso date em UTC. Ex: since=2018-04-01T00:00:00"
   "until", "String", "Não", "iso date em UTC. Ex: until=2016-04-01T00:00:00"

Exemplo de URL (filtrando por pedidos aprovados e negados pelo PDV que tenham sido criados desde 01/09/2018 00:00:00 UTC):

``/v1/{:PARTNER_SLUG}/order?status=4,5&since=2018-09-01T00:00:00``

**Campos Extras:**

Os campos extras são retornados nessa chamada caso o pedido tenha informações adicionais como taxa de entrega ou descontos.

Descrição dos campos:

.. csv-table::
   :header: "Campo", "Comentário"
   :widths: 20, 20
   
   "optional", "Campo booleano (true ou false)"
   "value", "Valor em R$ do extra/desconto"
   "key",	"Campo descritivo do valor extra/desconto"
   "label", "Nome do valor extra/desconto"
   
Exemplo de resposta contendo um pedido:

.. code-block:: python

   {
   "pagination":{
      "next":null,
      "total":1,
      "page":1,
      "previous":null
   },
   "data":[
      {
         "pos_reference":"",
         "customer_document":"53189076871",
         "service_charge_value":null,
         "id":1047534,
         "display_code":null,
         "order_type":5,
         "nested_items":[
            {
               "base_unit_pos_price":null,
               "pos_reference":"",
               "pos_name":"",
               "description":"",
               "dragged_by":null,
               "addition":0.0,
               "redeem_id":null,
               "unit_price":"35.00",
               "base_unit_price":null,
               "product":{
                  "id":52012,
                  "name":"Meio a Meio"
               },
               "unit_pos_price":null,
               "order_id":1047534,
               "order_position":1,
               "discount":0.0,
               "prepare_rightaway":true,
               "unit_points":0,
               "product_type":2,
               "items":[
                  {
                     "base_unit_pos_price":null,
                     "pos_reference":"",
                     "pos_name":"",
                     "description":"",
                     "dragged_by":null,
                     "addition":0.0,
                     "redeem_id":null,
                     "unit_price":null,
                     "base_unit_price":null,
                     "product":{
                        "id":52013,
                        "name":"Escolha os sabores"
                     },
                     "unit_pos_price":null,
                     "order_id":1047534,
                     "order_position":2,
                     "discount":0.0,
                     "prepare_rightaway":true,
                     "unit_points":0,
                     "product_type":1,
                     "items":[
                        {
                           "base_unit_pos_price":null,
                           "pos_reference":"",
                           "pos_name":null,
                           "description":"None",
                           "dragged_by":null,
                           "addition":0.0,
                           "redeem_id":null,
                           "unit_price":null,
                           "base_unit_price":null,
                           "product":{
                              "id":52014,
                              "name":"Marguerita"
                           },
                           "unit_pos_price":null,
                           "order_id":1047534,
                           "order_position":3,
                           "discount":0.0,
                           "prepare_rightaway":true,
                           "unit_points":0,
                           "product_type":0,
                           "items":[
                              
                           ],
                           "partition":null,
                           "is_note":false,
                           "pos_parent_position":null,
                           "parent_order_position":2,
                           "quantity":"1.000"
                        },
                        {
                           "base_unit_pos_price":null,
                           "pos_reference":"",
                           "pos_name":null,
                           "description":"None",
                           "dragged_by":null,
                           "addition":0.0,
                           "redeem_id":null,
                           "unit_price":null,
                           "base_unit_price":null,
                           "product":{
                              "id":52017,
                              "name":"Presunto Parma"
                           },
                           "unit_pos_price":null,
                           "order_id":1047534,
                           "order_position":4,
                           "discount":0.0,
                           "prepare_rightaway":true,
                           "unit_points":0,
                           "product_type":0,
                           "items":[
                              
                           ],
                           "partition":null,
                           "is_note":false,
                           "pos_parent_position":null,
                           "parent_order_position":2,
                           "quantity":"1.000"
                        }
                     ],
                     "partition":null,
                     "is_note":false,
                     "pos_parent_position":null,
                     "parent_order_position":1,
                     "quantity":"1.000"
                  }
               ],
               "partition":null,
               "is_note":false,
               "pos_parent_position":null,
               "parent_order_position":null,
               "quantity":"1.000"
            },
            {
               "base_unit_pos_price":null,
               "pos_reference":"",
               "pos_name":null,
               "description":"",
               "dragged_by":null,
               "addition":0.0,
               "redeem_id":null,
               "unit_price":"14.00",
               "base_unit_price":null,
               "product":{
                  "id":71662,
                  "name":"Kombucha Maracujá Garrafa Booz 320ml"
               },
               "unit_pos_price":null,
               "order_id":1047534,
               "order_position":5,
               "discount":0.0,
               "prepare_rightaway":true,
               "unit_points":0,
               "product_type":2,
               "items":[
                  
               ],
               "partition":null,
               "is_note":false,
               "pos_parent_position":null,
               "parent_order_position":null,
               "quantity":"1.000"
            },
            {
               "base_unit_pos_price":null,
               "pos_reference":"",
               "pos_name":null,
               "description":"",
               "dragged_by":null,
               "addition":0.0,
               "redeem_id":null,
               "unit_price":null,
               "base_unit_price":null,
               "product":{
                  "id":71669,
                  "name":"Embalagem"
               },
               "unit_pos_price":null,
               "order_id":1047534,
               "order_position":6,
               "discount":0.0,
               "prepare_rightaway":true,
               "unit_points":0,
               "product_type":2,
               "items":[
                  
               ],
               "partition":null,
               "is_note":false,
               "pos_parent_position":null,
               "parent_order_position":null,
               "quantity":"2.000"
            }
         ],
         "preparation_time_minimum":64,
         "pos_import_status":null,
         "payable_value":"49.65",
         "status":3,
         "creation_datetime":"2020-06-04T00:23:34.162787Z",
         "table_reference":"",
         "total_value":"57.00",
         "redeem":false,
         "printed":false,
         "address":{
            "city":"São Paulo",
            "geoLat":"-23.5682759000",
            "country":"Brazil",
            "complement":"Bairro: Paraíso | Complemento: 2o andar",
            "number":"70",
            "zipCode":"04003-000",
            "state":"SP",
            "street":"Rua Coronel Oscar Porto",
            "geoLon":"-46.6491211000"
         },
         "customer":{
            "telephone":"11971652467",
            "email":"felipe@onyo.com",
            "document":"53189076871",
            "id":32434,
            "name":"Felipe Armoni Teste"
         },
         "preparation_time_maximum":74,
         "items":[
            {
               "base_unit_pos_price":null,
               "pos_reference":"",
               "pos_name":null,
               "description":"None",
               "dragged_by":null,
               "addition":0.0,
               "redeem_id":null,
               "unit_price":null,
               "base_unit_price":null,
               "product":{
                  "id":52014,
                  "name":"Marguerita"
               },
               "unit_pos_price":null,
               "order_id":1047534,
               "order_position":3,
               "discount":0.0,
               "prepare_rightaway":true,
               "unit_points":0,
               "product_type":0,
               "partition":null,
               "is_note":false,
               "pos_parent_position":null,
               "parent_order_position":2,
               "quantity":"1.000"
            },
            {
               "base_unit_pos_price":null,
               "pos_reference":"",
               "pos_name":"",
               "description":"",
               "dragged_by":null,
               "addition":0.0,
               "redeem_id":null,
               "unit_price":null,
               "base_unit_price":null,
               "product":{
                  "id":52013,
                  "name":"Escolha os sabores"
               },
               "unit_pos_price":null,
               "order_id":1047534,
               "order_position":2,
               "discount":0.0,
               "prepare_rightaway":true,
               "unit_points":0,
               "product_type":1,
               "partition":null,
               "is_note":false,
               "pos_parent_position":null,
               "parent_order_position":1,
               "quantity":"1.000"
            },
            {
               "base_unit_pos_price":null,
               "pos_reference":"",
               "pos_name":"",
               "description":"",
               "dragged_by":null,
               "addition":0.0,
               "redeem_id":null,
               "unit_price":"35.00",
               "base_unit_price":null,
               "product":{
                  "id":52012,
                  "name":"Meio a Meio"
               },
               "unit_pos_price":null,
               "order_id":1047534,
               "order_position":1,
               "discount":0.0,
               "prepare_rightaway":true,
               "unit_points":0,
               "product_type":2,
               "partition":null,
               "is_note":false,
               "pos_parent_position":null,
               "parent_order_position":null,
               "quantity":"1.000"
            },
            {
               "base_unit_pos_price":null,
               "pos_reference":"",
               "pos_name":null,
               "description":"None",
               "dragged_by":null,
               "addition":0.0,
               "redeem_id":null,
               "unit_price":null,
               "base_unit_price":null,
               "product":{
                  "id":52017,
                  "name":"Presunto Parma"
               },
               "unit_pos_price":null,
               "order_id":1047534,
               "order_position":4,
               "discount":0.0,
               "prepare_rightaway":true,
               "unit_points":0,
               "product_type":0,
               "partition":null,
               "is_note":false,
               "pos_parent_position":null,
               "parent_order_position":2,
               "quantity":"1.000"
            },
            {
               "base_unit_pos_price":null,
               "pos_reference":"",
               "pos_name":null,
               "description":"",
               "dragged_by":null,
               "addition":0.0,
               "redeem_id":null,
               "unit_price":null,
               "base_unit_price":null,
               "product":{
                  "id":71669,
                  "name":"Embalagem"
               },
               "unit_pos_price":null,
               "order_id":1047534,
               "order_position":6,
               "discount":0.0,
               "prepare_rightaway":true,
               "unit_points":0,
               "product_type":2,
               "partition":null,
               "is_note":false,
               "pos_parent_position":null,
               "parent_order_position":null,
               "quantity":"2.000"
            },
            {
               "base_unit_pos_price":null,
               "pos_reference":"",
               "pos_name":null,
               "description":"",
               "dragged_by":null,
               "addition":0.0,
               "redeem_id":null,
               "unit_price":"14.00",
               "base_unit_price":null,
               "product":{
                  "id":71662,
                  "name":"Kombucha Maracujá Garrafa Booz 320ml"
               },
               "unit_pos_price":null,
               "order_id":1047534,
               "order_position":5,
               "discount":0.0,
               "prepare_rightaway":true,
               "unit_points":0,
               "product_type":2,
               "partition":null,
               "is_note":false,
               "pos_parent_position":null,
               "parent_order_position":null,
               "quantity":"1.000"
            }
         ],
         "extras":[
            {
               "optional":false,
               "value":"-7.35",
               "key":"discount",
               "label":"15OFF_LABARBARA_CHEFSCLUB"
            },
            {
               "optional":false,
               "value":"8.00",
               "key":"additional",
               "label":"Entrega"
            }
         ],
         "payments":[
            {
               "status":"canceled",
               "gateway_code":"vtex",
               "is_onyo_affiliation":false,
               "payment_method":"credit",
               "transaction_id":"BB2AF9F03FA744A79EF62858222C4B25",
               "value":"49.65",
               "numerical_id":1054575,
               "transaction_date":"2020-06-04 00:23:34",
               "acquirer":{
                  "pos_reference":"",
                  "id":1,
                  "name":"Cielo"
               },
               "acquirer_return":{
                  "Tid":"91744583",
                  "Message":null,
                  "ReturnCode":null,
                  "authId":"744583"
               },
               "payment_method_pos_reference":"",
               "transaction_code":"TESTPAY1054575",
               "card":{
                  "masked_number":"4444331111",
                  "printed_name":"Felipe",
                  "card_brand":{
                     "pos_reference":"",
                     "code":"visa",
                     "id":8,
                     "name":"Visa"
                  }
               }
            }
         ],
         "error":null,
         "discount_value":"7.35",
         "sequence_number":null
      }
   ]
  }
  
Detalhe de pedido (order-detail)
---------------------------------------

**Endpoint:** GET /v1/{:PARTNER_SLUG}/order/{:order_id}

**Descrição:** Essa chamada retorna o JSON do pedido informado na URL.
A resposta dessa chamada é o mesmo conteúdo da lista de itens da chamada de listagem de pedidos, porém apenas com o objeto do pedido solicitado na URL. 


Atualização de pedido (order-patch)
---------------------------------------

**Endpoint:** PATCH /v1/{:PARTNER_SLUG}/order/{:order_id}

**Descrição:** Essa chamada permite a atualização do status de um pedido para 4 (aceito / POS_ACCEPTED) ou 5 (erro / POS_DENIED).
Caso haja algum erro com o pedido é importante que o campo erro seja enviado junto com o status 5.

Exemplo de payload de aprovação de pedido:

``{ "status": 4 }``

Exemplo de payload de reprovação de pedido:

.. code-block:: python

   {
   "status":5,
   "error":{
      "type":"onyo.order.invalid-data",
      "message":"Código de Produto Inválido",
      "productErrors":[
         {
            "id":"http://api.onyo.com/v1/mobile/product/500",
            "error":{
               "type":"onyo.order.item-inconsistent"
            }
         }
      ]
   }
   }

Campos disponíveis para atualização.

.. csv-table::
   :header: "Campo", "TIPO", "OBRIGATÓRIO", "COMENTÁRIO"
   :widths: 20, 20, 20, 30

   "status", "Inteiro", "Não", "Status que o PDV deseja atualizar o pedido. Ex: 4 (pos-accepted), 5 (pos-denied) ou 6 (ready)."
   "error", "ErrorObject", "Sim", "Detalhes do motivo de negação do pedido pelo PDV"
   
ErrorObject:

.. csv-table::
   :header: "Campo", "TIPO", "OBRIGATÓRIO", "COMENTÁRIO"
   :widths: 20, 20, 20, 30

   "type", "String", "Sim", "Código de erro."
   "detail", "Object", "Não", "Detalhes do erro, para fins de debug, não precisa seguir um formato específico."
   "message", "String", "Não", "Mensagem de erro"
   "productErrors", "list of ProductErrorObject", "Não", "Lista de erros de produtos, caso tenha ocorrido erro especificamente em algum produto"
   
ProductErrorObject description:

.. csv-table::
   :header: "Campo", "TIPO", "OBRIGATÓRIO", "COMENTÁRIO"
   :widths: 20, 20, 20, 30

   "id", "URL", "Sim", "Url do produto que contém erro"
   "error", "ErrorObject", "Sim", "Objeto de erro"