# Apteka

# Dokumentacja aplikacji "appTEKA"

## 1. Informacje ogólne

**Nazwa projektu:** appTEKA  
**Autor:** Małgorzata Kulik, Małgorzata Golonko, Magda Kupiecka
**Opis:**
Aplikacja "appTEKA" jest przeznaczona do zarządzania danymi klientów oraz lekami w aptece. Składa się z graficznego interfejsu logowania (GUI), panelu tekstowego administratora oraz obsługi plików CSV i XLSX.

## 2. Wymagania systemowe

- Python 3.11 lub wyższy
- System operacyjny: Windows/Linux/macOS
- Zewnętrzne biblioteki:
  - `pandas`
  - `openpyxl`
  - `tkinter`

## 3. Struktura projektu

appTEKA/
├── DATABASE/
│ ├── address.csv
│ ├── customer.csv
│ ├── drugs.xlsx
│ └── users.csv
├── main.py
├── main_GUI.py
├── manage.py
├── customers.py
└── README.md

## 4. Moduły i funkcjonalności

### 4.1 `main_GUI.py` - Panel logowania (GUI)

- Umożliwa logowanie użytkowników z pliku `users.csv`.
- Klasa: `LoginWelcomeApp`
- Główne funkcje:
  - `show_login_screen()`
  - `user_logon(username, password)`
  - `show_welcome_screen()`
- Po zalogowaniu wyświetlany jest komunikat powitalny.

### 4.2 `customers.py` - Obsługa klientów

- Rejestracja i usuwanie klientów.
- Zapis danych klienta do `customer.csv`, `address.csv` i pliku `ID.txt`.
- Zatwierdzanie danych:
  - Imię, nazwisko, miasto, kraj: tylko litery
  - Email: tylko domeny .pl i .com
  - Telefon: 9 cyfr
- Funkcje:
  - `register_customer()`
  - `delete_customer()`
  - `admin_panel()`

### 4.3 `manage.py` - Obsługa leków

- Operacje na pliku `drugs.xlsx` (zapis i usuwanie leków).
- Główne funkcje:
  - `add_drug()`
  - `del_drug()`

### 4.4 `main.py` - Główna pętla programu

- Uruchamia kolejno:
  - `add_drug()`
  - `del_drug()`
  - `admin_panel()`

## 5. Pliki danych

### 5.1 `users.csv`

Zawiera dane do logowania:

id,username,password,grant
001,admin,admin,admin
002,user,user,user


### 5.2 `customer.csv`

Zawiera dane klientów:

ID,NAME,E-MAIL,PHONE,CREATED,UPDATED
201,Jan Kowalski,jan@wp.pl,123456789,2024-06-13,2024-06-13


### 5.3 `address.csv`

Zawiera dane adresowe:

ID,STREET,CITY,COUNTRY
201,Lipowa 12,Warszawa,Polska


### 5.4 `drugs.xlsx`

Zawiera dane o lekach:

ID,DRUG,ON_RECEPT,NO_PACKAGES_AVAILABLE,DATE
1,Polopiryna,NO,1200,2024-03-25


## 6. Przykładowy scenariusz użycia

### 6.1 Logowanie

1. Uruchom `main_GUI.py`
2. Wprowadź login: `admin`, hasło: `admin`
3. Otrzymasz komunikat "Welcome admin"

### 6.2 Rejestracja klienta

1. Uruchom `main.py`
2. W menu administratora wybierz opcję 1
3. Wprowadź dane klienta
4. Dane zostaną zapisane w plikach CSV i jako `ID.txt`

### 6.3 Dodanie leku

1. W menu administratora wybierz opcję dodania leku
2. Podaj nazwę leku, informację o recepcie, liczbę opakowań

## 7. Bezpieczeństwo i potwierdzanie danych

- zatwierdzanie danych wejściowych na poziomie formularzy i terminala.
- Dane logowania nie są szyfrowane.

## 8. Podsumowanie

Aplikacja "appTEKA" umożliwia w sposob podstawowy zarządzanie klientami oraz lekami w aptece. Obsługuje rejestrację, logowanie, edycję i usuwanie danych w formacie CSV/XLSX oraz korzysta z graficznego i tekstowego interfejsu użytkownika.
