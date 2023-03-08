#include <iostream>
#include <string>
using namespace std;

int menu();
void choose(int &a, int &b);
int gcd(int a, int b = 26);
string clean(string m);
string encrypt_msg(string m, int a, int b);
string decrypt_msg(string c, int a_inv, int b);
int get_inv(int a);

int main() {
  string clear, cipher;
  int a, b;
  int selection = 10;
  do {
    selection = menu();

    if (selection == 0)
      return 0;

    else if (selection == 1 || selection == 2)
      choose(a, b);

    if (selection == 1) {
      cout << "Enter the message to encrypt: ";
      getline(cin, clear);
      clear = clean(clear);
      cipher = encrypt_msg(clear, a, b);
      cout << "Encrypted message: " << cipher << endl;
    } else if (selection == 2) {
      cout << "Enter the message to decrypt: ";
      getline(cin, cipher);
      clear = decrypt_msg(cipher, get_inv(a), b);
      cout << "Decrypted message: " << clear << endl;
    }
  } while (selection);

  return 0;
}

int menu() {
  char choice;
  cout << "Do you want to: " << endl;
  cout << "(E)ncrypt" << endl
       << "(D)ecrypt\n"
       << "(Q)uit\n";
  cin >> choice;
  if (choice == 'e' || choice == 'E') {
    cin.ignore(80, '\n');
    return 1;
  } else if (choice == 'd' || choice == 'D') {
    cin.ignore(80, '\n');
    return 2;
  } else if (choice == 'q' || choice == 'Q') {
    cin.ignore(80, '\n');
    return 0;
  } else {
    cin.ignore(80, '\n');
    return 10;
  }
}
void choose(int &a, int &b) {
  bool check;
  do {
    cout << "Please enter your first number" << endl;
    cin >> a;
    if (!cin || a < 0 || gcd(a) != 1) {
      if (gcd(a) != 1 && cin && a > 0)
        cout << "The number must be co prime to 26" << endl;
      cin.clear();
      cin.ignore(80, '\n');
      check = false;

    } else
      check = true;
  } while (!check);
  cin.ignore(80, '\n');
  do {
    cout << "Please enter your second number" << endl;
    cin >> b;
    if (!cin || b <= 0) {
      cin.clear();
      cin.ignore(80, '\n');
      check = false;
    } else
      check = true;
  } while (!check);

  cin.ignore(80, '\n');
}
int gcd(int a, int b) {
  int c;
  do {
    c = a % b;
    a = b;
    b = c;

  } while (c != 0);

  return a;
}
string clean(string m) {
  string cleaned = "";
  int prev = 0;
  for (int i = 0; i < m.size() + 1; i++) {
    if (m[i] < 'a')
      m[i] += 32;
    if (m[i] < 97 || m[i] > 122) {
      cleaned += m.substr(prev, i - prev);
      prev = i + 1;
    }
  }
  return cleaned;
}
string encrypt_msg(string m, int a, int b) {
  for (int i = 0; i < m.size(); i++) {
    m[i] = ((a * (m[i] - 'a') + b) % 26) + 'a';
  }
  return m;
}
string decrypt_msg(string c, int a_inv, int b) {
  for (int i = 0; i < c.size(); i++) {
    c[i] = ((26 + (a_inv * (c[i] - 'a' - b)) % 26) % 26) + 'a';
  }
  return c;
}
int get_inv(int a) {
  bool check = false;
  int x = 0;
  do {
    x++;
    if ((a * x) % 26 == 1)
      check = true;
  } while (!check);
  return x;
}
