# 🧠 Simulação de Computador com Login (C++)

## 📌 Código

```#include <iostream>
using namespace std;
#include <string>

enum Estado {
    DESLIGADO,
    LIGADO
};

class Registro {
public:
   int Login() {
    bool Logado = false;
    string username = "Daniboy";
    int senha = 6767;
    int senhaVer;
    string userVer;

    do {
        cout << "Username: ";
        cin >> userVer;

        cout << "Senha: ";
        cin >> senhaVer;

        if (cin.fail()) { // 🔥 aqui resolve o bug
            cout << "senha invalida (so numero)" << endl;
            cin.clear();
            cin.ignore(1000, '\n');
            continue;
        }

        if (username != userVer || senha != senhaVer) {
            cout << "erro no login" << endl;    
        } else {
            cout << "login feito" << endl;
            Logado = true;
        }

    } while (!Logado);

    return 0;
}
};

class Computador {
public:
    int PC() {
        bool Ligado = true;
        Registro Login;

        char comando;

        cout << "\nDigite (t = ligar): ";
        cin >> comando;

        if (comando == 't') {

            cout << "   Ligou!" << endl;

            while (Ligado) {

                cout << "Digite (d = desligar, l = logar): ";
                cin >> comando;

                if (comando == 'l') {

                    Login.Login();

                    while (true) {
                        cout << "Digite (d = desligar): ";
                        cin >> comando;

                        if (comando == 'd') {
                            Ligado = false;
                            cout << "   Desligou!" << endl;
                            break;
                        } else {
                            cout << "comando invalido" << endl;
                            cin.clear();
                            cin.ignore(1000, '\n'); // limpa entrada
                        }
                    }

                } else if (comando == 'd') {
                    cout << "   Desligou!" << endl;
                    Ligado = false;

                } else {
                    cout << "comando invalido" << endl;
                    cin.clear();
                    cin.ignore(1000, '\n'); // limpa entrada
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
