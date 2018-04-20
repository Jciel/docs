## Introdução

Bem-vindo! É através desta API que você irá integrar seu sistema ao nosso, todas operações que podem ser feitas com a API se encontra abaixo.

Nossa API é **RESTful** e todas as respostas são em JSON. 

## Endpoint

Todas as requisições são feitas no endpoint:

**https://app.squidfacil.com.br/api**

## Autenticação

![Screenshot](img/oauth.png)

Utilizamos o protocolo OAuth2 para autorização na API.

### Obter o token de acesso


Faça uma chamada **POST** em **https://app.squidfacil.com.br/oauth** usando as credenciais de integração da sua loja. No corpo de requisição, defina grant_type para **client_credentials**. Quando você executa o comando, a Squid Fácil gera e retorna um novo token de acesso (access token).

### Endpoint

POST https://app.squidfacil.com.br/oauth

### Parâmetros (form-data)

| Nome          | Descrição                                               | Detalhes          |
| ------------- | ------------------------------------------------------- | ----------------- |
| grant_type    | Tipo de autenticação (client_credentials)               | string, required  |
| client_id     | Identificador do cliente (encontrado no painel da loja) | string, required  |
| client_secret | Senha (encontrado no painel da loja)                    | string, required  |

### Resposta (JSON)

```json
{
  "access_token": "735edb27e0995d9fe4296dd912e9ea1d0165806d",
  "expires_in": 3600,
  "token_type": "Bearer",
  "scope": null
}
```

Após receber o token de acesso, para autenticar-se é necesśario mandar o seguinte cabeçalho (HEADER) nas proximas requisições (token demonstrativo):

Authorization: Bearer 735edb27e0995d9fe4296dd912e9ea1d0165806d

## Produtos

### Listar todos os produtos

Neste endpoint, retornaremos todos os produtos fornecidos por algum fornecedor em nosso catálogo, estejam eles disponíveis atualmente, ou não.

### Endpoint

GET https://app.squidfacil.com.br/api/products

### Parâmetros

| Nome          | Descrição                                                      | Detalhes          |
| ------------- | -------------------------------------------------------------- | ----------------- |
| page          | Página dos produtos à serem retornados.                        | number            |
| per_page      | Quantidade de produtos por página à serem retornados (Max:25). | number            |
| updated_since | Lista produtos que foram alterados desde a data informada.     | Y-m-d H:i:s       |

### Resposta (JSON)

