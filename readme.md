# TRABALHO 01:  Gerenciamento de restaurante
Trabalho desenvolvido durante a disciplina de BD1

# Sumário

### 1. COMPONENTES<br>
Integrantes do grupo<br>
Daniel Henrique Alarcon: d.hapinheiro@gmail.com<br>
Henrique Bravim: henriquembravim@gmail.com<br>
João Victor Rangel: joao.victor00726@gmail.com<br>
...<br>

### 1.2 Introdução e Motivação
Este trabalho foi desenvolvido na disciplina de banco de dados do semestre 2024/1, com o objetivo de aplicar conceitos teóricos e práticos de modelagem e gerenciamento de banco de dados em um contexto hipotético.


### 2.MINI-MUNDO<br>

***Descrever o mini-mundo! (Não deve ser maior do que 30 linhas, se necessário resumir para justar) <br>
Entrevista com o usuário e identificação dos requisitos.(quando for o caso de sistemas com cliente  real)<br>
Descrição textual das regras de negócio definidas como um  subconjunto do mundo real 
cujos elementos são propriedades que desejamos incluir, processar, armazenar, 
gerenciar, atualizar, e que descrevem a proposta/solução a ser desenvolvida.

> O sofisticado restaurante "Le Gourmet", conhecido por sua sofisticação e excelência, enfrenta desafios na gestão devido sua clientela exigente. Para manter o alto padrão e eficiência, Sr.Manoel decidiu implementar um sistema integrado que garantisse a precisão no gerenciamento do seu negócio.
O sistema deve ter: Clientes, Pedidos, Menu, Inventário os clientes podem ser atendidos no restaurante ou fazer o pedido para entrega, cada cliente deve ter o nome, telefone para contato e local onde mora caso peça para entrega, os pedidos devem ser compostos por um ou mais itens do menu, podem ser para consumo local, viagem ou para entrega, cada pedido deve ter um status entre "em preparo, pronto, entregue ou cancelado", também deve registrar a data e hora do pedido. o Menu é deve ser composto por diversos itens, cada item possui nome, descrição, preço e categoria, o menu pode ser atualizado conforme necessário pelo gerente do estabelecimento. o inventário deve controlar os insumos e ingredientes necessários para a preparação dos itens do menu, cada item deve possuir um nome, quantidade disponível e data de validade, o inventário deve ser atualizado conforme os insumos são utilizados e repostos.

### 3.PERGUNTAS A SEREM RESPONDIDAS<br>
#### 3.1 QUAIS PERGUNTAS PODEM SER RESPONDIDAS COM O SISTEMA PROPOSTO?
    a) O sistema proposto poderá fornecer quais tipos de relatórios e informaçes? 
> Nosso pricipal foco dos relatorios é monitorar quantidade de vendas para garantir que negocio do cliente está progredindo positivamente.
    
    b) Crie uma lista com os 5 principais relatórios que poderão ser obtidos por meio do sistema proposto!
    
> Nosso sistema do restaurante precisa inicialmente dos seguintes relatórios:
* Relatorio informando a quantidade de cliente atendido de um periodo.
* Relatorio que calcule todas as vendas de um periodo e informe um valor bruto.
* Relatorio de itens fora de estoque.
* Relatorio de vendas por categoria informando quais itens do cardápio foram mais vendidos de um periodo.
* Relatorio de custo e margem de lucro calculando os custos dos ingredientes em relação ao relatorio de de vendas para determinar a margem de lucro.

    
### 5.MODELO CONCEITUAL<br>
    ***A) Utilizar a Notação adequada (Preferencialmente utilizar o BR Modelo 3)
    B) O mínimo de entidades do modelo conceitual pare este trabalho será igual a 3 e o Máximo 5.
        * informe quais são as 3 principais entidades do sistema em densenvolvimento<br>(se houverem mais de 3 entidades, pense na importância da entidade para o sistema)       
    C) Principais fluxos de informação/entidades do sistema (mínimo 3). <br>Dica: normalmente estes fluxos estão associados as tabelas que conterão maior quantidade de dados 
    D) Qualidade e Clareza
        Garantir que a semântica dos atributos seja clara no esquema (nomes coerentes com os dados).
        Criar o esquema de forma a garantir a redução de informação redundante, possibilidade de valores null, 
        e tuplas falsas (Aplicar os conceitos de normalização abordados).   
        
