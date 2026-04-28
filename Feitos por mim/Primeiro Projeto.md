# 🧠 Simulação de Computador com Login (C++)

## 📌 Código

```cpp id="q8v2m1"
#include <iostream>
using namespace std;
#include <string>

enum Estado {
    DESLIGADO,
    LIGADO
};

class Registro {
public:
    int Login() {
        static bool Logado = false;
        string username = "pedroguloso";
        int senha = 1234;
        int senhaVer;
        string userVer;

        do {
            cout << "Username: ";
            cin >> userVer;
            cout << "Senha: ";
            cin >> senhaVer;

            if (username != userVer || senha != senhaVer) {
                cout << "erro no login" << endl;    
            } else {
                cout << "login feito" << endl;
                Logado = true;
            }

        } while (Logado == false);

        return 0;
    }
};

class Computador {
public:
    int PC() {
        static bool Ligado = true;
        Registro Login;
        Estado estadoAtual = LIGADO;

        char comando;

        cout << "\nDigite (t = ligar): ";
        cin >> comando;

        if (comando == 't') {
            while (Ligado == true) {
                switch (estadoAtual) {

                case LIGADO:
                    cout << "   Ligou!" << endl;
                    cout << "Digite (d = desligar, l = logar): ";
                    cin >> comando;

                    if (comando == 'l') {
                        Login.Login();

                        cout << "Digite (d = desligar): ";
                        cin >> comando;

                        if (comando == 'd') {
                            Ligado = false;
                            cout << "   Desligou!" << endl;
                        } else {
                            cout << "comando invalido";
                        }

                    } else if (comando == 'd') {
                        cout << "   Desligou!" << endl;
                        Ligado = false;

                    } else {
                        cout << "comando invalido";
                    }

                    break;

                case DESLIGADO:
                    cout << "   Desligado!" << endl;
                    Ligado = false;
                    break;
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
