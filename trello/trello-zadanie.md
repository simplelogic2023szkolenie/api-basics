# Instrukcje Testowania API Trello


###  1. Create a Board - POST /1/boards/

https://developer.atlassian.com/cloud/trello/rest/api-group-boards/#api-boards-post

    Stwórz tablicę, jako nazwę przekaż losowy tekst używając wybranej zmiennej dynamicznej:
    https://learning.postman.com/docs/writing-scripts/script-references/variables-list/
    
    dodaj qyery param defaultLists=false

    
    W zakładce test:
    - dodaj test sprawdzający status code
    - zapisz otrzymane ID tablicy jako zmienną kolekcji o nazwie 'boardId'

pm.collectionVariables.set("boardId", pm.response.json().id);


### 2. Create a new List - POST /1/lists

https://developer.atlassian.com/cloud/trello/rest/api-group-lists/#api-lists-post
  
    Dodaj do tablicy listę o nazwie DONE
    
    W zakładce test:
    - dodaj test sprawdzający status code
    - dodaj test sprawdzający czy nazwa listy otrzymana w response to DONE
    - zapisz otrzymane ID listy jako zmienną kolekcji o nazwie 'doneId'
    
### 3. Create a new List - POST /1/lists

https://developer.atlassian.com/cloud/trello/rest/api-group-lists/#api-lists-post
   
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