![image](https://github.com/user-attachments/assets/dd0e944e-051b-4fbc-acea-5e73b27cacaf)

#### 5.1 Validação do Modelo Conceitual
    [Grupo01]: [Nomes dos que participaram na avaliação]
    [Grupo02]: [Nomes dos que participaram na avaliação]

#### 5.2 Descrição dos dados 
	MENU: Tabela que armazena informações relativas ao cardápio do restaurante.
	ID_MENU: Campo que armazena a chave primária de um item da tabela Menu.
	NOME: Campo que armazena o nome do item no cardápio.
	DESCRICAO: Campo que armazena a descrição detalhada do item no cardápio.
	PRECO: Campo que armazena o preço do item no cardápio.
	***CATEGORIA: Campo que armazena a categoria que o item pertence (exemplo: entrada, prato principal, sobremesa).
	
	ITEM: Tabela que armazena informações relativas aos itens.
	ID_ITEM: Campo que armazena a chave primária de um item na tabela de itens.
	QUANTIDADE: Campo que armazena a quantidade do item em um pedido específico.
	
	PEDIDO: Tabela que armazena informações relativas aos pedidos feitos no restaurante.
	ID_PEDIDO: Campo que armazena a chave primária de um pedido.
	DATA_HORA: Campo que armazena a data e a hora que o pedido foi realizado.
	STATUS: Campo que armazena o status atual do pedido (exemplo: entregue, preparando ou cancelado).
	TIPO: Campo que armazena o tipo do pedido (exemplo: para entrega ou consumo no local).
	
	CLIENTE: Tabela que armazena as informações relativas aos clientes do restaurante.
	ID_CLIENTE: Campo que armazena a chave primária do cliente.
	NOME: Campo que armazena o nome do cliente.
	TELEFONE: Campo que armazena o número de contato do cliente.
	ENDERECO: Campo que armazena o endereço do cliente para entrega de pedidos.
	
	INVENTARIO: Tabela que armazena as informações relativas ao inventário do restaurante.
	ID_INVENTARIO: Campo que armazena a chave primária de um item do inventário.
	NOME: Campo que armazena o nome do item no inventário.
	QTD_DISPONIVEL: Campo que armazena a quantidade disponível de um item no inventário.
	DATA_VALIDADE: Campo que armazena a data de validade do item no inventário.

    

># Marco de Entrega 01: Do item 1 até o item 5.2 (5 PTS) <br> 

### 6	MODELO LÓGICO<br>
        a) inclusão do esquema lógico do banco de dados
        b) verificação de correspondencia com o modelo conceitual 
        (não serão aceitos modelos que não estejam em conformidade)
