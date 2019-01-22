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
