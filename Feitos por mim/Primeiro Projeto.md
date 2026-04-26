# 🧠 Simulação de Computador com Login (C++)

## 📌 Código

```cpp id="q8v2m1"
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
        string username = "tito";
        int senha = 1234;

        do {
            cout << "Username: ";
            cin >> username;
            cout << "Senha: ";
            cin >> senha;

            if (username != "tito" or senha != 1234) {
                cout << "erro no login" << endl;
            } else if (username == "tito" or senha == 1234) {
                cout << "login feito" << endl;
            }

        } while (username != "tito" or senha != 1234);

        return 0;
    }
};

class Computador {
public:
    int PC() {
        static bool Ligado = true;
        Registro Login;
        Estado estadoAtual = LIGADO;

        char comandoLogar;
        char comandoLigar;
        char comandoDesligar;
        char comando;

        cout << "\nDigite (t = ligar): ";
        cin >> comandoLigar;

        if (comandoLigar == 't') {
            while (Ligado == true) {
                switch (estadoAtual) {

                case LIGADO:
                    if (comandoLigar == 't') {
                        estadoAtual = LIGADO;
                        cout << "   Ligou!" << endl;

                        cout << "Digite (d = desligar, l = logar): ";
                        cin >> comando;

                        if (comando == 'l') {
                            do {
                                Login.Login();
                                Ligado = false;

                                cout << "Digite (d = desligar): ";
                                cin >> comandoDesligar;

                                if (comandoDesligar = 'd') {
                                    Ligado = false;
                                    break;
                                } else {
                                    cout << "comando invalido";
                                }

                            } while (Ligado == false and comando == 'l');

                        } else if (comando == 'd') {
                            cout << "   Desligou!";
                            Ligado = false;
                            break;

                        } else {
                            cout << "comando invalido";
                        }

                    } else {
                        cout << "comando invalido";
                    }

                case DESLIGADO:
                    if (comandoDesligar == 'd') {
                        estadoAtual = DESLIGADO;
                        cout << "   Desligou!" << endl;

                        do {
                            Ligado = false;
                        } while (Ligado == true);
                    }
                }
            }

        } else {
            cout << "comando invalido";
        }

        return 0;
    }
};

int main() {
    Computador PC;
    PC.PC();
}
```