![image](https://github.com/user-attachments/assets/75bc07f2-66d6-4c0f-91ca-400af497a658)


### 7	MODELO FÍSICO<br>
        a) inclusão das instruções de criacão das estruturas em SQL/DDL 
        (criação de tabelas, alterações, etc..) 

	CREATE TABLE IF NOT EXISTS Cliente (
	    id_cliente SERIAL PRIMARY KEY,
	    nome VARCHAR(255) NOT NULL,
	    telefone VARCHAR(20),
	    endereco VARCHAR(255)
	);
	
	CREATE TABLE IF NOT EXISTS Inventario (
	    id_inventario SERIAL PRIMARY KEY,
	    nome VARCHAR(255) NOT NULL,
	    quantidade_disponivel INT NOT NULL,
	    data_validade DATE
	    
	CREATE TABLE IF NOT EXISTS Menu (
	    id_menu SERIAL PRIMARY KEY,
	    nome VARCHAR(255) NOT NULL,
	    descricao VARCHAR(255),
	    preco FLOAT NOT NULL
	);
	
	CREATE TABLE IF NOT EXISTS Item (
	    id_item SERIAL PRIMARY KEY,
	    fk_id_menu INT NOT NULL,
	    quantidade INT NOT NULL,
	    FOREIGN KEY (fk_id_menu) REFERENCES Menu(id_menu)
	);
	
	CREATE TABLE IF NOT EXISTS Pedido (
	    id_pedido SERIAL PRIMARY KEY,
	    fk_id_cliente INT NOT NULL,
	    fk_id_item INT NOT NULL,
	    data_hora TIMESTAMP NOT NULL,
	    status VARCHAR(50) NOT NULL,
	    tipo VARCHAR(50) NOT NULL,
	    FOREIGN KEY (fk_id_cliente) REFERENCES Cliente(id_cliente),
	    FOREIGN KEY (fk_id_item) REFERENCES Item(id_item)
	);
      
### 8	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>
        ***a) Script das instruções relativas a inclusão de dados 
	Requisito mínimo: (Script dev conter: Drop para exclusão de tabelas + create definição de para tabelas e estruturas de dados + insert para dados a serem inseridos)
        OBS
	1) Criar um novo banco de dados para testar a restauracao (em caso de falha na restauração o grupo não pontuará neste quesito)
        2) script deve ser incluso no template em um arquivo no formato .SQL

	-- Criação do banco de dados
	DROP DATABASE IF EXISTS RestauranteDB;
	CREATE DATABASE RestauranteDB;
	
	-- Criando as tabelas:
	CREATE TABLE Cliente (
	    id_cliente SERIAL PRIMARY KEY,
	    nome VARCHAR(100) NOT NULL,
	    telefone VARCHAR(15) NOT NULL,
	    endereco VARCHAR(255)
	);
	
	CREATE TABLE Inventario (
	    id_inventario SERIAL PRIMARY KEY,
	    nome VARCHAR(100) NOT NULL,
	    quantidade_disponivel INTEGER NOT NULL,
	    data_validade DATE NOT NULL
	);
	
	CREATE TABLE Menu (
	    id_menu SERIAL PRIMARY KEY,
	    nome VARCHAR(100) NOT NULL,
	    descricao VARCHAR,
	    preco DECIMAL(10, 2) NOT NULL
	);
	
	CREATE TABLE Item (
	    id_item SERIAL PRIMARY KEY,
	    fk_id_menu INTEGER,
	    quantidade INTEGER NOT NULL,
	    FOREIGN KEY (fk_id_Menu) REFERENCES Menu(ID_Menu)
	);
	
	CREATE TABLE Pedido (
	    id_pedido SERIAL PRIMARY KEY,
	    fk_id_cliente INTEGER,
	    fk_id_item INTEGER,
	    data_hora TEXT NOT NULL,
	    status VARCHAR NOT NULL,
	    tipo VARCHAR NOT NULL,
	    FOREIGN KEY (fk_id_Item) REFERENCES Item(id_item),
	    FOREIGN KEY (fk_id_Cliente) REFERENCES Cliente(id_cliente)
	);
	
	-- Inserindo dados nas tabelas:
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Ana Silva', '1234567890', 'Rua das Flores, 123');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Carlos Oliveira', '2345678901', 'Avenida Paulista, 456');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Maria Santos', '3456789012', 'Rua do Comércio, 789');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('João Pereira', '4567890123', 'Rua da Alegria, 101');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Lucas Lima', '5678901234', 'Avenida Brasil, 202');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Fernanda Costa', '6789012345', 'Rua das Palmeiras, 303');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Roberto Fernandes', '7890123456', 'Rua dos Coqueiros, 404');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Patrícia Almeida', '8901234567', 'Rua das Orquídeas, 505');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Felipe Martins', '9012345678', 'Avenida das Magnólias, 606');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Juliana Silva', '0123456789', 'Rua dos Jacarandás, 707');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Daniel Oliveira', '1234567891', 'Rua das Begônias, 808');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Isabela Lima', '2345678902', 'Rua dos Ipês, 909');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Ricardo Souza', '3456789013', 'Rua dos Cedros, 1010');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Amanda Costa', '4567890124', 'Avenida das Rosas, 1111');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Pedro Santos', '5678901235', 'Rua das Azaléias, 1212');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Sofia Fernandes', '6789012346', 'Rua das Figueiras, 1313');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Gustavo Pereira', '7890123457', 'Rua dos Lírios, 1414');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Carla Almeida', '8901234568', 'Rua dos Cravos, 1515');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Marcelo Lima', '9012345679', 'Avenida das Cactos, 1616');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Eliane Silva', '0123456790', 'Rua dos Girassóis, 1717');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Thiago Martins', '1234567892', 'Rua das Violetas, 1818');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Larissa Costa', '2345678903', 'Rua das Magnólias, 1919');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('André Oliveira', '3456789014', 'Rua dos Jacarandás, 2020');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Michele Fernandes', '4567890125', 'Rua das Azaléias, 2121');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Jorge Souza', '5678901236', 'Rua das Orquídeas, 2222');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Nathália Almeida', '6789012347', 'Rua dos Lírios, 2323');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Eduardo Santos', '7890123458', 'Rua dos Cedros, 2424');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Ana Paula Lima', '8901234569', 'Rua das Rosas, 2525');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Fábio Costa', '9012345680', 'Rua das Begônias, 2626');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Juliano Silva', '0123456791', 'Rua dos Ipês, 2727');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Raquel Pereira', '1234567893', 'Rua dos Coqueiros, 2828');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Joana Fernandes', '2345678904', 'Rua das Figueiras, 2929');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Lucas Souza', '3456789015', 'Avenida das Cactos, 3030');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Patrícia Lima', '4567890126', 'Rua das Violetas, 3131');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Ricardo Pereira', '5678901237', 'Rua dos Girassóis, 3232');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Beatriz Almeida', '6789012348', 'Rua dos Cedros, 3333');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Vinícius Martins', '7890123459', 'Rua das Azaléias, 3434');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Elaine Silva', '8901234570', 'Rua das Magnólias, 3535');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Luana Santos', '9012345681', 'Rua dos Jacarandás, 3636');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Thiago Oliveira', '0123456792', 'Rua dos Coqueiros, 3737');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Juliana Fernandes', '1234567894', 'Rua das Orquídeas, 3838');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Bruno Costa', '2345678905', 'Rua das Figueiras, 3939');
	INSERT INTO Cliente (nome, telefone, endereco) VALUES ('Ana Clara Lima', '3456789016', 'Rua das Violetas, 4040');
	
	
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Farinha', 100, '2024-12-31');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Açúcar', 200, '2024-11-30');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Ovo', 500, '2024-10-15');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Leite', 150, '2024-09-20');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Manteiga', 80, '2024-08-10');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Queijo', 120, '2024-12-01');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Presunto', 90, '2024-11-15');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Tomate', 200, '2024-10-30');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Cebola', 180, '2024-09-15');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Alho', 75, '2024-08-25');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Cenoura', 160, '2024-11-10');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Batata', 200, '2024-12-20');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Abobrinha', 140, '2024-10-05');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Pimentão', 130, '2024-11-01');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Brócolis', 110, '2024-09-30');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Espinafre', 90, '2024-12-10');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Alface', 180, '2024-08-15');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Rúcula', 100, '2024-11-20');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Couve', 120, '2024-09-05');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Feijão', 300, '2025-01-15');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Arroz', 250, '2025-02-01');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Macarrão', 200, '2024-12-25');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Salsa', 90, '2024-08-30');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Manjericão', 80, '2024-09-10');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Orégano', 70, '2024-10-05');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Páprica', 60, '2024-11-20');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Cominho', 55, '2024-12-01');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Alecrim', 65, '2024-09-25');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Louro', 75, '2024-10-15');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Canela', 85, '2024-12-05');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Cravo', 95, '2024-11-10');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Gengibre', 110, '2024-09-20');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Azeite', 120, '2025-01-10');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Vinagre', 130, '2025-02-20');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Molho de Soja', 100, '2025-03-15');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Ketchup', 140, '2025-04-10');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Maionese', 150, '2025-05-05');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Mostarda', 160, '2025-06-01');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Mel', 90, '2025-07-10');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Açúcar Mascavo', 70, '2025-08-15');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Sal', 80, '2025-09-20');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Pimenta', 85, '2025-10-25');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Chá', 95, '2025-11-30');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Peito de Frango', 50, '2025-08-03');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Carne Moída', 50, '2025-08-03');
	
	
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Pizza Margherita', 'Pizza com molho de tomate e queijo mozzarella', 29.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Cookie de Nutella', 'Cookie Recheado com Nutella e gotas de chocolate', 34.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Coxinha', 'Massa com Frango e Catupiry', 5.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Kibe', 'Massa de Triguilho com carne moída', 5.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Joelho de Presunto e Queijo', 'Massa com Presunto e Queijo', 29.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Lasanha à Bolonhesa', 'Lasanha com molho à bolonhesa e queijo', 34.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Hambúrguer Classic', 'Hambúrguer com queijo, alface e tomate', 19.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Espaguete à Carbonara', 'Espaguete com molho cremoso de ovo e queijo', 24.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Risoto de Cogumelos', 'Risoto cremoso com cogumelos e parmesão', 28.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Salmão Grelhado', 'Salmão grelhado com molho de limão e ervas', 35.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Filé Mignon', 'Filé mignon grelhado com batatas', 42.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Coxa de Frango Assada', 'Coxa de frango assada com legumes', 22.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Sopa de Abóbora', 'Sopa cremosa de abóbora com especiarias', 18.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Salada Caesar', 'Salada com peito de frango, queijo parmesão e molho Caesar', 21.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Tiramisu', 'Sobremesa italiana de café e mascarpone', 14.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Cheesecake', 'Cheesecake com calda de frutas vermelhas', 16.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Brownie', 'Brownie de chocolate com sorvete', 12.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Mousse de Maracujá', 'Mousse leve de maracujá', 15.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Pudim', 'Pudim tradicional de leite', 13.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Café Espresso', 'Café forte e concentrado', 6.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Chá Verde', 'Chá verde fresco e aromático', 7.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Suco de Laranja', 'Suco natural de laranja', 8.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Água Mineral', 'Água mineral com gás', 4.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Refri', 'Refrigerante sabor cola', 5.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Pizza Calabresa', 'Pizza com calabresa, cebola e azeitonas', 31.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Pizza Quatro Queijos', 'Pizza com quatro tipos de queijo', 33.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Pizza de Frango com Catupiry', 'Pizza de frango desfiado com catupiry', 32.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Pizza de Peperoni', 'Pizza com fatias de peperoni e queijo', 34.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Calzone de Presunto e Queijo', 'Calzone recheado com presunto e queijo', 25.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Lasanha Vegetariana', 'Lasanha com vegetais e molho de tomate', 27.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Spaghetti ao Pesto', 'Espaguete com molho pesto de manjericão', 26.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Frango Tandoori', 'Frango marinado e assado com especiarias indianas', 31.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Bife a Cavalo', 'Bife com ovo frito e arroz', 29.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Sushi Mix', 'Combinado de sushi com variedade de peixes', 39.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Temaki de Salmão', 'Temaki recheado com salmão fresco', 22.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Yakimeshi', 'Arroz frito com legumes e carne', 24.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Paella', 'Paella de frutos do mar com arroz', 42.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Bacalhau à Brás', 'Bacalhau desfiado com batata palha e ovos', 35.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Feijoada', 'Feijoada completa com acompanhamentos', 34.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Moqueca', 'Moqueca de peixe com arroz e farofa', 37.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Frango à Parmegiana', 'Frango empanado com molho de tomate e queijo', 29.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Canelone de Carne', 'Canelone recheado com carne moída e queijo', 26.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Ravioli de Queijo', 'Ravioli recheado com queijo e molho de manteiga', 25.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Picanha na Brasa', 'Picanha grelhada com molho de alho', 40.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Costela de Porco', 'Costela assada com barbecue', 35.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Pasta Alfredo', 'Pasta com molho Alfredo de queijo', 27.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Pão de Alho', 'Pão com alho e manteiga', 12.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Croissant', 'Croissant fresco e amanteigado', 10.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Empada de Frango', 'Empada recheada com frango', 15.90);
	INSERT INTO Menu (nome, descricao, preco) VALUES ('Risoto de Camarão', 'Risoto com Camarão', 35.90);
	
	
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (1, 100);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (2, 80);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (3, 150);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (4, 60);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (5, 70);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (6, 90);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (7, 50);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (8, 110);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (9, 130);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (10, 120);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (11, 90);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (12, 70);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (13, 60);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (14, 40);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (15, 100);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (16, 80);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (17, 90);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (18, 70);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (19, 50);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (20, 30);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (21, 40);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (22, 50);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (23, 60);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (24, 70);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (25, 80);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (26, 90);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (27, 100);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (28, 110);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (29, 120);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (30, 130);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (31, 140);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (32, 150);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (33, 160);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (34, 170);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (35, 180);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (36, 190);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (37, 200);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (38, 210);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (39, 220);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (40, 230);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (41, 240);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (42, 250);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (43, 260);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (44, 270);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (45, 280);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (46, 290);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (47, 300);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (48, 310);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (49, 320);
	INSERT INTO Item (fk_id_menu, quantidade) VALUES (50, 330);
	
	
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (1, 1, '2024-08-01 12:00:00', 'Entregue', 'Dine-in');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (2, 2, '2024-08-01 12:30:00', 'Preparando', 'Takeaway');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (3, 3, '2024-08-01 13:00:00', 'Cancelado', 'Delivery');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (4, 4, '2024-08-01 13:30:00', 'Entregue', 'Dine-in');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (5, 5, '2024-08-01 14:00:00', 'Preparando', 'Takeaway');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (6, 6, '2024-08-01 14:30:00', 'Entregue', 'Delivery');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (7, 7, '2024-08-01 15:00:00', 'Cancelado', 'Dine-in');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (8, 8, '2024-08-01 15:30:00', 'Preparando', 'Takeaway');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (9, 9, '2024-08-01 16:00:00', 'Entregue', 'Delivery');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (10, 10, '2024-08-01 16:30:00', 'Cancelado', 'Dine-in');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (11, 11, '2024-08-01 17:00:00', 'Preparando', 'Takeaway');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (12, 12, '2024-08-01 17:30:00', 'Entregue', 'Delivery');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (13, 13, '2024-08-01 18:00:00', 'Cancelado', 'Dine-in');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (14, 14, '2024-08-01 18:30:00', 'Preparando', 'Takeaway');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (15, 15, '2024-08-01 19:00:00', 'Entregue', 'Delivery');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (16, 16, '2024-08-01 19:30:00', 'Cancelado', 'Dine-in');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (17, 17, '2024-08-01 20:00:00', 'Preparando', 'Takeaway');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (18, 18, '2024-08-01 20:30:00', 'Entregue', 'Delivery');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (19, 19, '2024-08-01 21:00:00', 'Cancelado', 'Dine-in');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (20, 20, '2024-08-01 21:30:00', 'Preparando', 'Takeaway');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (21, 21, '2024-08-01 22:00:00', 'Entregue', 'Delivery');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (22, 22, '2024-08-01 22:30:00', 'Cancelado', 'Dine-in');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (23, 23, '2024-08-01 23:00:00', 'Preparando', 'Takeaway');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (24, 24, '2024-08-01 23:30:00', 'Entregue', 'Delivery');
	INSERT INTO Pedido (fk_id_cliente, fk_id_item, data_hora, status, tipo) VALUES (25, 25, '2024-08-02 00:00:00', 'Cancelado', 'Dine-in');