```json
{
  "_links": {
    "self": {
      "href": "https://app.squidfacil.com.br/api/products?page=1"
    },
    "first": {
      "href": "https://app.squidfacil.com.br/api/products"
    },
    "last": {
      "href": "https://app.squidfacil.com.br/api/products?page=1328"
    },
    "next": {
      "href": "https://app.squidfacil.com.br/api/products?page=2"
    }
  },
  "_embedded": {
    "product": [
      {
        "sku": "SQUID3540",
        "name": "Capacete Urban Tamanho M Azul Bi061 - Atrio",
        "slug": "capacete-urban-tamanho-m-azul-bi061-atrio",
        "categories": [
          {
            "id": "57684886aaaec43423598086",
            "name": "Capacetes",
            "slug": "capacetes"
          }
        ],
        "brand": "Atrio",
        "warranty": 90,
        "available": true,
        "immediateShipment": false,
        "stockQuantity": 557,
        "gtin": "7899838806815",
        "ncm": "00000000",
        "images": [],
        "mainImage": {
          "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/capacete-urban-tamanho-m-azul-bi061-atrio1.png",
          "title": null,
          "types": {
            "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/capacete-urban-tamanho-m-azul-bi061-atrio1.png",
            "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/capacete-urban-tamanho-m-azul-bi061-atrio1.png",
            "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/capacete-urban-tamanho-m-azul-bi061-atrio1.png",
            "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/capacete-urban-tamanho-m-azul-bi061-atrio1.png"
          }
        },
        "attachments": [],
        "description": "- Esporte: Proteção Individual\r\n- Marca: Atrio/Multilaser\r\n- Modelo: Bi061\r\n- Referência: Capacete Urban\r\n- Cor (Es): Azul\r\n- Gênero: Unissex\r\n- Garantia Do Fabricante: 03 Meses Contra Defeitos De Fabricação",
        "shortDescription": "Capacete Urban Tamanho M Azul Bi061 - Atrio",
        "technicalDescription": "- Esporte: Proteção Individual\r\n- Marca: Atrio/Multilaser\r\n- Modelo: Bi061\r\n- Referência: Capacete Urban\r\n- Cor (Es): Azul\r\n- Gênero: Unissex\r\n- Garantia Do Fabricante: 03 Meses Contra Defeitos De Fabricação",
        "includedItems": "- 01 Capacete",
        "measurements": {
          "weight": 276,
          "height": 12,
          "length": 27,
          "width": 2
        },
        "suggestedRetailPrice": {
          "amount": 7990,
          "currency": "BRL"
        },
        "squidPrice": {
          "amount": 3970,
          "currency": "BRL"
        },
        "profitMargin": {
          "amount": 4020,
          "currency": "BRL"
        },
        "_embedded": {
          "category": {
            "id": "57684886aaaec43423598086",
            "name": "Capacetes",
            "slug": "capacetes",
            "parents": [
              {
                "id": "55ad24154c7a6fdb5013ab00",
                "name": "Para Bicicleta",
                "slug": "para-bicicleta"
              }
            ],
            "children": [],
            "_links": {
              "self": {
                "href": "https://app.squidfacil.com.br/api/categories/57684886aaaec43423598086"
              }
            }
          }
        },
        "_links": {
          "self": {
            "href": "https://app.squidfacil.com.br/api/products/SQUID3540"
          }
        }
      },
      {
        "sku": "SQUID3539",
        "name": "Capacete Urban Tamanho M Branco/Azul Bi059 - Atrio",
        "slug": "capacete-urban-tamanho-m-brancoazul-bi059-atrio",
        "categories": [
          {
            "id": "57684886aaaec43423598086",
            "name": "Capacetes",
            "slug": "capacetes"
          }
        ],
        "brand": "Atrio",
        "warranty": 90,
        "available": true,
        "immediateShipment": false,
        "stockQuantity": 672,
        "gtin": "7899838806792",
        "ncm": "00000000",
        "images": [
          {
            "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/capacete-urban-tamanho-m-brancoazul-bi059-atrio2.png",
            "title": null,
            "types": {
              "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/capacete-urban-tamanho-m-brancoazul-bi059-atrio2.png",
              "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/capacete-urban-tamanho-m-brancoazul-bi059-atrio2.png",
              "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/capacete-urban-tamanho-m-brancoazul-bi059-atrio2.png",
              "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/capacete-urban-tamanho-m-brancoazul-bi059-atrio2.png"
            }
          }
        ],
        "mainImage": {
          "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/capacete-urban-tamanho-m-brancoazul-bi059-atrio1.png",
          "title": null,
          "types": {
            "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/capacete-urban-tamanho-m-brancoazul-bi059-atrio1.png",
            "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/capacete-urban-tamanho-m-brancoazul-bi059-atrio1.png",
            "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/capacete-urban-tamanho-m-brancoazul-bi059-atrio1.png",
            "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/capacete-urban-tamanho-m-brancoazul-bi059-atrio1.png"
          }
        },
        "attachments": [],
        "description": "Capacete Urban Tamanho M Branco/Azul Bi059 - Atrio",
        "shortDescription": "Capacete Urban Tamanho M Branco/Azul Bi059 - Atrio",
        "technicalDescription": "- Esporte: Proteção Individual\r\n- Marca: Atrio/Multilaser\r\n- Modelo: Bi059\r\n- Referência: Capacete Urban\r\n- Cor (Es): Branco/Azul\r\n- Gênero: Unissex\r\n- Garantia Do Fabricante: 03 Meses Contra Defeitos De Fabricação",
        "includedItems": "- 01 Capacete Urban Tamanho M Branco/Azul Bi059",
        "measurements": {
          "weight": 270,
          "height": 2,
          "length": 28,
          "width": 15
        },
        "suggestedRetailPrice": {
          "amount": 7990,
          "currency": "BRL"
        },
        "squidPrice": {
          "amount": 3970,
          "currency": "BRL"
        },
        "profitMargin": {
          "amount": 4020,
          "currency": "BRL"
        },
        "_embedded": {
          "category": {
            "id": "57684886aaaec43423598086",
            "name": "Capacetes",
            "slug": "capacetes",
            "parents": [
              {
                "id": "55ad24154c7a6fdb5013ab00",
                "name": "Para Bicicleta",
                "slug": "para-bicicleta"
              }
            ],
            "children": [],
            "_links": {
              "self": {
                "href": "https://app.squidfacil.com.br/api/categories/57684886aaaec43423598086"
              }
            }
          }
        },
        "_links": {
          "self": {
            "href": "https://app.squidfacil.com.br/api/products/SQUID3539"
          }
        }
      }
    ]
  },
  "page_count": 1328,
  "page_size": 2,
  "total_items": 2655,
  "page": 1
}
```

### Listar todos os produtos disponíveis

Todos os produtos disponíveis para compra em nosso catálogo.

### Endpoint

GET https://app.squidfacil.com.br/api/products/available

### Parâmetros

| Nome          | Descrição                                                      | Detalhes          |
| ------------- | -------------------------------------------------------------- | ----------------- |
| page          | Página dos produtos à serem retornados.                        | number            |
| per_page      | Quantidade de produtos por página à serem retornados (Max:25). | number            |
| updated_since | Lista produtos que foram alterados desde a data informada.     | Y-m-d H:i:s       |

### Resposta (JSON)

