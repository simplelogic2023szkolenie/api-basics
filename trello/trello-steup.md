# Instrukcja Uzyskania Klucza API dla Trello

#### Krok 1: Tworzenie Tymczasowego Emaila
1. Otwórz stronę [temp-mail.org](https://temp-mail.org/pl/) aby utworzyć tymczasowy adres email.
   - Alternatywnie, możesz użyć własnego adresu email.

#### Krok 2: Rejestracja w Trello
1. Przejdź do strony rejestracji Trello: [Trello Sign Up](https://trello.com/pl/signup).
2. Zarejestruj się używając tymczasowego emaila lub własnego adresu.

#### Krok 3: Aktywacja Konta i Nadanie Hasła
1. Sprawdź swoją skrzynkę pocztową (tymczasową lub własną) i aktywuj konto Trello poprzez link aktywacyjny.
2. Ustaw hasło dla swojego nowego konta Trello.

#### Krok 4: Logowanie i Tworzenie Tablicy
1. Zaloguj się na swoje konto Trello.
2. Utwórz nową tablicę w Trello. Gdy zostaniesz zapytany o plan premium, wybierz opcję darmową.

#### Krok 5: Power-Ups
1. Po stworzeniu tablicy, przejdź do strony zarządzania Power-Ups: [Trello Power-Ups Admin](https://trello.com/power-ups/admin).
2. Zaakceptuj regulamin, aby kontynuować.

#### Krok 6: Tworzenie Nowego Power-Up
1. Utwórz nowy Power-Up klikając [tutaj](https://trello.com/power-ups/admin/new).
2. Wypełnij wymagane pola w formularzu.

#### Krok 7: Uzyskanie Klucza API
1. Po stworzeniu Power-Up, zostaniesz przeniesiony do okna z danymi Twojego API.
2. Zapisz sobie wyświetlony klucz API w notatniku (na zdjęciu pkt nr 1)
3. Następnie wygeneruj nowy token, kliknij w 'token' oznaczony na zdjęciu numerem 2 i następnie przejdź przez cały proces aby wygenerować token.
5. Skopiuj i zapisz sobie wygenerowany token w notatniku

![Trello API Key](img/trello-token-2.png)



## Zadanie 2: Stworzenie Kolekcji Trello

Utwórz kolekcję w Postmanie na podstawie poniższych specyfikacji:

1. Otwórz aplikację Postman.
2. W lewym panelu wybierz `Collections`.
3. Kliknij `+` oraz wybierz opcję `blank collection` aby stworzyć nową kolekcję
4. Wpisz nazwę kolekcji: `Trello`.
5. Kliknij `ctrl+s` aby zapisać kolekcję.

Instrukcje

- W zakładce variables dodaj zmienne: `boardId`, `cardId`, `actionId`, `doneListId`, `todoListId`
- Dodaj poniższy pre-request script:

```js
pm.request.addQueryParams("key={{key}}")
pm.request.addQueryParams("token={{token}}")
```



## Zadanie 3: Stworzenie Środowiska Trello

Utwórz środowisko w Postmanie zgodnie z poniższymi specyfikacjami:

1. W Postmanie, wybierz ikonę `Environments` w lewym panelu.
2. Kliknij `+` aby stworzyć nowe środowisko.
3. Wpisz nazwę środowiska: `Trello Environment`.
4. Dodaj następujące zmienne środowiskowe:
   - `baseUrl` z wartością `https://api.trello.com/1`
   - `key` z wartością `tutaj-twoj-klucz-api-z-trello`
   - `token` z wartością `tutaj-twoj-token-z-trello`
5. Po dodaniu zmiennych, kliknij `ctrl+s` aby zapisać środowisko.

