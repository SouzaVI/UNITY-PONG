# 🕹️ Aula 2 – Criando e Programando os Jogadores

## 🎯 Objetivo da Aula

Nesta aula, vamos:

* Criar os jogadores (barrinhas brancas).
* Adicionar colisão a eles.
* Programar seus movimentos com teclado.
* Impedir que saiam da tela.
* Alterar a cor de fundo da tela para preto.

---

## 🎮 1. Criando os Jogadores

### Passo a passo:

1. Acesse a pasta **Gráficos** na aba `Project`.
2. Arraste o sprite do jogador para a área da cena (Scene).
3. Clique duas vezes no objeto criado e renomeie como **Jogador 1**.
4. Para criar o **Jogador 2**, repita o processo e renomeie como **Jogador 2**.

---

## 🧱 2. Adicionando Colisor (Collider)

### Por que?

Sem colisão, a bola atravessaria os jogadores.

### Como fazer:

1. Selecione o jogador.
2. Clique em **Add Component** > pesquise por **Box Collider 2D**.
3. Adicione o componente.

Repita para o **Jogador 2**.

---

## 📏 3. Posicionando os Jogadores

* Use a ferramenta de mover (atalho: tecla `W`).
* Segure **Ctrl** para mover em pequenos passos.
* **Jogador 1:** Posição X = `-7.75`
* **Jogador 2:** Posição X = `7.75`

---

## 🧠 4. Programando os Jogadores

### Criando o script:

1. Na aba `Project`, crie a pasta **Scripts**.
2. Dentro dela, crie um novo C# Script chamado `ControleDosJogadores`.

### Estrutura do Script:

```csharp
using UnityEngine;
using UnityEngine.InputSystem;

public class ControleDosJogadores : MonoBehaviour
{
    public float velocidadeDoJogador;
    public bool jogador1;
    public float yMinimo;
    public float yMaximo;

    void Update()
    {
        if (jogador1)
        {
            MoverJogador1();
        }
        else
        {
            MoverJogador2();
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

## ⚙️ 5. Aplicando o Script

1. Selecione o **Jogador 1**.

2. Arraste o script para ele.

3. No Inspector:

   * `velocidadeDoJogador`: `7`
   * `jogador1`: **marcado**
   * `yMinimo`: `-4`
   * `yMaximo`: `4`

4. Faça o mesmo com o **Jogador 2**, mas deixe `jogador1` **desmarcado**.

---

## 🖤 6. Mudando a Cor de Fundo da Câmera

1. Selecione a **Main Camera**.
2. No Inspector, marque **Clear Flags: Solid Color**.
3. Clique na cor e escolha **preto**.

---

## ✅ Teste Final

Clique em **Play**:

* Jogador 1 se move com `W` (cima) e `S` (baixo).
* Jogador 2 se move com `↑` e `↓`.
* Nenhum jogador ultrapassa os limites da tela.
* Fundo preto e barras brancas, estilo clássico do Pong.

---

## ✨ Próxima Aula

Vamos criar e programar a **bolinha** do jogo!

---

Se desejar, posso também gerar um **PDF ilustrado** dessa apostila para você aplicar em sala ou imprimir. Deseja isso?
