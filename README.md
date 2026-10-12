# Cel projektu

Napisz w C++ konsolową aplikację umożliwiającą zarządzanie zadaniami. Program powinien wykorzystywać programowanie obiektowe, wybrane elementy biblioteki standardowej C++, obsługę plików oraz polimorfizm.

Projekt powinien być podzielony na pliki .h i .cpp.

# 1. Podstawowa obsługa zadań

Program powinien umożliwiać:

dodanie nowego zadania,
wyświetlenie wszystkich zadań,
wyszukanie zadania po identyfikatorze,
oznaczenie zadania jako wykonane,
usunięcie zadania,
zakończenie programu.
Każde zadanie powinno posiadać co najmniej:

unikalny identyfikator
opis
priorytet od 1 do 5
informację, czy zostało wykonane
Nieprawidłowy priorytet powinien zostać odrzucony.

# 2. Programowanie obiektowe

Zaprojektuj klasę reprezentującą ogólne zadanie.

Należy świadomie wykorzystać:

public
protected
private
Uczeń powinien potrafić wyjaśnić różnice między tymi poziomami dostępu oraz uzasadnić, dlaczego konkretne pole lub metoda znajduje się w danej sekcji.

Należy zastosować konstruktor oraz destruktor.

# 3. Różne rodzaje zadań

Program powinien obsługiwać przynajmniej trzy rodzaje zadań:

Zadanie proste — posiada podstawowe informacje o zadaniu.

Zadanie terminowe — dodatkowo posiada termin wykonania.

Zadanie cykliczne — posiada termin oraz informację, co ile dni zadanie jest powtarzane.

Należy wykorzystać dziedziczenie.

# 4. Klasa abstrakcyjna i polimorfizm

Ogólne zadanie powinno stanowić wspólną klasę bazową dla różnych rodzajów zadań.

Należy zastosować funkcje:

virtual
oraz przynajmniej jedną funkcję czysto wirtualną:

virtual ... = 0;
Program powinien przechowywać różne rodzaje zadań we wspólnej kolekcji i obsługiwać je poprzez wskaźnik do klasy bazowej.

Uczeń powinien umieć wyjaśnić:

czym jest polimorfizm,
dlaczego używana jest funkcja virtual,
czym jest klasa abstrakcyjna,
czym jest funkcja czysto wirtualna,
dlaczego destruktor klasy bazowej powinien być wirtualny.

# 5. Biblioteka standardowa

Do przechowywania zadań należy wykorzystać:

std::vector
Do obsługi tekstu:

std::string
Przynajmniej w jednym miejscu należy przejść po vector za pomocą iteratora:

std::vector<...>::iterator
lub:

std::vector<...>::const_iterator
Uczeń powinien znać podstawowe operacje:

push_back()
erase()
begin()
end()
empty()
size()

# 6. Dynamiczna pamięć

W wersji edukacyjnej projektu należy wykorzystać klasyczne:

new
delete
Przykładowo różne typy zadań mogą być przechowywane jako:

std::vector<Zadanie*>
Program nie powinien pozostawiać zaalokowanych obiektów po zakończeniu działania.

Uczeń powinien umieć wyjaśnić:

co robi new,
co robi delete,
czym różni się obiekt od wskaźnika,
dlaczego potrzebny jest destruktor menedżera,
czym jest wyciek pamięci.

# 7. Menu konsolowe

Program powinien posiadać czytelne menu, np.:

===== MENEDZER ZADAN =====

1. Dodaj zadanie proste
2. Dodaj zadanie terminowe
3. Dodaj zadanie cykliczne
4. Pokaz zadania
5. Wykonaj zadanie
6. Usun zadanie
7. Znajdz zadanie
0. Wyjscie

Wybor:
Nieprawidłowe dane wejściowe nie powinny powodować zakończenia programu.

# 8. Obsługa wyjątków

Należy zastosować przynajmniej jeden wyjątek, np. dla:

