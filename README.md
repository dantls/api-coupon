
# API de Market e Cupons

Este projeto fornece uma API para gerenciar mercados e cupons associados a eles. A API permite listar mercados por categoria, visualizar detalhes de um mercado específico, e gerar cupons de desconto para os mercados.

## Tecnologias Utilizadas

- **Node.js**: Ambiente de execução para JavaScript.
- **Express.js**: Framework para construção da API.
- **Prisma**: ORM para interagir com o banco de dados.
- **Zod**: Biblioteca de validação de dados.
- **Crypto**: Módulo do Node.js para gerar cupons únicos.

## Instalação

1. **Clone o repositório**:

   ```bash
   git clone https://github.com/seu-usuario/nome-do-repositorio.git
   cd nome-do-repositorio
   ```

2. **Instale as dependências**:

   ```bash
   npm install
   ```

3. **Configuração do banco de dados**:
   Certifique-se de que o banco de dados está configurado corretamente. Utilize o Prisma para rodar as migrações necessárias:

   ```bash
   npx prisma migrate deploy
   ```

4. **Variáveis de ambiente**:
   Configure o arquivo `.env` para definir as credenciais do banco de dados, como:

   ```bash
   DATABASE_URL="postgresql://usuario:senha@localhost:5432/banco"
   ```

## Endpoints

### 1. **Obter mercados por categoria**

   **Método**: `GET`

   **Rota**: `/markets/:category_id`

   **Parâmetros**:
   - `category_id` (UUID): ID da categoria para filtrar os mercados.

   **Resposta**:
   - Retorna uma lista de mercados pertencentes à categoria especificada.

   **Exemplo de Requisição**:
   ```bash
   GET /markets/123e4567-e89b-12d3-a456-426614174000
   ```

   **Exemplo de Resposta**:
   ```json
   [
     {
       "id": "1",
       "name": "Mercado 1",
       "categoryId": "123e4567-e89b-12d3-a456-426614174000"
     },
     {
       "id": "2",
       "name": "Mercado 2",
       "categoryId": "123e4567-e89b-12d3-a456-426614174000"
     }
   ]
   ```

### 2. **Obter detalhes de um mercado específico**

   **Método**: `GET`

   **Rota**: `/markets/:id`

   **Parâmetros**:
   - `id` (UUID): ID do mercado para obter seus detalhes.

   **Resposta**:
   - Retorna os detalhes do mercado, incluindo as regras associadas a ele.

   **Exemplo de Requisição**:
   ```bash
   GET /markets/123e4567-e89b-12d3-a456-426614174000
   ```

   **Exemplo de Resposta**:
   ```json
   {
     "id": "123e4567-e89b-12d3-a456-426614174000",
     "name": "Mercado 1",
     "rules": [
       { "rule": "Desconto de 10%" }
     ]
   }
   ```

### 3. **Gerar um cupom para um mercado**

   **Método**: `POST`

   **Rota**: `/coupons/:market_id`

   **Parâmetros**:
   - `market_id` (UUID): ID do mercado para gerar um cupom.

   **Resposta**:
   - Retorna um código de cupom único.

   **Exemplo de Requisição**:
   ```bash
   POST /coupons/123e4567-e89b-12d3-a456-426614174000
   ```

   **Exemplo de Resposta**:
   ```json
   {
     "coupon": "ABC12345"
   }
   ```

   **Erros Possíveis**:
   - Se o mercado não for encontrado, o sistema retornará um erro 404.
   - Se não houver cupons disponíveis, retornará uma mensagem indicando a indisponibilidade.

## Execução

Para rodar a API em seu ambiente local, basta executar o comando abaixo:

```bash
npm run dev
```

Isso irá iniciar o servidor na porta `3000` (configurável através das variáveis de ambiente).

## Estrutura do Projeto

- `src/controllers`: Contém os controladores da API (`MarketsController`, `CouponsController`).
- `src/routes`: Define as rotas da API.
- `src/database`: Contém a configuração do Prisma.
- `src/utils`: Funções utilitárias (como o `AppError`).
- `prisma`: Contém os arquivos de migração e schema do banco de dados.

## Contribuindo

1. Fork este repositório.
2. Crie uma branch para a sua feature (`git checkout -b feature/nova-feature`).
3. Faça commit das suas mudanças (`git commit -am 'Adiciona nova feature'`).
4. Envie para o repositório remoto (`git push origin feature/nova-feature`).
5. Abra um Pull Request.

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).
```

Agora está tudo no formato correto para um arquivo `README.md`. Basta copiar e colar o conteúdo em um arquivo `.md` dentro do seu projeto.
