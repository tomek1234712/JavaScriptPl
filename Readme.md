Sekcja 1.1 Używanie console.log()

Wstep
Wszystkie nowoczesne przeglądarki internetowe, Node.js oraz prawie wszystkie inne środowiska JavaScript obsługują zapisywanie wiadomości na konsoli przy użyciu zestawu metod rejestrowania. Najczęstszą z tych metod jest console.log ().
W środowisku przeglądarki funkcja console.log () jest używana głównie do celów debugowania.

Pierwsze Kroki
Otworz konsole JavaScript w przeglądarce, wpisz nastepujace polecenie i nacisnij enter;
console.log("Hello, World!");
Spowoduje to zalogowanie sie do konsoli
W powyższym przykładzie funkcja console.log () wypisuje Hello, World! do konsoli i zwraca niezdefiniowane (pokazane powyżej w oknie wyjściowym konsoli). Wynika to z faktu, że funkcja console.log () nie ma jawnie zwracanej wartości.

Rejestrowanie zmiennych
console.log () może być używany do rejestrowania zmiennych dowolnego rodzaju; nie tylko string- rejestrator znak. Po prostu podaj zmienną, która ma być wyświetlana w konsoli, na przykład:
var foo = "bar";
console.log (foo);
Spowoduje to zalogowanie się do konsoli:
var foo = "bar";
console.log(foo);
bar
undefined
Jeśli chcesz zarejestrować dwie lub więcej wartości, po prostu oddzielaj je przecinkami. Spacje będą automatycznie dodawane między każdym argumentem podczas konkatenacji:
var thisVar = 'first value';
var thatVar = 'second value';
console.log("thisVar:", thisVar, "and thatVar:" thatVar);
wyjdzie thisVar: first value and thatVar: second value

Placeholders
Możesz użyć console.log () w połączeniu z symbolami zastępczymi:
var greet = "Hello", who = "World"; console.log ("% s,% s!", pozdrawiam, kto);
Spowoduje to zalogowanie się do konsoli:
var greet = "Hello", who = "World"; console.log ("% s,% s!", pozdrawiam, kto);
Hello, World!

Logowanie obiektów
Poniżej widzimy wynik logowania obiektu. Jest to często przydatne do rejestrowania odpowiedzi JSON z wywołań API.
console.log({ 'Email': '', 'Groups': {}, 'Id': 33, 'IsHiddenInUI': false, 'IsSiteAdmin': false, 'LoginName': 'i:0#.w|virtualdomain\\user2', 'PrincipalType': 1, 'Title': 'user2' });

Logowanie elementów HTML
Masz możliwość logowania dowolnego elementu, który istnieje w DOM. W tym przypadku rejestrujemy element body:
console.log (document.body);
Spowoduje to zalogowanie się do konsoli:
Sekcja 1.2: Korzystanie z DOM API
DOM oznacza Document Object Model. Jest to obiektowa prezentacja złożonych dokumentów, takich jak XML i HTML.
Ustawienie właściwości textContent elementu jest jednym ze sposobów wyprowadzania tekstu na stronie internetowej.
Na przykład rozważ następujący tag HTML:

<p id = "paragraph"> </p>
Aby zmienić jego właściwość textContent, możemy uruchomić następujący kod JavaScript:
document.getElementById ("paragraph"). textContent = "Hello, World";
Spowoduje to wybranie elementu z paragrafem id i ustawienie jego treści tekstowej na "Hello, World":
<p id = "paragraph"> Hello, World </p>
Możesz również użyć JavaScript, aby programowo utworzyć nowy element HTML. Rozważmy na przykład dokument HTML z następującą treścią:
<body> <h1> Dodawanie elementu </h1> </body>
W naszym JavaScriptu tworzymy nowy znacznik <p> z właściwością textContent i dodajemy go na końcu treści html:
var element = document.createElement ("p"); element.textContent = "Hello, World"; document.body.appendChild (element); // dodaj nowo utworzony element do DOM
To zmieni twój korpus HTML na:
<body> <h1> Dodawanie elementu </h1> <p>Hello, World </p> </body>
Zauważ, że aby manipulować elementami w DOM przy użyciu JavaScript, kod JavaScript musi zostać uruchomiony po utworzeniu odpowiedniego elementu w dokumencie. Można to osiągnąć, umieszczając znaczniki JavaScript <script> po wszystkich innych treści <body>. Alternatywnie możesz również użyć detektora zdarzeń do słuchania np. zdarzenie onload okna, dodanie kodu do tego detektora zdarzeń opóźni uruchomienie kodu do momentu załadowania całej zawartości strony.
Trzecim sposobem upewnienia się, że cały DOM został załadowany, jest objęcie kodu manipulacji DOM funkcją czasu oczekiwania wynoszącą 0 ms. W ten sposób ten kod JavaScript jest ponownie umieszczany w kolejce na końcu kolejki wykonawczej, co daje przeglądarce szansę na zakończenie pewnych czynności niezwiązanych ze skryptem JavaScript, które czekają na zakończenie przed przystąpieniem do tego nowego fragmentu JavaScript.