```json
{
  "_links": {
    "self": {
      "href": "https://app.squidfacil.com.br/api/products/available?page=1"
    },
    "first": {
      "href": "https://app.squidfacil.com.br/api/products/available"
    },
    "last": {
      "href": "https://app.squidfacil.com.br/api/products/available?page=685"
    },
    "next": {
      "href": "https://app.squidfacil.com.br/api/products/available?page=2"
    }
  },
  "_embedded": {
    "product": [
      {
        "sku": "SQUID3540",
        "name": "Capacete Urban Tamanho M Azul Bi061 - Atrio",
        "slug": "capacete-urban-tamanho-m-azul-bi061-atrio",
        "categories": [
          {
            "id": "57684886aaaec43423598086",
            "name": "Capacetes",
            "slug": "capacetes"
          }
        ],
        "brand": "Atrio",
        "warranty": 90,
        "available": true,
        "immediateShipment": false,
        "stockQuantity": 557,
        "gtin": "7899838806815",
        "ncm": "00000000",
        "images": [],
        "mainImage": {
          "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/capacete-urban-tamanho-m-azul-bi061-atrio1.png",
          "title": null,
          "types": {
            "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/capacete-urban-tamanho-m-azul-bi061-atrio1.png",
            "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/capacete-urban-tamanho-m-azul-bi061-atrio1.png",
            "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/capacete-urban-tamanho-m-azul-bi061-atrio1.png",
            "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/capacete-urban-tamanho-m-azul-bi061-atrio1.png"
          }
        },
        "attachments": [],
        "description": "- Esporte: Proteção Individual\r\n- Marca: Atrio/Multilaser\r\n- Modelo: Bi061\r\n- Referência: Capacete Urban\r\n- Cor (Es): Azul\r\n- Gênero: Unissex\r\n- Garantia Do Fabricante: 03 Meses Contra Defeitos De Fabricação",
        "shortDescription": "Capacete Urban Tamanho M Azul Bi061 - Atrio",
        "technicalDescription": "- Esporte: Proteção Individual\r\n- Marca: Atrio/Multilaser\r\n- Modelo: Bi061\r\n- Referência: Capacete Urban\r\n- Cor (Es): Azul\r\n- Gênero: Unissex\r\n- Garantia Do Fabricante: 03 Meses Contra Defeitos De Fabricação",
        "includedItems": "- 01 Capacete",
        "measurements": {
          "weight": 276,
          "height": 12,
          "length": 27,
          "width": 2
        },
        "suggestedRetailPrice": {
          "amount": 7990,
          "currency": "BRL"
        },
        "squidPrice": {
          "amount": 3970,
          "currency": "BRL"
        },
        "profitMargin": {
          "amount": 4020,
          "currency": "BRL"
        },
        "_embedded": {
          "category": {
            "id": "57684886aaaec43423598086",
            "name": "Capacetes",
            "slug": "capacetes",
            "parents": [
              {
                "id": "55ad24154c7a6fdb5013ab00",
                "name": "Para Bicicleta",
                "slug": "para-bicicleta"
              }
            ],
            "children": [],
            "_links": {
              "self": {
                "href": "https://app.squidfacil.com.br/api/categories/57684886aaaec43423598086"
              }
            }
          }
        },
        "_links": {
          "self": {
            "href": "https://app.squidfacil.com.br/api/products/SQUID3540"
          }
        }
      },
      {
        "sku": "SQUID3539",
        "name": "Capacete Urban Tamanho M Branco/Azul Bi059 - Atrio",
        "slug": "capacete-urban-tamanho-m-brancoazul-bi059-atrio",
        "categories": [
          {
            "id": "57684886aaaec43423598086",
            "name": "Capacetes",
            "slug": "capacetes"
          }
        ],
        "brand": "Atrio",
        "warranty": 90,
        "available": true,
        "immediateShipment": false,
        "stockQuantity": 672,
        "gtin": "7899838806792",
        "ncm": "00000000",
        "images": [
          {
            "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/capacete-urban-tamanho-m-brancoazul-bi059-atrio2.png",
            "title": null,
            "types": {
              "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/capacete-urban-tamanho-m-brancoazul-bi059-atrio2.png",
              "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/capacete-urban-tamanho-m-brancoazul-bi059-atrio2.png",
              "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/capacete-urban-tamanho-m-brancoazul-bi059-atrio2.png",
              "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/capacete-urban-tamanho-m-brancoazul-bi059-atrio2.png"
            }
          }
        ],
        "mainImage": {
          "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/capacete-urban-tamanho-m-brancoazul-bi059-atrio1.png",
          "title": null,
          "types": {
            "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/capacete-urban-tamanho-m-brancoazul-bi059-atrio1.png",
            "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/capacete-urban-tamanho-m-brancoazul-bi059-atrio1.png",
            "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/capacete-urban-tamanho-m-brancoazul-bi059-atrio1.png",
            "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/capacete-urban-tamanho-m-brancoazul-bi059-atrio1.png"
          }
        },
        "attachments": [],
        "description": "Capacete Urban Tamanho M Branco/Azul Bi059 - Atrio",
        "shortDescription": "Capacete Urban Tamanho M Branco/Azul Bi059 - Atrio",
        "technicalDescription": "- Esporte: Proteção Individual\r\n- Marca: Atrio/Multilaser\r\n- Modelo: Bi059\r\n- Referência: Capacete Urban\r\n- Cor (Es): Branco/Azul\r\n- Gênero: Unissex\r\n- Garantia Do Fabricante: 03 Meses Contra Defeitos De Fabricação",
        "includedItems": "- 01 Capacete Urban Tamanho M Branco/Azul Bi059",
        "measurements": {
          "weight": 270,
          "height": 2,
          "length": 28,
          "width": 15
        },
        "suggestedRetailPrice": {
          "amount": 7990,
          "currency": "BRL"
        },
        "squidPrice": {
          "amount": 3970,
          "currency": "BRL"
        },
        "profitMargin": {
          "amount": 4020,
          "currency": "BRL"
        },
        "_embedded": {
          "category": {
            "id": "57684886aaaec43423598086",
            "name": "Capacetes",
            "slug": "capacetes",
            "parents": [
              {
                "id": "55ad24154c7a6fdb5013ab00",
                "name": "Para Bicicleta",
                "slug": "para-bicicleta"
              }
            ],
            "children": [],
            "_links": {
              "self": {
                "href": "https://app.squidfacil.com.br/api/categories/57684886aaaec43423598086"
              }
            }
          }
        },
        "_links": {
          "self": {
            "href": "https://app.squidfacil.com.br/api/products/SQUID3539"
          }
        }
      }
    ]
  },
  "page_count": 685,
  "page_size": 2,
  "total_items": 1369,
  "page": 1
}
```

