# 💻 Máquina de Estados em C++ — Simulação de Computador com Login

## 📌 Descrição

Este projeto é uma implementação simples de uma **máquina de estados finitos (FSM)** em C++, simulando o comportamento básico de um computador:

* Ligar / Desligar
* Sistema de Login
* Controle por comandos do usuário

O objetivo principal é praticar:

* Estruturas de controle (`switch`, `while`, `do-while`)
* Uso de `enum` para estados
* Organização com classes
* Entrada de dados com `cin`

---

## 🧠 Conceito aplicado

A lógica segue o modelo:

```
[ESTADO ATUAL] + [ENTRADA] → [NOVO ESTADO]
```

Estados possíveis:

* `DESLIGADO`
* `LIGADO`

---

## ⚙️ Funcionalidades

* 🔘 Alternar estado do computador (`t`)
* 🔐 Sistema de login com usuário e senha
* 🔁 Loop de execução até condição de saída
* 📥 Entrada de comandos via teclado

---

## 🧩 Código

```cpp
#include <iostream>
using namespace std;

enum Estado {
    DESLIGADO,
    LIGADO
};

class Registro {
public:
    int Login() {
        static bool Logado = false;
        string username = "valentino";
        int senha = 1709;

        do {
            cout << "Username: ";
            cin >> username;
            cout << "Senha: ";
            cin >> senha;

            if (username != "valentino" || senha != 1709) {
                cout << "erro no login" << endl;
            } else if (username == "valentino" || senha == 1709) {
                cout << "login feito" << endl;
                Logado = true;
                break;
            }

        } while (username != "valentino" || senha != 1709);

        return 0;
    }
};

class Computador {
public:
    int PC() {
        static bool Ligado = false;
        Registro Login;
        Estado estadoAtual = LIGADO;
        char comando;

        cout << "\nDigite (t = toggle, s = sair): ";
        cin >> comando;

        while (Ligado == false) {

            if (comando == 't') {
                switch (estadoAtual) {

                case LIGADO:
                    if (comando == 't') {
                        estadoAtual = LIGADO;
                        cout << "   Ligou!" << endl;
                        cout << "Digite (t = toggle l = logar): ";
                        cin >> comando;

                        do {
                            Login.Login();
                            Ligado = true;
                        } while (comando == 'l' && Ligado != true);
                    }

                case DESLIGADO:
                    if (comando == 't') {
                        estadoAtual = DESLIGADO;
                        cout << "   Desligou!" << endl;
                        cout << "Digite (t = toggle): ";
                        cin >> comando;
                    }
                }
            }
        }

        return 0;
    }
};

int main() {
    Computador PC;
    PC.PC();
}
```

---

## ⚠️ Observações

Alguns pontos podem ser melhorados futuramente:

* Uso de `&&` ao invés de `||` no login (validação correta)
* Adicionar `break` nos `case` para evitar execução indevida
* Implementar comando de saída (`s`)
* Melhor separação de responsabilidades entre classes

---

## 🚀 Possíveis melhorias

* Transformar a FSM em classes separadas por estado
* Criar interface mais amigável (menu interativo)
* Adicionar persistência de usuários
* Simular mais funções de um sistema (arquivos, programas, etc.)

---

## 🎯 Objetivo do projeto

Esse projeto foi desenvolvido como prática para entender melhor:

* Lógica de programação
* Estruturas de decisão
* Organização de código em C++

---

## 👨‍💻 Autor

Projeto desenvolvido por **Valentino** 💡

---

## ⭐ Observação final

Esse é um projeto de aprendizado — simples, mas com uma base muito importante.
Máquinas de estado são usadas em jogos, sistemas embarcados, interfaces e muito mais.

> Pequeno projeto, grande conceito.
