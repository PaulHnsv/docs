.. PedePronto documentation , created by
   Paulo Henrique on Thu Jan 21 16:55:16 2021.
   
Endpoints Da API
***********************

Login / Company
=====================

Os endpoints abaixo fazem parte do fluxo de Login e Company (cada company representa um restaurante parceiro da Onyo), o qual é utilizado para se obter o token da company, o qual é utilizado em todos os outros endpoints.
Caso a Onyo forneça o token da company, não é necessário implementar o fluxo abaixo.
O fluxo de Login e Company funciona da seguinte maneira:

1. Fazer uma chamada de Login para obter o token do usuário.
2. Fazer uma chamada de Company, usando o token do usuário, para obter a lista de companies.
3. Guardar o token da company escolhida para que ele seja utilizado nas demais chamadas.


.. toctree::
   :maxdepth: 2
   
   login
   company
   


Pedidos
=====================

.. toctree::
   :maxdepth: 2
   
   pedidos
   

Resgate
===============================

.. toctree::
   :maxdepth: 2
   
   resgate
   

Produtos
=============================

.. toctree::
   :maxdepth: 2
   
   produtos
   
   
Envio de SMS (SGM)
==============================

.. toctree::
   :maxdepth: 2
   
   SMS