### Listar todos os produtos indisponíveis

Todos os produtos que estão atualmente indisponíveis, fora de estoque ou desativados.

### Endpoint

GET https://app.squidfacil.com.br/api/products/unavailable

### Parâmetros

| Nome          | Descrição                                                      | Detalhes          |
| ------------- | -------------------------------------------------------------- | ----------------- |
| page          | Página dos produtos à serem retornados.                        | number            |
| per_page      | Quantidade de produtos por página à serem retornados (Max:25). | number            |
| updated_since | Lista produtos que foram alterados desde a data informada.     | Y-m-d H:i:s       |

### Resposta (JSON)

```json
{
  "_links": {
    "self": {
      "href": "https://app.squidfacil.com.br/api/products/unavailable?page=1"
    },
    "first": {
      "href": "https://app.squidfacil.com.br/api/products/unavailable"
    },
    "last": {
      "href": "https://app.squidfacil.com.br/api/products/unavailable?page=643"
    },
    "next": {
      "href": "https://app.squidfacil.com.br/api/products/unavailable?page=2"
    }
  },
  "_embedded": {
    "product": [
      {
        "sku": "SQUID3439",
        "name": "Super Massa Dinossauros Estrela",
        "slug": "super-massa-dinossauros-estrela",
        "categories": [
          {
            "id": "575091c0aaaec420e57f5ce8",
            "name": "Brinquedos 04 Anos em Diante",
            "slug": "brinquedos-04-anos-em-diante"
          },
          {
            "id": "575091f2aaaec44edc7f5d02",
            "name": "Brinquedos 04 Anos em Diante",
            "slug": "brinquedos-04-anos-em-Diante"
          }
        ],
        "brand": "Estrela",
        "warranty": 90,
        "available": false,
        "immediateShipment": false,
        "stockQuantity": 0,
        "gtin": "7896027545180",
        "ncm": "00000000",
        "images": [
          {
            "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/super-massa-dinossauros-estrela2.png",
            "title": null,
            "types": {
              "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/super-massa-dinossauros-estrela2.png",
              "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/super-massa-dinossauros-estrela2.png",
              "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/super-massa-dinossauros-estrela2.png",
              "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/super-massa-dinossauros-estrela2.png"
            }
          }
        ],
        "mainImage": {
          "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/super-massa-dinossauros-estrela1.png",
          "title": null,
          "types": {
            "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/super-massa-dinossauros-estrela1.png",
            "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/super-massa-dinossauros-estrela1.png",
            "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/super-massa-dinossauros-estrela1.png",
            "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/super-massa-dinossauros-estrela1.png"
          }
        },
        "attachments": [],
        "description": "A fabriquinha Super Massa da Estrela é a oportunidade ideal para os seus filhos começarem a criar formas e descobrir novas cores. São formas divertidas e moldes diferentes para a criança criar as mais variadas brincadeiras. A Super Massa Dinossauros vem vários moldes de dinossauros para a criança criar os animais mais aterrorizantes! Também acompanham moldes para criar árvores e brincar junto ao cenário. Um momento de muita diversão que irá desenvolver a coordenação motora, a criatividade, a imaginação, a percepção das cores, espessuras e muito mais. Um brinquedo que une diversão e aprendizagem!",
        "shortDescription": "Super Massa Dinossauros Estrela",
        "technicalDescription": "- Marca: Estrela\r\n- Tipo de Brincadeira: Massa de modelar\r\n- Idade recomendada: 3 a 4 anos\r\n- Gênero: Unissex\r\n- Composição/Material: Plástico\r\n- Número de Participantes: 1 ou mais\r\n- Como Brincar: Utilizar a massa de modelar para moldar árvores e dinossauros preferidos",
        "includedItems": "- 5 moldes de dinossauros\r\n- 1 molde do tronco de árvore\r\n- 1 molde para topo da árvore\r\n- 1 faca\r\n- 1 cenário A3\r\n- 3 potes Super Massa com 50g cada",
        "measurements": {
          "weight": 470,
          "height": 20,
          "length": 30,
          "width": 5
        },
        "_embedded": {
          "category": {
            "id": "575091c0aaaec420e57f5ce8",
            "name": "Brinquedos 04 Anos em Diante",
            "slug": "brinquedos-04-anos-em-diante",
            "parents": [
              {
                "id": "55a402ce7bec50e1413c809d",
                "name": "Brinquedos Meninos",
                "slug": "brinquedos-meninos"
              }
            ],
            "children": [],
            "_links": {
              "self": {
                "href": "http://app.squidfacil.com.br/api/categories/575091c0aaaec420e57f5ce8"
              }
            }
          }
        },
        "_links": {
          "self": {
            "href": "http://app.squidfacil.com.br/api/products/SQUID3439"
          }
        }
      },
      {
        "sku": "SQUID3341",
        "name": "Travesseiro Látex Lavável Sintético Eucaliptus p/fronhas 50x70",
        "slug": "travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x70",
        "categories": [
          {
            "id": "57053f1d263a7b6f441adce1",
            "name": "Travesseiros",
            "slug": "travesseiros"
          }
        ],
        "brand": "Fibrasca",
        "warranty": 90,
        "available": false,
        "immediateShipment": false,
        "stockQuantity": 0,
        "gtin": "7896630342169",
        "ncm": "94049000",
        "images": [
          {
            "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x702.png",
            "title": null,
            "types": {
              "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x702.png",
              "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x702.png",
              "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x702.png",
              "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x702.png"
            }
          },
          {
            "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x703.png",
            "title": null,
            "types": {
              "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x703.png",
              "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x703.png",
              "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x703.png",
              "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x703.png"
            }
          },
          {
            "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x704.png",
            "title": null,
            "types": {
              "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x704.png",
              "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x704.png",
              "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x704.png",
              "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x704.png"
            }
          },
          {
            "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x705.png",
            "title": null,
            "types": {
              "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x705.png",
              "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x705.png",
              "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x705.png",
              "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x705.png"
            }
          }
        ],
        "mainImage": {
          "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x701.png",
          "title": null,
          "types": {
            "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x701.png",
            "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x701.png",
            "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x701.png",
            "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/travesseiro-latex-lavavel-sintetico-eucaliptus-pfronhas-50x701.png"
          }
        },
        "attachments": [],
        "description": "Para um bom descanso, seja em casa ou durante uma viagem, o ideal é que se possa usufruir de travesseiros confortáveis, higiênicos e com altura que seja especifica para a cada necessidade pessoal e fisiológica.\r\nO Travesseiro Fibrasca Látex Sintético Eucaliptus, foi confeccionado com uma exclusiva tecnologia de moléculas abertas tornam possível a passagem da água por dentro da espuma de látex sintético, proporcionando mais praticidade ao lavar.\r\nPossui ainda orifícios de circulação do ar, que melhoram o frescor do produto, ajudando para prevenção de proliferação de ácaros, fungos e bactérias, visto que, seu revestimento em malha de algodão possui leve aroma de eucalipto em seu enchimento, proporcionando o melhor bem-estar ao deitar.",
        "shortDescription": "Travesseiro Látex Lavável Sintético Eucaliptus p/fronhas 50x70",
        "technicalDescription": "**Características Gerais**\r\n- Moderno e sofisticado \r\n- Deixará sua residência harmoniosa e delicada \r\n- Produzido através de matérias primas de boa qualidade \r\n- Resistente e seguro \r\n- Nº de Fios: Não Possui\r\n- Formato: Convencional\r\n- Composição do revestimento: 100% Viscose\r\n- Composição do enchimento: 100% Poliuretano\r\n- Tecido: Malha\r\n- Antialérgico: sim\r\n- Antiácaro: sim\r\n- Antibactéria: sim\r\n- Antifungo: sim\r\n- Íons de Prata: não\r\n- Anatômico: não\r\n- Ortopédico: não\r\n- Lavável: sim\r\n- Indicado p/: dormir de lado,de barriga p/ cima,de bruços\r\n- Medidas: 50 x 70 cm\r\n- Cor: Branco\r\n\r\n**Cuidados com o Produto **\r\n- Produto integralmente lavável em máquina; \r\n- Não lavar acima de 40ºC; \r\n- Não alvejar, não branquear; \r\n- Secar de preferência na posição horizontal.",
        "includedItems": "- 1 Travesseiro Fibrasca Látex Sintético Eucaliptus com Fibras Naturais em Malha 50 x 70 cm 1 Peça - Branco",
        "measurements": {
          "weight": 600,
          "height": 58,
          "length": 12,
          "width": 37
        },
        "_embedded": {
          "category": {
            "id": "57053f1d263a7b6f441adce1",
            "name": "Travesseiros",
            "slug": "travesseiros",
            "parents": [
              {
                "id": "56bb5f99263a7b466d00f432",
                "name": "Casa e Decoração",
                "slug": "casa-decoracao"
              }
            ],
            "children": [],
            "_links": {
              "self": {
                "href": "https://app.squidfacil.com.br/api/categories/57053f1d263a7b6f441adce1"
              }
            }
          }
        },
        "_links": {
          "self": {
            "href": "https://app.squidfacil.com.br/api/products/SQUID3341"
          }
        }
      }
    ]
  },
  "page_count": 643,
  "page_size": 2,
  "total_items": 1286,
  "page": 1
}
```

