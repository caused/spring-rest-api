# Exercício MasterTech - Ponto Eletronico
Projeto para teste de nivelamento do curso ministrado pela Mastertech

Nesse exercício foi utilizado as seguintes tecnologias:
* Java 8
* Spring Boot (2.1.5.RELEASE)
* Spring Data
* H2

Requisições abaixo foram feitas a partir de http://localhost:8080

# API de Usuário

## GET /usuario

O body de envio é vazio.

Exemplo de resposta:

```json
[
    {
        "id": 1,
        "nome": "Renato",
        "cpf": "111111111",
        "email": "renato@teste.com",
        "dataCadastro": "10/02/2020"
    },
    {
        "id": 2,
        "nome": "Gustavo",
        "cpf": "3794775852",
        "email": "gustavo@teste.com",
        "dataCadastro": "10/02/2020"
    }
]

```

## GET /usuario/{codigo}
Listagem somente de um usuário específico.



Exemplo de resposta:

```json
{
    "id": 1,
    "nome": "Renato",
    "cpf": "111111111",
    "email": "renato@teste.com",
    "dataCadastro": "10/02/2020"
}
```

## POST /usuario

exemplo de request:

```json
{
	"nome" :"Gustavo",
	"cpf" : "3794775852",
	"email" : "gustavo@teste.com",
	"dataCadastro" : "10/02/2020"
}
```

resposta:

```json
{
    "id": 1,
    "nome": "Gustavo",
    "cpf": "3794775852",
    "email": "gustavo@teste.com",
    "dataCadastro": "10/02/2020"
}
```

## PUT /usuario/{codigo}

Exemplo de request:

```json
{
	"cpf": "37948852875"
}
```

Exemplo de response:

```json
{
    "id": 1,
    "nome": "Gustavo",
    "cpf": "37948852875",
    "email": "gustavo@teste.com",
    "dataCadastro": "10/02/2020"
}
```

# API - Ponto Eletronico

## POST /ponto

Exemplo de request:

```json
{
	"dataHoraBatida" : "04/03/2020 18:00",
	"tipo" : "SAIDA",
	"usuario" : {
		"id" : 1
	}
}
```

Exemplo de response:

```json
{
    "id": 3,
    "dataHoraBatida": "2020-03-04T18:00:00",
    "tipo": "SAIDA"
}
```

## GET /ponto/{usuarioId}
API que retorna horas trabalhadas e ponto do usuário

Exemplo de response:

```json
{
    "horasTrabalhadas": 8,
    "usuario": {
        "id": 1,
        "nomeCompleto": "Renato",
        "cpf": "111111111",
        "email": "renato@teste.com",
        "dataCadastro": "2020-02-10",
        "listaPonto": [
            {
                "id": 2,
                "dataHoraBatida": "2020-03-04T10:00:00",
                "tipo": "ENTRADA"
            },
            {
                "id": 3,
                "dataHoraBatida": "2020-03-04T18:00:00",
                "tipo": "SAIDA"
            }
        ]
    }
}
```

