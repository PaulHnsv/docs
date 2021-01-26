.. PedePronto documentation , created by
   Paulo Henrique on Thu Jan 21 16:55:16 2021.


Autenticação
---------------------------------------

Todas as requisições abaixo devem ser autenticadas. A autenticação deve ser fornecida através do envio do token da company através do header HTTP Authorization.
O token da company pode ser fornecido diretamente pela Onyo ou pode ser obtido através das chamadas de login e company acima.
Por exemplo, caso a integração esteja configurada para trabalhar com o Amor os Pedaços do Shopping Mooca Plaza, então todas as chamadas devem ter o seguinte header:

``Authorization: Basic Mzg5OjM4OQ==``


Criação de resgate (offline-order)
---------------------------------------

**Endpoint:** POST /v1/{:PARTNER_SLUG}/offline-order

**Descrição:** Essa chamada é utilizada para que o PDV crie um resgate de pontos.
Nela, o PDV passa uma identificação do usuário e uma listagem de produtos e a API debita os pontos necessários do saldo de fidelidade daquele usuário.

Exemplo de payload:

.. code-block:: python

   {
		"customer_identifier": "1234231",
		"customer_identifier_type": "badge",
		"products": [
			{"pos_reference": "prod1", "quantity": "1.000"},
			...
		]
   }

Campos:

.. csv-table::
   :header: "Campo", "Tipo", "Obrigatório", "Comentário"
   :widths: 20, 20, 20, 40

   "customer_identifier", "String", "Sim", "Identificador do usuário"
   "customer_identifier_type", "String", "Sim", "Tipo da identificação. Por enquanto, só o valor “badge” é aceito."
   "products", "Lista de ProductObject", "Sim", "Lista de produtos"
   
ProductObject:

.. csv-table::
   :header: "Campo", "Tipo", "Obrigatório", "Comentário"
   :widths: 20, 20, 20, 40

   "pos_reference", "String", "Sim", "Identificador do produto na loja"
   "quantity", "String", "Sim", "Valor decimal da quantidade daquele produto"
   
Exemplo de resposta de sucesso:

.. code-block:: python
   
   200
   {}

Exemplo de resposta de falta de saldo:

.. code-block:: python

   400
   {
      "error": "onyo.order.redeem-insufficient-points",
      "message": ""
   }
