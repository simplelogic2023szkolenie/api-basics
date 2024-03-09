## Zadanie 1: Pobieranie listy postów
1. Utwórz zapytanie GET do URL: `https://jsonplaceholder.typicode.com/posts`.
2. Nadaj zapytaniu nazwę `Get Posts List` i zapisz w kolekcji.
3. Przejdź do zakładki "Tests" i dodaj dwa testy:
   - Snippet "Status code: Code is 200" aby sprawdzić kod odpowiedzi.
   - Snippet "Response body: JSON value check" z JSONPath dla wartości `length` i oczekiwaną wartością odpowiadającą liczbie postów `100`, aby sprawdzić liczbę postów w odpowiedzi.
4. Wyślij zapytanie i sprawdź wyniki testów.

<details>
<summary>Podpowiedzi</summary>

 `jsonData.length`

</details>



## Zadanie 2: Pobieranie szczegółów konkretnego posta
1. Utwórz zapytanie GET do URL: `https://jsonplaceholder.typicode.com/posts/1`.
2. Nadaj zapytaniu nazwę `Get Post Details` i zapisz w kolekcji.
3. Przejdź do zakładki "Tests" i dodaj dwa testy:
   - Snippet "Status code: Code is 200" aby sprawdzić kod odpowiedzi.
   - Snippet "Response body: JSON value check" z JSONPath dla wartości `id` i oczekiwaną wartością `1`, aby sprawdzić, czy pole `id` w odpowiedzi ma wartość `1`.
4. Wyślij zapytanie i sprawdź wyniki testów.

<details>
<summary>Podpowiedzi</summary>

 `jsonData.id`

</details>

## Zadanie 3: Tworzenie nowego posta
1. Utwórz zapytanie POST do URL: `https://jsonplaceholder.typicode.com/posts`.
2. W sekcji `Body` wybierz typ `raw` i format `JSON (application/json)`.
3. Wpisz body dla POST-a:

```json
{
	"title": "foo",
	"body": "bar",
	"userId": 1
}
```

4. Nadaj zapytaniu nazwę `Create Post` i zapisz w kolekcji.
5. Przejdź do zakładki "Tests" i dodaj dwa testy:
- Snippet "Status code: Code is 201" aby sprawdzić kod odpowiedzi.
- Snippet "Response body: JSON value check" z JSONPath dla wartości `title` i oczekiwaną wartością `foo` aby sprawdzić wartość klucza `title` w odpowiedzi.
6. Wyślij zapytanie i sprawdź wyniki testów.

<details>
<summary>Podpowiedzi</summary>

 `jsonData.title`

</details>


## Zadanie 4: Usuwanie posta
1. Utwórz zapytanie DELETE do URL: `https://jsonplaceholder.typicode.com/posts/1`.
2. Nadaj zapytaniu nazwę `Delete Post` i zapisz w kolekcji.
3. Przejdź do zakładki "Tests" i dodaj dwa testy:
- Snippet "Status code: Code is 200" aby sprawdzić kod odpowiedzi.
4. Wyślij zapytanie i sprawdź wyniki testów.


## Zadanie 5: Filtracja postów według userId
1. Utwórz zapytanie GET z parametrem query `userId=1` do URL: `https://jsonplaceholder.typicode.com/posts......` (kropki podane zeby nie spoilerować rozwiązania całego zadania)
2. Nadaj zapytaniu nazwę `Filter Posts by User` i zapisz w kolekcji.
3. Przejdź do zakładki "Tests" i dodaj dwa testy:
   - Snippet "Status code: Code is 200" aby sprawdzić kod odpowiedzi.
   - Snippet "Response body: JSON value check" z JSONPath `jsonData.length` i oczekiwaną wartością, na przykład `10`, jeśli spodziewasz się 10 postów, aby sprawdzić liczbę postów zwróconych dla `userId=1`.
4. Wyślij zapytanie i sprawdź wyniki testów.

<details>
<summary>Podpowiedź dla poprawnego ULRa z parametrem </summary>

 `https://jsonplaceholder.typicode.com/posts?userId=1`

</details>


## Zadanie 6: Aktualizowanie istniejącego posta
1. Utwórz zapytanie PUT do URL: `https://jsonplaceholder.typicode.com/posts/1`.
2. W sekcji `Body` wpisz nowe dane dla posta:

```json

{
	"title": "updated title",
	"body": "updated body",
	"userId": 1
}
```

3. Nadaj zapytaniu nazwę `Update Post` i zapisz w kolekcji.
4. Przejdź do zakładki "Tests" i dodaj dwa testy:
- Snippet "Status code: Code is 200" aby sprawdzić kod odpowiedzi.
- Snippet "Response body: JSON value check" z JSONPath dla wartości `title` i oczekiwaną wartością `updated title` aby sprawdzić wartość klucza `title` w odpowiedzi.
- Snippet "Response body: JSON value check" z JSONPath dla wartości `id` i oczekiwaną wartością `1`, aby sprawdzić, czy pole `id` w odpowiedzi ma wartość `1`.
5. Wyślij zapytanie i sprawdź wyniki testów.

<details>
<summary>Podpowiedzi</summary>

 `jsonData.title`
 `jsonData.id`

</details>



## Zadanie 7: Częściowa aktualizacja posta
1. Utwórz zapytanie PATCH do URL: `https://jsonplaceholder.typicode.com/posts/1`.
2. W sekcji `Body` wpisz tylko jedno pole, które chcesz zaktualizować:

```json
{
	"title": "patched title"
}
```

3. Nadaj zapytaniu nazwę `Patch Post` i zapisz w kolekcji.
4. Przejdź do zakładki "Tests" i dodaj dwa testy:
- Snippet "Status code: Code is 200" aby sprawdzić kod odpowiedzi.
- Snippet "Response body: JSON value check" z JSONPath dla wartości `title` i oczekiwaną wartością `patched title` aby sprawdzić wartość klucza `title` w odpowiedzi.
5. Wyślij zapytanie i sprawdź wyniki testów.

<details>
<summary>Podpowiedzi</summary>

 `jsonData.title`

</details>