### 9	TABELAS E PRINCIPAIS CONSULTAS<br>
    OBS: Usa template da disciplina disponibilizado no Colab.<br>
    
A partir daqui, vamos para o colab: https://colab.research.google.com/drive/1i5rY6VJrsFX8wEVJNH-iQRVEae2EdjJl#scrollTo=-Xk52UNhyDEv<br>
 
#### 9.1	CONSULTAS DAS TABELAS COM TODOS OS DADOS INSERIDOS (Todas) <br>

#### 9.2	CONSULTAS DAS TABELAS COM FILTROS WHERE (Mínimo 4)<br>

#### 9.3	CONSULTAS QUE USAM OPERADORES LÓGICOS, ARITMÉTICOS E TABELAS OU CAMPOS RENOMEADOS (Mínimo 11)
    a) Criar 5 consultas que envolvam os operadores lógicos AND, OR e Not
    b) Criar no mínimo 3 consultas com operadores aritméticos 
    c) Criar no mínimo 3 consultas com operação de renomear nomes de campos ou tabelas

#### 9.4	CONSULTAS QUE USAM OPERADORES LIKE E DATAS (Mínimo 12) <br>
    a) Criar outras 5 consultas que envolvam like ou ilike
    b) Criar uma consulta para cada tipo de função data apresentada.