nieprawidłowego priorytetu,
nieprawidłowego okresu zadania cyklicznego,
problemu z plikiem.
Przykładowe elementy:

throw std::invalid_argument(...);
oraz:

````
try
{
    // ...
}
catch (const std::exception& blad)
{
    // ...
}
````
Uczeń powinien potrafić wyjaśnić różnicę między zwracaniem false a zgłaszaniem wyjątku.

# 9. Zapisywanie danych do pliku

Program powinien umożliwiać zapis zadań i ich ponowne wczytanie po uruchomieniu programu.

Pierwsza wersja może wykorzystywać plik tekstowy.

Uczeń powinien znać:
````
std::ifstream
std::ofstream
std::getline
````
oraz rozumieć różnicę między:

odczytem,
nadpisywaniem pliku,
dopisywaniem do pliku.
Rozszerzenie

Przygotować również wersję wykorzystującą plik binarny.

Uczeń powinien poznać:
````
std::ios::binary
read()
write()
reinterpret_cast
````
oraz potrafić wyjaśnić, dlaczego nie należy bezpośrednio zapisywać całego obiektu zawierającego std::string i funkcje wirtualne jako surowych bajtów.

# 10. Wzorzec Decorator

Program powinien posiadać możliwość formatowania tekstu w konsoli.

Należy zastosować wzorzec projektowy Decorator.

Minimalne dekoratory:
```
pogrubienie
podkreślenie
kolor czerwony
````
Przykładowe zastosowanie:
````
nagłówek               → pogrubiony
zadanie priorytetu 5   → pogrubione
błąd                   → czerwony + pogrubiony
wykonane zadanie       → podkreślone
````
Dekoratory powinny móc być łączone.

Uczeń powinien potrafić wyjaśnić, dlaczego:
````
Tekst
 ↑
Dekorator
 ↑
DekoratorPogrubienia
````
jest lepszym przykładem Decoratora niż zwykła funkcja pogrubTekst().

# 11. ANSI i obsługa konsoli

Program powinien wykorzystywać wybrane sekwencje ANSI.

Uczeń powinien znać przynajmniej:
````
reset formatowania
pogrubienie
podkreślenie
kolor tekstu
czyszczenie linii
czyszczenie ekranu
ustawienie pozycji kursora
````
Operacje terminala warto zamknąć w osobnej klasie, np. odpowiedzialnej za obsługę konsoli.

Nie należy rozrzucać kodów:
````
"\033[...]"
````
po całym programie.

# 12. Odświeżanie interfejsu

Program nie powinien bez potrzeby dopisywać kolejnych kopii menu pod poprzednimi.

W wersji podstawowej można:

ustawić kursor na początku ekranu,
ponownie narysować interfejs.
W wersji rozszerzonej należy przechowywać poprzedni i aktualny stan ekranu oraz aktualizować tylko zmienione linie.

Przykład:
````
poprzednio:
[ ] Projekt

teraz:
[x] Projekt
Program powinien zmienić tylko tę linię zamiast czyścić i rysować cały ekran.
````
Dodatkowe: wykorzystać alternatywny ekran terminala oraz ukrywanie/pokazywanie kursora.

# 13. Podział odpowiedzialności

Kod nie powinien znajdować się w jednej klasie ani w jednym main.cpp.

Należy rozdzielić przynajmniej:
````
model zadania
        ↓
rodzaje zadań
        ↓
zarządzanie kolekcją
        ↓
prezentacja tekstu
        ↓
obsługa terminala
        ↓
main / menu
````
main.cpp powinien przede wszystkim uruchamiać aplikację i sterować jej głównym przebiegiem.

# 14. Organizacja projektu

Przykładowo:
````
projekt/
├── Zadanie.h
├── Zadanie.cpp
├── ...
├── MenedzerZadan.h
├── MenedzerZadan.cpp
├── ...
├── main.cpp
└── Makefile
````
Projekt powinien dać się skompilować jednym poleceniem:

# make
