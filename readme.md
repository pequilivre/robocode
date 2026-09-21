# Torneio de Robocode (Versão 2.0)

![Logo oficial do Robocode](https://robocode.sourceforge.io/gfx/robocode_logo_tanks.png)

* [Informações Gerais](#info-geral)
* [Regras](#regras)
* [Pesagem do Robô](#pesagem)
* [Datas Importantes](#datas-importantes)
* [Premiação](#premiacao)
* [Tutoriais e outros recursos](#tutoriais)

## <a name="info-geral"></a>Informações Gerais

**Data:** Segunda-feira, 21 de setembro de 2026

**Horário:** 15h30-17h00

**Local:** Anfiteatro Inferior (Centro de Aulas 1, UFJ Jatobá)

**Disciplina:** Inteligência Artificial (ICE0627) — 2026.2

## <a name="regras"></a>Regras

**Definição dos grupos:** Através do ranqueamento pelo desempenho médio em 20 rodadas (*round*) contra os bots *Crazy*, *Corners*, e *Fire*.

**Tamanho dos grupos:** Serão realizados os chaveamentos para as batalhas (*battle*) em grupos de quatro bots. Apenas dois bots passam para a próxima fase. Na eventualidade de um grupo sorteado com apenas três bots, o quarto bot dessa batalha será o *Crazy* (passando para a próxima fase apenas os dois melhores bots inscritos).

**Quantidade de batalhas:** Em cada batalha, ocorrerão 3 rodadas com transmissão ao vivo durante o torneio. A partir das quartas-de-final, ocorrerão 5 rodadas em cada batalha.

**Tamanho do Robô:** MicroBot (código até **750 bytes**).

**Versão do Robocode:** 1.11.1 (Disponível no [site oficial da plataforma](https://robocode.sourceforge.io/)).

**Grupos:** de 1 a 2 pessoas.

**Participação:** Grupos de 1 a 2 pessoas, exclusivamente entre alunos matriculados na disciplina de Inteligência Artificial (ICE0627), sob responsabilidade do Prof. Esdras.

**Uso de agentes de inteligência artificial para a criação do bot:** Este é um espaço para diversão e aprendizagem. Não há desejo algum de que este seja um torneio de quem encontre o melhor bot "na internet" e vença a competição. Explore essa oportunidade como uma chance de aprender mais sobre agentes inteligentes, implementação de software, e ter um pouco mais de experiência com o desenvolvimento de sistemas baseados em eventos. Utilize ferramentas de inteligência artificial (e.g., ChatGPT, DeepSeek) para contribuir na evolução do seu aprendizado, e não o oposto. Uma [formação crítica](https://periodicos.newsciencepubl.com/arace/article/view/6295) é muito mais interessante para o seu futuro do que uma dependência de ferramentas como essas.

## <a name="pesagem"></a>Pesagem do Robô

Para participar do torneio, o seu robô deverá ter, no máximo, o tamanho de um **MicroBot**, ou seja, **até 750 bytes de código**.

A pesagem deve ser feita sobre o arquivo `.class` compilado do robô, e não diretamente sobre o arquivo `.java`.

Você pode realizar a pesagem utilizando a ferramenta `Codesize`, que já está disponível dentro da pasta do Robocode.

### Passo a passo

#### 1. Compile o seu robô

Primeiro, desenvolva e compile normalmente o seu robô no Robocode.

Ao final, você deverá ter um arquivo `.class` correspondente à classe principal do seu robô.

Por exemplo, supondo que o seu robô se chame `MeuRobo`, você deverá encontrar algo semelhante a:

```text
MeuRobo.class
```

dentro da pasta `robots` da instalação do Robocode.

#### 2. Abra um terminal na pasta principal do Robocode

Entre na pasta que contém a instalação do Robocode.

Por exemplo:

```text
robocode/
├── libs/
├── robots/
├── config/
└── ...
```

O terminal deverá estar aberto **na raiz dessa pasta**, isto é, na mesma pasta que contém `libs` e `robots`.

#### 3. Execute o Codesize

O comando básico para pesar um robô é:

```bash
java -cp "./libs/*" codesize.Codesize ./robots/MeuRobo.class
```

Substitua `MeuRobo.class` pelo nome e pelo caminho do arquivo `.class` do seu robô.

Por exemplo:

```bash
java -cp "./libs/*" codesize.Codesize ./robots/sample/Crazy.class
```

#### 4. Confira o valor apresentado na coluna `size`

A ferramenta apresentará uma tabela semelhante a:

```text
    Code    Class    Class
Nr  size    size     files    Location
--------------------------------------------------------------------
1   223     1721     1        Crazy.class
```

Para a **pesagem do torneio**, considere o valor apresentado na coluna **`Code size`**.

No exemplo acima:

```text
Crazy.class → 223 bytes
```

Portanto, esse robô está dentro do limite de MicroBot.

### É possível pesar vários robôs de uma vez

Você também pode informar vários arquivos `.class` no mesmo comando.

Por exemplo:

```bash
java -cp "./libs/*" codesize.Codesize ./robots/sample/Crazy.class ./robots/sample/Walls.class ./robots/sample/Fire.class
```

A saída será semelhante a:

```text
    Code    Class    Class
Nr  size    size     files    Location
--------------------------------------------------------------------
1   173     1727     1        Fire.class
2   186     1588     1        Walls.class
3   223     1721     1        Crazy.class
```

Observe que a ferramenta pode apresentar os arquivos em uma ordem diferente daquela utilizada no comando. Portanto, confira sempre a coluna **`Location`** para saber a qual robô pertence cada valor.

Nesse exemplo:

| Robô          |   `Code size` |
| ------------- | ------------: |
| `Crazy.class` | **223 bytes** |
| `Walls.class` | **186 bytes** |
| `Fire.class`  | **173 bytes** |

Os três são **NanoBots**, pois possuem menos de 250 bytes de código.

Para este torneio, entretanto, o limite será mais amplo: **serão aceitos robôs com até 750 bytes**, permitindo a participação de **MicroBots**.

### Como saber se o meu robô está dentro do limite?

A regra é simples:

```text
Code size ≤ 750 bytes  →  ROBÔ APTO
Code size > 750 bytes  →  ROBÔ NÃO APTO
```

Por exemplo:

```text
MeuRobo.class → 638 bytes
```

Como `638 ≤ 750`, o robô está dentro do limite.

Já:

```text
MeuRobo.class → 812 bytes
```

Como `812 > 750`, o robô ultrapassa o limite e não poderá participar.

### Atenção: pese o `.class` correto

A pesagem deve ser feita sobre o **arquivo `.class` que será utilizado pelo Robocode**.

Não utilize:

* o tamanho do arquivo `.java`;
* o tamanho mostrado pelo gerenciador de arquivos;
* o tamanho total da pasta do projeto;
* o tamanho do arquivo `.jar`;
* o tamanho de todos os arquivos da instalação do Robocode.

Utilize o valor de **`Code size` apresentado pelo `Codesize` para o arquivo `.class` do seu robô**.

### Dica

É recomendável realizar a pesagem **antes da inscrição**, para verificar se o seu robô está dentro do limite de 750 bytes.

**MUITO CUIDADO!!!**: Se o robô estiver acima do limite, você **não** terá tempo para simplificar o código e realizar uma nova pesagem. O não-envio correto (ou o não-envio) do robô da sua equipe será considerado uma desistência de realização desse desafio e afetará, consequentemente, o seu índice de comprometimento na disciplina.

## <a name="datas-importantes"></a>Datas importantes

* **Inscrição do bot:** até dia **21 de setembro de 2026, às 8h da manhã**, via [Formulário do Google](https://forms.gle/hXFuBENF5nuGWMMn6).
* **Torneio:** **21 de setembro de 2026, das 15h30 às 17h00**.

## <a name="premiacao"></a>Premiação

Existe uma premiação que ainda está a ser confirmada por vocês, por questão de disponibilidade. Para alunos matriculados na disciplina de Inteligência Artificial (ICE0627) 2026.2 na Universidade Federal de Jataí (UFJ), o responsável pelo bot inscrito que chegar mais longe na competição pode receber um *voucher* para um **rodízio de pizza junto com a turma**, com **data ainda a definir e confirmação pendente**. Se a equipe do bot inscrito tiver mais de um integrante, o *voucher* de um rodízio será dividido igualmente entre todos os membros.

Possivelmente teremos uma singela lembrança para todos os participantes.

## <a name="tutoriais"></a>Tutoriais e Outros Recursos

* Página Oficial do Robocode: <br>
  https://robocode.sourceforge.io/

* Documentação Oficial do Robocode: <br>
  https://robowiki.net/wiki/Main_Page

* Manual do RoboCode (Prof. Helder Linhares Bertoldo dos Reis (UFJF): <br>
  https://wiki.sj.ifsc.edu.br/images/7/73/ITL60801-Robocode-Manual2.pdf

* Curso de Robocode no Youtube em 4 aulas com o Prof. José de Assis (Senac-SP): <br>
  https://www.youtube.com/watch?v=XSCP6cddqRA&list=PLbEOwbQR9lqxdW98mY-40IZQ5i8ZZyeQx&index=37

* Curso de Robótica com RoboCode (Centro Paula Souza): <br>
  http://www.robotica.cpscetec.com.br/material.php?ano=2025&atv=6

* Curso de RoboCode do Prof. Adam Bignold (*in English*): <br>
  https://www.youtube.com/watch?v=GyVH8_C1QbQ&list=PLEb0SeDAVThdFdhrKLEF4-xjOjOVhncmT

* *Robocode Crash Course* com o Prof. Spencer (*in English*): <br>
  https://www.youtube.com/watch?v=uzu7iFFC9vI&list=PLdmQEhafuhGo-mYI3pl2y_27OSE85w8GZ&index=1

## Organização e Contato

Prof. Esdras L. Bispo Jr. ([bispojr@ufj.edu.br](mailto:bispojr@ufj.edu.br))