># Marco de Entrega 02: Do item 6. até o item 9.1 (5 PTS) <br>

#### 9.5	INSTRUÇÕES APLICANDO ATUALIZAÇÃO E EXCLUSÃO DE DADOS (Mínimo 6)<br>
    a) Criar minimo 3 de exclusão
    b) Criar minimo 3 de atualização

#### 9.6	CONSULTAS COM INNER JOIN E ORDER BY (Mínimo 6)<br>
    a) Uma junção que envolva todas as tabelas possuindo no mínimo 2 registros no resultado
    b) Outras junções que o grupo considere como sendo as de principal importância para o trabalho

#### 9.7	CONSULTAS COM GROUP BY E FUNÇÕES DE AGRUPAMENTO (Mínimo 6)<br>
    a) Criar minimo 2 envolvendo algum tipo de junção

#### 9.8	CONSULTAS COM LEFT, RIGHT E FULL JOIN (Mínimo 4)<br>
    a) Criar minimo 1 de cada tipo

#### 9.9	CONSULTAS COM SELF JOIN E VIEW (Mínimo 6)<br>
        a) Uma junção que envolva Self Join (caso não ocorra na base justificar e substituir por uma view)
        b) Outras junções com views que o grupo considere como sendo de relevante importância para o trabalho

#### 9.10	SUBCONSULTAS (Mínimo 4)<br>
     a) Criar minimo 1 envolvendo GROUP BY
     b) Criar minimo 1 envolvendo algum tipo de junção

