.. PedePronto documentation , created by
   Paulo Henrique on Thu Jan 21 16:55:16 2021.

Apêndice
==================

Tipos de Pedido (order-type)
----------------------------------

.. csv-table::
   :header: "Id", "Código", "Descrição"
   :widths: 20, 20, 20


   "1",	"counter", "Um pedido a ser recebido no balcão para ser consumido no restaurante ou praça de alimentação"
   "2", "to-go", "Uma encomenda a ser retirada embalada para ser consumida em outro local"
   "3",	"curbside",	"Um pedido a ser retirado no Drive Thru"
   "4",	"table", "Um pedido para ser servido na mesa informada"
   "5",	"delivery", "Um pedido a ser entregue no endereço informado"
   "6",	"card", "Um pedido para ser registrado em um cartão de consumo"
   "7",	"payment", "Um pagamento por itens encomendados pessoalmente"
   "8",	"coupon", "Um pedido que será resgatado na loja, mas que não deve ser preparado até que o cliente a resgate pessoalmente"
   "9",	"room-service",	"Um pedido a ser entregue no local informado considerando algumas opções restritivas, como por exemplo um prédio comercial"
   

Status de Pedido
-------------------------

.. csv-table::
   :header: "Id", "Código", "Descrição"
   :widths: 20, 20, 20


   "0",	"canceled", "Cancelado devido ao pagamento ter sido negado ou cancelado manualmente pela Onyo"
   "1", "backend-received", "Aguardando processamento do pagamento "
   "2",	"payment-authorized", "Pagamento aprovado, aguardando processamento pelo PDV"
   "3",	"pos-received", "Recebido pelo PDV, aguardando confirmação"
   "4",	"pos-accepted", "Aceito pelo PDV"
   "5",	"pos-denied", "Negado pelo PDV"
   "6",	"ready", "Pedido pronto para ser recebido pelo consumidor (informado pela loja)"
   "7",	"dispatched", "Saiu para entrega (delivery)"
   "8",	"delivered", "Entregue para o consumidor"
   "9", "received", "Recebido pelo consumidor (informado pelo próprio consumidor)"
   "13", "preparing", "Pedido sendo preparado pela loja"
   "15", "product-unavailable", "Preparo do pedido pausado devido a indisponibilidade de algum produto. Aguardando decisão do consumidor"
   "16", "customer-action-needed", "Preparo do pedido pausado devido a uma dúvida do Staff da loja. Aguardando informação do consumidor"
   
Status não aplicáveis para integrações deste manual

.. csv-table::
   :header: "Id", "Código", "Descrição"
   :widths: 20, 20, 20
   
   "10", "consumed", "Consumido pelo cliente (Descontinuado)"
   "11", "pos-imported", "Importado pelo sistema de PDV"
   "12", "pos-import-error", "Não importado pelo sistema de PDV"
   "14", "pos-analysing", "Em análise pelo sistema de PDV"


Códigos de erro de pedido
----------------------------------

.. csv-table::
   :header: "Código", "Código para produto", "Comentário"
   :widths: 20, 20, 20
   
   "onyo.order.customer-invalid", "", "Quando há alguma inconsistência na informação do cliente entre a Onyo e o PDV"
   "onyo.order.item-invalid-value", "", "Quando há alguma inconsistência no valor do pedido entre a Onyo e o PDV"
   "onyo.order.order-invalid", "", "Quando há alguma inconsistência no formato do pedido entre a Onyo e o PDV"
   "onyo.order.payment-invalid", "", "Quando há alguma inconsistência no pagamento entre a Onyo e o PDV"
   "onyo.order.product-missing", "", "Quando está faltando um produto obrigatório para o pedido em questão"
   "onyo.order.invalid-data", "onyo.order.item-inconsistent", "Quando há alguma inconsistência no registro de um determinado produto (ex .: preço ou pontos)"
   "onyo.order.invalid-data", "onyo.order.item-quantity-min", "Quando a quantidade  de um determinado produto ou subproduto for inferior ao mínimo"
   "onyo.order.invalid-data", "onyo.order.item-subproduct-unexisting", "Quando o subproduto não pode ser pedido para um produto porque não existe para a loja ou não é filho do suposto produto pai"
   "onyo.order.invalid-data", "onyo.order.item-unavailable-time", "Quando o produto não pode ser pedido devido às restrições de tempo"
   "onyo.order.invalid-data", "onyo.order.item-unavailable", "Quando o produto não pode ser pedido porque está fora de estoque"
   "onyo.order.invalid-data", "onyo.order.item-unexisting", "Quando o produto informado não existe no PDV"