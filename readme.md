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

> O sofisticado restaurante "Le Gourmet", conhecido por sua sofisticação e excelência, enfrenta desafios na gestão devido sua clientela exigente. Para manter o alto padrão e eficiência, Sr.Manoel decidiu implementar um sistema integrado que garantisse a precisão no gerenciamento do seu negócio.
O sistema deve ter: Clientes, Pedidos, Menu, Inventário os clientes podem ser atendidos no restaurante ou fazer o pedido para entrega, cada cliente deve ter o nome, telefone para contato e local onde mora caso peça para entrega, os pedidos devem ser compostos por um ou mais itens do menu, podem ser para consumo local, viagem ou para entrega, cada pedido deve ter um status entre "em preparo, pronto, entregue ou cancelado", também deve registrar a data e hora do pedido. o Menu é deve ser composto por diversos itens, cada item possui nome, descrição, preço e categoria, o menu pode ser atualizado conforme necessário pelo gerente do estabelecimento. o inventário deve controlar os insumos e ingredientes necessários para a preparação dos itens do menu, cada item deve possuir um nome, quantidade disponível e data de validade, o inventário deve ser atualizado conforme os insumos são utilizados e repostos.

### 3.PERGUNTAS A SEREM RESPONDIDAS<br>
#### 3.1 QUAIS PERGUNTAS PODEM SER RESPONDIDAS COM O SISTEMA PROPOSTO?
    a) O sistema proposto poderá fornecer quais tipos de relatórios e informaçes? 
> Nosso pricipal foco dos relatorios é monitorar quantidade de vendas para garantir que negocio do cliente está progredindo positivamente.
    
    b) Crie uma lista com os 5 principais relatórios que poderão ser obtidos por meio do sistema proposto!
    
> Nosso sistema do restaurante precisa inicialmente dos seguintes relatórios:

Relatório 1: Exibir todos os ingredientes que estão vencidos ou estão prestes a vencer e a quantidade deles.

Relatório 2: Exibir o valor total de vendas por cada produto ao longo do tempo.

Relatório 3: Exibir a média de gasto dos clientes.

Relatório 4: Exibir os itens mais vendidos nos últimos 3 meses.