### Buscar um produto

Retorna um produto.

### Endpoint

GET https://app.squidfacil.com.br/api/products/[SKU]

### Parâmetros

| Nome          | Descrição                                   | Detalhes               |
| ------------- | ------------------------------------------- | ---------------------- |
| sku           | SKU do produto.                             | alphanumeric, required |


### Resposta (JSON)

```json
{
  "sku": "SQUID3439",
  "name": "Super Massa Dinossauros Estrela",
  "slug": "super-massa-dinossauros-estrela",
  "categories": [
    {
      "id": "575091c0aaaec420e57f5ce8",
      "name": "Brinquedos 04 Anos em Diante",
      "slug": "brinquedos-04-anos-em-diante"
    },
    {
      "id": "575091f2aaaec44edc7f5d02",
      "name": "Brinquedos 04 Anos em Diante",
      "slug": "brinquedos-04-anos-em-Diante"
    }
  ],
  "brand": "Estrela",
  "warranty": 90,
  "available": false,
  "immediateShipment": false,
  "stockQuantity": 0,
  "gtin": "7896027545180",
  "ncm": "00000000",
  "images": [
    {
      "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/super-massa-dinossauros-estrela2.png",
      "title": null,
      "types": {
        "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/super-massa-dinossauros-estrela2.png",
        "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/super-massa-dinossauros-estrela2.png",
        "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/super-massa-dinossauros-estrela2.png",
        "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/super-massa-dinossauros-estrela2.png"
      }
    }
  ],
  "mainImage": {
    "filename": "http://d27evgefuqvq7p.cloudfront.net/uploads/original/super-massa-dinossauros-estrela1.png",
    "title": null,
    "types": {
      "small": "http://d27evgefuqvq7p.cloudfront.net/uploads/small/super-massa-dinossauros-estrela1.png",
      "medium": "http://d27evgefuqvq7p.cloudfront.net/uploads/medium/super-massa-dinossauros-estrela1.png",
      "large": "http://d27evgefuqvq7p.cloudfront.net/uploads/large/super-massa-dinossauros-estrela1.png",
      "extralarge": "http://d27evgefuqvq7p.cloudfront.net/uploads/extralarge/super-massa-dinossauros-estrela1.png"
    }
  },
  "attachments": [],
  "description": "A fabriquinha Super Massa da Estrela é a oportunidade ideal para os seus filhos começarem a criar formas e descobrir novas cores. São formas divertidas e moldes diferentes para a criança criar as mais variadas brincadeiras. A Super Massa Dinossauros vem vários moldes de dinossauros para a criança criar os animais mais aterrorizantes! Também acompanham moldes para criar árvores e brincar junto ao cenário. Um momento de muita diversão que irá desenvolver a coordenação motora, a criatividade, a imaginação, a percepção das cores, espessuras e muito mais. Um brinquedo que une diversão e aprendizagem!",
  "shortDescription": "Super Massa Dinossauros Estrela",
  "technicalDescription": "- Marca: Estrela\r\n- Tipo de Brincadeira: Massa de modelar\r\n- Idade recomendada: 3 a 4 anos\r\n- Gênero: Unissex\r\n- Composição/Material: Plástico\r\n- Número de Participantes: 1 ou mais\r\n- Como Brincar: Utilizar a massa de modelar para moldar árvores e dinossauros preferidos",
  "includedItems": "- 5 moldes de dinossauros\r\n- 1 molde do tronco de árvore\r\n- 1 molde para topo da árvore\r\n- 1 faca\r\n- 1 cenário A3\r\n- 3 potes Super Massa com 50g cada",
  "measurements": {
    "weight": 470,
    "height": 20,
    "length": 30,
    "width": 5
  },
  "_embedded": {
    "category": {
      "id": "575091c0aaaec420e57f5ce8",
      "name": "Brinquedos 04 Anos em Diante",
      "slug": "brinquedos-04-anos-em-diante",
      "parents": [
        {
          "id": "55a402ce7bec50e1413c809d",
          "name": "Brinquedos Meninos",
          "slug": "brinquedos-meninos"
        }
      ],
      "children": [],
      "_links": {
        "self": {
          "href": "https://app.squidfacil.com.br/api/categories/575091c0aaaec420e57f5ce8"
        }
      }
    }
  },
  "_links": {
    "self": {
      "href": "https://app.squidfacil.com.br/api/products/SQUID3439"
    }
  }
}
```

