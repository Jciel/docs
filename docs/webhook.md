## Introdução

Webhook é uma forma de recebimento de informações quando um evento acontece. O webhook na prática, é a forma de receber informações entre dois sistemas de uma forma passiva.

O webhook é uma maneira prática e eficiente que a Squid Fácil usa para fornecer a outras aplicações informações em tempo real.

Enviaremos uma requisição HTTP POST para o URL cadastrada no painel da sua loja, com detalhes de todos os eventos inscritos. O formato de dados que você receberá é JSON.

## Eventos

### Estoque

Serão enviadas todas alterações de estoque, exceto produtos com mais de 500 unidades em estoque.

```json
{
   "type":"stock",
   "clientId":"6cd0aa38-0053-4dd3e-9029-1076e34D5d34",
   "sku":"SQUID3802",
   "quantity":400
}
```

### Preço

Serão enviadas todas alterações de preço.

```json
{
   "type":"price",
   "clientId":"6cd0aa38-0053-4dd3e-9029-1076e34D5d34",
   "sku":"SQUID3802",
   "oldPrice":22151,
   "newPrice":22473,
   "oldSuggestedPrice":33990,
   "newSuggestedPrice":33990
}
```

### Remessa imediata

Serão enviadas notificações quando o produto estiver disponível ou não para remessa imediata.

```json
{
   "type":"immediate-shipment",
   "clientId":"6cd0aa38-0053-4dd3e-9029-1076e34D5d34",
   "sku":"SQUID3802",
   "immediateShipment":false
}
```

### Status de disponibilidade

Serão enviadas notificações quando o produto estiver disponível ou não para compra.

```json
{
   "type":"availability-status",
   "clientId":"6cd0aa38-0053-4dd3e-9029-1076e34D5d34",
   "sku":"SQUID3802",
   "available":true
}
```

### Status do produto

Serão enviadas notificações quando o produto estiver ativo ou não no catálogo. Produtos inativos não aparecem no catálogo.
 
```json
{
   "type":"product-status",
   "clientId":"6cd0aa38-0053-4dd3e-9029-1076e34D5d34",
   "sku":"SQUID3799",
   "active":true
}
```

### Status do pedido

Serão enviadas notificações quando o pedido mudar de status.
 
```json
{
    "type":"order-status",
    "clientId":"6cd0aa38-0053-4dd3e-9029-1076e34D5d34",
    "orderId":"54616",
    "status":"Labeling",
    "motive":"",
    "updatedAt":"2017-04-21 00:22:04"
}
```

## Assinatura

Saiba como verificar a autenticidade de uma mensagem recebida.

A requisição do webhook que vem da Squid Fácil possui um campo no cabeçalho (HEADER) **X-Squid-Signature** que contém um json web token (JWT) [https://jwt.io/](https://jwt.io/) assinado pelo ***client_secret*** da sua loja.

O algoritmo utilizado é ***HS256***.