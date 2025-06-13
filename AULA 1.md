# 🎮 Aula: Criando um Jogo de Ping Pong no Computador com Unity!

## 🌟 Objetivo da aula:

Vamos criar um joguinho chamado **Pong**, parecido com ping pong. Cada jogador controla uma barra. A bola vai bater de um lado pro outro, e o objetivo é não deixar ela passar!

---

## 📁 Parte 1 – Preparando a Unity

### O que é a Unity?

Unity é um programa que usamos para **criar jogos**. Com ele, desenhamos, programamos e testamos tudo o que queremos que aconteça no jogo.

### 👣 Passo a passo:

1. Abrir a Unity Hub e criar um novo projeto 2D com o nome: `JogoDePingPong`
2. Ativar o novo Input System:

   * `Edit > Project Settings > Player`
   * Em **Active Input Handling**, selecione: `Input System Package (New)`
   * Reinicie a Unity se for solicitado

### Criar os personagens:

* **Jogador1**:

  * `Hierarquia > 2D Object > Sprite > Square`
  * Renomear para `Jogador1`, redimensionar para uma barra, posicionar à esquerda

* **Jogador2**:

  * Duplicar o Jogador1 (`Ctrl + D`), renomear para `Jogador2`, posicionar à direita

* **Bola**:

  * `2D Object > Sprite > Circle`, renomear como `Bola`, colocar no centro

---

## 👩‍💻 Parte 2 – O Código do Jogador

### Criar um script:

1. `Assets > Create > C# Script`
2. Nome: `ControleDosJogadores`
3. Abrir e colar o código abaixo:

```csharp
using UnityEngine;
using UnityEngine.InputSystem; // Usa o novo sistema de entrada

public class ControleDosJogadores : MonoBehaviour
{
    public float velocidadeDoJogador; // Velocidade que a barra se move
    public bool jogador1; // Se for verdadeiro, é o jogador 1

    public float yMinimo; // Limite inferior da tela
    public float yMaximo; // Limite superior da tela

    void Update()
    {
        if (jogador1)
        {
            MoverJogador1(); // Controlado com W e S
        }
        else
        {
            MoverJogador2(); // Controlado com setas ↑ e ↓
        }
    }

    private void MoverJogador1()
    {
        transform.position = new Vector2(transform.position.x, Mathf.Clamp(transform.position.y, yMinimo, yMaximo));

        var teclado = Keyboard.current;

        if (teclado.wKey.isPressed)
        {
            transform.Translate(Vector2.up * velocidadeDoJogador * Time.deltaTime);
        }

        if (teclado.sKey.isPressed)
        {
            transform.Translate(Vector2.down * velocidadeDoJogador * Time.deltaTime);
        }
    }

    private void MoverJogador2()
    {
        transform.position = new Vector2(transform.position.x, Mathf.Clamp(transform.position.y, yMinimo, yMaximo));

        var teclado = Keyboard.current;

        if (teclado.upArrowKey.isPressed)
        {
            transform.Translate(Vector2.up * velocidadeDoJogador * Time.deltaTime);
        }

        if (teclado.downArrowKey.isPressed)
        {
            transform.Translate(Vector2.down * velocidadeDoJogador * Time.deltaTime);
        }
    }
}
```

---

## 🛠️ Parte 3 – Conectando o Script aos Objetos

1. Selecione `Jogador1` na Hierarquia

   * Adicione o script `ControleDosJogadores`
   * Marque a caixinha **jogador1 = true**
   * Preencha no Inspector:

     * `velocidadeDoJogador` (ex: 5)
     * `yMinimo` (ex: -4)
     * `yMaximo` (ex: 4)

2. Repita para `Jogador2`

   * **Desmarque** a caixinha `jogador1`
   * Use os mesmos valores

---

## ▶️ Parte 4 – Testando o Jogo

* Clique no botão **Play**
* Controles:

  * Jogador 1: **W / S**
  * Jogador 2: **↑ / ↓**

---

# 🧐 Conceitos de Programação Usados no Pong

## 📆 1. `class` – O Projeto da Coisa

> **Como explicar para crianças:**
> Pense em **"class"** como a **receita de um bolo**. Ela mostra **como o objeto vai funcionar** no jogo.

```csharp
public class ControleDosJogadores : MonoBehaviour
```

Esse pedaço está dizendo:
👉 “Aqui está o plano para fazer um jogador que se move para cima e para baixo.”

---

## ⚙️ 2. `void` – Uma Ação que Não Devolve Nada

> **Como explicar:**
> Imagina que você está dando uma ordem: "Vai lá e limpa seu quarto!"
> Você só dá o comando, não espera nada de volta.

```csharp
void Update() { ... }
void MoverJogador1() { ... }
```

Essas partes são **ações** que o jogo faz.

---

## 🔐 3. `private` e `public` – Segredo ou Não

> **Como explicar:**

* `public` (público) = **todo mundo pode ver e usar**
* `private` (privado) = **só o código de dentro pode usar**

```csharp
public float velocidadeDoJogador;
private void MoverJogador1() { ... }
```

---

## 📊 4. `float` – Um Número com Vírgula

> **Como explicar:**
> `float` é um tipo de número que pode ter **vírgula**, tipo:

* 3.5
* 7.2
* 0.1

```csharp
public float velocidadeDoJogador;
```

---

## 🔢 5. `bool` – Verdadeiro ou Falso

> **Como explicar:**
> `bool` é como uma **chave de liga e desliga**, só tem duas opções:

* **true** (ligado)
* **false** (desligado)

```csharp
public bool jogador1;
```

---

## 🔄 Explicando o Código Parte por Parte

* `Update()`: roda o tempo todo, verifica se alguma tecla está sendo apertada
* `MoverJogador1()` e `MoverJogador2()`: movem os jogadores
* `Keyboard.current`: lê o teclado
* `Translate(...)`: move a barra
* `Clamp(...)`: impede que a barra ultrapasse os limites da tela

---

## 🎓 Conclusão da Aula

Você aprendeu:

* Criar objetos no Unity
* Controlar um personagem com o teclado
* Escrever e entender um código em C#
* Usar o novo sistema de entrada

Na próxima aula: faremos a bola se mover e colidir com os jogadores!