## Estoques

Lista o estoque de todos os produtos.

### Endpoint

GET https://app.squidfacil.com.br/api/stocks

### Parâmetros

| Nome          | Descrição                                                        | Detalhes  |
| ------------- | ---------------------------------------------------------------- | ----------|
| page          | Página dos estoques à serem retornados.                          | number    |
| per_page      | Quantidade de produtos por página à serem retornados (Max:1000). | number    |


### Resposta (JSON)

```json
{
  "_links": {
    "self": {
      "href": "https://app.squidfacil.com.br/api/stocks?page=1"
    },
    "first": {
      "href": "https://app.squidfacil.com.br/api/stocks"
    },
    "last": {
      "href": "https://app.squidfacil.com.br/api/stocks?page=531"
    },
    "next": {
      "href": "https://app.squidfacil.com.br/api/stocks?page=2"
    }
  },
  "_embedded": {
    "stock": [
      {
        "sku": "SQUID11",
        "stockQuantity": "0"
      },
      {
        "sku": "SQUID13",
        "stockQuantity": "0"
      },
      {
        "sku": "SQUID14",
        "stockQuantity": "0"
      },
      {
        "sku": "SQUID15",
        "stockQuantity": "0"
      },
      {
        "sku": "SQUID16",
        "stockQuantity": "0"
      }
    ]
  },
  "page_count": 531,
  "page_size": 5,
  "total_items": 2655,
  "page": 1
}
```

## Pedidos

### Cadastrar pedidos

Neste endpoint é possível cadastrar um pedido no sistema da Squid Fácil. Você deve informar os dados do consumidor, lista de itens e as informações de entrega.

### Endpoint

POST https://app.squidfacil.com.br/api/orders

### Parâmetros (JSON)

