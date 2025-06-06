# Projeto E-commerce C&J

**Integrantes:**
*   Cauê Domingues (RA: 1988969)
*   João Pedro Déo Gonçalves (RA: 1963003)

**Link do vídeo no YouTube:**
*   [Link a ser inserido aqui após o upload]

## Descrição do Projeto

Este projeto consiste em uma interface de e-commerce desenvolvida como parte de uma atividade acadêmica. O objetivo principal foi criar uma loja virtual interativa utilizando Vue.js 3 (com Composition API) e Vue Router para a navegação entre páginas. Para simular um catálogo de produtos dinâmico, o projeto integra-se com a API pública [DummyJSON](https://dummyjson.com/), que fornece dados de produtos, incluindo imagens, descrições, preços e categorias.

A aplicação apresenta um design responsivo, adaptando-se a diferentes tamanhos de tela, e utiliza Tailwind CSS para estilização, garantindo uma aparência moderna e consistente.

## Funcionalidades Implementadas

O C&J E-commerce oferece uma experiência de navegação intuitiva, permitindo aos usuários explorar produtos de diversas maneiras. A aplicação conta com uma barra de navegação lateral fixa que facilita o acesso às diferentes categorias de produtos disponíveis, como Fragâncias, Mobílias, Notebooks e Motos, além de um link para a Página Inicial que exibe um mix de todos os produtos.

Cada página de categoria, assim como a página inicial, apresenta os produtos em formato de cards, exibindo informações essenciais como imagem, título e preço. Para lidar com um grande volume de produtos, foi implementada a funcionalidade de paginação, permitindo ao usuário navegar sequencialmente pelos itens disponíveis tanto na visão geral quanto dentro de categorias específicas.

Ao clicar em um card de produto, o usuário é direcionado para uma página de detalhes dedicada, onde informações mais completas são apresentadas, incluindo uma imagem ampliada, descrição detalhada, marca, categoria, preço, estoque disponível e avaliação média (representada por estrelas). Um botão "Comprar" também está presente, embora sua funcionalidade de adição ao carrinho não esteja implementada nesta versão.

Adicionalmente, a barra de navegação lateral inclui um campo de busca dinâmica. Conforme o usuário digita o nome de um produto, a aplicação consulta a API em tempo real e exibe os resultados correspondentes logo abaixo do campo, com links diretos para as respectivas páginas de detalhes dos produtos encontrados.



## Instruções para Execução Local

Para executar este projeto em seu ambiente local, siga os passos abaixo. É necessário ter o Node.js e o npm (ou yarn) instalados em sua máquina.

Primeiramente, clone este repositório para o seu computador utilizando o comando:
```bash
git clone <URL_DO_REPOSITORIO>
```

Após clonar, navegue até o diretório raiz do projeto pelo terminal:
```bash
cd CAUE_ECOMMERCE
```

Em seguida, instale todas as dependências necessárias para o projeto. Execute o comando:
```bash
npm install
```
Ou, se preferir usar o Yarn:
```bash
yarn install
```

Com as dependências instaladas, você pode iniciar o servidor de desenvolvimento local. Utilize o comando:
```bash
npm run dev
```
Ou, com Yarn:
```bash
yarn dev
```

Este comando iniciará a aplicação utilizando o Vite. O terminal exibirá o endereço local (geralmente algo como `http://localhost:5173/`) onde a aplicação estará acessível. Abra este endereço em seu navegador para visualizar e interagir com o projeto.


Funcionalidades:
Pagina home:
![Home](https://github.com/user-attachments/assets/bfbdad6e-0f3c-4218-82ac-7610e3431f2a)

Sessão categorias:
![Categorias](https://github.com/user-attachments/assets/6761b04d-79d1-4fb8-8d51-234ac9a35749)

Barra de pesquisa:
![Pesquisa de itens](https://github.com/user-attachments/assets/f76c4e39-e108-443c-896d-38c571d8e5aa)

Barra de pesquisa em ação:
![Pesquisa de itens_descrição](https://github.com/user-attachments/assets/1ec7a077-dbc9-45c7-be86-708f3d760daa)

Quantidade em estoque:
![Quantidade estoque](https://github.com/user-attachments/assets/02d7b80c-2d4f-4fe1-a842-4723ef5e4f66)





