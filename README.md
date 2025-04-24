# Banco-de-la-dados
create database viagem;
use viagem;
create table passageiro(
id_passageiro int not null auto_increment,
nome varchar(100),
idade varchar(3),
sexo char(1),
rg varchar(20),
primary key(id_passageiro)
);
desc passageiro;

create table viagem(
id_viagem int not null auto_increment,
data_viagem date,
poltrona varchar(50),
valor float,
cod_passageiro int,
primary key(id_viagem)
);
desc viagem;

create table destino(
id_destino int not null auto_increment,
cidade varchar(100),
estado varchar(100),
cod_passageiro int,
primary key(id_destino)
);
desc destino;

create table pacote(
id_pacote int not null auto_increment,
nome_pacote varchar(100),
cod_destino int,
cod_viagem int,
primary key(id_pacote)
);
desc pacote;
 
alter table viagem add foreign key (cod_passageiro) references
passageiro (id_passageiro);

alter table destino add foreign key (cod_passageiro) references
passageiro (id_passageiro);

alter table pacote add foreign key (cod_destino) references
destino (id_destino);

alter table pacote add foreign key (cod_viagem) references
viagem (id_viagem);

insert into passageiro (nome, idade, sexo, rg) values
('Jorge','17','M','1.234.567.8-9');

insert into passageiro (nome, idade, sexo, rg) values
('Matheus','17','M','1.234.567.8-9');

insert into passageiro (nome, idade, sexo, rg) values
('Lucas','17','F','1.234.567.8-9');

insert into passageiro (nome, idade, sexo, rg) values
('Batman','55','M','1.234.567.8-9');

select * from passageiro;

insert into viagem (data_viagem, poltrona, valor, cod_passageiro) values
('2025-08-02','44','130.00','2');

insert into viagem (data_viagem, poltrona, valor, cod_passageiro) values
('2025-10-22','30','120.00','4');

insert into viagem (data_viagem, poltrona, valor, cod_passageiro) values
('2025-06-30','1','100.00','1');

insert into viagem (data_viagem, poltrona, valor, cod_passageiro) values
('2025-08-30','10','50.00','3');

select * from viagem;

insert into destino (cidade, estado, cod_passageiro) values
('Paranagua','Paranagua','3');

insert into destino (cidade, estado, cod_passageiro) values
('Praia','Paranagua','2');

insert into destino (cidade, estado, cod_passageiro) values
('Paranagua','Curitiba','4');

insert into destino (cidade, estado, cod_passageiro) values
('Matinhos','Curitiba','1');

select * from destino;

insert into pacote (nome_pacote, cod_destino, cod_viagem) values
('Passeio','2','4');

insert into pacote (nome_pacote, cod_destino, cod_viagem) values
('Passeio','4','2');

insert into pacote (nome_pacote, cod_destino, cod_viagem) values
('Natal','3','1');

insert into pacote (nome_pacote, cod_destino, cod_viagem) values
('Ano Novo','1','3');

select * from pacote;

select viagem.id_viagem, passageiro.nome, viagem.data_viagem
from viagem
inner join passageiro on viagem.cod_passageiro=passageiro.id_passageiro;

select passageiro.sexo, passageiro.nome, destino.cidade
from destino
inner join passageiro on destino.cod_passageiro=passageiro.id_passageiro;