```json
{
  "consumer": {
    "consumerType": "naturalPerson",
    "name": "João Silva",
    "email": "joao@example.com",
    "phoneNumber": "(15) 3031-4002",
    "mobilePhoneNumber": "(15) 9898-4002",
    "cpfCnpj": "26141951546",
    "address": {
      "postalCode": "18015-075",
      "street": "R. Padre Pedro Domingos Paes",
      "number": 109,
      "district": "Vila Haro"
    }
  },
  "items": [
    {
      "sku": "SQUID1869",
      "quantity": 1,
      "salePrice": 5000
    }
  ],
  "shippingMethod": "CUSTOM_LABEL",
  "customLabelUrl": "https://minha_url_etiqueta.com",
  "trackingCode": "SW485376878BR"
}
```

### Status do pedido

| Status                                                    | Descrição                                                       |
| --------------------------------------------------------- | --------------------------------------------------------------- |
| On request (Em solicitação)                               | Um pedido do produto foi feito para a fábrica. *                |
| In transit (Em trânsito)                                  | O pedido feito para fabrica está a caminho da Squid Fácil. *    |
| Labeling (Em emissão Fiscal)                              | Aguardando a emissão da nota fiscal.                            |
| Picking (Em separação)                                    | Separação e preparação do pedido.                               |
| On dispatch (Em expedição)                                | Expedição do pedido.                                            |
| Submitted (Remetido)                                      | Pedido enviado para o cliente final.                            |
| Sent (Entregue)                                           | Pedido entregue.                                                |
| Canceled (Cancelado)                                      | Pedido cancelado.                                               |
| Available for withdrawal (Disponível para retirada)       | Pedido com retirada local disponível para o cliente retirar.    |
| Awaiting item (Aguardando item)                           | Troca solicitada, aguardando produto do cliente.                |
| Awaiting exchange (Aguardando troca)                      | Produto a ser trocado chegou na Squid Fácil, processando troca. |

\* Somente pedidos de remessa normal (que não são remessa imediata) passam por esses status

### Dados variáveis

**Tipo do consumidor (consumerType):** naturalPerson ou legalPerson

**Situação do contribuinte (taxpayerSituation):** 1 = Contribuinte ICMS, 2 = Contribuinte isento e 3 = Não contribuinte

## Métodos de envio (shippingMethod):

| Nome             | Código          |
| ---------------- | --------------- |
| PAC              | PAC             |
| PAC + AR         | PAC_AR          |
| SEDEX            | SEDEX           |
| SEDEX + AR       | SEDEX_AR        |
| e-SEDEX          | E_SEDEX         |
| e-SEDEX + AR     | E_SEDEX_AR      |
| Jamef            | JAMEF           |
| Jadlog Econômico | JADLOG_ECONOMIC |
| Jadlog .com      | JADLOG_DOTCOM   |
| Minha Etiqueta   | CUSTOM_LABEL    |
| Retirada Local   | LOCAL_WITHDRAW  |

### Resposta (JSON)

```json
{
  "id": "2587",
  "date": "28/03/2016 10:53:48",
  "status": "Submitted",
  "subtotal": {
    "amount": 11668,
    "currency": "BRL"
  },
  "total": {
    "amount": 11868,
    "currency": "BRL"
  },
  "shipment": {
    "id": "CUSTOM_LABEL",
    "name": "Custom label",
    "trackingCode": null,
    "price": {
      "amount": 0,
      "currency": "BRL"
    }
  },
  "store": {
    "name": "Teste - SP",
    "platform": "Megafashion",
    "url": "",
    "phoneNumber": "12312312312",
    "mobilePhoneNumber": "12922222222",
    "address": {
      "country": "Brasil",
      "state": "SP",
      "postalCode": "18015062",
      "city": "Sorocaba",
      "district": "Vila Haro",
      "street": "Rua Padre Pedro Domingos Paes",
      "number": "115",
      "complement": ""
    }
  },
  "consumer": {
    "cpf": "26141951546",
    "name": "João Silva",
    "email": "joao@example.com",
    "phone": "(15) 3031-4002",
    "mobilePhone": "(15) 9898-4002",
    "address": {
      "country": "Brasil",
      "state": "SP",
      "postalCode": "18015-075",
      "city": "Sorocaba",
      "district": "Vila Haro",
      "street": "R. Padre Pedro Domingos Paes",
      "number": "109",
      "complement": ""
    }
  },
  "items": [
    {
      "product": "Polidor Automotivo - Au605",
      "sku": "SQUID1869",
      "quantity": 1,
      "price": {
        "amount": 11668,
        "currency": "BRL"
      },
      "salePrice": {
        "amount": 5000,
        "currency": "BRL"
      }
    }
  ],
  "_links": {
    "self": {
      "href": "https://app.squidfacil.com.br/api/orders/2587"
    }
  }
}
```

### Buscar um pedido

Retorna um pedido.

### Endpoint

GET https://app.squidfacil.com.br/api/orders/[order_id]

### Parâmetros

| Nome          | Descrição                                   | Detalhes               |
| ------------- | ------------------------------------------- | ---------------------- |
| order_id      | Identificador do pedido.                    | number, required       |


### Resposta (JSON)

