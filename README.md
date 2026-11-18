# Reprodutor de Músicas com Arduino

Projeto da disciplina **CCP020 - Digital Experience Ultimate**, do Centro Universitário FEI, com o professor Isaac.

**Grupo:**
- Samuel - RA 52.126.003-4
- Lucas - RA 52.126.005-9
- John - RA  52.126.027-3


## 1. Introdução

A ideia foi montar um reprodutor de músicas usando só o Arduino e alguns componentes simples. mas logo no começo percebemos que tinha bastante coisa para resolver: como fazer o Arduino "tocar" uma música sem ter um arquivo de áudio, como guardar várias músicas na memória pequena dele e como deixar a escolha da música prática para quem estiver usando, sem precisar de computador ou celular.

Nossos objetivos eram:
- tocar alguns sons conhecidos (temas de jogos, filmes e séries que a gente gosta) em um buzzer;
- mostrar a lista de músicas em um display LCD, com uma setinha (`->`) indicando qual está selecionada;
- usar botões como controles para navegar pelo menu, tocar e parar a música;
- usar os LEDs para mostrar rapidamente se o reprodutor está tocando ou parado.


## 2. Metodologia

### 2.1 Materiais utilizados

| Componente | Qtd. | Para que serviu |
|------------|------|-----------------|
| Arduino Uno | 1 | O "cérebro" do projeto: lê os botões, controla o LCD e os LEDs e gera as notas |
| Buzzer piezoelétrico | 1 | É onde as músicas tocam |
| Display LCD 16x2 | 1 | Mostra o menu de músicas e se está "Reproduzindo" ou "Parado" |
| Potenciômetro | 1 | Ajusta o contraste do LCD |
| Botões (push button) | 4 | Controlam o reprodutor |
| LED verde | 1 | Acende quando a música está tocando |
| LED vermelho | 1 | Acende quando o reprodutor está parado |
| Resistores | 3 | Protegem os LEDs e a luz de fundo do LCD |
| Protoboard | 1 | Base para montar o circuito |
| Jumpers | vários | Ligações entre os componentes |
| Cabo USB | 1 | Alimentação e envio do código |

### 2.2 Métodos

Antes de mexer nos componentes de verdade, montamos todo o circuito no **Tinkercad**. Assim deu para testar as ligações e o código sem correr o risco de queimar nada. Com a simulação funcionando, passamos para a montagem física na protoboard, seguindo o mesmo esquema.

Na programação, cada música virou uma lista de notas e quanto tempo cada nota dura. O Arduino percorre essa lista e toca nota por nota no buzzer usando a função `tone()`. O LCD mostra duas músicas por vez, e a setinha `->` marca a que está selecionada.

Depois disso foi uma fase grande de testes: acertar o tempo das notas para a música ficar reconhecível, arrumar o contraste do display e conferir q;ue os botões respondessem direito.

**Projeto montado (Tinkercad):**

![Projeto montado no Tinkercad](imagens/esquema_tinkercad.png)

**Ligações:**

| Componente | Pino do Arduino |
|------------|-----------------|
| LCD RS | D7 |
| LCD E | D6 |
| LCD D4, D5, D6, D7 | D5, D4, D3, D2 |
| Botão 1 | D12 |
| Botão 2 | D11 |
| Botão 3 | D10 |
| Botão 4 | D8 |
| Buzzer | D9 |
| LED verde | D13 |
| LED vermelho | A0 |

## 3. Experimentos

No vídeo dá para ver o reprodutor funcionando do começo ao fim. A sequência é esta:

1. **Menu inicial:** quando iniciammos o Arduino, o display já mostra a lista de músicas, com a setinha `->` na primeira opção.
2. **Navegando pelo menu:** usando os botões, dá para subir e descer na lista. O display mostra duas músicas por vez, e a setinha acompanha a seleção.
3. **Tocando uma música:** quando escolhemos uma música, o display muda para "Reproduzindo" com o nome dela, o LED verde acende e a melodia começa a tocar no buzzer.
4. **Parando a música:** ao parar, o display mostra "Parado" junto com o nome da música, e o LED vermelho indica que nada está tocando.

As músicas que colocamos foram: **Doom, Corinthians, Star Wars, Zelda, Star Trek, Harry Potter e Game of Thrones**.

### Vídeo

[![Assistir ao vídeo](https://youtu.be/b4Jwq2KSv70)

## 4. Tecnologias utilizadas

- **Arduino Uno**
- **C/C++ (linguagem do Arduino)**
- **Arduino IDE**, para escrever e enviar o código
- **Biblioteca `LiquidCrystal`**, para controlar o display
- **Função `tone()`**, para gerar as notas no buzzer
- **Tinkercad**, para simular o circuito antes de montar
- **Git e GitHub**, para organizar e entregar o projeto

## 5. Conclusão

No fim, a solução foi mais simples do que parecia no começo. Em vez de tentar tocar um arquivo de áudio, transformamos cada música em uma sequência de notas e durações, e o Arduino toca uma por uma no buzzer. Dessa forma conseguimos colocar várias músicas sem precisar de nenhum módulo extra.

Para a escolha das músicas, montamos um menu no display LCD controlado pelos botões, que deixou o uso bem intuitivo. Os LEDs verde e vermelho acabaram ajudando bastante, porque mostram na hora o que está acontecendo. Simular tudo no Tinkercad antes também fez diferença, porque a montagem física já começou com as ligações certas.

O projeto foi uma boa forma de colocar em prática o que vimos na disciplina: programar o microcontrolador, ler botões e usar um display. Se fôssemos continuar, uma ideia seria usar um módulo de MP3 (como o DFPlayer) para tocar o áudio original das músicas, ou colocar um controle de volume.


