# Desafio: Programação Orientada a Objetos em Java

Este projeto tem como objetivo demonstrar o uso dos conceitos de Programação Orientada a Objetos (POO) através da criação de um sistema de Bootcamp, onde utilizamos os principais pilares da POO: Abstração, Encapsulamento, Herança e Polimorfismo.

## Estrutura de Classes

O projeto é composto pelas seguintes classes:

### 1. `Bootcamp.java`

Classe que representa o Bootcamp, contendo um conjunto de `Conteudos` (cursos e mentorias) e um conjunto de `Devs` inscritos. Os atributos principais são:

- **nome**: Nome do Bootcamp.
- **descricao**: Descrição do Bootcamp.
- **conteudos**: Conjunto de conteúdos que compõem o Bootcamp (cursos e mentorias).
- **devsInscritos**: Conjunto de desenvolvedores inscritos no Bootcamp.

### 2. `Conteudo.java`

Classe abstrata que define os atributos e métodos comuns a todos os tipos de conteúdo, como curso e mentoria. O método abstrato `calcularXp()` é implementado nas classes filhas.

- **titulo**: Título do conteúdo.
- **descricao**: Descrição do conteúdo.
- **XP_PADRAO**: Valor padrão de XP para o cálculo de experiência.

### 3. `Curso.java`

Classe que estende `Conteudo` e representa um curso. Possui um atributo adicional:

- **cargaHoraria**: Carga horária do curso.

### 4. `Mentoria.java`

Classe que estende `Conteudo` e representa uma mentoria. Possui um atributo adicional:

- **data**: Data da mentoria.

### 5. `Dev.java`

Classe que representa um desenvolvedor inscrito no Bootcamp. Esta classe contém:

- **nome**: Nome do desenvolvedor.
- **conteudosInscritos**: Conjunto de conteúdos em que o dev está inscrito.
- **conteudosConcluidos**: Conjunto de conteúdos que o dev já concluiu.

A classe também possui métodos para se inscrever em um Bootcamp, progredir no conteúdo e calcular o total de XP acumulado.

## Pilares da Programação Orientada a Objetos (POO)

### 1. Abstração

A abstração é representada pela classe `Conteudo`, que é abstrata e define os atributos e métodos comuns entre cursos e mentorias.

### 2. Encapsulamento

O encapsulamento é utilizado para proteger os atributos das classes, utilizando modificadores de acesso `private` e fornecendo métodos públicos para acessar e modificar esses atributos.

### 3. Herança

A herança é aplicada nas classes `Curso` e `Mentoria`, que estendem a classe abstrata `Conteudo`, herdando seus atributos e métodos.

### 4. Polimorfismo

O polimorfismo é aplicado ao tratar cursos e mentorias como instâncias da classe `Conteudo`, permitindo que ambos sejam manipulados de forma genérica no Bootcamp.

## Exemplo de Uso

Aqui está um exemplo de como utilizar as classes criadas no projeto:

```java
public class Main {
    public static void main(String[] args) {
        Curso curso1 = new Curso();
        curso1.setTitulo("Curso Java");
        curso1.setDescricao("Aprenda Java do básico ao avançado");
        curso1.setCargaHoraria(8);

        Curso curso2 = new Curso();
        curso2.setTitulo("Curso JavaScript");
        curso2.setDescricao("Aprenda JavaScript para front-end");
        curso2.setCargaHoraria(4);

        Mentoria mentoria = new Mentoria();
        mentoria.setTitulo("Mentoria de Java");
        mentoria.setDescricao("Tire suas dúvidas sobre Java");
        mentoria.setData(LocalDate.now());

        Bootcamp bootcamp = new Bootcamp();
        bootcamp.setNome("Bootcamp Java Developer");
        bootcamp.setDescricao("Descrição do Bootcamp Java Developer");
        bootcamp.getConteudos().add(curso1);
        bootcamp.getConteudos().add(curso2);
        bootcamp.getConteudos().add(mentoria);

        Dev devBruno = new Dev();
        devBruno.setNome("Bruno Lopes");
        devBruno.inscreverBootcamp(bootcamp);
        System.out.println("Conteúdos Inscritos Bruno: " + devBruno.getConteudosInscritos());
        devBruno.progredir();
        devBruno.progredir();
        System.out.println("-");
        System.out.println("Conteúdos Inscritos Bruno: " + devBruno.getConteudosInscritos());
        System.out.println("Conteúdos Concluídos Bruno: " + devBruno.getConteudosConcluidos());
        System.out.println("XP: " + devBruno.calcularTotalXp());
    }
}
