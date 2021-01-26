.. PedePronto documentation , created by
   Paulo Henrique on Thu Jan 21 16:55:16 2021.


Company
--------------------------

**Endpoint:** GET v1/{:PARTNER_SLUG}/companies

**Descrição:**
Essa chamada retorna todas as companies (restaurantes) cadastrados na Onyo e o seu respectivo token.
Esse token deverá ser utilizado em todas as chamadas subsequentes.

Essa chamada recebe autenticação via JWT, com o token do tipo Bearer recebido na chamada de login acima.

**Headers:**

.. csv-table::
   :header: "PARÂMETRO", "TIPO", "OBRIGATÓRIO", "COMENTÁRIO"
   :widths: 20, 20, 20, 30

   "Authorization",	"String", "Sim", "Deve conter o token Bearer de usuário retornado pelo login."

Exemplo de URL (com layout simples e sem paginação):
``v1/company``

Exemplo dos dados retornados:

.. code-block:: python
   
   [
    	{
        	"numericalId": 246,
        	"name": "Almanara - Cidade de SP",
        	"settings": {
            	"integrationName": "Without integration",
            	"integration": 0,
              "allowCreditRewards": false
        	},
        	"brand": "https://api.staging.onyo.com/v1/brand/85",
        	"posToken": "Basic XYX",
        	"brandName": "Almanara",
        	"id": "https://api.staging.onyo.com/v1/company/246"
    	},
    	{
        	"numericalId": 326,
        	"name": "Amor aos Pedaços - Cidade São Paulo",
        	"settings": {
            	"integrationName": "Without integration",
            	"integration": 0,
              "allowCreditRewards": false
        	},
        	"brand": "https://api.staging.onyo.com/v1/brand/114",
        	"posToken": "Basic XYX",
        	"brandName": "Amor aos Pedaços",
        	"id": "https://api.staging.onyo.com/v1/company/326"
    	},
    	{
        	"numericalId": 389,
        	"name": "Amor aos Pedaços - Mooca Plaza",
        	"settings": {
            	"integrationName": "Without integration",
            	"integration": 0,
              "allowCreditRewards": false
        	},
        	"brand": "https://api.staging.onyo.com/v1/brand/114",
        	"posToken": "Basic XYX",
        	"brandName": "Amor aos Pedaços",
        	"id": "https://api.staging.onyo.com/v1/company/389"
    	}
	]