># Marco de Entrega 03: Do item 9.2 até o ítem 9.10 (10 PTS)<br>

### 10 RELATÓRIOS E GRÁFICOS

#### a) análises e resultados provenientes do banco de dados desenvolvido (usar modelo disponível)
#### b) link com exemplo de relatórios será disponiblizado pelo professor no AVA
#### OBS: Esta é uma atividade de grande relevância no contexto do trabalho. Mantenha o foco nos 5 principais relatórios/resultados visando obter o melhor resultado possível.

    

### 11	AJUSTES DA DOCUMENTAÇÃO, CRIAÇÃO DOS SLIDES E VÍDEO PARA APRESENTAÇAO FINAL <br>

#### a) Modelo (pecha kucha)<br>
#### b) Tempo de apresentação 6:40 

># Marco de Entrega 04: Itens 10 e 11 (20 PTS) <br>
<br>
<br>




### 12 FORMATACAO NO GIT:<br> 
https://help.github.com/articles/basic-writing-and-formatting-syntax/
<comentario no git>
    
##### About Formatting
    https://help.github.com/articles/about-writing-and-formatting-on-github/
    
##### Basic Formatting in Git
    
    https://help.github.com/articles/basic-writing-and-formatting-syntax/#referencing-issues-and-pull-requests
    
    