Relatório 5: Exibir a distribuição de vendas por hora do dia, para identificar os horários de pico.


    
### 5.MODELO CONCEITUAL<br>

        
![Conceitual](https://github.com/user-attachments/assets/585687ae-a783-460f-833e-fc6fdf361ad4)


#### 5.1 Validação do Modelo Conceitual
    [Grupo01]: [Nomes dos que participaram na avaliação]
    [Grupo02]: [Nomes dos que participaram na avaliação]

#### 5.2 Descrição dos dados 
	MENU: Tabela que armazena informações relativas ao cardápio do restaurante.
	ID_MENU: Campo que armazena a chave primária de um item da tabela Menu.
	NOME: Campo que armazena o nome do item no cardápio.
	DESCRICAO: Campo que armazena a descrição detalhada do item no cardápio.
	PRECO: Campo que armazena o preço do item no cardápio.

	
	COMANDA: Tabela que armazena informações relativas a comanda.
	ID_COMANDA: Campo que armazena a chave primária de um item na tabela de comanda.
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

![logico](https://github.com/user-attachments/assets/2936e60a-68d5-4ae7-a1d6-d3bfa6e219ae)


### 7	MODELO FÍSICO<br>
        DROP TABLE IF EXISTS Comanda;
	DROP TABLE IF EXISTS Pedido;
	DROP TABLE IF EXISTS Cliente;
	DROP TABLE IF EXISTS Inventario;
	DROP TABLE IF EXISTS Menu;
	
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
	
	CREATE TABLE Pedido (
	    id_pedido SERIAL PRIMARY KEY,
	    fk_id_cliente INTEGER,
	    data_hora TEXT NOT NULL,
	    status VARCHAR NOT NULL,
	    tipo VARCHAR NOT NULL,
	    FOREIGN KEY (fk_id_cliente) REFERENCES Cliente(id_cliente) ON DELETE CASCADE
	);
	
	CREATE TABLE Comanda (
	    id_comanda SERIAL PRIMARY KEY,
	    fk_id_pedido INTEGER,
	    fk_id_menu INTEGER,
	    quantidade INTEGER NOT NULL,
	    FOREIGN KEY (fk_id_pedido) REFERENCES Pedido(id_pedido) ON DELETE CASCADE,
	    FOREIGN KEY (fk_id_menu) REFERENCES Menu(id_menu) ON DELETE CASCADE
	);
      
### 8	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>
	
	
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
	INSERT INTO cliente (nome, telefone, endereco) VALUES ('Mariana Santos', '2345678910', 'Rua dos Girassóis, 4141');
	INSERT INTO cliente (nome, telefone, endereco) VALUES ('Felipe Almeida', '3456789021', 'Avenida Paulista, 4242');
	INSERT INTO cliente (nome, telefone, endereco) VALUES ('Gabriela Costa', '4567890132', 'Rua das Palmeiras, 4343');
	INSERT INTO cliente (nome, telefone, endereco) VALUES ('Mateus Lima', '5678901243', 'Rua das Rosas, 4444');
	INSERT INTO cliente (nome, telefone, endereco) VALUES ('Isabela Silva', '6789012354', 'Rua das Azaléias, 4545');
	INSERT INTO cliente (nome, telefone, endereco) VALUES ('Vinícius Pereira', '7890123465', 'Rua dos Cravos, 4646');
	INSERT INTO cliente (nome, telefone, endereco) VALUES ('Caroline Oliveira', '8901234576', 'Rua dos Ipês, 4747');
	
	
	
	
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
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Leite Condensado', 100, '2025-01-01');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Creme de Leite', 120, '2024-12-31');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Chocolate em Pó', 200, '2025-02-15');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Fermento em Pó', 150, '2025-03-20');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Coco Ralado', 180, '2025-04-10');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Amido de Milho', 220, '2025-05-05');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Molho de Tomate', 250, '2025-06-25');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Ervilha', 180, '2024-11-15');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Milho', 200, '2024-10-30');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Azeitona', 160, '2025-01-20');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Palmito', 140, '2025-02-05');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Sardinha', 110, '2025-03-10');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Atum', 100, '2025-04-15');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Camarão', 90, '2025-05-20');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Lula', 80, '2025-06-25');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Bacalhau', 70, '2025-07-30');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Pão de Forma', 150, '2024-08-20');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Pão Francês', 180, '2024-08-25');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Requeijão', 140, '2024-12-05');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Iogurte', 130, '2024-09-10');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Café', 200, '2025-02-01');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Suco de Laranja', 160, '2025-03-05');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Suco de Uva', 140, '2025-04-20');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Refrigerante', 300, '2025-06-15');
	INSERT INTO Inventario (nome, quantidade_disponivel, data_validade) VALUES ('Água Mineral', 500, '2025-07-01');
	
	
	
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
	
	INSERT INTO Pedido (fk_id_cliente, data_hora, status, tipo) VALUES
	(1, '2024-08-06 19:30', 'Em preparo', 'Entrega'),
	(1, '2024-07-15 12:00', 'Entregue', 'Entrega'),
	(1, '2024-06-25 18:00', 'Retirado', 'Retirada'),
	(1, '2024-05-30 14:00', 'Cancelado', 'Retirada');
	INSERT INTO Pedido (fk_id_cliente, data_hora, status, tipo) VALUES
	(2, '2024-08-07 20:00', 'Em preparo', 'Entrega'),
	(2, '2024-07-10 13:00', 'Retirado', 'Retirada'),
	(2, '2024-06-20 17:00', 'Entregue', 'Entrega'),
	(2, '2024-05-05 15:00', 'Cancelado', 'Entrega');
	INSERT INTO Pedido (fk_id_cliente, data_hora, status, tipo) VALUES
	(3, '2024-08-01 12:30', 'Em preparo', 'Entrega'),
	(3, '2024-07-25 19:00', 'Retirado', 'Retirada'),
	(3, '2024-06-15 14:00', 'Entregue', 'Entrega'),
	(3, '2024-05-10 16:00', 'Cancelado', 'Retirada');
	INSERT INTO Pedido (fk_id_cliente, data_hora, status, tipo) VALUES
	(4, '2024-08-05 13:00', 'Em preparo', 'Entrega'),
	(4, '2024-07-18 12:00', 'Entregue', 'Entrega'),
	(4, '2024-06-05 11:00', 'Retirado', 'Retirada'),
	(4, '2024-05-25 14:00', 'Cancelado', 'Retirada');
	INSERT INTO Pedido (fk_id_cliente, data_hora, status, tipo) VALUES
	(5, '2024-08-07 18:00', 'Em preparo', 'Entrega'),
	(5, '2024-07-05 20:00', 'Retirado', 'Retirada'),
	(5, '2024-06-12 15:00', 'Entregue', 'Entrega'),
	(5, '2024-05-20 19:00', 'Cancelado', 'Entrega');
	INSERT INTO Pedido (fk_id_cliente, data_hora, status, tipo) VALUES
	(6, '2024-08-06 17:00', 'Em preparo', 'Entrega'),
	(6, '2024-07-15 20:00', 'Retirado', 'Retirada'),
	(6, '2024-06-25 16:00', 'Entregue', 'Entrega'),
	(6, '2024-05-10 14:00', 'Cancelado', 'Retirada');
	INSERT INTO Pedido (fk_id_cliente, data_hora, status, tipo) VALUES
	(7, '2024-08-01 19:00', 'Em preparo', 'Entrega'),
	(7, '2024-07-20 13:00', 'Entregue', 'Entrega'),
	(7, '2024-06-10 12:00', 'Retirado', 'Retirada'),
	(7, '2024-05-05 17:00', 'Cancelado', 'Retirada');
	INSERT INTO Pedido (fk_id_cliente, data_hora, status, tipo) VALUES
	(8, '2024-08-07 21:00', 'Em preparo', 'Entrega'),
	(8, '2024-07-25 12:00', 'Retirado', 'Retirada'),
	(8, '2024-06-30 18:00', 'Entregue', 'Entrega'),
	(8, '2024-05-15 20:00', 'Cancelado', 'Entrega');
	INSERT INTO Pedido (fk_id_cliente, data_hora, status, tipo) VALUES
	(9, '2024-08-02 14:00', 'Em preparo', 'Entrega'),
	(9, '2024-07-05 15:00', 'Entregue', 'Entrega'),
	(9, '2024-06-20 11:00', 'Retirado', 'Retirada'),
	(9, '2024-05-25 13:00', 'Cancelado', 'Retirada');
	INSERT INTO Pedido (fk_id_cliente, data_hora, status, tipo) VALUES
	(10, '2024-08-07 16:00', 'Em preparo', 'Entrega'),
	(10, '2024-07-12 19:00', 'Retirado', 'Retirada'),
	(10, '2024-06-22 17:00', 'Entregue', 'Entrega'),
	(10, '2024-05-30 20:00', 'Cancelado', 'Entrega');
	INSERT INTO Pedido (fk_id_cliente, data_hora, status, tipo) VALUES
	(11, '2024-05-07 12:00', 'Retirado', 'Retirada'),
	(12, '2024-05-07 19:00', 'Entregue', 'Entrega'),
	(13, '2024-05-08 15:00', 'Entregue', 'Entrega'),
	(14, '2024-05-07 13:00', 'Retirado', 'Retirada'),
	(15, '2024-04-30 18:00', 'Cancelado', 'Entrega'),
	(16, '2024-04-25 12:00', 'Entregue', 'Entrega'),
	(17, '2024-04-26 20:00', 'Cancelado', 'Retirada'),
	(18, '2024-04-25 16:00', 'Retirado', 'Retirada'),
	(19, '2024-04-22 13:00', 'Entregue', 'Entrega'),
	(20, '2024-03-25 17:00', 'Retirado', 'Retirada'),
	(21, '2024-03-30 19:00', 'Cancelado', 'Entrega'),
	(22, '2024-03-15 12:00', 'Entregue', 'Entrega'),
	(23, '2024-03-20 20:00', 'Retirado', 'Retirada'),
	(24, '2024-03-10 14:00', 'Entregue', 'Entrega'),
	(25, '2024-03-05 13:00', 'Cancelado', 'Retirada'),
	(27, '2024-02-25 17:00', 'Retirado', 'Retirada'),
	(28, '2024-02-20 19:00', 'Cancelado', 'Entrega'),
	(29, '2024-02-15 12:00', 'Entregue', 'Entrega'),
	(30, '2024-02-10 20:00', 'Retirado', 'Retirada'),
	(31, '2024-08-07 11:00', 'Retirado', 'Retirada'),
	(32, '2024-08-07 18:00', 'Entregue', 'Entrega'),
	(33, '2024-08-08 14:00', 'Entregue', 'Entrega'),
	(34, '2024-08-07 12:00', 'Retirado', 'Retirada'),
	(35, '2024-07-30 17:00', 'Cancelado', 'Entrega'),
	(36, '2024-07-25 11:00', 'Entregue', 'Entrega'),
	(37, '2024-07-26 19:00', 'Cancelado', 'Retirada'),
	(38, '2024-07-25 15:00', 'Retirado', 'Retirada'),
	(39, '2024-07-22 12:00', 'Entregue', 'Entrega'),
	(40, '2024-06-25 16:00', 'Retirado', 'Retirada'),
	(41, '2024-06-30 18:00', 'Cancelado', 'Entrega'),
	(42, '2024-06-15 11:00', 'Entregue', 'Entrega'),
	(43, '2024-06-20 19:00', 'Retirado', 'Retirada'),
	(44, '2024-06-10 13:00', 'Entregue', 'Entrega'),
	(45, '2024-06-05 12:00', 'Cancelado', 'Retirada'),
	(46, '2024-05-30 11:00', 'Entregue', 'Entrega'),
	(47, '2024-05-25 16:00', 'Retirado', 'Retirada'),
	(48, '2024-05-20 18:00', 'Cancelado', 'Entrega'),
	(49, '2024-05-15 11:00', 'Entregue', 'Entrega'),
	(50, '2024-05-10 19:00', 'Retirado', 'Retirada');
	INSERT INTO Comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES
	(1, 1, 2),
	(1, 2, 1),
	(2, 3, 1),
	(2, 4, 2),
	(3, 2, 1),
	(3, 5, 1),
	(4, 1, 1),
	(4, 3, 1),
	(5, 2, 2),
	(5, 5, 1),
	(6, 1, 1),
	(6, 4, 2),
	(7, 3, 2),
	(7, 5, 2),
	(8, 1, 2),
	(8, 3, 1),
	(9, 2, 1),
	(9, 5, 1),
	(10, 4, 1),
	(10, 5, 2),
	(11, 3, 2),
	(11, 4, 1),
	(12, 1, 1),
	(12, 2, 2),
	(13, 2, 1),
	(13, 3, 1),
	(14, 4, 1),
	(14, 5, 1),
	(15, 1, 1),
	(15, 2, 1),
	(16, 3, 2),
	(16, 4, 1),
	(17, 1, 2),
	(17, 4, 1),
	(18, 2, 1),
	(18, 3, 2),
	(19, 5, 1),
	(19, 4, 2),
	(20, 2, 2),
	(20, 3, 1),
	(21, 1, 1),
	(21, 5, 1),
	(22, 2, 2),
	(22, 4, 1),
	(23, 3, 1),
	(23, 5, 1),
	(24, 4, 2),
	(24, 1, 1),
	(25, 1, 2),
	(25, 2, 1),
	(26, 3, 2),
	(26, 4, 1),
	(27, 2, 1),
	(27, 5, 2),
	(28, 1, 1),
	(28, 4, 2),
	(29, 1, 2),
	(29, 5, 1),
	(30, 2, 1),
	(30, 3, 1),
	(31, 4, 1),
	(31, 5, 2),
	(32, 2, 1),
	(32, 3, 2),
	(33, 3, 1),
	(33, 4, 1),
	(34, 1, 1),
	(34, 2, 2),
	(35, 4, 2),
	(35, 5, 1),
	(36, 1, 1),
	(36, 5, 2),
	(37, 2, 1),
	(37, 3, 1),
	(38, 4, 1),
	(38, 5, 2),
	(39, 1, 2),
	(39, 3, 1),
	(40, 2, 1),
	(40, 4, 2),
	(11, 1, 2),
	(11, 2, 1),
	(11, 3, 3),
	(11, 4, 1),
	(11, 5, 2),
	(12, 6, 1),
	(12, 7, 2),
	(12, 8, 1),
	(12, 9, 2),
	(12, 10, 3),
	(13, 11, 1),
	(13, 12, 2),
	(13, 13, 1),
	(13, 14, 2),
	(13, 15, 3),
	(14, 16, 1), (14, 17, 2), (14, 18, 1), (14, 19, 2), (14, 20, 3),
	(15, 21, 1), (15, 22, 2), (15, 23, 1), (15, 24, 2), (15, 25, 3),
	(16, 26, 1), (16, 27, 2), (16, 28, 1), (16, 29, 2), (16, 30, 3),
	(17, 31, 1), (17, 32, 2), (17, 33, 1), (17, 34, 2), (17, 35, 3),
	(18, 36, 1), (18, 37, 2), (18, 38, 1), (18, 39, 2), (18, 40, 3),
	(19, 41, 1), (19, 42, 2), (19, 43, 1), (19, 44, 2), (19, 45, 3),
	(20, 46, 1), (20, 47, 2), (20, 48, 1), (20, 49, 2), (20, 50, 3),
	(21, 1, 1), (21, 2, 2), (21, 3, 1), (21, 4, 2), (21, 5, 3),
	(22, 6, 1), (22, 7, 2), (22, 8, 1), (22, 9, 2), (22, 10, 3),
	(23, 11, 1), (23, 12, 2), (23, 13, 1), (23, 14, 2), (23, 15, 3),
	(24, 16, 1), (24, 17, 2), (24, 18, 1), (24, 19, 2), (24, 20, 3),
	(25, 21, 1), (25, 22, 2), (25, 23, 1), (25, 24, 2), (25, 25, 3),
	(26, 26, 1), (26, 27, 2), (26, 28, 1), (26, 29, 2), (26, 30, 3),
	(27, 31, 1), (27, 32, 2), (27, 33, 1), (27, 34, 2), (27, 35, 3),
	(28, 36, 1), (28, 37, 2), (28, 38, 1), (28, 39, 2), (28, 40, 3),
	(29, 41, 1), (29, 42, 2), (29, 43, 1), (29, 44, 2), (29, 45, 3),
	(30, 46, 1), (30, 47, 2), (30, 48, 1), (30, 49, 2), (30, 50, 3),
	(31, 1, 1), (31, 2, 2), (31, 3, 1), (31, 4, 2), (31, 5, 3),
	(32, 6, 1), (32, 7, 2), (32, 8, 1), (32, 9, 2), (32, 10, 3),
	(33, 11, 1), (33, 12, 2), (33, 13, 1), (33, 14, 2), (33, 15, 3),
	(34, 16, 1), (34, 17, 2), (34, 18, 1), (34, 19, 2), (34, 20, 3),
	(35, 21, 1), (35, 22, 2), (35, 23, 1), (35, 24, 2), (35, 25, 3),
	(36, 26, 1), (36, 27, 2), (36, 28, 1), (36, 29, 2), (36, 30, 3),
	(37, 31, 1), (37, 32, 2), (37, 33, 1), (37, 34, 2), (37, 35, 3),
	(38, 36, 1), (38, 37, 2), (38, 38, 1), (38, 39, 2), (38, 40, 3),
	(39, 41, 1), (39, 42, 2), (39, 43, 1), (39, 44, 2), (39, 45, 3),
	(40, 46, 1), (40, 47, 2), (40, 48, 1), (40, 49, 2), (40, 50, 3),
	(41, 1, 1), (41, 2, 2), (41, 3, 1), (41, 4, 2), (41, 5, 3),
	(42, 6, 1), (42, 7, 2), (42, 8, 1), (42, 9, 2), (42, 10, 3),
	(43, 11, 1), (43, 12, 2), (43, 13, 1), (43, 14, 2), (43, 15, 3),
	(44, 16, 1), (44, 17, 2), (44, 18, 1), (44, 19, 2), (44, 20, 3),
	(45, 21, 1), (45, 22, 2), (45, 23, 1), (45, 24, 2), (45, 25, 3),
	(46, 26, 1), (46, 27, 2), (46, 28, 1), (46, 29, 2), (46, 30, 3),
	(47, 31, 1), (47, 32, 2), (47, 33, 1), (47, 34, 2), (47, 35, 3),
	(48, 36, 1), (48, 37, 2), (48, 38, 1), (48, 39, 2), (48, 40, 3),
	(49, 41, 1), (49, 42, 2), (49, 43, 1), (49, 44, 2), (49, 45, 3),
	(50, 46, 1), (50, 47, 2), (50, 48, 1), (50, 49, 2), (50, 50, 3);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (51, 1, 2);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (51, 3, 1);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (52, 2, 3);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (52, 4, 2);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (53, 5, 1);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (53, 7, 2);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (54, 6, 4);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (54, 8, 1);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (55, 9, 2);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (55, 10, 3);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (57, 11, 1);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (57, 12, 2);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (58, 13, 2);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (58, 14, 1);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (59, 15, 2);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (59, 16, 1);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (60, 17, 2);
	INSERT INTO comanda (fk_id_pedido, fk_id_menu, quantidade) VALUES (60, 18, 3);

### 9	TABELAS E PRINCIPAIS CONSULTAS<br>
    
O tópico 9 foi inteiramente desenvolvido no colab podendo ser acessado através desse link: 
https://colab.research.google.com/drive/1i5rY6VJrsFX8wEVJNH-iQRVEae2EdjJl#scrollTo=-Xk52UNhyDEv<br>
 


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