```json
{
  "id": "42",
  "date": "02/09/2015 15:34:46",
  "status": "Submitted",
  "subtotal": {
    "amount": 43131,
    "currency": "BRL"
  },
  "total": {
    "amount": 44961,
    "currency": "BRL"
  },
  "shipment": {
    "id": "SEDEX",
    "name": "Sedex",
    "trackingCode": null,
    "price": {
      "amount": 1830,
      "currency": "BRL"
    }
  },
  "store": {
    "name": "Bob's store",
    "platform": "Magento",
    "url": "teste",
    "phoneNumber": "(47) 9645-1342",
    "mobilePhoneNumber": "(47) 9645-1341",
    "address": {
      "country": "Brasil",
      "state": "SC",
      "postalCode": "89027-450",
      "city": "Blumenau",
      "district": "Progresso",
      "street": "Rua Olga Hadlich",
      "number": "133",
      "complement": ""
    }
  },
  "consumer": {
    "cpf": "05331700950",
    "name": "James Woodson",
    "email": "jameswoodson@hotmail.com",
    "phone": "5539309999",
    "mobilePhone": "55888888888",
    "address": {
      "country": "Brasil",
      "state": "SP",
      "postalCode": "01311300",
      "city": "São Paulo",
      "district": "Bela Vista",
      "street": "Avenida Paulista",
      "number": "100",
      "complement": ""
    }
  },
  "items": [
    {
      "product": "Capa Clear View Galaxy S6 Edge Dourada ",
      "sku": "SQUID1864",
      "quantity": 3,
      "price": {
        "amount": 14377,
        "currency": "BRL"
      },
      "salePrice": {
        "amount": 15600,
        "currency": "BRL"
      }
    }
  ],
  "_links": {
    "self": {
      "href": "http://app.squidfacil.com.br/api/orders/42"
    }
  }
}
```

## Calcular frete

Você deve informar o código postal e uma lista de itens para receber as formas de entrega disponíveis.

### Endpoint

POST https://app.squidfacil.com.br/api/shipments

### Parâmetros (JSON)

```json
{
  "postalCode": "03110300",
  "items": [
    {
      "sku": "SQUID1234",
      "quantity": 5,
      "price": {
        "amount": 500,
        "currency": "BRL"
      }
    },
    {
      "sku": "SQUID1348",
      "quantity": 2,
      "price": {
        "amount": 550,
        "currency": "BRL"
      }
    }
  ]
}
```

### Resposta (JSON)

```json
{
  "0": {
    "id": "SEDEX",
    "name": "Sedex",
    "price": 2248,
    "currency": "BRL"
  },
  "1": {
    "id": "PAC",
    "name": "PAC",
    "price": 1514,
    "currency": "BRL"
  },
  "_links": {
    "self": {
      "href": "https://app.squidfacil.com.br/api/shipments"
    }
  }
}
```

## Loja

Neste endpoint, retornaremos o dados da sua loja.

### Endpoint

GET https://app.squidfacil.com.br/api/stores

### Resposta (JSON)

```json
{
  "_links": {
    "self": {
      "href": "https://app.squidfacil.com.br/api/stores"
    }
  },
  "_embedded": {
    "store": [
      {
        "id": "4270808f-d1d3-4314-a7e4-6c6b590c7a26",
        "name": "Teste - MG",
        "type": "CompanyStore",
        "status": "Approved",
        "platform": "Outra plataforma",
        "url": "",
        "address": {
          "street": "Rua oito",
          "number": "100",
          "complement": "",
          "district": "Centro",
          "city": "Campestre",
          "state": "MG",
          "country": "Brasil",
          "postalCode": "37730970"
        },
        "contact": {
          "phoneNumber": "0000000",
          "mobilePhoneNumber": "0000000"
        },
        "taxData": {
          "responsibleName": "João",
          "cnpj": "12689176000181",
          "taxpayerSituation": 1,
          "ie": "149.441.630/4749"
        },
        "webhook": {
          "isActive": true,
          "payloadUrl": "http://minha-url.com",
          "events": [
            "stock",
            "immediate-shipment",
            "availability-status"
          ]
        },
        "_links": {
          "self": {
            "href": "https://app.squidfacil.com.br/api/stores/4270808f-d1d3-4314-a7e4-6c6b590c7a26"
          }
        }
      }
    ]
  },
  "total_items": 1
}
```

## Webhook

Neste endpoint é possível cadastrar, atualizar e verificar a propriedade da URL.

### Endpoint

PATCH https://app.squidfacil.com.br/api/stores/[store_id]

### Parâmetros (JSON)
Cadastrar ou atualizar

```json
{
	"webhook": {
      "isActive": true,
      "payloadUrl": "http://minha-url.com",
      "events": [
          "stock",
          "immediate-shipment",
          "availability-status"
      ]
    }
}
```

### Eventos disponíveis

| Nome                      | Código              |
| ------------------------- | ------------------- |
| Estoque                   | stock               |
| Preço                     | price               |
| Remessa imediata          | immediate-shipment  |
| Status de disponibilidade | availability-status |
| Status do produto         | product-status      |
| Status do pedido          | order-status        |

Atenção: Sempre que você alterar a URL, vamos enviar uma requisição POST com um código de verificação para a URL. A verificação informa a Squid Fácil que você é um proprietário autorizado da URL informada.
Veja abaixo como verificar sua URL.

### Endpoint

PATCH https://app.squidfacil.com.br/api/stores/[store_id]

### Parâmetros (JSON)

Verificar a propriedade da URL, utilize o código de verificação recebido via POST. [Veja um exemplo de código de verificação recebido via POST.](webhook.md#codigo-de-verificacao)

```json
{
    "webhook": {
      "verificationCode": "4688163e-258f-43b0-9c18-2b009afd376e"
    }
}
```
