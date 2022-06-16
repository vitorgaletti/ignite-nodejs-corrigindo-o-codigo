# Desafio 03 - Corrigindo o código

## :computer: Sobre o desafio

<hr>

Nesse desafio, temos uma aplicação Node.js que está em processo de desenvolvimento mas que já possui os testes necessários para fazer toda a validação dos requisitos (você não deve mexer nos testes).
Após algumas alterações no código da aplicação, parte dos testes deixaram de passar e agora só você pode resolver esse problema. Bora lá? 🚀

Essa aplicação realiza o CRUD (**C**reate, **R**ead, **U**pdate, **D**elete) de repositórios de projetos. Além disso, é possível dar likes em repositórios cadastrados, aumentando a quantidade de likes em 1 a cada vez que a rota é chamada.

A estrutura de um repositório ao ser criado é a seguinte:

```jsx
{
  id: uuid(),
  title,
  url,
  techs,
  likes: 0
}
```

Descrição de cada propriedade:

- **id** deve ser um uuid válido;
- **title** é o título do repositório (por exemplo "unform");
- **url** é a URL que aponta para o repositório (por exemplo "[https://github.com/unform/unform](https://github.com/unform/unform)");
- **techs** é um array onde cada elemento deve ser uma string com o nome de uma tecnologia relacionada ao repositório (por exemplo: ["react", "react-native", "form"]);
- **likes** é a quantidade de likes que o repositório recebeu (e que vai ser incrementada de 1 em 1 a cada chamada na rota de likes).

Note que a quantidade de likes deve sempre ser zero no momento de criação.

## :rocket: Techs

<ul>
  <li> Javascript </li>
  <li> Node.js </li>
  <li> Express </li>
  <li> uuid </li>
  <li> cors </li>
</ul>

## Desenvolvimento

---

### Pré-requisitos

- Instalar [Node.js](https://nodejs.org)

- Instalar [Yarn](https://yarnpkg.com/)

### Clone o repositório

```bash
$ git clone https://github.com/vitorgaletti/ignite-nodejs-corrigindo-o-codigo.git
```

### Executar Projeto

```bash
# Mudar para directório
$ cd ignite-nodejs-corrigindo-o-codigo/
```

- Instalar dependências

```bash
$ yarn install
```

- Execute

```bash
$ yarn dev
```

- Executar scripts

|        Ação        | Utilização  |
| :----------------: | :---------: |
| Iniciar o servidor | `yarn dev`  |
|  Executar testes   | `yarn test` |

URL da API = http://localhost:3333

<br>

## API Reference

#### Listar todos os repositórios cadastrados

```http
GET /repositories
```

| Response Field | Type     | Description                                       |
| :------------- | :------- | :------------------------------------------------ |
| `id`           | `number` | Identificador do repositório                      |
| `title`        | `string` | Título do repositório                             |
| `url`          | `string` | Link do repositório                               |
| `techs`        | `array`  | Conjunto de tecnologias utilizadas no repositório |
| `likes`        | `number` | Quantidade de likes                               |

| Status code | Description          |
| :---------- | :------------------- |
| `200`       | Visualiza um usuário |

```json
{
  [
	  {
		"id": "8dccf4de-c357-4cee-ab3c-bbb2e8f45460",
		"title": "Umbriel",
		"url": "https://github.com/Rocketseat/umbriel",
		"techs": [
			"Node",
			"Express",
			"TypeScript"
		],
		"likes": 0
	  }
  ]
}
```

#### Criar um repositório

```http
POST /repositories
```

| Request Field | Type     | Description                                       |
| :------------ | :------- | :------------------------------------------------ |
| `title`       | `string` | Título da repositório                             |
| `url`         | `string` | Link do repositório                               |
| `techs`       | `array`  | Conjunto de tecnologias utilizadas no repositório |

| Status code | Description                    |
| :---------- | :----------------------------- |
| `201`       | Repositório criado com sucesso |

```json
{
  "title": "Umbriel",
  "url": "https://github.com/Rocketseat/umbriel",
  "techs": ["Node", "Express", "TypeScript"]
}
```

#### Alterar um repositório

```http
PUT /repositories/:id
```

| Parameter | Type     | Description                  |
| :-------- | :------- | :--------------------------- |
| `id`      | `number` | Identificador do repositório |

| Request Field | Type     | Description                                       |
| :------------ | :------- | :------------------------------------------------ |
| `title`       | `string` | Título do repositório                             |
| `url`         | `string` | Link do repositório                               |
| `techs`       | `array`  | Conjunto de tecnologias utilizadas no repositório |
| `likes`       | `number` | Quantidade de likes                               |

| Status code | Description                      |
| :---------- | :------------------------------- |
| `200`       | Repositório alterado com sucesso |
| `404`       | Repositório não encontrado       |

```json
{
  "title": "teste",
  "url": "https://github.com/vitorgaletti/ignite-nodejs-corrigindo-o-codigo",
  "techs": ["Python"],
  "likes": 10
}
```

#### Excluir uma repositório

```http
DELETE /repositories/:id
```

| Parameter | Type     | Description                  |
| :-------- | :------- | :--------------------------- |
| `id`      | `number` | Identificador do repositório |

| Status code | Description                      |
| :---------- | :------------------------------- |
| `204`       | Repositório excluido com sucesso |
| `404`       | Repositório não encontrado       |

#### Dar like no repositório

```http
POST /repositories/:id/like
```

| Parameter | Type     | Description                  |
| :-------- | :------- | :--------------------------- |
| `id`      | `number` | Identificador do repositório |

| Response Field | Type     | Description         |
| :------------- | :------- | :------------------ |
| `likes`        | `number` | Quantidade de likes |

| Status code | Description                     |
| :---------- | :------------------------------ |
| `200`       | Like no repositório com sucesso |
| `404`       | Repositório não encontrado      |

```json
{
  "likes": 1
}
```

## Autor

- [@vitorgaletti](https://github.com/vitorgaletti)
