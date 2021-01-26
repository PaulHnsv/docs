.. PedePronto documentation , created by
   Paulo Henrique on Thu Jan 21 16:55:16 2021.


Autenticação
---------------------------------------

Todas as requisições abaixo devem ser autenticadas. A autenticação deve ser fornecida através do envio do token da company através do header HTTP Authorization.
O token da company pode ser fornecido diretamente pela Onyo ou pode ser obtido através das chamadas de login e company acima.
Por exemplo, caso a integração esteja configurada para trabalhar com o Amor os Pedaços do Shopping Mooca Plaza, então todas as chamadas devem ter o seguinte header:

``Authorization: Basic Mzg5OjM4OQ==``


Envio de SMS
---------------------------------------

**Endpoint:** POST /v1/{:PARTNER_SLUG}/sgm/sms

**Descrição:** Essa URL recebe um número de telefone celular e envia para ele um SMS convidando o usuário a fazer parte da Onyo.
Se o telefone já estiver cadastrado na nossa plataforma, ele retorna um erro.


Exemplo de envio de telefone com sucesso:

.. code-block:: python

   {telephone: "11234567890"}

Exemplo de resposta:

.. code-block:: python

   {"token": "c0256437-aa26-4da0-a6dc-e90ea390a432"}

Exemplo de envio de telefone com repetido:

.. code-block:: python

   {telephone: "11111111111"}

Exemplo de resposta:

.. code-block:: python

   {
	"description": {
    	"telephone": {
        	"rootError": "onyo.user.phone-already.exists"
    	}
	},
	"error": "onyo.user.phone-already.exists" 
   }
   
Campos:

.. csv-table::
   :header: "Campo", "Tipo", "Obrigatório", "Comentário"
   :widths: 20, 20, 20, 40

   "telephone",	"String", "Sim", "Número de celular para o qual será enviado o SMS. Deve ser o número completo com DDD, sem formatação."

