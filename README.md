# Documentação Técnica Website Easy360 (Backend)

## Descrição
Este guia fornece um passo a passo detalhado sobre como utilizar o novo projeto do website da Easy360.

Nosso objetivo foi migrar de um sistema com tecnologias desatualizadas, como PHP, para uma plataforma moderna e mais eficaz, garantindo maior agilidade nas manutenções futuras e adotando tecnologias amplamente utilizadas no mercado.


## Índice
1. [Introdução](#introducao)
2. [Requisitos](#requisitos)
3. [Instalação](#instalacao)
4. [Configuração](#configuracao)
5. [Uso](#uso)
6. [Estrutura do Projeto](#estrutura-do-projeto)
7. [API](#api)

---

## 1. Introdução <a name="introducao"></a>
O projeto foi totalmente pensado para utilizar uma tecnologia que daria menos dor de cabeça para os desenvolvedores e deixaria a aplicação mais fluida.

Na construção do backend, escolhemos a linguagem Node.js com o framework Express e TypeScript devido à sua alta performance em operações assíncronas e capacidade de gerenciar milhares de requisições simultâneas em tempo real.

Para o banco de dados, utilizamos PostgreSQL junto com a ORM Prisma para simplificar o gerenciamento de dados e otimizar o desenvolvimento.


## 2. Requisitos <a name="requisitos"></a>
Para garantir o funcionamento correto do projeto, alguns requisitos devem ser seguidos, como versões específicas de linguagem, bibliotecas e dependências externas.

Abaixo estão listadas todas as versões e pacotes necessários para o funcionamento da aplicação.

- Node.Js v20.180(LTS)

- PostgreSQL v16 

- Jsonwebtoken v9.0.2

- Bcrypt v5.1.1

- Nodemailer v6.9.15
  
---

## 3. Instalação <a name="instalacao"></a>
Passos para instalar o projeto localmente.

```bash
# Clonar o repositório
git clone https://github.com/NicollasDavi/easy360_backend
```
```bash
# Navegar para o diretório do projeto
cd .\easy360_backend\
```
```bash
# Instalar dependências
npm install
```

## 4. Configuração <a name="configuracao"></a>
Para garantir a segurança do projeto, foram criadas algumas variáveis de ambiente que estão localizadas no arquivo .env. No entanto, esse arquivo não é disponibilizado no repositório e deve ser criado dentro da pasta do projeto.

Para que o projeto funcione corretamente, crie o arquivo .env e digite o seguinte script dentro dele:

```bash
PORT=3000

DATABASE_URL="postgresql://postgres.ylolgjqittpydtpulwxo:94aRoRCjcotSSqeK@aws-0-us-west-1.pooler.supabase.com:6543/postgres?pgbouncer=true"

DIRECT_URL="postgresql://postgres.ylolgjqittpydtpulwxo:94aRoRCjcotSSqeK@aws-0-us-west-1.pooler.supabase.com:5432/postgres"
```

## 5. Uso <a name="uso"></a>
Instruções para rodar o projeto.

```bash
# Iniciar o projeto em desenvolvimento
npm run dev
```

```bash
# Iniciar o projeto em produção
npm start
```

## 6. Estrutura do Projeto <a name="estrutura-do-projeto"></a>
```
easy360_backend/
|
|  ├── node_modulos/       # Dependências do Node 
|  ├── prisma/             # Schema do banco de dados
|
|  ├── src/  
|  |   ├── controllers/    # Contém os controladores da aplicação 
|  |   ├── middleware/     # Contém as autenticações e autorizações
|  |   ├── routes/         # Define as rotas dos endpoints
|  |   └── utils/          # Lógica de envio de emails
|  |
|  └── index.ts            # Configura um servidor Express com diversas rotas de API e inicia o servidor na porta 3001
|  |
|  └── prismaClient.ts     # Inicializa e exporta uma instância do cliente Prisma para interações com o banco de dados
|  |
|  └── swagger.ts          # Configura a documentação da API usando Swagger
|
|
└── .env                   # Variáveis de ambiente
|
└── package-lock.json      # Gerencia dependências e scripts do projeto
|
└── package.json           # Garante a consistência das versões das dependências 
|
└── tsconfig.json          # Configura opções de compilação do TypeScript
```
## 7. API <a name="api"></a>
Exemplo de requisição e resposta da API:

GET http://localhost:3001/api/capaHome/buscar
* Retorna as infomações presentes na capa de home do website da Easy360
```
[
  {
    "id": 2,
    "titulo": "Desbloqueie o poder dos dados da sua indústria!",
    "texto": "Visualize de forma simples e fácil os Cenários e Gargalos do seu negócio para impulsionar sua competitividade.",
    "texto_botao": "Navegue pela Easy",
    "url_botao": "/",
    "texto_inferior": "Vamos lá!",
    "criado_em": "2024-10-21T18:33:01.099Z",
    "atualizado_em": "2024-10-23T01:25:30.214Z"
  }
]
```
PUT http://localhost:3001/api/capaHome/atualizar
* Deve ser passado no corpo da requisição o json para atualizar os campos
```
[
  {
    "titulo": "Campos atualizados",
    "texto": "Campos atualizados",
    "texto_botao": "Campos atualizados",
    "url_botao": "/",
    "texto_inferior": "Campos atualizados",
    "criado_em": "2024-10-21T18:33:01Z",
    "atualizado_em": "2024-10-23T01:25:30Z"
  }
]
```
Ao realizar as alterações um detalhe deve ser levado em consideração.

para os campos "criado_em" e "atualizado_em" devem seguir o formato ISO-8601

```bash
# Exemplo (10/12/2024 - 12:00)
2024-12-10T12:00:00Z
```







