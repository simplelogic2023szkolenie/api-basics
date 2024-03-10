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



## Zadanie 2: Stworzenie Środowiska Trello

Utwórz środowisko w Postmanie zgodnie z poniższymi specyfikacjami:

1. W Postmanie, wybierz ikonę `Environments` w lewym panelu.
2. Kliknij `+` aby stworzyć nowe środowisko.
3. Wpisz nazwę środowiska: `Trello Environment`.
4. Dodaj następujące zmienne środowiskowe:
   - `baseUrl` z wartością `https://api.trello.com/1`
   - `key` z wartością `tutaj-twoj-klucz-api-z-trello`
   - `token` z wartością `tutaj-twoj-token-z-trello`
5. Po dodaniu zmiennych, kliknij `ctrl+s` aby zapisać środowisko.


## Zadanie 3: Stworzenie Kolekcji Trello

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


# Instrukcje Testowania API Trello


###  1. Create a Board - POST /1/boards/

https://developer.atlassian.com/cloud/trello/rest/api-group-boards/#api-boards-post

    Stwórz tablicę, jako nazwę przekaż losowy tekst używając wybranej zmiennej dynamicznej:
    https://learning.postman.com/docs/writing-scripts/script-references/variables-list/
    
    W zakładce test:
    - dodaj test sprawdzający status code
    - zapisz otrzymane ID tablicy jako zmienną kolekcji o nazwie 'boardId'

### 2. Create a new List - POST /1/lists

[https://developer.atlassian.com/cloud/trello/rest/api-group-cards/#api-cards-post
](https://developer.atlassian.com/cloud/trello/rest/api-group-lists/#api-lists-post)
  
    Dodaj do tablicy listę o nazwie DONE
    
    W zakładce test:
    - dodaj test sprawdzający status code
    - dodaj test sprawdzający czy nazwa listy otrzymana w response to DONE
    - zapisz otrzymane ID listy jako zmienną kolekcji o nazwie 'doneId'
    
### 3. Create a new List - POST /1/lists

[https://developer.atlassian.com/cloud/trello/rest/api-group-cards/#api-cards-post
](https://developer.atlassian.com/cloud/trello/rest/api-group-lists/#api-lists-post)
   
    Dodaj do tablicy listę o nazwie TODO
    
    W zakładce test:
    - dodaj test sprawdzający status code
    - dodaj test sprawdzający czy w body reponse atrybut closed równy jest false
    - zapisz otrzymane ID listy jako zmienną kolekcji o nazwie 'todoId'
    
### 4. Create a new Card - POST /1/cards

https://developer.atlassian.com/cloud/trello/rest/api-group-cards/#api-cards-post

    Stwórz nową kartę w liście TODO o nazwie RestIntroduction
    
    W zakładce test:
    - dodaj test sprawdzający status code
    - dodaj test sprawdzający czy w reponse body name karty to RestIntroduction
    - zapisz otrzymane ID   jako zmienną kolekcji o nazwie 'cardId'
    
### 5. Add a new comment to a Card - POST /1/cards/{id}/actions/comments

https://developer.atlassian.com/cloud/trello/rest/api-group-cards/#api-cards-id-actions-comments-post

    Dodaj do karty komentarz o treści “done!”
    
    W zakładce test:
    - dodaj test sprawdzający status code
    - dodaj test sprawdzający czy w reponse body tekst komentarza to "done!"
    - zapisz otrzymane ID tablicy jako zmienną kolekcji o nazwie 'actionId'
    
### 6. Create Reaction for Action - POST /1/actions/{idAction}/reactions

https://developer.atlassian.com/cloud/trello/rest/api-group-actions/#api-actions-idaction-reactions-post

    Utwórz reakcje do komentarza -> wysłanie emoji LIKE 
    
    Wysłanie reakcji zgodnie z dokumentacją bedzie od Ciebie wymagać przekazania 
    w body JSONa określającego, które emojii dodać. Aby dodać LIKE użyj poniży JSON:
        
```json
{
    "unified": "1F44D",
    "shortName": "+1"
}  
```   
    W zakładce test:
    - dodaj test sprawdzający status code
    
### 7. Update a Card - PUT /1/cards/{id}

https://developer.atlassian.com/cloud/trello/rest/api-group-cards/#api-cards-id-put

    Przenieś kartę z TODO na DONE
    
    W zakładce test:
    - dodaj test sprawdzający status code
    
### 8. Delete a Board - DELETE /1/boards/{id}

https://developer.atlassian.com/cloud/trello/rest/api-group-boards/#api-boards-id-delete

    Usuń tablicę
    
    W zakładce test:
    - dodaj test sprawdzający status code
    
### 9. Get a Board - GET /1/boards/{id}

https://developer.atlassian.com/cloud/trello/rest/api-group-boards/#api-boards-id-get

    Spróbuj pobrać dane usuniętej tablicy
    
    W zakładce test:
    - dodaj test sprawdzający status code = 404    