##### Working with advanced formatting
    https://help.github.com/articles/working-with-advanced-formatting/
#### Mastering Markdown
    https://guides.github.com/features/mastering-markdown/

    
### OBSERVAÇÕES IMPORTANTES

#### Todos os arquivos que fazem parte do projeto (Imagens, pdfs, arquivos fonte, etc..), devem estar presentes no GIT. Os arquivos do projeto vigente não devem ser armazenados em quaisquer outras plataformas.
1. <strong>Caso existam arquivos com conteúdos sigilosos<strong>, comunicar o professor que definirá em conjunto com o grupo a melhor forma de armazenamento do arquivo.

#### Todos os grupos deverão fazer Fork deste repositório e dar permissões administrativas ao usuário do git "profmoisesomena", para acompanhamento do trabalho.

#### Os usuários criados no GIT devem possuir o nome de identificação do aluno (não serão aceitos nomes como Eu123, meuprojeto, pro456, etc). Em caso de dúvida comunicar o professor.


Link para BrModelo:<br>
http://www.sis4.com/brModelo/download.html
<br>


Link para curso de GIT<br>
![https://www.youtube.com/curso_git](https://www.youtube.com/playlist?list=PLo7sFyCeiGUdIyEmHdfbuD2eR4XPDqnN2?raw=true "Title")


