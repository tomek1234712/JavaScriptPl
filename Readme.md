Punkt 1.1 Używanie console.log()

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

Punkt 1.2: Korzystanie z DOM API
DOM oznacza Document Object Model. Jest to obiektowa prezentacja złożonych dokumentów, takich jak XML i HTML.
Ustawienie właściwości textContent elementu jest jednym ze sposobów wyprowadzania tekstu na stronie internetowej.
Na przykład rozważ następujący tag HTML:

<p id = "paragraph"> </ p>
Aby zmienić jego właściwość textContent, możemy uruchomić następujący kod JavaScript:
document.getElementById ("paragraph"). textContent = "Hello, World";
Spowoduje to wybranie elementu z paragrafem id i ustawienie jego treści tekstowej na "Hello, World":
<p id = "paragraph"> Hello, World </ p>
Możesz również użyć JavaScript, aby programowo utworzyć nowy element HTML. Rozważmy na przykład dokument HTML z następującą treścią:
<body> <h1> Dodawanie elementu </ h1> </ body>
W naszym JavaScriptu tworzymy nowy znacznik <p> z właściwością textContent i dodajemy go na końcu treści html:
var element = document.createElement ("p"); element.textContent = "Hello, World"; document.body.appendChild (element); // dodaj nowo utworzony element do DOM
To zmieni twój korpus HTML na:
< body> <h1> Dodawanie elementu </ h1> <p> Hello, World </ p> </ body>
Zauważ, że aby manipulować elementami w DOM przy użyciu JavaScript, kod JavaScript musi zostać uruchomiony po utworzeniu odpowiedniego elementu w dokumencie. Można to osiągnąć, umieszczając znaczniki JavaScript <script> po wszystkich innych treści <body>. Alternatywnie możesz również użyć detektora zdarzeń do słuchania np. zdarzenie onload okna, dodanie kodu do tego detektora zdarzeń opóźni uruchomienie kodu do momentu załadowania całej zawartości strony.
Trzecim sposobem upewnienia się, że cały DOM został załadowany, jest objęcie kodu manipulacji DOM funkcją czasu oczekiwania wynoszącą 0 ms. W ten sposób ten kod JavaScript jest ponownie umieszczany w kolejce na końcu kolejki wykonawczej, co daje przeglądarce szansę na zakończenie pewnych czynności niezwiązanych ze skryptem JavaScript, które czekają na zakończenie przed przystąpieniem do tego nowego fragmentu JavaScript.

Punkt 1.3: Korzystanie z window.alert()
W metodzie ostrzegania na ekranie pojawia się wizualne pole alarmowe. Parametr metody ostrzegania jest wyświetlany użytkownikowi w postaci zwykłego tekstu:
window.alert(message);
Ponieważ okno jest obiektem globalnym, można wywołać również następujące skróty:
alert(message);
Co zatem robi window.alert()? Weźmy następujący przykład:
alert('hello, world');

Uwagi
Metoda alert jest technicznie właściwością obiektu okna, ale ponieważ wszystkie właściwości okna są automatycznie zmiennymi globalnymi, możemy użyć alertu jako zmiennej globalnej zamiast jako właściwości okna, co oznacza, że można bezpośrednio użyć alert() zamiast window.alert().
W przeciwieństwie do korzystania z konsoli.log, alert działa jako modalna zachęta, co oznacza, że wywołanie kodu alertów zostanie wstrzymane do momentu otrzymania odpowiedzi. Tradycyjnie oznacza to, że żaden inny kod JavaScript nie zostanie wykonany, dopóki alarm nie zostanie odrzucony:
alert('Pauza!'); konsola.log('Alert został usunięty');
Jednakże specyfikacja pozwala na dalsze wykonywanie kodu wyzwalanego zdarzeniami, nawet jeśli okno dialogowe modalne jest nadal wyświetlane. W takich implementacjach możliwe jest uruchomienie innego kodu podczas wyświetlania modalnego okna dialogowego.
Więcej informacji na temat korzystania z metody alertów można znaleźć w temacie podpowiedzi modali.
Stosowanie alertów jest zazwyczaj zniechęcane na korzyść innych metod, które nie blokują użytkownikom możliwości interakcji ze stroną - w celu stworzenia lepszych wrażeń użytkownika. Niemniej jednak może być przydatna do debugowania.
Począwszy od Chrome 46.0, window.alert() jest blokowany wewnątrz <iframe>, chyba że jego atrybut piaskownicy ma wartość allow-modal.

Sekcja 1.4: Korzystanie z window.prompt()
Łatwym sposobem na uzyskanie danych wejściowych od użytkownika jest użycie metody prompt().
Podpowiedź składniowa (tekst, [domyślnie]);
tekst: Tekst wyświetlany w polu zachęty. default: Domyślna wartość dla wejścia ﬁeld (opcjonalnie).
Przykłady var age = prompt("Ile lat masz?"); console.log(age); // Drukuje wartość dodaną przez użytkownika

Jeśli użytkownik kliknie przycisk OK, wartość wejściowa zostanie zwrócona. W przeciwnym razie metoda zwraca null.
Wartością zwracaną zachęty jest zawsze łańcuch, chyba że użytkownik kliknie przycisk Cancel , w którym to przypadku zwraca null. Safari jest wyjątkiem w tym, że gdy użytkownik kliknie przycisk Cancel, funkcja zwraca pusty łańcuch. Stamtąd można przekonwertować wartość zwrotu na inny typ, taki jak liczba całkowita.
Uwagi
Podczas wyświetlania okna dialogowego użytkownik nie ma dostępu do innych części strony, ponieważ okna dialogowe są oknami modalnymi. Począwszy od Chrome 46.0 metoda ta jest blokowana wewnątrz <ramki>, chyba że jej atrybut piaskownicy ma wartość allow-modal.

Punkt 1.5: Korzystanie z window.conﬁrm()
Metoda window.confirm() wyświetla okno dialogowe modalne z opcjonalnym komunikatem i dwoma przyciskami, OK i Cancel.
Weźmy teraz następujący przykład:
result = window.confirm(message);
Tutaj komunikat jest opcjonalnym ciągiem znaków, który ma być wyświetlany w oknie dialogowym, a wynikiem jest wartość boolean wskazująca, czy wybrano opcję OK czy Cancel (true oznacza OK).
window.confirm() jest zazwyczaj używany do zapytania użytkownika o potwierdzenie przed wykonaniem niebezpiecznej operacji, takiej jak usunięcie czegoś w Panelu sterowania:
if(window.confirm("Czy na pewno chcesz to usunąć?"))) {
deleteItem(itemId);
}
Jeśli potrzebujesz go do późniejszego wykorzystania, możesz po prostu zapisać wynik interakcji użytkownika w zmiennej:

var deleteConfirm = window.confirm("Czy na pewno chcesz to usunąć?");
Uwagi
Argument ten jest opcjonalny i nie jest wymagany przez specyfikację. Okna dialogowe są oknami modalnymi - uniemożliwiają użytkownikowi dostęp do reszty interfejsu programu do momentu zamknięcia okna dialogowego. Z tego powodu nie należy nadużywać żadnej funkcji, która tworzy okno dialogowe (lub okno modalne). I niezależnie od tego, istnieją bardzo dobre powody, aby unikać używania okien dialogowych do konfirmacji. Począwszy od Chrome 46.0 metoda ta jest blokowana wewnątrz <iframe>, chyba że jej atrybut piaskownicy ma wartość allow-modal. Powszechnie przyjmuje się wywoływanie metody conﬁrm z usuniętą notacją okna, ponieważ obiekt okna jest zawsze ukryty. Zaleca się jednak wyraźne określenie obiektu okna, ponieważ oczekiwane zachowanie może się zmienić z powodu implementacji na niższym poziomie zakresu z podobnie nazwanymi metodami.

Punkt 1.6: Korzystanie z interfejsu API DOM (z tekstem graficznym: płótno, SVG lub plik obrazu)
Użycie elementów płóciennych
HTML dostarcza elementu płótna do budowania obrazów rastrowych.
Najpierw buduj płótno do przechowywania informacji o pikselach obrazu.
var canvas = document.createElement('canvas'); canvas.width = 500; canvas.height = 250;
Następnie wybierz kontekst płótna, w tym przypadku dwuwymiarowy:
var ctx = canvas.getContext('2d');
Następnie należy ustawić właściwości związane z tekstem:
ctx.font = '30px Cursive'; ctx.fillText("Hello world!", 50, 50);
Następnie wstaw element płótna do strony, aby przejść na stronę eﬀect
document.body.appendChild(canvas);
Korzystanie z SVG
SVG służy do budowania skalowalnej grafiki wektorowej i może być używany w HTML.
Najpierw utwórz kontener elementu SVG o wymiarach:
var svg = document.createElementNS('http://www.w3.org/2000/svg', 'svg'); svg.width = 500; svg.height = 50;
Następnie zbuduj element tekstowy z pożądanym położeniem i charakterystyką czcionki:
var text = document.createElementNS('http://www.w3.org/2000/svg', 'text'); text.setAttribute('x', '0');
text.setAttribute("y", "50"); text.style.fontFamily = "Times New Roman"; text.style.fontSize = "50";
Następnie dodaj rzeczywisty tekst, aby wyświetlić go do elementu tekstowego:
text.textContent = "Hello world!
Na koniec dodaj element tekstowy do naszego kontenera svg i dodaj element svg container do dokumentu HTML:
svg.appendChild(text); document.body.appendChild(svg);
Profil obrazu
Jeśli masz już plik obrazu zawierający żądany tekst i umieściłeś go na serwerze, możesz dodać adres URL obrazu, a następnie dodać obraz do dokumentu w następujący sposób:
var img = new Image(); img.src = 'https://i.ytimg.com/vi/zecueq-mo4M/maxresdefault.jpg'; document.body.appendChild(img);

Rozdział 2: Zmienne JavaScript
variable_name {Required}. Nazwa zmiennej: używana przy wywołaniu. = [Opcjonalnie] Przypisanie (określenie zmiennej) wartość {wymagane przy użyciu Przypisanie}. Wartość zmiennej [domyślnie: nieokreślona].
Zmienne są tym, co składa się na większość JavaScript. Te zmienne składają się na rzeczy od liczb do obiektów, które są w całym JavaScript, aby ułatwić sobie życie.

Punkt 2.1: Określanie zmiennej
var myVariable = "To jest zmienna!
Jest to przykład określenia zmiennych. Zmienna ta jest nazywana "ciągiem znaków", ponieważ ma znaki ASCII (A-Z, 0-9, !@#\$, itd.)

Punkt 2.2: Użycie zmiennej
var number1 = 5; number1 = 3;
Tutaj określiliśmy numer o nazwie "number1", który był równy 5, jednak w drugim wierszu zmieniliśmy wartość na 3.
Aby pokazać wartość zmiennej, logujemy ją do konsoli lub używamy window.alert():
console.log(numer1); // 3 window.alert(numer1); // 3
Aby dodać, odjąć, pomnożyć, dzielić, itd:
number1 = number1 + 5; // 3 + 5 = 8 number1 = number1 - 6; // 8 - 6 = 2 var number2 = number1 \* 10; // 2 (razy) 10 = 20 var number3 = number2 / number1; // 20 (podzielone przez) 2 = 10;
Możemy również dodać łańcuchy, które będą je łączyć lub łączyć. Na przykład:
var myString = "Jestem " + "string!"; // "Jestem ciągiem!

Punkt 2.3: Rodzaje zmiennych
var myInteger = 12; // 32-bitowa liczba (od -2,147,483,648 do 2,147,483,647) var myLong = 9310141419482; // 64-bitowa liczba (od -9,223,372,036,854,775,808 do 9,223,372,036,854,875,807) var myFloat = 5.5; // 32-bitowa liczba zmiennoprzecinkowa (dziesiętna) var myDouble = 9310141419482.22; // 64-bitowa liczba zmiennoprzecinkowa
var myBoolean = true; // 1-bit true/false (0 lub 1) var myBoolean2 = false;
var myNotANumber = NaN; var NaN_Example = 0/0; // NaN: Podział przez zero nie jest możliwy
var notDefined; // niezdefiniowany: nie zdefiniowaliśmy go do niczego jeszcze
window.alert(aRandomVariable); // niezdefiniowany
var myNull = null; // zerowy /// itd.

Punkt 2.4: Tablice i obiekty
var myArray = []; // pusta tablica
Tablica jest zbiorem zmiennych. Na przykład:
var favoriteFruits = ["apple", "orange", "strawberry"];
var carsInParkingLot = ["Toyota", "Ferrari", "Lexus"];
var employees = ["Billy", "Bob", "Joe"];
var primeNumbers = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31];
var randomVariables = [2, "any type works", niezdefiniowane, zerowe, prawdziwe, 2.51, true, 2.51;
myArray = ["zero", "jeden", "dwa"];
window.alert(myArray[0]); // 0 jest pierwszym elementem tablicy // w tym przypadku wartością byłaby "zero" myArray = ["John Doe", "Billy"]; elementNumber = 1;
window.alert(myArray[elementNumber]); // Billy
Obiekt to grupa wartości; w przeciwieństwie do tablic możemy zrobić coś lepszego od nich:
myObject = {}; john = {imię i nazwisko: "John", ostatnia nazwa: "Doe", pełna nazwa: "John Doe"}; billy = {imię i nazwisko: "Billy", ostatnia nazwa: niezdefiniowana, pełna nazwa: "Billy" };
window.alert (john.fullname); // John Doe window.alert (billy.firstname); // Billy
Zamiast tworzyć tablicę ["John Doe", "Billy"] i nazywać myArray[0], możemy po prostu nazwać john.fullname i billy.fullname.

Rozdział 3: Wbudowane stałe

Punkt 3.1: zerowe
null służy do przedstawiania celowego braku wartości obiektu i jest wartością prymitywną. W przeciwieństwie do niezdefiniowanej, nie jest właściwością obiektu globalnego.
Jest równa niezdefiniowanej, ale nie identycznej z nią.
null === niezdefiniowany; // true null === niezdefiniowany; // false
CAREFUL: Typ null to "obiekt".
typeof null; // "object";
Aby prawidłowo sprawdzić, czy wartość jest pusta, porównać ją z operatorem ścisłej równości
var a = null;
a === null; // true

Punkt 3.2: Testing for NaN using isNaN()
window.isNaN()
Funkcja globalna isNaN() może być użyta do sprawdzenia, czy określona wartość lub wyrażenie ocenia jako NaN. Funkcja ta (w skrócie) sprawdza najpierw, czy wartość jest liczbą, czy nie próbuje jej przekonwertować (_), a następnie sprawdza, czy wynikowa wartość jest NaN. Z tego powodu ta metoda testowania może powodować zamieszanie.
(_) Metoda "konwersji" nie jest tak prosta, zobacz ECMA-262 18.2.3, aby uzyskać szczegółowe wyjaśnienie algorytmu.
Te przykłady pomogą Ci lepiej zrozumieć zachowanie isNaN():
isNaN(NaN); // true
isNaN(1); // false: 1 to liczba
isNaN(-2e-4); // false: -2e-4 to liczba (-0.0002) w notacji naukowej
isNaN(Infinity); // false: Nieskończoność jest liczbą
isNaN(true); // false: konwersja na 1, który jest liczbą
isNaN(false); // false: konwersja na 0, który jest liczbą
isNaN(null); // false: konwersja na 0, który jest liczbą
isNaN(""); // false: konwersja na 0, który jest liczbą
isNaN(" "); // false: konwersja na 0, który jest liczbą
isNaN("45.3"); // false: łańcuch reprezentujący liczbę, przekonwertowany na 45.3
isNaN("1.2e3"); // false: łańcuch reprezentujący liczbę, skonwertowany na 1.2e3
isNaN("Infinity"); // false: łańcuch reprezentujący liczbę, skonwertowany na Infinity
isNaN(new Date); // false: Obiekt daty, skonwertowany do milisekund od epoki jest
isNaN("10\$"); // true : konwersja nie powiodła się, znak dolara nie jest cyfrą
isNaN ("hello"); // true : konwersja nie powiodła się, żadna cyfra w ogóle nie jest
isNaN(niezdefiniowana); // true : skonwertowany do NaN
isNaN(); // true : skonwertowany do NaN (domyślnie niezdefiniowany) isNaN(funkcja(){}); // true : konwersja nie powiodła się
isNaN({}); // true : konwersja nie powiodła się
isNaN([1, 2]); // true : skonwertowany do "1, 2", którego nie można przekonwertować do liczby.

Ten ostatni jest nieco trudny: sprawdzenie, czy tablica jest NaN. Aby to zrobić, konstruktor Number() po raz pierwszy konwertuje tablicę
do łańcucha, następnie do liczby; jest to powód, dla którego isNaN([]) i isNaN([34]) zwracają false, ale isNaN([1, 2]) i isNaN([true]) oba zwracają true: ponieważ są przekonwertowane odpowiednio na "", "34", "1,2" i "true". Ogólnie tablica jest uważana za NaN przez isNaN(), chyba że posiada tylko jeden element, którego reprezentacja łańcuchowa może być przekonwertowana na prawidłową liczbę.
Wersja ≥ 6
Number.isNaN()
W ECMAScript 6, funkcja Number.isNaN() została zaimplementowana przede wszystkim w celu uniknięcia problemu window.isNaN() wymuszonego przeliczenia parametru na liczbę. Number.isNaN(), rzeczywiście, nie próbuje przekonwertować wartości na liczbę przed testowaniem. Oznacza to również, że tylko wartości typu numer, które są również NaN, zwracają true (co w zasadzie oznacza tylko Number.isNaN(NaN)).
Z ECMA-262 20.1.2.4:
Kiedy wywoływany jest Number.isNaN z jednym numerem argumentu, podejmowane są następujące kroki:
Jeżeli Typ (numer) nie jest Number, zwróć false.1. Jeżeli numer jest NaN, zwróć true.2. W przeciwnym razie zwróć false.3.
Kilka przykładów:
// Jeden i jedyny numer.isNaN(NaN); // true
// Numbers Number.isNaN(1); // false Number.isNaN(-2e-4); // false Number.isNaN(Infinity); // false
// Wartości nie typu Numer.isNaN(true); // false Number.isNaN(false); // false Number.isNaN(null); // false Number.isNaN(""); // false Number.isNaN(" "); // false Number.isNaN("45.3"); // false Number.isNaN("1.2e3"); // false Number.isNaN("Infinity"); // false Number.isNaN(new Date); // false Number.isNaN("10\$"); // false Number.isNaN("hello"); // false Number.isNaN(niezdefiniowany); // false Number.isNaN(); // false Number.isNaN(funkcja(){}); // false Number.isNaN({}); // false Number.isNaN([]); // false Number.isNaN([1]); // false Number.isNaN([1, 2]); // false Number.isNaN([true]); // false
Punkt 3.3: NaN
NaN oznacza "Not a Number". Gdy funkcja matematyczna lub operacja w JavaScript nie może zwrócić określonego numeru, to zamiast tego zwraca wartość NaN.
Jest to własność obiektu globalnego i odniesienie do Number.NaN
window.hasOwnProperty ("NaN"); // prawdziwy NaN; // NaN
Być może myląco, NaN jest nadal uważany za numer.
typ NaN; // "liczba
Nie sprawdzaj NaN używając operatora równości. Zobacz isNaN zamiast tego.
NaN == NaN // false NaN === NaN // false

Punkt 3.4: undeﬁned and null
Na pierwszy rzut oka może się wydawać, że nieważne i niezdefiniowane są w zasadzie takie same, jednak są subtelne, ale ważne diﬀerences
niezdefiniowana jest brak wartości w kompilatorze, ponieważ tam gdzie powinna ona być wartością, nie została ona wprowadzona, tak jak w przypadku nieprzypisanej zmiennej.
undefined jest wartością globalną, która reprezentuje brak przypisanej wartości. typeof undefined === 'undefined' null jest obiektem, który wskazuje, że zmiennej została jednoznacznie przypisana "no value". typeof null === 'object'
Ustawienie zmiennej na niezdefiniowaną oznacza, że zmienna eﬀectively nie istnieje. Niektóre procesy, takie jak serializacja JSON, mogą odbierać niezdefiniowane właściwości z obiektów. W przeciwieństwie do tego, null właściwości wskazują, że zostaną zachowane, więc można wyraźnie przekazać pojęcie "pustej" właściwości.
Poniższa ocena do niezdefiniowanych:
Zmienna, gdy jest zadeklarowana, ale nie przypisana do niej wartość (tzn. określona) let foo; console.log('is undefined?', foo === niezdefiniowana); // jest niezdefiniowana? Prawdziwy Dostęp do wartości właściwości, która nie istnieje niech foo = { a: a' }; console.log('is undefined?', foo.b === niezdefiniowana); // jest niezdefiniowana? true Zwrot wartości funkcji, która nie zwraca wartości foo() { return; } console.log('is undefined?', foo() === niezdefiniowana); // jest niezdefiniowana? true Wartość argumentu funkcji, który jest zadeklarowany, ale został pominięty w funkcji wywołania foo(param) { console.log('is undefined?', param === niezdefiniowany); } foo('a'); foo(); // jest niezdefiniowany? false /// is unefined?
niezdefiniowana jest również właściwością globalnego obiektu okna.
// Tylko w przeglądarkach console.log (window.undefined); // niezdefiniowane window.hasOwnProperty('undefined'); // true Version < 5
Przed ECMAScript 5 można było zmienić wartość właściwości window.undefined na jakąkolwiek inną wartość potencjalnie łamiącą wszystko.

Punkt 3.5: Nieskonczonosc
1 / 0; // Infinity // zekaj! co to?
Nieskończoność jest właściwością globalnego obiektu (dlatego jest zmienną globalną), która reprezentuje matematyczne poczucie przynależności. Jest to odniesienie do Number.POSITIVE_INFINITY
Jest ona większa niż jakakolwiek inna wartość i można ją uzyskać dzieląc przez 0 lub oceniając wyrażenie liczby, która jest tak duża, że overﬂows Oznacza to, że nie ma podziału przez 0 błędów w JavaScript, jest Inﬁnity!
Istnieje również -Infinity, która jest matematycznie ujemna i jest niższa niż jakakolwiek inna wartość.
Aby uzyskać -Infinity zaprzecza się nieskończoności, lub uzyskać odniesienie do niej w Number.NEGATIVE_INFINITY.

- (Nieskończoność); // - Nieskończoność
  Teraz bawmy się na przykładach:
  Nieskończoność > 123192310293; // prawdziwość
  -Infinity < -123192310293; // prawdziwość
  1 / 0; // nieskończoność Math.pow(123123123, 9123192391023); // nieskończoność Numer.MAX_VALUE \* 2; // nieskończoność 23 // nieskończoność; /// 0 - nieskończoność - nieskończoność = = = = liczba.NEGATYWNA_INFINITY; // true -0; // -0 , tak, w języku jest ujemne 0 === -0; // true 1 / -0; // -Infinity 1 // 0 === 1 / -0; // false Infinity + Infinity; // Infinity
  var a = 0, b = -0;
  a === b; // true 1 / a === 1 / b; // false
  // Wypróbuj swoje własne!

  Punkt 3.6: Stałe liczbowe
  Konstruktor liczb ma wbudowane stałe, które mogą być przydatne
  Numer.MAX_VALUE; // 1.7976931348623157e+308 Numer.MAX_SAFE_INTEGER; // 9007199254740991
  Numer.MIN_VALUE; // 5e-324 Numer.MIN_SAFE_INTEGER; // -9007199254740991
  Numer.EPSILON; // 0.00000000000000000002220446049250313
  Numer.POSITIVE_INFINITY; // Infinity Number.NEGATIVE_INFINITY; // -Infinity
  Numer.NaN; // NaN
  W wielu przypadkach różni operatorzy w JavaScript zerwą z wartościami spoza zakresu (Number.MIN_SAFE_INTEGER, Number.MAX_SAFE_INTEGER)
  Należy zauważyć, że Number.EPSILON reprezentuje diﬀerent pomiędzy jedną a najmniejszą liczbą większą niż jedna, a tym samym najmniejszą możliwą liczbą diﬀerence pomiędzy dwiema wartościami liczbowymi diﬀerent Jednym z powodów, dla których należy to wykorzystać, jest charakter tego, w jaki sposób liczby są przechowywane przez JavaScript patrz

Punkt 3.7: Operacje, które zwracają NaN
Matematyczne operacje na wartościach innych niż liczby zwracają NaN.
"b" _ 3 "cde" - "e" [1, 2, 3] _ 2
Wyjątek: Tablice jednoliczbowe.
2] \* [3] // Zwroty 6
Pamiętaj również, że operator + konkatenuje ciągi.
"a" + "b" // Zwroty "ab
Podzielenie zera przez zero zwraca NaN.
0 / 0 /// NaN
Uwaga: W matematyce ogólnie (w przeciwieństwie do programowania JavaScript), dzielenie przez zero nie jest możliwe.

Punkt 3.8: Funkcje biblioteki matematycznej, które zwracają NaN
Ogólnie rzecz biorąc, funkcje matematyczne, którym podano argumenty niecyfrowe, zwracają NaN.
Math.floor ("a")
Kwadratowy korzeń ujemnej liczby zwraca NaN, ponieważ Math.sqrt nie obsługuje liczb wyimaginowanych lub złożonych.
Math.sqrt(-1)

Rozdział 4: Uwagi Sekcja 4.1: Korzystanie z komentarzy
Aby dodać adnotacje, podpowiedzi lub wykluczyć jakiś kod z wykonywania JavaScript zapewnia dwa sposoby komentowania linii kodu
Pojedynczy wiersz Komentarz //
Wszystko po // aż do końca linii jest wyłączone z wykonania.
element funkcjiAt( event ) { // Ustawia element ze współrzędnych zdarzenia return document.elementFromPoint(event.clientX, event.clientY); } // TODO: napisać więcej fajnych rzeczy! Komentarz wielowierszowy /\*_/
Wszystko pomiędzy otwarciem /_ a zamknięciem _/ jest wyłączone z wykonania, nawet jeśli otwarcie i zamknięcie znajdują się na liniach diﬀerent
/_ Ustawia element ze współrzędnych zdarzenia. Użyj jak: var clickedEl = someEl.addEventListener("click", elementAt, false); _/ element funkcjiAt( event ) { return document.elementFromPoint(event.clientX, event.clientY); } /_ TODO: napisz więcej użytecznych komentarzy! \*/ Sekcja 4.2: Używanie komentarzy HTML w JavaScript (Zła praktyka)
Komentarze HTML (opcjonalnie poprzedzone białą przestrzenią) spowodują, że kod (w tej samej linii) będzie również ignorowany przez przeglądarkę, choć jest to uważane za złą praktykę.
Komentarze jednowierszowe z sekwencją otwierającą komentarz HTML (<!-- --):
Uwaga: Interpretator JavaScript ignoruje tutaj zamykające znaki komentarzy HTML (-->).

<!-- Komentarz jednowierszowy. <!-- -- --> Identyczne do używania `//` od <!-- -- --> zamknięcie `-->` jest ignorowane.

Tę technikę można zaobserwować w starszym kodzie, aby ukryć JavaScript przed przeglądarkami, które go nie obsługują:

<script type="text/javascript" language="JavaScript"> <!-/* Arbitralny kod JavaScript.   Stare przeglądarki traktowałyby go jak kod HTML. */ // -->
</script>

Komentarz zamykający HTML może być również użyty w JavaScript (niezależnie od komentarza otwierającego) na początku linii (opcjonalnie poprzedzony białą przestrzenią), co również powoduje ignorowanie reszty linii:
--> Niedostępny kod JS
Fakty te zostały również wykorzystane w celu umożliwienia stronie wywołania się jako HTML, a po drugie jako JavaScript. Na przykład:
<!-self.postMessage('reached JS "file"); /_ --> <!DOCTYPE html> <script> var w1 = new Worker('#1'); w1.onmessage = funkcja (e) { console.log(e.data); // 'reached JS "file" }; </script> <!-_/ -->
Podczas uruchamiania HTML, wszystkie wielowierszowe teksty pomiędzy komentarzami <!-- i --> są ignorowane, więc zawarty w nich JavaScript jest ignorowany podczas uruchamiania jako HTML.
Jednak jako JavaScript, podczas gdy linie rozpoczynające się od <!-- i --> są ignorowane, ich eﬀect nie ma uciec przez wiele linii, więc linie następujące po nich (np. self.postMessage(....) nie będą ignorowane, gdy są uruchamiane jako JavaScript, przynajmniej do momentu, gdy dotrą do komentarza JavaScript, oznaczonego przez /_ i _/. Takie komentarze JavaScript są używane w powyższym przykładzie do ignorowania pozostałego tekstu HTML (aż do -->, który jest również ignorowany jako JavaScript).

Rozdział 5: Konsola
Informacje wyświetlane przez konsolę debugging/web są udostępniane za pomocą wielu metod obiektu konsoli Javascript, z którymi można się zapoznać za pośrednictwem konsoli.dir(konsoli). Oprócz właściwości console.memory, wyświetlane metody są zazwyczaj następujące (pobrane z wyjścia Chromium):
assert clear count debug dirxml error groupCollapsed groupEnd info log markTimeline proﬁleEnd table timeEnd timeEnd timeStamp timelineEnd trace warn
Otwieranie konsoli
W większości obecnych przeglądarek Konsola JavaScript Console została zintegrowana jako zakładka w Narzędziach dla programistów. Skróty klawiszowe wymienione poniżej otworzą Narzędzia dla programistów, może być konieczne przełączenie się na prawą kartę po tym czasie.
Chrome
Otwarcie panelu "Konsola" w Chrome's DevTools:
Windows / Linux: dowolne z poniższych opcji.
Ctrl + Shift + J Ctrl + Shift + I , następnie kliknij na zakładkę "Web Console" lub naciśnij ESC, aby włączyć konsolę i oﬀ F12 , następnie kliknij na zakładkę "Console" lub naciśnij ESC, aby włączyć konsolę i oﬀ
Mac OS: Cmd + Opt + J
Firefox
Otwarcie panelu "Konsola" w Narzędziach programistycznych Firefoksa:
Windows / Linux: dowolne z poniższych opcji.
Ctrl + Shift + K Ctrl + Shift + I , następnie kliknij na zakładkę "Web Console" lub naciśnij ESC, aby włączyć konsolę i oﬀ F12 , następnie kliknij na zakładkę "Web Console" lub naciśnij ESC, aby włączyć konsolę i oﬀ
Mac OS: Cmd + Opt + K
Edge i Internet Explorer
Otwarcie panelu "Konsola" w narzędziu F12 Developer Tools:
F12 , następnie kliknij zakładkę "Konsola
Safari
Otwierając panel "Konsola" w Safari Web Inspector musisz najpierw włączyć menu rozwijane w Preferencjach Safari
Następnie możesz wybrać z menu "Develop->Show Error Console" lub nacisnąć ⌘ + Option + C
Opera
Otwarcie "Konsoli" w operze:
Ctrl + Shift + I, następnie kliknij na zakładkę "Konsola
Zgodność
W przypadku używania lub emulowania przeglądarki Internet Explorer 8 lub wcześniejszych wersji (np. poprzez Compatibility View / Enterprise Mode), konsola będzie zdefiniowana tylko wtedy, gdy narzędzia dewelopera są aktywne, więc wyrażenia konsola.log() mogą powodować wyjątek i uniemożliwiać wykonanie kodu. Aby to złagodzić, możesz sprawdzić, czy konsola jest dostępna przed zalogowaniem:
if (typeof window.console !== 'undefined') { console.log("Hello World"); }
Albo na początku skryptu możesz zidentyfikować, czy konsola jest dostępna, a jeśli nie, określić funkcję null, aby złapać wszystkie
i zapobiec wyjątkom.
if (!window.console) { console = {log: function() {}}}; }
Zauważ, że ten drugi przykład zatrzyma wszystkie dzienniki konsoli, nawet jeśli okno dewelopera zostało otwarte.
Użycie tego drugiego przykładu uniemożliwi użycie innych funkcji, takich jak console.dir(obj), chyba że jest to wyraźnie dodane.
Debugowanie konsoli przeglądarki lub konsoli internetowej jest generalnie używane przez programistów do identyfikacji błędów, rozumienia ﬂow wykonania, logowania danych i do wielu innych celów w czasie uruchomienia. Informacje te są dostępne poprzez obiekt konsoli.

Punkt 5.1: Czas pomiaru - konsola czasu()
console.time() może być użyty do pomiaru czasu trwania zadania w kodzie.
Wywołanie console.time([label]) uruchamia nowy timer. Kiedy console.timeEnd([label]) jest wywoływany, czas, który upłynął, w milisekundach, od czasu pierwotnego wywołania .time() jest obliczany i rejestrowany. Z powodu tego zachowania, możesz wywołać .timeEnd() wielokrotnie z tą samą etykietą, aby zarejestrować czas, jaki upłynął od momentu wykonania pierwotnego wywołania .time().
Przykład 1:
console.time('response in');
alert('Click to continue'); console.timeEnd('response in');
alert('One more time'); console.timeEnd('response in');
wyświetli:
odpowiedź w: 774.967ms odpowiedź w: 1402.199ms
Przykład 2:
var elms = document.getElementsByTagName('\*'); //wybór wszystkich elementów na stronie
console.time("Loop time");
dla (var i = 0; i < 5000; i+++) { dla (var j = 0, długość = elms.length; j < length; j < length; j+++) { // nic do zrobienia ... } }
console.timeEnd("Loop time");
będzie wysyłany na zewnątrz:
Czas pętli: 40.716ms

Punkt 5.2: Formatowanie wyjścia konsoli
Wiele metod drukowania w konsoli może również obsługiwać formatowanie łańcuchów typu C, używając tokenów %:
console.log('%s ma %d punktów', 'Sam', 100);
Wyświetla Sam ma 100 punktów.
Pełna lista formatów specifiksów w JavaScript jest:
Speciﬁer Output %s Formatuje wartość jako ciąg %i lub %d Formatuje wartość jako liczbę całkowitą %f Formatuje wartość jako wartość ﬂoating point %o Formatuje wartość jako rozszerzalny element DOM %O Formatuje wartość jako rozszerzalny element DOM %O Formatuje wartość jako rozszerzalny obiekt JavaScript %c Stosuje reguły stylu JavaScript do wyjściowego ciągu znaków jako określony przez drugi parametr
Zaawansowana stylizacja
Gdy po lewej stronie łańcucha zostanie umieszczony specifiks formatu CSS (%c), metoda drukowania zaakceptuje drugi parametr z regułami CSS, które umożliwiają precyzyjną kontrolę nad formatowaniem tego łańcucha:
console.log('%cHello world!', 'color: blue; font-size: xx-large');
Wyświetlacze:
Możliwe jest użycie wielu próbek w formacie %c:
każdy podłańcuch po prawej stronie %c ma odpowiedni parametr w metodzie drukowania; parametr ten może być pustym ciągiem znaków, jeśli nie ma potrzeby stosowania reguł CSS do tego samego podłańcucha; jeśli znaleziono dwa specifiksy w formacie %c, pierwszy (zawarty w %c) i drugi podłańcuch będą miały swoje reguły określone odpowiednio w 2. i 3. parametrze metody drukowania. jeśli znalezione zostaną odpowiednio trzy specifiksy w formacie %c, wtedy 1., 2. i 3. podłańcuch będzie miał swoje reguły określone odpowiednio w 2.
console.log ("%cHello %cHello %cWorld%c!", // łańcuch do wydrukowania "kolor: niebieski;", // stosuje formatowanie kolorystyczne na 1. podłańcuchu "rozmiar czcionki: xx-large;", // stosuje formatowanie czcionki na 2. podłańcuchu "/_ no CSS rule_/" /// nie stosuje się do pozostałego podłożyska);
Wyświetlacze:
Używanie grup do wgłębienia wyjścia
Wyjście może być wcięte i zamknięte w składanej grupie w konsoli do debugowania za pomocą następujących metod:
console.groupCollapsed(): tworzy zwiniętą grupę wpisów, którą można rozszerzyć za pomocą przycisku ujawniania w celu ujawnienia wszystkich wpisów wykonanych po wywołaniu tej metody; console.group(): tworzy zwiniętą grupę wpisów, którą można zwinąć, aby ukryć wpisy po wywołaniu tej metody.
Wgłębienie może być usunięte dla wpisów późniejszych przy użyciu następującej metody:
console.groupEnd(): opuszcza bieżącą grupę, pozwalając na wydruk nowszych wpisów w grupie nadrzędnej po wywołaniu tej metody.
Grupy mogą być kaskadowane, aby umożliwić tworzenie wielu wcięć wyjściowych lub składanych warstw wewnątrz siebie:

Punkt 5.3: Drukowanie na konsoli debuggowania przeglądarki
Konsola debuggowania przeglądarki może być używana do drukowania prostych wiadomości. Debugowanie lub konsolę internetową można otworzyć bezpośrednio w przeglądarce (klawisz F12 w większości przeglądarek - więcej informacji na ten temat znajduje się w uwagach poniżej), a metodę logowania obiektu JavaScript konsoli można wywołać wpisując poniższe słowa:
console.log('My message');
Następnie, po naciśnięciu klawisza Enter , wyświetli się komunikat My message w konsoli debuggowania.
console.log() można wywołać z dowolną liczbą argumentów i zmiennych dostępnych w bieżącym zakresie. Wiele argumentów zostanie wydrukowanych w jednym wierszu z małą odstępem między nimi.
var obj = { test: 1 }; console.log(['string'], 1, obj, window);
Metoda logowania wyświetli w konsoli debugowania następujące informacje:
1 Obiekt { test: 1 } Okno { /_ obcięte _/ }
Oprócz prostych łańcuchów, console.log() może obsługiwać inne typy, takie jak tablice, obiekty, daty, funkcje itp:
console.log([0, 3, 32, 'łańcuch']); console.log({ klucz1: 'wartość', klucz2: 'inna wartość'});
Wyświetla:
Tablica [0, 3, 32, 'łańcuch'] Obiekt { klucz1: 'wartość', klucz2: 'inna wartość'}
Zagnieżdżone obiekty mogą zostać zwinięte:
console.log({ klucz1: 'val', klucz2: ['one', 'two'], klucz3: { a: 1, b: 2 } });
Wyświetlacze:
Obiekt { klucz1: 'val', klucz2: Array[2], klucz3: Obiekt } } Obiekt }.
Niektóre typy, takie jak obiekty i funkcje Date mogą być wyświetlane pod adresem diﬀerently
console.log (nowa Data(0)); console.log(test funkcji a, b) { return c; });
Wyświetla:
Środa 31 grudnia 1969 r. 19:00:00 GMT-0500 (wschodni standardowy czas) test funkcji (a, b) { zwrot c; })
Inne metody drukowania
Oprócz metody dziennika, nowoczesne przeglądarki obsługują również podobne metody:
console.info - po lewej stronie drukowanego ciągu (ciągów) lub obiektu (obiektów) pojawia się mała ikona informacyjna (ⓘ). console.warn - po lewej stronie pojawia się mała ikona ostrzegawcza (!). W niektórych przeglądarkach tło dziennika jest żółte. console.error - po lewej stronie pojawia się mała ikona czasu (⊗). W niektórych przeglądarkach tło dziennika jest czerwone. console.timeStamp - wyświetla aktualny czas i określony ciąg, ale nie jest standardowy:
console.timeStamp('msg');
Wyświetlacze:
00:00:00:00.001 msg
console.trace - wysyła bieżący ślad stosu lub wyświetla to samo wyjście, co metoda logowania, jeśli jest wywołana w zakresie globalnym.
sec() { first();

} funkcja first() { console.trace(); } sec();
Wyświetla:
first sec (funkcja anonimowa)
Powyższy obrazek przedstawia wszystkie funkcje, z wyjątkiem znacznika czasu, w wersji Chrome 56.
Metody te zachowują się podobnie jak metoda logowania i w konsolach debugujących diﬀerent debugowanie może być renderowane w kolorach lub formatach diﬀerent
W niektórych debuggerach informacje o poszczególnych obiektach mogą być dalej rozszerzane przez kliknięcie drukowanego tekstu lub małego trójkąta (►), który odnosi się do odpowiednich właściwości obiektu. Te zawalające się właściwości obiektu mogą być otwierane lub zamykane w logu. Dodatkowe informacje na ten temat można znaleźć w pliku console.dir

Punkt 5.4: Włączenie śledzenia stosu podczas logowania console.trace()
funkcja foo() { console.trace('Moje log statement'); }
foo();
Wyświetli to w konsoli:
Moje log statement VM696:1 foo @ VM696:1 (funkcja anonimowa) @ (program):1
Uwaga: Tam, gdzie jest to możliwe, warto również wiedzieć, że ten sam ślad stosu jest dostępny jako właściwość obiektu Error. Może to być przydatne do późniejszego przetwarzania i zbierania automatycznych informacji zwrotnych.
var e = new Error('foo'); console.log(e.stack);

Punkt 5.5: Tabulacja wartości - console.table()
W większości środowisk, console.table() może być używany do wyświetlania obiektów i tablic w formacie tabelarycznym.
Na przykład:
console.table(['Hello', 'world']);
wyświetla jak:
(indeks) wartość 0 "Hello" 1 "world" console.table({foo: 'bar', bar: 'baz'});
wyświetla jak:
(indeks) wartość "foo" "bar" "bar" "baz" var personArr = [ {"personId": 123, "nazwa": "Jhon", "miasto": "Melbourne", "telefon nr": "1234567890" }, {"personId": 124, "nazwisko": "Amelia", "miasto": "Sydney", "telefon nr": "1234567890" }, {"personId": 125, "nazwisko": "Emily", "miasto": "Perth", "phoneNo": "1234567890" }, {"personId": 126, "nazwisko": "Abraham", "miasto": "Perth", "phoneNo": "1234567890" } ]; console.table(personArr, ["name", "personId"])
wyświetla jak:

Punkt 5.6: Liczenie - konsola.count()
console.count([obj]) umieszcza licznik na wartości obiektu podanej jako argument. Przy każdym wywołaniu tej metody licznik jest zwiększany (z wyjątkiem pustego łańcucha '''). Etykieta wraz z numerem jest wyświetlana w konsoli debuggowania zgodnie z następującym formatem:
etykieta]: X
etykieta przedstawia wartość obiektu przekazanego jako argument, a X reprezentuje wartość licznika.
Wartość obiektu jest zawsze brana pod uwagę, nawet jeśli zmienne są podawane jako argumenty:
var o1 = 1, o2 = '2', o3 = ""; console.count(o1); console.count(o2); console.count(o3);
console.count(1); console.count('2'); console.count(''');
Wyświetlacze:
1: 1 2: 1 : 1 1: 2 2: 2 : 1
Łańcuchy z liczbami są konwertowane na obiekty Number:
console.count (42.3);
console.count(Number('42.3')); console.count('42.3');
Wyświetlacze:
42.3: 1 42.3: 2 42.3: 3
Funkcje zawsze wskazują na obiekt funkcji globalnej:
console.count(console.constructor); console.count(function(){}); console.count(Object); var fn1 = funkcja myfn(){}; console.count(fn1); console.count(Number);
Wyświetla:
obiekt Funkcja]: 1 [obiekt Funkcja]: 2 [obiekt Funkcja]: 3 [obiekt Funkcja]: 4 [obiekt Funkcja]: 5
Niektóre obiekty otrzymują konkretne liczniki powiązane z typem obiektu, do którego się odnoszą:
console.count(niezdefiniowany); console.count(document.Batman); var obj; console.count(obj); console.count(numer(niezdefiniowany)); console.count(NaN); console.count(NaN+3); console.count(1/0); console.count(String(1/0)); console.count(window); console.count(dokument); konsola count(konsola); konsola count(konsola.**proto**); konsola count(prototyp konsoli.constructor.prototype); konsola count(konsola.count(konsola.**proto**.prototype.prototype); konsola count(Object.getPrototypeOf(konsola)); konsola.count(null);
Wyświetlacze:
Niezdefiniowane: 1 niezdefiniowane: 2 niezdefiniowane: 3 NaN: 1 NaN: 2 NaN: 3 Nieskończoność: 1 Nieskończoność: 2 [obiekt Okno obiektu]: 1 [obiekt HTMLDokument]: 1 [obiekt Obiekt]: 1
obiekt Obiekt]: 2 [obiekt Obiekt]: 3 [obiekt]: 4 [obiekt]: 5 null: 1 Pusty łańcuch lub brak argumentu
Jeżeli podczas sekwencyjnego wprowadzania metody zliczania w konsoli debuggowania nie podano argumentu, jako parametr przyjmuje się pusty łańcuch, tzn:
console.count(); : 1 > console.count('''); : 2 > console.count(""); : 3

Punkt 5.7: Czyszczenie konsoli - konsola.clear()
Możesz wyczyścić okno konsoli używając metody console.clear(). Usuwa to wszystkie wcześniej wydrukowane komunikaty w konsoli i w niektórych środowiskach może wydrukować komunikat taki jak "Console was cleared".

Punkt 5.8: Wyświetlanie obiektów i XML interaktywnie console.dir(), console.dirxml()
console.dir(object) wyświetla interaktywną listę właściwości określonego obiektu JavaScript. Wyjście jest prezentowane jako hierarchiczna lista z trójkątami ujawniającymi, które pozwalają zobaczyć zawartość obiektów dziecięcych.
var myObject = { "foo":{ "bar": "data" } };
console.dir(myObject);
wyświetlacze:
console.dirxml(object) drukuje reprezentację XML elementów opisowych obiektu, jeśli to możliwe, lub reprezentację JavaScript, jeśli nie. Wywołanie console.dirxml() na elementach HTML i XML jest równoważne wywołaniu console.log().
Przykład 1:
console.dirxml(dokument)
Przykład 2:
console.log(dokument)
Przykład 3:
var myObject = { "foo":{ "bar": "data" } };
console.dirxml(myObject);

Punkt 5.9: Debugowanie z zapewnieniami - console.assert()
Zapisuje komunikat o błędzie do konsoli, jeśli assertion jest fałszywy. W przeciwnym razie, jeżeli assertion jest prawdziwe, to nic nie robi.
console.assert('one' === 1);
Po assertionie można podać wiele argumentów - mogą to być łańcuchy lub inne obiekty - które będą drukowane tylko wtedy, gdy assertion jest fałszywe:
console.assert nie rzuca AssertionError (z wyjątkiem Node.js), co oznacza, że metoda ta jest niekompatybilna z większością frameworków testowych i że wykonanie kodu nie przerwie się na nieudanym assertion.

Rozdział 6: Typy danych w JavaScript Sekcja 6.1: Typ danych
typeof jest funkcją 'oﬃcial', której używa się do uzyskania typu w JavaScript, jednak w niektórych przypadkach może to przynieść pewne nieoczekiwane rezultaty...

1. Stringi
   typ "String" lub typ daty (2011,01,01,01)
   "sznur".
2. Liczby
   typ 42
   "liczba
3. Bool
   typ prawdy (ważne wartości prawdziwe i fałszywe)
   "boolean
4. Obiekt
   typ {} lub typ [] lub typ [] lub typ zerowy lub typ /aaaa/ lub typ błędu()
   "obiekt".
5. Funkcja
   typ funkcji(){}
   "funkcja
6. Nieokreślony
   var1; typ var1
   "nieokreślony

Punkt 6.2: Znalezienie klasy obiektu
Aby określić, czy obiekt został skonstruowany przez określonego konstruktora, czy też odziedziczył po nim, możesz użyć polecenia instanceof:
/// Chcemy, żeby ta funkcja wzięła sumę liczb do niej przekazanych ///To może być wywołane jako suma (1, 2, 3) lub suma([1, 2, 3]) i powinna dawać 6 funkcji sum(...argumenty) { jeśli (arguments.length === 1) { const [firstArg] = argumenty jeśli (firstArg instanceof Array) { //firstArg jest czymś w rodzaju [1, 2, 3] zwraca sumę(...firstArg) //calls sum(1, 2, 3) } } zwróć argumenty.reduce((a, b) => a + b) }
console.log (suma (1, 2, 3)) //6 console.log (suma([1, 2, 3])) //6 console.log (suma(4)) //4
Zwróć uwagę, że wartości prymitywne nie są uważane za instancje żadnej klasy:
console.log(2 instancja Number) //false console.log('abc' instanceof String) //false console.log(true instance of Boolean) //false console.log(Symbol() instanceof Symbol) //false
Każda wartość w JavaScript oprócz wartości zerowej i niezdefiniowanej posiada również właściwość konstruktora przechowującą funkcję, która została użyta do jej skonstruowania. Działa to nawet z prymitywami.
//Whereas instanceof wychwytuje również instancje podklas, // używając obj.constructor nie konsola.log([] instanceof Object, [] instanceof Array) //true true console.log([].constructor === Object, [].constructor === Array) //false true
funkcja isNumber(wartość) { //null.constructor i undefined.constructor rzucają błąd podczas dostępu, jeśli (wartość === null || value === niezdefiniowana) zwróci fałszywą wartość.constructor === Liczba } console.log(isNumber(isNumber(null), isNumber(undefined)). //false false console.log(isNumber('abc'), isNumber([]), isNumber() => 1)) //false false console.log(isNumber(0), isNumber(Number('10.1')), isNumber(NaN)) //trawdziwa prawda prawda Sekcja 6.3: Uzyskiwanie typu obiektu według nazwy konstruktora
Kiedy jeden z typem operatora dostaje obiekt typu, należy on do kategorii marnotrawstwo....
W praktyce możesz potrzebować zawęzić go do jakiego rodzaju "obiektu" jest w rzeczywistości i jednym ze sposobów, aby to zrobić, jest użycie nazwy konstruktora obiektu, aby uzyskać to, czym jest ﬂavour obiektu w rzeczywistości: Object.prototype.toString.call(yourObject)

1. String
   Obiekt.prototyp.toString.call("String")
   "String Obiektowy".
   GoalKicker.com - JavaScript® Notes for Professionals 35
2. Liczba
   Obiekt.prototyp.doString.call(42)
   "liczba obiektów".
3. Bool
   Prototyp.toString.call(true)
   "Obiekt boolean]".
4. Obiekt
   Obiekt.prototyp.toString.call(Object())) lub Object.prototyp.toString.call({})
   "Obiekt]".
5. Funkcja
   Obiekt.prototyp.toString.call(funkcja(){})
   "Funkcja obiektu]".
6. Data
   Obiekt.prototyp.toString.call (nowa data (2015, 10, 21))
   "Data obiektu".
7. Regex
   Object.prototype.toString.call(new RegExp()) lub Object.prototype.toString.call(/foo/);
   "Obiekt RegExp]".
8. Tablica
   Object.prototype.toString.call([]);
   "Obiekt tablica]".
9. Nieważne
   Obiekt.prototyp.toString.call(null);
   "Obiekt nieważny".
10. Nieokreślony
    Obiekt.prototyp.toString.call(niezdefiniowany);
    "Obiekt nieokreślony]".
11. Błąd
    Object.prototype.toString.call(Error()));
    "Obiekt Błąd]".

Rozdział 7: Stringi
Sekcja 7.1: Podstawowe informacje i łączenie sznurków
Łańcuchy w JavaScript mogą być zawarte w Pojedynczych cudzysłowach "przywitanie", Podwójne cudzysłowy "Witaj" i (z ES2015, ES6) w Szablonach literalnych (backticks) `zwitek`.
var hello = "Hello"; var world = 'world'; var helloW = `Hello World`; // ES2015 / ES6
Łańcuchy mogą być tworzone z innych typów za pomocą funkcji String().
var intString = String(32); // "32" var booleanString = String(true); // "true" var nullString = String(null); // "null
Albo toString() może być użyty do konwersji liczb, logicznych lub obiektów na łańcuchy.
var intString = (5232).toString(); // "5232" var booleanString = (false).toString(); // "false" var objString = ({}).toString(); // "[object Object]".
Łańcuchy mogą być również tworzone przy użyciu metody String.fromCharCode.
String.fromCharCode (104,101,108,108,108,111) //"hello
Tworzenie obiektu String przy użyciu nowego słowa kluczowego jest dozwolone, ale nie jest zalecane, ponieważ zachowuje się on jak Obiekty w przeciwieństwie do pierwotnych łańcuchów.
var objectString = new String("Tak, jestem obiektem String"); typeof objectString;//"object" type of objectString.valueOf();//"string" Concatenating Strings
Złączenie łańcuchowe można wykonać za pomocą operatora + konkatenacja, lub wbudowaną metodą concat() na prototypie obiektu String.
var foo = "Foo"; var bar = "Bar"; console.log(foo + bar); // => "FooBar" console.log(foo + " " + bar); // => "Foo Bar".
foo.concat(bar) // => "FooBar" "a".concat("b", " " ", "d") // => "ab d
Łańcuchy mogą być łączone ze zmiennymi niestrunowymi, ale będą typować - przekształcając zmienne niestrunowe w łańcuchy.
var string = "string"; var number = 32; var boolean = true;
console.log (łańcuch + numer + boolean); // "string32true" String Templates
Wersja ≥ 6
Łańcuchy mogą być tworzone za pomocą szablonów literalnych (backticks) `hello`.
var greeting = `Hello`;
Za pomocą dosłowności szablonów można wykonać interpolację łańcuchów używając \${zmienna} wewnątrz dosłownie szablonów:
var place = `Świat`; var greet = ` Hello ${place}!`` console.log(pozdrawiam); // "Hello World! Możesz użyć String.raw, aby uzyskać backslashes do bycia w łańcuchu bez modyfikacji. `areszciereszcieb`// = aeracjąb String.raw`a Instancjib` // = aeracjąb

Section 7.2: Odwrotny ciąg
Najbardziej "popularnym" sposobem odwrócenia łańcucha w JavaScript jest następujący fragment kodu, co jest dość powszechne:
funkcja reverseString(str) { return str.split(''').reverse().join('''); }
reverseString('string'); // "gnirts
Będzie to jednak działać tylko tak długo, jak długo odwrócony łańcuch nie zawiera par zastępczych. Symbole astralne, tj. znaki spoza podstawowej wielojęzycznej płaszczyzny, mogą być reprezentowane przez dwie jednostki kodu i będą prowadzić tę naiwną technikę w celu uzyskania błędnych wyników. Ponadto znaki z łączącymi znakami (np. diaereza) pojawią się na znaku logicznym "następny" zamiast oryginalnego znaku, z którym zostały połączone.
'??????????''.split('').reverse().join('''); //fails
Podczas gdy metoda ta będzie działać w większości języków, to naprawdę dokładny, zgodny z zasadami kodowania algorytm odwracania ciągów znaków jest nieco bardziej zaangażowany. Jedną z takich implementacji jest maleńka biblioteka Esrever, która używa wyrażeń regularnych do dopasowywania znaków i par zastępczych w celu perfekcyjnego wykonania odwracania.
Wyjaśnienie
Section Explanation Result str Łańcuch wejściowy "string
String.prototyp.split( deliminator )
Dzielenie str strita łańcucha na tablicę. Parametr "" oznacza podział na poszczególne znaki.
["s", "t", "r", "i", "n", "g"].
Array.prototype.reverse() Zwraca tablicę z dzielonego łańcucha z jego elementami w odwrotnej kolejności. ["g", "n", "i", "r", "t", "s"].
Array.prototype.join( deliminator )
Łączy elementy tablicy w ciąg. Parametr "" oznacza pusty deliminator (tzn. elementy tablicy są umieszczone obok siebie).
"gnirts
Praca z operatorem rozsiewu
Wersja ≥ 6
funkcja reverseString(str) { return [...String(str)].reverse().join(''); }
console.log(reverseString('stackoverflow')); // "wolfrevokcats" console.log(reverseString(1337)); // "7331" console.log(reverseString([1, 2, 3])); // "3,2,1".
Niestandardowa funkcja rewersu()
funkcja reverse(string) { var strRev = ""; dla (var i = string.length - 1; i >= 0; i--) { strRev += string[i]; } return strRev; }
reverse("zebra"); // "arbez"

Sekcja 7.3: Porównywanie łańcuchów
Aby porównać łańcuchy alfabetycznie, użyj localeCompare(). Zwraca to wartość ujemną, jeśli łańcuch referencyjny jest leksykograficznie (alfabetycznie) przed porównywanym łańcuchem (parametr), wartość dodatnią, jeśli pojawia się później, i wartość 0, jeśli są one równe.
var a = "hello"; var b = "world";
console.log (a.localeCompare(b)); /// -1
Operatory > i < mogą być również używane do leksykograficznego porównywania ciągów znaków, ale nie mogą zwrócić wartości zerowej (można to sprawdzić przy pomocy operatora równości ==). W rezultacie, forma funkcji localeCompare() może być zapisana w ten sam sposób:

funkcja strcmp(a, b) { jeżeli (a === b) { zwrot 0; }
if (a > b) { zwrot 1; }
return -1; }
console.log(strcmp("hello", "world")); // -1 console.log(strcmp("hello", "hello")); // 0 console.log(strcmp("world", "hello")); // 1
Jest to szczególnie przydatne w przypadku korzystania z funkcji sortowania, która porównuje się na podstawie znaku wartości zwracanej (np. sortowania).
var arr = ["banany", "żurawina", "jabłka"]; arr.sort(funkcja a, b) { zwrócić a.localeCompare(b);
})); console.log(arr); // ["jabłka", "banany", "żurawiny" ]

Sekcja 7.4: Znak dostępu w indeksie w ciąg
Użyj charAt() aby uzyskać znak w określonym indeksie w łańcuchu.
var string = "Hello, World!"; console.log( string.charAt(4) ); // "o
Alternatywnie, ponieważ łańcuchy mogą być traktowane jak tablice, użyj indeksu poprzez notację w nawiasie.
var string = "Hello, World!"; console.log( string[4] ); // "o
Aby uzyskać kod znaków znaku w określonym indeksie, użyj charCodeAt().
var string = "Hello, World!"; console.log( string.charCodeAt(4) ); // 111
Zauważ, że wszystkie te metody są metodami gettera (zwróć wartość). Łańcuchy w JavaScript są niezmienne. Innymi słowy, żadna z nich nie może być użyta do ustawienia znaku na pozycji w łańcuchu.

Punkt 7.5: Cytaty skokowe
Jeśli Twój ciąg jest zamknięty (np.) w pojedynczych cudzysłowach, musisz uciec od wewnętrznego dosłownego cytatu z odwrotnym ukośnikiem Instancji
var text = "Lycia'albero oznacza drzewo w języku włoskim"; console.log( text ); Instancji "L'albero oznacza drzewo w języku włoskim".
To samo dotyczy podwójnych kwotowań:
var text = "czuję się "higheracją";
Szczególną uwagę należy zwrócić na ucieczkę cudzysłowów, jeśli przechowujesz reprezentacje HTML w Stringu, ponieważ łańcuchy HTML wykorzystują cytaty w dużych ilościach, tj. w atrybutach:
var content = "<p class=Firma specjalna">Hello World!</p>"; // ważny String var hello = '<p class="special">I Instancji'd like to say "Hi"</p>"; // ważny String
Cytaty w łańcuchach HTML mogą być również reprezentowane za pomocą &apos; (lub &#39;) jako pojedynczy cytat i &quot; ( lub &#34;) jako podwójne cytaty.
var hi = "<p class='special'>I'd like to say &quot;Hi&quot;</p>"; // valid String var hello = '<p class='special'>I&apos;d like to say "Hi"</p>'; // valid String
Uwaga: Użycie &apos; i &quot; nie nadpisze podwójnych cudzysłowów, które przeglądarki mogą automatycznie umieszczać na cudzysłowach atrybutów. Na przykład <p class=special> jest tworzone do <p class="special">, przy użyciu &quot; może prowadzić do <p class=""special""> gdzie ⃞" będzie <p class="special">.
Wersja ≥ 6
Jeśli łańcuch ma ' i " możesz rozważyć użycie dosłownic szablonowych (znanych również jako łańcuchy szablonów w poprzednich wydaniach ES6), które nie wymagają ucieczki ' i ". Używają one backtykatów (` ) zamiast pojedynczych lub podwójnych cudzysłowów. var x = ``"Ucieczka " i ' może stać się bardzo denerwująca `;

Punkt 7.6: Licznik słów
Powiedzmy, że masz <textarea> i chcesz uzyskać informacje o liczbie:
Znaki (ogółem) Znaki (bez spacji) Słowa Linie
funkcja wordCount( val ){ var wom = val.match(/ 2002/1S+/g); return { znakiNoSpaces : val.replace(/ 2002/1s+/g, '').length, znaki : val.length, words : wom ? wom ? wom length : 0, lines : val.split(/ 2002/1r\* Instancjin/).length }; }
// Użyj jak: wordCount( someMultilineText ).words; // (Liczba słów)
jsPrzykład skrzydłowy

Sekcja 7.7: Przycinanie białej przestrzeni
Aby przyciąć białą przestrzeń od krawędzi sznurka, użyj String.prototype.trim:
"niektóre białe łańcuchy ".trim(); // "niektóre białe łańcuchy".
Wiele silników JavaScript, ale nie Internet Explorer, wdrożyło niestandardowe metody trimLeft i trimRight. Obecnie na etapie 1 procesu jest propozycja znormalizowanych metod trimStart i trimEnd, aliasowanych do trimLeft i trimRight dla kompatybilności.
// Propozycja etapu 1 " to jest ja ".trimStart(); // "to jest ja " " to jest ja ".trimEnd(); // " to jest ja".
// Metody niestandardowe, ale obecnie wdrażane przez większość silników " to ja ".trimLeft(); // "to ja " " to ja ".trimRight(); // " to ja" Sekcja 7.8: Podział łańcucha na tablicę
Użyj .split, aby przejść od łańcuchów do tablicy dzielonych podłoży:
var s = "jeden, dwa, trzy, cztery, cztery, pięć" s.split(", "); // ["jeden", "dwa", "trzy", "cztery", "pięć"]
Użyj metody tablicowej .join, aby wrócić do łańcucha:
s.split(", ").join("--"); // "one-two--three--four--five

Punkt 7.9: Stringi są unicode
Wszystkie łańcuchy JavaScript są unicode!
var s = "some ∆≈ƒ unicode ¡™Ł¢¢¢¢"; s.charCodeAt(5); // 8710
W JavaScript nie ma surowych bajtów ani łańcuchów binarnych. Aby eﬀectively obsługiwać dane binarne, użyj Typed Arrays.

Punkt 7.10: Wykrywanie łańcucha
Aby wykryć, czy parametr jest łańcuchem prymitywnym, należy użyć typeof:
var aString = "mój łańcuch"; var anInt = 5; var anObj = {}; typeof aString === "string"; // true typeof anInt === "string"; // false typeof anObj === "string"; // false
Jeśli kiedykolwiek masz obiekt String, poprzez nowy String("somestr"), to powyższe nie będzie działać. W tym przypadku możemy użyć instancji:
var
Jeśli kiedykolwiek masz obiekt String, poprzez nowy String("somestr"), to powyższe nie będzie działać. W tym przypadku możemy użyć instancji:
var aStringObj = new String("my string"); aStringObj instanceof String; // true
Aby objąć obie instancje, możemy napisać prostą funkcję helpera:
var isString = funkcja(wartość) { typ zwrotu wartości === "łańcuch" || wartość instancji String; };
var aString = "Primitive String"; var aStringObj = new String("String Object"); isString(aString); // true isString(aStringObj); // true isString({}); // false isString(5); // false
Albo możemy skorzystać z funkcji toString obiektu. Może to być przydatne, jeśli musimy sprawdzać inne typy, jak również powiedzieć w instrukcji przełącznika, ponieważ metoda ta obsługuje inne typy danych, jak również tak samo jak typof.
var pString = "Primitive String"; var oString = new String("Object Form of String"); Object.prototype.toString.call(pString);//"[object String]" Prototyp.toString.call(oString);//"[object String]".  
Bardziej solidnym rozwiązaniem jest niewykrywanie ciągów znaków, a jedynie sprawdzanie, jaka funkcjonalność jest wymagana. Na przykład:
var aString = "Primitive String"; // Ogólne sprawdzenie metody łańcucha if(aString.substring) {
} // Wyraźne sprawdzenie metody prototypu podłańcucha
if(aString.substring ===String.prototype.substring) { aString.substring(0, ); }

Sekcja 7.11: Podłoże z plastrami
Użyj .slice() do wyodrębnienia podłoży podanych w dwóch indeksach:
var s = "0123456789abcdefg"; s.slice(0, 5); // "01234" s.slice(5, 6); // "5
Biorąc pod uwagę jeden indeks, zajmie od tego indeksu do końca łańcucha:
s.slice(10); // "abcdefg"

Sekcja 7.12: Kod znaków
Metoda charCodeAt pobiera kod znaków Unicode pojedynczego znaku:
var charCode = "µ".charCodeAt(); // Kod znaku litery µ wynosi 181
Aby otrzymać kod znaku w łańcuchu znaków, jako parametr do charCodeAt jest przekazywane 0-położenie znaku jako parametr:
var charCode = "ABCDE".charCodeAt(3); // Kod znaku "D" to 68 Wersja ≥ 6
Niektóre symbole Unicode nie występują w jednym znaku i zamiast tego wymagają dwóch par zastępczych UTF-16 do kodowania. Dotyczy to kodów znaków powyżej 216 - 1 lub 63553. Te rozszerzone kody znaków lub wartości punktów kodowych można pobrać za pomocą codePointAt:
// Grinning Face Emoji ma kod 128512 lub 0x1F600 var codePoint = "???".codePointAt();

Sekcja 7.13: String Representations of Numbers
JavaScript ma natywną konwersję z liczby na łańcuch dla dowolnej bazy od 2 do 36.
Najczęstszą reprezentacją po przecinku (podstawa 10) jest szesnastkowa (podstawa 16), ale zawartość tej sekcji działa dla wszystkich podstaw w tym zakresie.
Aby przekonwertować liczbę z liczby dziesiętnej (podstawa 10) na liczbę szesnastkową (podstawa 16), można użyć metody łańcuchowej toString z radix 16.
// podstawa 10 Liczba var b10 = 12;
// base 16 Reprezentacja łańcuchów var b16 = b10.toString(16); // "c
Jeżeli reprezentowana liczba jest liczbą całkowitą, operacja odwrotna może być wykonana z parseInt i radix 16 ponownie
// Podstawa 16 Reprezentacja strun var b16 = "c";
// podstawa 10 Liczba var b10 = parseInt (b16, 16); // 12
Aby przekonwertować dowolną liczbę (tzn. liczbę nieintegrującą) z jej reprezentacji String na liczbę, operacja musi być podzielona na dwie części: część całkowitą i część ułamkową.
Wersja ≥ 6 niech b16 = "3.243f3e0370cdc"; // Podział na liczbę całkowitą i ułamki niech [i16, f16] = b16.split('.');
// Obliczyć podstawę 10 części całkowitej niech i10 = parseInt(i16, 16); // 3
// Obliczyć frakcję bazową 10 części niech f10 = parseInt(f16, 16) / Math.pow(16, f16.length); // 0,14158999999999988
// Złożyć 10 części podstawy razem, aby znaleźć liczbę niech b10 = i10 + f10; // 3.14159
Uwaga 1: Należy zachować ostrożność, ponieważ w wyniku mogą pojawić się drobne błędy ze względu na diﬀerences w tym, co jest możliwe do przedstawienia w bazie diﬀerent Może być pożądane przeprowadzenie pewnego rodzaju zaokrągleń w późniejszym terminie. Uwaga 2: Bardzo długie odwzorowania liczb mogą również powodować błędy ze względu na dokładność i maksymalne wartości liczb w środowisku, w którym dokonuje się konwersji.

Rozdział 8: Data
Parametr Wartość szczegółów Liczba milisekund od 1 stycznia 1970 r. 00:00:00:00.000 UTC (epoka Unix) dateAsString Data sformatowana jako ciąg znaków (więcej informacji w przykładach)
rok
Wartość roku z daty. Należy również podać miesiąc, w przeciwnym razie wartość będzie interpretowana jako liczba milisekund. Zwróć również uwagę, że wartości pomiędzy 0 a 99 mają specjalne znaczenie. Zobacz przykłady.
miesiąc
Miesiąc, w zakresie 0-11. Należy pamiętać, że użycie wartości spoza określonego zakresu dla tego i następujących parametrów nie spowoduje błędu, ale raczej spowoduje, że wynikowa data "przewróci się" do następnej wartości. Zobacz przykłady: Data, w zakresie 1-31. godzina Opcjonalnie: Godzina, w zakresie 0-23. minuta Opcjonalnie: Minuta, w zakresie 0-59. sekundy Opcjonalnie: Drugi, w zakresie 0-59. milisekundy Opcjonalnie: Milisekunda, w zakresie 0-999. Punkt 8.1: Utwórz nowy obiekt Data
Aby utworzyć nowy obiekt Date należy użyć konstruktora Date():
bez argumentów
Date() tworzy instancję Date zawierającą bieżący czas (do milisekund) i datę.
z jednym argumentem liczby całkowitej
Data(m) tworzy instancję Date zawierającą czas i datę odpowiadającą czasowi Epoch (1 stycznia 1970 r., UTC) plus m milisekundy. Przykład: nowa data (749019369738) podaje datę Sun, 26 września 1993 r. 04:56:09 GMT.
z argumentem łańcuchowym
DateString (dateString) zwraca obiekt Date, który wynika po przetworzeniu dateString z Date.parse.
z dwoma lub więcej całkowitymi argumentami
Date(i1, i2, i3, i4, i5, i6) odczytuje argumenty jako rok, miesiąc, dzień, godziny, minuty, sekundy, milisekundy i uruchamia odpowiedni Dateobject. Zauważ, że miesiąc jest indeksowany w JavaScript, więc 0 oznacza styczeń, a 11 oznacza grudzień. Przykład: nowa data (2017, 5, 1) daje 1 czerwca 2017.

Daty eksploracji
Zwróć uwagę, że przykłady te zostały wygenerowane w przeglądarce w Centralnej Strefie Czasowej USA, w czasie dnia, o czym świadczy kod. Tam gdzie porównanie z UTC było pouczające, użyto Date.prototype.toISOString()
aby pokazać datę i godzinę w UTC (Z w sformatowanym ciągu oznacza UTC).
// Tworzy obiekt Date z bieżącą datą i godziną z var var przeglądarki użytkownika teraz = new Date(); now.toString() === 'Mon Apr 11 2016 16:10:41 GMT-0500 (Central Daylight Time)' // true // well, w momencie pisania tego zapisu, i tak
// Tworzy obiekt Date w Unix Epoch (tj. "1970-01-01T00:00:00:00.000Z") var epoch = new Date(0); epch.toISOString() === "1970-01-01T00:00:00:00.000Z" // true
// Tworzy obiekt Date z datą i czasem 2,012 milisekundy // po Unix Epoch (tj. "1970-01-01T00:00:02.012Z"). var ms = new Date(2012); date2012.toISOString() === '1970-01-01T00:00:02.012Z' // true
// Tworzy obiekt Date z pierwszym dniem lutego 2012 r. // w lokalnej strefie czasowej. var one = new Date(2012, 1); one.toString() === "Wed Feb 01 2012 00:00:00 GMT-0600 (Centralny Standard Time)" // true
// Tworzy obiekt Date z pierwszym dniem roku 2012 w lokalnej // strefie czasowej. // (Miesiące są oparte na zerze) var zero = nowa data (2012, 0); zero.toString() === "Słońce 01 2012 00:00:00 GMT-0600 (centralny czas standardowy)" // true
// Tworzy obiekt Date z pierwszym dniem roku 2012, w UTC. var utc. var utc. = new Date(Date.UTC(2012, 0)); utc.toString() === "Sat Dec 31 2011 18:00:00:00 GMT-0600 (Centralny czas standardowy)" // true utc.toISOString() === "2012-01-01T00:00:00.000Z" // true
// Parses a string into a Date object (format ISO 8601 dodany w ECMAScript 5.1) // Implementacje powinny zostać przyjęte UTC ze względu na format ISO 8601 i oznaczenie Z var iso = new Date('2012-01-01T00:00:00:00.000Z'); iso.toISOString() === '2012-01-01T00:00:00.000Z' // true
// Parsesuje ciąg znaków w obiekt Date (RFC w JavaScript 1.0) var local = new Date("Sun, 01 Jan 2012 00:00:00:00 -0600"); local.toString() === "Sun Jan 01 2012 00:00:00:00 GMT-0600 (centralny czas standardowy)" // true
// Parsuje ciąg znaków w żadnym konkretnym formacie, przez większość czasu. Zauważ, że parsowanie // logika w tych przypadkach jest bardzo zależne od implementacji, a zatem może się zmieniać // w różnych przeglądarkach i wersjach. var anything = new Date('11/12/2012'); anything.toString() === 'Mon 12 Nov 2012 00:00:00:00 GMT-0600 (Central Standard Time)' // true, w Chrome 49 64-bit na Windows 10 w en-US locale. Inne wersje w // innych lokalizacjach mogą uzyskać inny wynik.
// Rolls values outside a specified range to the next value. var rollover = new Date(2012, 12, 32, 25, 62, 62, 62, 1023); rollover.toString() === 'Sat Feb 02 2013 02:03:03:03 GMT-0600 (Central Standard Time)' // true; zwróć uwagę na to, że miesiąc przewrócił się do lutego; pierwszy miesiąc przewrócił się do // stycznia w oparciu o miesiąc 12 (gdzie 11 to grudzień), a następnie ponownie z powodu dnia 32 // (styczeń ma 31 dni).
// Specjalne daty dla lat w zakresie 0-99 var special1 = new Date(12, 0); special1.toString() === "Mon Jan 1912 00:00:00:00 GMT-0600 (centralny czas standardowy)`// true // Jeśli faktycznie chcesz ustawić rok na rok 12 CE, musisz użyć metody // setFullYear(): special1.setFullYear(12); special1.toString() === 'Sun Jan 01 12 00:00:00:00 GMT-0600 (Centralny Standard Time)` // true
Sekcja 8.2: Konwersja do formatu łańcuchowego
Convert to String var date1 = new Date(); date1.toString();
Zwroty: "Piąty kwiecień 15 2016 07:48:48 GMT-0400 (czas wschodniego światła dziennego)
Convert to Time String var date1 = new Date(); date1.toTimeString();
Zwroty: "07:48:48:48 GMT-0400 (czas wschodniego światła dziennego)
Convert to Date String var date1 = new Date(); date1.toDateString();
Zwroty: "Thu Apr 14 2016
Convert to UTC String var date1 = new Date(); date1.toUTCString();
Zwroty: "Fri, 15 kwietnia 2016 r. 11:48:48:48 GMT
Konwersja na ISO String var date1 = new Date(); date1.toISOString();
Zwroty: "2016-04-14T23:49:08.596Z
Convert to GMT String var date1 = new Date(); date1.toGMTString();
Zwroty: "Thu, 14 kwiecień 2016 23:49:08 GMT
Ta funkcja została oznaczona jako przestarzała, więc niektóre przeglądarki mogą nie obsługiwać jej w przyszłości. Sugeruje się użycie toUTCString() zamiast tego.
Convert to Locale Date String var date1 = new Date(); date1.toLocaleDateString();
Zwroty: "4/14/2016"
Funkcja ta zwraca łańcuch daty uwzględniający lokalizację użytkownika w oparciu o domyślną lokalizację użytkownika.
date1.toLocaleDateString([locales [, options]]])
może być użyty do dostarczenia specyfikacji lokalnej, ale jest to specyfikacja implementacji przeglądarki. Na przykład,
date1.toLocaleDateString(["zh", "en-US"]);
spróbuje wydrukować łańcuch w chińskim locale używając amerykańskiego angielskiego jako rezerwowego. Parametr opcji może być użyty w celu zapewnienia określonego formatowania. Na przykład:
var opcje = { dzień tygodnia: long", rok: numeryczne", miesiąc: long", dzień: "numeric" }; date1.toLocaleDateString([], opcje);
skutkowałoby to
"Czwartek, 14 kwietnia 2016 r.
Więcej informacji na ten temat można znaleźć w MDN. 

Sekcja 8.3: Tworzenie daty z UTC
Domyślnie obiekt Data jest tworzony jako czas lokalny. Nie zawsze jest to pożądane, na przykład podczas komunikacji daty pomiędzy serwerem a klientem, który nie znajduje się w tej samej strefie czasowej. W tym scenariuszu nie chce się w ogóle martwić o strefy czasowe, aż do momentu, gdy data musi być wyświetlana w czasie lokalnym, jeśli jest to nawet wymagane w ogóle.
Problem
W tym problemie chcemy przekazać określoną datę (dzień, miesiąc, rok) z kimś w strefie czasowej diﬀerent Pierwsze wdrożenie naiwnie wykorzystuje czas lokalny, co prowadzi do błędnych wyników. Drugie wdrożenie wykorzystuje daty UTC, aby uniknąć stref czasowych, w których nie są one potrzebne.
Zrezygnować z podejścia z wynikami WRONG

format funkcjiDate(dayOfWeek, dzień, miesiąc, rok) { var daysOfWeek = ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"];  var miesiące = ["Jan", "Feb", "Mar", "Apr", "Maj", "Jun", "Jul", "Sierpień", "Wrzesień", "Październik", "Nov", "Grudzień"]; dni powracająceOfWeek[dayOfWeek] + " " " + miesiące[miesiace] + " " + dzień + " " " " + rok; }.
//Foo mieszka w kraju z timezone GMT + 1 var birthday = new Date(2000,0,1); konsola.log("Foo urodził się na: "+ formatDate(urodziny.getDay(), urodziny.getDate(), urodziny.getMonth(), urodziny.getFullYear()));
sendToBar(urodziny.getTime());
Przykładowe wyjście:
Foo urodziło się dalej: Sat 1 stycznia 2000
/Meanwhile gdzie indziej....
//Bar mieszka w kraju z timezone GMT - 1 var birthday = new Date(receiveFromFoo()); console.log("Foo urodził się na: "+ formatDate(birthday.getDay(), birthday.getDate(), birthday.getMonth(), birthday.getFullYear()));
Przykładowe wyjście:
Foo urodził się dalej: Piątek 31 grudnia 1999
I tak Bar zawsze wierzył, że Foo urodził się ostatniego dnia 1999 roku.
Poprawne podejście format funkcjiDate (dzieńOfWeek, dzień, miesiąc, rok) { var daysOfWeek = ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"];  var miesiące = ["Jan", "Feb", "Mar", "Apr", "Maj", "Jun", "Jul", "Sierpień", "Wrzesień", "Październik", "Nov", "Grudzień"]; dni powracająceOfWeek[dayOfWeek] + " " " + miesiące[miesiace] + " " + dzień + " " " " + rok; }.
//Foo mieszka w kraju o strefie czasowej GMT + 1 var birthday = nowa data (Date.UTC(2000,0,1)); konsola.log("Foo urodził się na: "+ formatData (urodziny.getUTCDay(), urodziny.getUTCDate(), urodziny.getUTCMonth(), urodziny.getUTCFullYear()));
sendToBar(urodziny.getTime());
Przykładowe wyjście:
Foo urodził się dalej: Sat 1 stycznia 2000 r.
/Meanwhile gdzie indziej....
//Bar mieszka w kraju z timezone GMT - 1 
var birthday = new Date(receiveFromFoo());
console.log("Foo urodził się na: "+ formatDate(urodziny.getUTCDay(), urodziny.getUTCDate(), urodziny.getUTCMonth(), urodziny.getUTCFullYear()));
Przykładowe wyjście:
Foo urodził się dalej: Sat 1 stycznia 2000 r.
Tworzenie daty z UTC
Jeśli chcemy stworzyć obiekt Date oparty na UTC lub GMT, możemy użyć metody Date.UTC(....). Używa tych samych argumentów co najdłuższy konstruktor Date. Metoda ta zwróci liczbę reprezentującą czas, który upłynął od 1 stycznia 1970 r., 00:00:00:00 UTC.
konsola.log (Date.UTC(2000,0,31,12));
Przykładowe wyjście:
949320000000
var utcDate = nowa data (Date.UTC(2000,0,31,12)); console.log(utcDate);
Przykładowe wyjście:
Mon 31 stycznia 2000 r. 13:00:00:00 GMT+0100 (West-Europa (standaardtijd))
Nic dziwnego, że diﬀerence pomiędzy czasem UTC a czasem lokalnym jest w rzeczywistości strefą czasową oﬀset przeliczoną na milisekundy.
var utcDate = nowa data (Data UTC (2000,0,31,12)); var localDate = nowa data (2000,0,31,12);
console.log(localDate - utcDate === utcDate.getTimezoneOffset() * 60 * 1000);
Wyjście próbki: prawdziwe
Zmiana obiektu Data
Wszystkie modyfikacje obiektów Date, takie jak setDate(....) i setFullYear(...) mają odpowiednik w czasie UTC, a nie w czasie lokalnym.
var date = new Date(); date.setUTCFullYear(2000,0,31); date.setUTCHours(12,0,0,0,0); console.log(date);
Przykładowe wyjście:
31 stycznia 2000 r. 13:00:00:00 GMT+0100 (West-Europa (standaardtijd))
Pozostałe modyfikacje specyfikacji UTC to .setUTCMonth(), .setUTCDate() (na dzień miesiąca), .setUTCMinutes(), .setUTCSeconds() i .setUTCMilliseconds().
Unikanie dwuznaczności z getTime() i setTime()
W przypadku, gdy powyższe metody są wymagane do diﬀerentiate pomiędzy dwuznacznością dat, zazwyczaj łatwiej jest podać datę jako ilość czasu, który upłynął od 1 stycznia 1970 r., 00:00:00:00 UTC. Ta pojedyncza liczba reprezentuje jeden punkt w czasie i może być w razie potrzeby przeliczana na czas lokalny.
var date = nowa data (Date.UTC(2000,0,31,12)); var timestamp = date.getTime(); //Alternatively var timestamp2 = Date.UTC(2000,0,31,12); console.log (timestamp === timestamp2);
Przykładowe wyjście: prawdziwe
//And podczas konstruowania daty z innego miejsca....var otherDate = new Date (timestamp);
//Represented jako uniwersalna data console.log (otherDate.toUTCString()); //Represented jako lokalna data console.log(otherDate);
Przykładowe wyjście:
Mon, 31 stycznia 2000 12:00:00:00 GMT Mon 31 stycznia 2000 13:00:00:00 GMT+0100 (West-Europa (standaardtijd))
/kod> Sekcja 8.4: Formatowanie daty w języku JavaScript
Formatowanie daty w języku JavaScript w nowoczesnych przeglądarkach
W nowoczesnych przeglądarkach (*), Date.prototype.toLocaleDateString() pozwala na określenie formatowania Date w wygodny sposób.
Wymaga następującego formatu :
dateObj.toLocaleDateString([locales [, options]])
Parametrem locales powinien być łańcuch z tagiem w języku BCP 47 lub tablica takich łańcuchów.
Parametrem opcji powinien być obiekt z niektórymi lub wszystkimi z poniższych właściwości:
localeMatcher : możliwe wartości to "lookup" i "best fit"; domyślnie "best fit" timeZone : jedyną wartością, którą muszą rozpoznać implementacje jest "UTC"; domyślnie jest domyślny czas pracy
godzina strefy12 : możliwe wartości są prawdziwe i fałszywe; domyślnie format zależy od lokalizacjiMatcher : możliwe wartości są "podstawowe" i "najlepiej dopasowane"; domyślnie "najlepiej dopasowane" dzień tygodnia : możliwe wartości są "wąskie", "krótkie" i "długie" epoki : możliwe wartości są "wąskie", "krótkie" i "długie" lata : możliwe wartości są "numeryczne" i "2-cyfrowy" miesiąc : możliwe wartości to "numeryczne", "2-cyfrowe", "wąskie", "krótkie" i "długie" dni : możliwe wartości to "numeryczne" i "2-cyfrowa" godzina : możliwe wartości to "numeryczne" i "2-cyfrowe" minuty : możliwe wartości to "numeryczne" i "2-cyfrowe" sekundy : możliwe wartości to "numeryczne" i "2-cyfrowe" timeZoneName : możliwe wartości to "krótkie" i "długie".
Jak używać var today = new Date().toLocaleDateString('en-GB', { dzień : 'numeric', miesiąc : 'short', rok : 'numeric' });
Wyjście, jeśli zostało wykonane w dniu 24 stycznia ʰ, 2036 :
24 stycznia 2036 r.
Przejście niestandardowe
Jeśli Date.prototype.toLocaleDateString() nie jest na tyle ﬂexible, aby zaspokoić wszelkie potrzeby, jakie możesz mieć, możesz rozważyć stworzenie własnego obiektu Date, który wygląda tak jak ten:
var DateObject = (function() { var monthNames = [ "January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December" ]; var date = function(str) { this.set(str); }; date.prototype = { set : function(str) { var dateDef = str ? new Date(str) : new Date(); this.day = dateDef.getDate(); this.dayPadded = (this.day < 10) ? ("0" + ten.dzień) : "" + ten.dzień; ten.miesiąc = dateDef.getMonth() + 1; ten.monthPadded = (ten.miesiąc < 10) ? ("0" + ten.miesiąc) : "" + ten.miesiąc; ten.monthName = monthNames[this.month - 1]; this.year = dateDef.getFullYear(); }, get : funkcja (właściwości, separator) { separator war separator = separator ? separator : '-' ret = []; dla (var i we właściwościach) { ret.push(this[i]]]); } ret.join(separator);
        } } }; data zwrotu; })();
Jeśli dodałeś ten kod i wykonałeś nowy DateObject() 20 stycznia ʰ, 2019, wytworzyłby obiekt z następującymi właściwościami:
dzień: 20 dayPadded: "20" miesiąc: 1 monthPadded: "01" monthName: "Styczeń" rok: 2019
Aby uzyskać sformatowany ciąg, możesz zrobić coś takiego:
new DateObject().get(['dayPadded', 'monthPadded', 'year']);
W ten sposób otrzymamy następujące wyjście:
20-01-2016
(*) Według MDN "nowoczesne przeglądarki" oznaczają Chrome 24+, Firefox 29+, IE11, Edge12+, Opera 15+ i Safari nightly build

 Sekcja 8.5: Uzyskaj liczbę milisekund, które upłynęły od 1 stycznia 1970 r.
Metoda statyczna Date.now zwraca liczbę milisekund, które upłynęły od 1 stycznia 1970 roku 00:00:00:00 UTC. Aby uzyskać liczbę milisekund, które upłynęły od tego czasu przy użyciu instancji obiektu Date, użyj jego metody getTime.
// uzyskać milisekundy używając statycznej metody teraz z Date console.log (Date.now());
// uzyskać milisekundy używając metody getTime of Date instance console.log((new Date()).getTime()); Punkt 8.6: Uzyskać aktualny czas i datę
Użyj nowego Date() aby wygenerować nowy obiekt Date zawierający bieżącą datę i godzinę.
Zauważ, że Date() wywoływany bez argumentów jest odpowiednikiem nowej Date(Date.now()).
Gdy już posiadasz obiekt daty, możesz zastosować dowolną z kilku dostępnych metod wyodrębnienia jego właściwości (np. getFullYear(), aby uzyskać 4-cyfrowy rok).
Poniżej znajduje się kilka popularnych metod daty.
Pobierz bieżący rok var year = (new Date()).getFullYear(); console.log(year); // Sample output: 2016
Pobierz bieżący miesiąc var month = (new Date()).getMonth(); console.log(month); // Sample output: 0
Proszę zauważyć, że 0 = styczeń. Jest tak dlatego, że miesiące wahają się od 0 do 11, więc często pożądane jest dodanie +1 do indeksu.
Pobierz bieżący dzień var day = (new Date()).getDate(); console.log(day); // Sample output: 31 Get the current hour var hours = (new Date()).getHours(); console.log(hours); // Sample output: 10 Get the current minutes var minutes = (new Date()).getMinutes(); console.log(minutes); // Sample output: 39 Get the current seconds var seconds = (new Date()).getSeconds(); console.log(second); // Sample output: 48 Pobierz aktualne milisekundy
Aby uzyskać milisekundy (od 0 do 999) instancji obiektu Date, użyj jego metody getMilliseconds.
var milliseconds = (new Date()).getMilliseconds(); console.log(milliseconds); // Wyjście: milliseconds właśnie teraz Konwertuj bieżący czas i datę na łańcuch czytelny dla człowieka var now = new Date(); // konwertuj datę na łańcuch w formacie UTC timezone: console.log(now.toUTCString()); // Wyjście: Środa, 21 czerwca 2017 r. 09:13:01 GMT
Metoda statyczna Date.now() zwraca liczbę milisekund, które upłynęły od 1 stycznia 1970 roku 00:00:00:00 UTC. Aby uzyskać liczbę milisekund, które upłynęły od tego czasu przy użyciu instancji obiektu Date, użyj jego metody getTime.
// uzyskać milisekundy używając statycznej metody teraz z Date console.log (Date.now());
// uzyskać milisekundy używając metody getTime of Date instance konssole.log((new Date()).getTime()); 

Punkt 8.7: Increment a Date Object
Aby zwiększyć liczbę obiektów daty w JavaScript, zazwyczaj możemy to zrobić:
var checkoutDate = new Date(); // Thu Jul 21 2016 10:05:13 GMT-0400 (EDT)
checkoutDate.setDate( checkoutDate.getDate() + 1 );
konsola.log (checkoutDate); // Piątek 22 lipca 2016 r. 10:05:13 GMT-0400 (EDT)
Za pomocą setDate można zmienić datę na dzień w następnym miesiącu, używając wartości większej niż liczba dni w bieżącym miesiącu 
var checkoutDate = new Date(); // Thu Jul 21 2016 10:05:13 GMT-0400 (EDT) checkoutDate.setDate( checkoutDate.getDate() + 12 ); console.log(checkoutDate); // Tue Aug 02 2016 10:05:13 GMT-0400 (EDT)
To samo dotyczy innych metod, takich jak getHours(), getMonth(), etc.
Dodawanie dni roboczych
Jeśli chcesz dodać dni robocze (w tym przypadku zakładam, że od poniedziałku do piątku) możesz skorzystać z funkcji setDate, choć potrzebujesz trochę dodatkowej logiki, aby rozliczać weekendy (oczywiście nie będzie to uwzględniać świąt narodowych) 
funkcja addWorkDays (startDate, dni) { // Pobierz dzień tygodnia jako liczbę (0 = niedziela, 1 = poniedziałek, .... 6 = sobota) var dow = startDate.getDay(); var daysToAdd = dni; // Jeżeli bieżący dzień jest niedzielą, dodaj jeden dzień, jeżeli (dow == 0) daysToAdd++; // Jeżeli data rozpoczęcia plus dodatkowe dni przypada w najbliższą sobotę lub po najbliższej sobocie, oblicz weekendy, jeżeli (dow + daysToAdd >= 6) { //Subtract days in current working weekendu od pozostałych dni roboczych varWorkDays = daysToAdd - (5 - dow);        //Dodaj dni robocze bieżącego tygodnia roboczegoToDodaj += 2; jeśli (pozostałe dni robocze > 5) { //Dodaj dwa dni za każdy tydzień roboczy, obliczając, ile tygodni jest wliczonych do dni roboczychToDodaj += 2 * Math.floor(pozostałeWorkDays / 5); //Exclude final weekend, jeśli pozostałeWorkDays decyduje o dokładnej liczbie tygodni, jeśli (pozostałeWorkDays % % == 0) daysToAdd -= 2; }    } startDate.setDate(startDate.getDate() + daysToAdd); return startDate; } 

Punkt 8.8: Konwersja do JSON
var date1 = new Date(); date1.toJSON();
Zwroty: "2016-04-14T23:49:08.596Z

Rozdział 9: Porównanie dat Sekcja 9.1: Porównanie wartości dat
Aby sprawdzić równość wartości Date:
var date1 = new Date(); var date2 = new Date(date1.valueOf() + 10); console.log (date1.valueOf() ==== date2.valueOf());
Przykładowe wyjście: false
Zauważ, że musisz użyć wartościOf() lub getTime() aby porównać wartości obiektów Date, ponieważ operator równości porówna, jeśli dwa obiekty odniesienia są takie same. Na przykład:
var date1 = new Date(); var date2 = new Date(); console.log (date1 ==== date2);
Przykładowe wyjście: false
Natomiast jeśli zmienne wskazują na ten sam obiekt:
var date1 = new Date(); var date2 = date1; console.log (date1 ==== date2);
Przykładowe wyjście: true
Jednakże, inni operatorzy porównania będzie działać jak zwykle i można użyć < i >, aby porównać, że jedna data jest wcześniej lub później niż inne. Na przykład:
var date1 = new Date(); var date2 = new Date(date1.valueOf() + 10); console.log (date1 < date2);
Przykładowe wyjście: true
Działa nawet wtedy, gdy operator uwzględnia równość:
var date1 = new Date(); var date2 = new Date(date1.valueOf()); console.log (date1 <= date2);
Przykładowe wyjście: prawdziwe

Sekcja 9.2: Obliczanie daty śmierci
Aby porównać diﬀerence z dwóch dat, możemy dokonać porównania w oparciu o timestamp.
var date1 = new Date(); var date2 = new Date(date1.valueOf() + 5000);
var dateDiff = date1.valueOf() - date2.valueOf(); var dateDiffInYears = dateDiff/1000/60/60/24/365; //konwersja milisekund na lata
console.log("Date difference in years : " + dateDiffInYears);

Rozdział 10: Działania porównawcze

 Sekcja 10.1: Abstrakcyjna równość / nierówność i konwersja typów
Problem
Operatorzy abstrakcyjnej równości i nierówności (== i !=) konwertują swoje operandy, jeśli typy operandów nie pasują do siebie. Ten typ przymusu jest powszechnym źródłem nieporozumień co do wyników tych operatorów, w szczególności, operatorzy ci nie zawsze są przejściowi, jak można by oczekiwać.
"" == 0; // true A 0 == "0"; // true A "" == "0"; // false B false === 0; // true false === "0"; // true
"" != 0; // false A 0 != "0"; // false A "" != "0"; // true B false != 0; // false != "0"; // false
Wyniki zaczynają mieć sens, jeśli wziąć pod uwagę, jak JavaScript konwertuje puste ciągi znaków na liczby.
Number("""); // 0 Number("0"); // 0 Number(false); // 0
Rozwiązanie
W wyrażeniu false B oba operandy są łańcuchami (""" i "0"), stąd nie będzie konwersji typu i ponieważ "" i "0" nie są tą samą wartością, "" == "0" jest fałszywe jak się tego oczekuje.
Jednym ze sposobów wyeliminowania nieoczekiwanego zachowania jest upewnienie się, że zawsze porównuje się operandy tego samego typu. Na przykład, jeśli chcesz, aby wyniki porównania liczbowego użyj konwersji explicit:
var test = (a,b) = (a,b) => Number(a) == Number(b); test(", 0); // true; test("0", 0); // true; // test("0", 0"); // true; test("abc", "abc"); // false as operands are not numbers
Lub, jeśli chcesz porównać łańcuchy:
var test = (a,b) = (a,b) => String(a) == String(b); test("", 0); // false; test("0", 0); // true test(", "0"); // false;
Przypis boczny: Liczba ("0") i nowa liczba ("0") to nie to samo! Podczas gdy pierwszy wykonuje konwersję typu, drugi utworzy nowy obiekt. Obiekty są porównywane przez odniesienie, a nie przez wartość, co wyjaśnia wyniki poniżej.
Number("0") == Number("0"); // true;
new Number("0") == new Number("0"); // false
Wreszcie, macie państwo możliwość korzystania z usług operatorów o ścisłej równości i nierównościach, którzy nie będą dokonywać żadnych ukrytych konwersji typu.
"" === 0; // false 0 === "0"; // false "" === "0"; // false
Dalsze odniesienia do tego tematu można znaleźć tutaj:
Który operator równy (=== vs ===) powinien być użyty w porównaniach JavaScript?
Abstrakcyjna równość (==) 

Sekcja 10.2: NaN Własność obiektu globalnego
NaN ("Not a Number") to specjalna wartość określana przez IEEE Standard for Floating-Point Arithmetic, która jest używana, gdy podawana jest wartość niecyfrowa, ale spodziewana jest liczba (1 *"dwa"), lub gdy obliczenie nie ma poprawnego wyniku liczbowego (Math.sqrt(-1)).
Jakakolwiek równość lub porównania relacyjne z NaN zwraca fałszywe wyniki, nawet porównując je z samym sobą. Ponieważ NaN ma oznaczać wynik bezsensownych obliczeń i jako taki nie jest równy wynikowi innych bezsensownych obliczeń.
(1 * "dwa") ====NaN //false
NaN ==== 0; // false NaN ==== NaN; // false Number.NaN ==== NaN; // false
NaN < 0; // fałszywe NaN > 0; // fałszywe NaN > 0; // fałszywe NaN >= NaN; // fałszywe NaN >= "dwa"; // fałszywe
Porównania, które nie są równorzędne, zawsze będą prawdziwe:
NaN !=== 0; // prawdziwy NaN !=== NaN; // prawdziwy Sprawdzanie, czy wartość jest NaN Wersja ≥ 6
Możesz przetestować wartość lub wyrażenie dla NaN używając funkcji Number.isNaN():
Number.isNaN(NaN); // true Number.isNaN(0 / 0); // true Number.isNaN('str' - 12); // true
Number.isNaN(24); // false Number.isNaN('24'); // false Number.isNaN(1 / 0); // false Number.isNaN(Infinity); // false
Number.isNaN('str'); // false Number.isNaN(niezdefiniowany); // false
Number.isNaN({}); // false Version < 6
Możesz sprawdzić, czy wartość jest NaN, porównując ją z wartością samą w sobie:
wartość !=== wartość; // true dla NaN, false dla każdej innej wartości
Możesz użyć następującego poliflla dla Number.isNaN():
Number.isNaN = Number.isNaN || funkcja(wartość) { wartość zwrotu !== wartość; }
Natomiast funkcja globalna isNaN() zwraca true nie tylko dla NaN, ale także dla każdej wartości lub wyrażenia, które nie mogą być wymuszone do liczby:
isNaN(NaN); // true isNaN(0 / 0); // true isNaN('str' - 12); // true
isNaN(24); // false isNaN('24'); // false isNaN(Infinity); // false
isNaN('str'); // true isNaN(niezdefiniowany); // true isNaN({}); // true
ECMAScript określa algorytm "identyczności" zwany SameValue, który od ECMAScript 6 może być wywoływany z Object.is. W przeciwieństwie do porównania == i ===, używając Object.is() traktuje NaN jako identyczne z samym sobą (i -0 jako nie identyczne z +0):
Object.is(NaN, NaN) // true Object.is(+0, 0) // false
NaN === NaN // false +0 === 0 // true Wersja < 6
Możesz użyć następującego poliflla dla Object.is() (z MDN):
if (!Object.is) { Object.is = funkcja (x, y) { // Algorytm SameValue if (x === y) { // Kroki 1-5, 7-10 // Kroki 6.b-6.e: +0 != -0 return x !== 0 || 1 / x === 1 / y; } else { // Step 6.a: NaN == NaN return x !== x &&& y !== y; }  }; } Punkty do odnotowania
NaN sam w sobie jest liczbą, co oznacza, że nie jest tożsamy z ciągiem "NaN", a co najważniejsze (choć może nieintuicyjnie):
typ(NaN) === "liczba"; //true 

Sekcja 10.3: Krótkotrwałe zwarcie u operatorów systemu wspomagania
Operator (&&) i operator (||) stosują zwarcia, aby zapobiec niepotrzebnej pracy, jeśli wynik operacji nie zmienia się wraz z dodatkową pracą.
W x & y y, y nie będzie oceniane, jeśli x oceni się jako fałszywe, ponieważ całe wyrażenie jest gwarantowane jako fałszywe.
W x || y, y nie będzie obliczane, jeśli x będzie obliczane jako prawdziwe, ponieważ całe wyrażenie jest gwarantowane jako prawdziwe.
Przykład z funkcjami
Weź następujące dwie funkcje:
funkcja T() { // Prawdziwa konsola.log("T"); zwróć true; }
funkcja F() { // False console.log("F"); zwróć false; }
Przykład 1
T() &&F(); // false
Wyjście:
T" "F
Przykład 2
F() &&T(); // false
Wyjście:
'F'
Przykład 3
T() || F(); // prawdziwe
Wyjście:
'T'
Przykład 4
F() || T(); // prawdziwe
Wyjście:
F" "T
Zwarcie w celu uniknięcia błędów
var obj; // obiekt ma wartość nieokreśloną if(obj.property){ }/// TypeError: Nie można odczytać właściwości 'właściwości' niezdefiniowanej jeśli (obj.property && obj !== niezdefiniowana){}// Line A TypeError: Nie można odczytać "własności" niezdefiniowanej
Wiersz A: jeśli odwrócisz zamówienie pierwsze warunkowe oświadczenie zapobiegnie błędowi na drugim, nie wykonując go, jeśli rzuci błąd
if(obj !== niezdefiniowany &&ob.property){}; // brak błędu
Ale powinien być używany tylko wtedy, gdy oczekujesz niezdefiniowanych
if(typ obj === "obiekt" &&ob.property){}; // opcja bezpieczna, ale wolniejsza
Zwarcie w celu podania wartości domyślnej
Za pomocą operatora || można wybrać albo wartość "truthy", albo wartość domyślną.
Na przykład, może to być użyte do zapewnienia, że wartość nullable jest konwertowana na wartość nieullable:
var nullableObj = null; var obj = nullableObj || {}; // wybiera {}
var nullableObj2 = {x: 5}; var obj2 = nullableObj2 || {} // {x: 5} {x: 5}.
Albo zwrócić pierwszą wartość prawdy
var truthyValue = {x: 10}; truthyValue zwrotu || {}; // zwróci {x: 10}
To samo można wykorzystać do wielokrotnego upadku:
envVariable || configValue || defaultConstValue // wybierz pierwszą "trutię" z tych
Krótkie zwarcie w celu wywołania funkcji opcjonalnej
Operator &&& może być użyty do oceny oddzwonienia zwrotnego tylko wtedy, gdy jest ono pozytywne:
funkcja myMethod(cb) { // Można to uprościć, jeśli (cb) { cb(); }

 // Do tego cb && cb(); }
Oczywiście powyższy test nie sprawdza, czy cb jest w rzeczywistości funkcją, a nie tylko obiektem/Array/String/Number. 

Punkt 10.4: Nieokreślony i nieokreślony
diﬀerences pomiędzy wartością zerową i nieokreśloną
null and und und undefined share abstract equality === but not strict equality ===,
null === niezdefiniowany // prawdziwy null === niezdefiniowany // false
Reprezentują one nieco diﬀerent
undefined oznacza brak wartości, np. przed utworzeniem właściwości identyfikatora/obiektu lub w okresie pomiędzy utworzeniem parametru identyfikatora/funkcji a jego pierwszym zestawem, jeśli taki istnieje. null oznacza celowy brak wartości dla identyfikatora lub właściwości, która została już utworzona.
Są to typy składni diﬀerent niezdefiniowana jest właściwością globalnego Obiektu, zwykle niezmienną w globalnym zakresie. Oznacza to, że wszędzie tam, gdzie można określić identyfikator inny niż w globalnej przestrzeni nazw, można ukryć niezdefiniowany z tego zakresu (chociaż rzeczy mogą być nadal niezdefiniowane) null jest słowem dosłownym, więc jego znaczenie nigdy nie może być zmieniane, a próba uczynienia tego będzie oznaczać błąd.
Podobieństwa między puste i niezdefiniowane
zerowe i niezdefiniowane są zarówno błędne, jak i niezdefiniowane.
if (null) console.log("not be logged"); if (undefined) console.log("not be logged");
Ani null ani und undefined equal false (zobacz to pytanie).
false === niezdefiniowany // false false == null // false false ===== niezdefiniowany // false false ===== null // false Using undefined
Jeśli nie można ufać obecnemu zakresowi, użyj czegoś, co ocenia jako nieokreślone, na przykład void 0;. Jeśli niezdefiniowany jest cieniowany przez inną wartość, jest tak samo zły jak shadowing Array lub Number. Unikaj ustawiania czegoś tak niezdefiniowanego. Jeśli chcesz usunąć pasek właściwości z Object foo, usuń foo.bar; zamiast tego. Identyfikator testu egzystencji foo przeciwko niezdefiniowanemu może rzucić błąd odniesienia, zamiast tego użyj typu foo przeciwko "niezdefiniowanemu". 

Sekcja 10.5: Abstrakcyjna równość (==)
Operacje abstrakcyjnego operatora równości są porównywane po konwersji na wspólny typ. Jak to zrobić?
konwersja odbywa się na podstawie specyfikacji operatora:
Wyszczególnienie dla operatora ===:
7.2.13 Abstrakcyjne porównanie równorzędności Porównanie x = y, gdzie x i y są wartościami, daje wynik prawdziwy lub fałszywy. Takie porównanie jest wykonywane w następujący sposób:
Jeśli Typ(x) jest taki sam jak Typ(y), to:1.
a. Zwróć wynik wykonania Strict Equality Comparison x ===== y.
Jeśli x jest puste, a y jest niezdefiniowane, zwróć true.2. Jeśli x jest niezdefiniowane, a y jest puste, zwróć true.3. Jeśli Typ(x) jest liczbą, a Typ(y) jest łańcuchem, zwróć wynik porównania x == ToNumber(y).4. Jeżeli Typ(x) jest String i Typ(y) jest liczbą, zwróć wynik porównania ToNumber(x) == y.5. Jeżeli Typ(x) jest liczbą logiczną, zwróć wynik porównania ToNumber(x) == y.6. Jeżeli Typ(y) jest liczbą logiczną, zwróć wynik porównania x == ToNumber(y).7. Jeśli Typ(x) jest albo String, albo Liczba, albo Symbol i Typ(y) jest Obiektem, zwróć wynik porównania 8. porównanie x == ToPrimitive(y). Jeśli Typ(x) jest Obiektem a Typ(y) jest albo String, Liczba, albo Symbol, zwróć wynik porównania ToPrimitive(x) == y. Zwróć false.10.
Przykłady: 1 == 1; // true 1 === true; // true (operand skonwertowany na liczbę: true => 1) 1 == '1'; // true (operand skonwertowany na liczbę: '1' => 1 ) 1 == '1.00'; // true 1 == '1.00000000001'; // false 1 == '1.000000000000000000001'; // true (true (true due to precision loss) null == niezdefiniowany; // true (spec #2) 1 === 2; // false 0 == false; // true 0 == true 0 == undefined; // false 0 == "; // true Section 10.6: Logic Operators with Booleans
var x = prawdziwe, y = fałszywe;
AND AND
Operator ten zwróci wartość true, jeśli oba wyrażenia ocenione zostaną jako prawdziwe. Ten operator boolean zastosuje zwarcie i nie będzie oceniał y, jeśli x oceni je jako fałszywe.
x &&y;
To zwróci false, ponieważ y jest false.
OR
Operator ten zwróci wartość true, jeśli jedno z dwóch wyrażeń oceni je jako prawdziwe. Ten operator wspomagający będzie zatrudniał zwarcie i y nie będą oceniane, jeśli x oceni je jako prawdziwe.
x || y;
To zwróci wartość true, ponieważ x jest true.
NIE DOTYCZY.
Operator ten zwróci false, jeśli wyrażenie po prawej stronie jest prawdziwe, a true, jeśli wyrażenie po prawej stronie jest fałszywe.
!x;
To zwróci false, ponieważ x jest true. Punkt 10.7: Automatyczne konwersje typów
Należy pamiętać, że numery mogą przypadkowo zostać zamienione na ciągi znaków lub NaN (nie liczba).
JavaScript jest luźno wpisywany. Zmienna może zawierać typy danych diﬀerent, a zmienna może zmienić typ danych:
var x = "Hello"; // typ x to łańcuch x = 5; // zmienia typ x na liczbę
Podczas wykonywania operacji matematycznych, JavaScript może konwertować liczby do łańcuchów:
var x = 5 + 7; // x.valueOf() jest 12, typ x jest liczbą var x = 5 + "7"; // x.valueOf() jest 57, typ x jest łańcuchem var x = "5" + 7; // x.valueOf() jest 57, typ x jest łańcuchem var x = 5 - 7; // x.valueOf() jest -2, typ x jest liczbą var x = 5 - "7"; // x.valueOf() jest -2, typ x jest liczbą var x = "5" - 7; // x.valueOf() jest -2, typ x jest liczbą var x = 5 - "x"; // x.valueOf() jest NaN, typ x jest liczbą
Odjęcie łańcucha od łańcucha nie generuje błędu, ale zwraca NaN (Not a Number):
"Hello" - "Dolly" // zwraca NaN Punkt 10.8: Operatorzy logiczni z wartościami nieboolanowymi (przymus boolean)
LUB (||), czytając od lewej do prawej, oceni pierwszą wartość truthy. Jeśli nie zostanie znaleziona żadna wartość truthy, zwracana jest ostatnia wartość.
var a = 'hello' || ''; // a = 'hello' var b = '' || []; // b = [] var c = '' || niezdefiniowany; // c = niezdefiniowany var d = 1 || 5;                    // d = 1 var e = 0 || {}; // e = {} var f = 0 || '' || 5; // f = 5 var g = '' || 'yay' || 'boo'; // g = 'yay'.
Logical AND (&&), czytając od lewej do prawej, oceni pierwszą wartość falsyfikatu. Jeśli nie znaleziono fałszywej wartości, zwracana jest ostatnia wartość.
GoalKicker.com - JavaScript® Notes for Professionals 68
var a = "hello" && ''; // a = '' var b = '' && []; // b = '' var c = niezdefiniowany && 0; // c = niezdefiniowany var d = 1 && 5; // d = 5 var e = 0 &&& {}; // e = 0 var f = 'hi' &&& [] && 'done'; // f = 'done' var g = 'bye' &&&' und& 'adios'; // g = und f = 'done' var g = 'bye' && 'adios'; // g = und und.
Tej sztuczki można użyć, na przykład, do ustawienia domyślnej wartości argumentu funkcji (przed ES6).
var foo = funkcja(val) { // jeśli val ocenia jako fałszywe, to zamiast tego zostanie zwrócona 'domyślna'. return val || 'default'; }
console.log( foo('burger') ); // burger console.log( foo(100) ); // 100 console.log( foo([]) ); // [] console.log( foo(0) ); // default console.log( foo(undefined) ); // default
Pamiętaj tylko, że dla argumentów, 0 i (w mniejszym stopniu) pusty łańcuch są również często poprawnymi wartościami, które powinny być wyraźnie podane i zastąpić domyślne, które przy tym wzorze nie będą (ponieważ są błędne). 

Sekcja 10.9: Pusta tablica
/* ToNumber(ToPrimitive([])) == ToNumber(false) */ [] == false; // true
Kiedy [].toString() jest wykonywany, wywołuje [].join(), jeśli istnieje, lub Object.prototype.toString() inaczej. To porównanie zwraca prawdę, ponieważ [].join() zwraca ''', który wymuszony na 0, jest równy false ToNumber.
Uważaj jednak, wszystkie obiekty są prawdziwe i Array jest instancją Object:
// Wewnętrznie jest to oceniane jako ToBoolean([]) === true ? truthy" : "fałszywy" [] ? trutia": "fałszywy"; // "truth" 

Sekcja 10.10: Operacje porównywania równości
JavaScript posiada cztery operacje porównywania równości diﬀerent
SameValue
Zwraca prawdę, jeśli oba operandy należą do tego samego typu i mają tę samą wartość.
Uwaga: wartość obiektu jest wartością odniesienia.
Możesz użyć tego algorytmu porównawczego poprzez Object.is (ECMAScript 6).
Przykłady:
Object.is(1, 1); // true 
Object.is(+0, -0); // false 
Object.is(NaN, NaN); // true 
Object.is(true, "true"); // false 
Object.is(false, 0); // false
Object.is(null, undefined); // false 
Object.is(1, "1"); // false 
Object.is([], []); // false
Algorytm ten posiada właściwości relacji równoważności:
Reﬂexivity: Object.is(x, x) jest prawdziwe, dla każdej wartości x Symetria: Object.is(x, y) jest prawdziwy jeśli i tylko jeśli Object.is(y, x) jest prawdziwy, dla dowolnych wartości x i y. Przełożenie: Jeżeli Object.is(x, y) i Object.is(y, z) są prawdziwe, to Object.is(x, z) jest również prawdziwe, dla dowolnych wartości x, y i z.
SameValueZero
Zachowuje się jak SameValue, ale uważa +0 i -0 za równe.
Możesz użyć tego algorytmu porównawczego poprzez Array.prototype.includes (ECMAScript 7).
Przykłady:
1].includes(1); // true [+0].includes(-0); // true [NaN].includes(NaN); // true [true].includes("true"); // false [false].includes(0); // false [false [1].includes("1"); // false [null].includes(undefined); // false [[].includes([]); // false
Algorytm ten nadal posiada właściwości relacji równoważności:
Reﬂexivity: x].includes(x) jest prawdziwe, dla każdej wartości x Symetria: x].includes(y) jest prawdziwe jeśli, i tylko jeśli, [y].includes(x) jest prawdziwe, dla dowolnych wartości x i y. Transitivity: Jeśli [x].includes(y) i [y].includes(z) są prawdziwe, to [x].includes(z) jest również prawdziwe, dla każdej wartości x, y i z.
Ścisłe porównanie równości
Zachowuje się jak SameValue, ale
Uważa, że +0 i -0 są równe. Uważa, że NaN diﬀerent jest wartością niższą niż jakakolwiek inna wartość, włączając w to samą siebie.
Możesz użyć tego algorytmu porównawczego za pomocą operatora === (ECMAScript 3).
Istnieje również operator !=== (ECMAScript 3), który neguje wynik ===.
Przykłady:
1 === 1; // true +0 === -0; // true NaN === NaN; // false true === "true"; // false false === 0; // false 1 === "1"; // false null === niezdefiniowany; // false [] === []; // false
Algorytm ten ma następujące właściwości
Symetria: x === y jest prawdą jeśli, i tylko jeśli, y === xistrue, dla dowolnych wartościxandy`. Przelotność: Jeśli x === y i y === z są prawdziwe, to x === z jest również prawdziwe, dla dowolnych wartości x, y i z.
Ale nie jest to relacja równoważności, ponieważ
NaN nie jest reﬂexive NaN !== NaN
Streszczenie Równość Porównanie
Jeśli oba operandy należą do tego samego typu, zachowuje się jak Strict Equality Comparison.
W przeciwnym razie wymusza je w następujący sposób:
undefined i null są uważane za równe Podczas porównywania liczby z ciągiem znaków, ciąg znaków jest wymuszony do liczby Podczas porównywania liczby boolean z czymś innym, ciąg znaków boolean jest wymuszony do liczby Podczas porównywania obiektu z liczbą, ciągiem znaków lub symbolem, obiekt jest wymuszony do liczby pierwotnej
W przypadku przymusu, wymuszone wartości są porównywane powtarzalnie. W przeciwnym razie algorytm zwraca false.
Możesz użyć tego algorytmu porównawczego za pomocą operatora === (ECMAScript 1).
Istnieje również operator != operator (ECMAScript 1), który neguje wynik ==.
Przykłady:
1 == 1; // true +0 == -0; // true NaN == NaN; // false true === "true"; // false false == 0; // true 1 === "1"; // true null === niezdefiniowany; // true [] == []; // false
Algorytm ten ma następującą właściwość:
Symetria: x == y jest prawdziwe jeśli, i tylko jeśli, y == x jest prawdziwe, dla dowolnych wartości x i y.
Ale nie jest to relacja równoważności, ponieważ
NaN nie jest reﬂexive NaN != NaN Transitivity nie utrzymuje, np. 0 == ''' i 0 == '0', ale '' != '0' 

Sekcja 10.11: Podmioty powiązane (<, <=, >, >=)
Gdy oba operandy są numeryczne, są porównywane normalnie:
1 < 2 // true 2 <= 2 // true 3 >= 5 // false true < false // false (domyślnie przekształcony na liczby, 1 > 0)
Gdy oba operandy są strunami, są porównywane leksykograficznie (według porządku alfabetycznego):
a" < 'b' // prawdziwe '1' < '2' // prawdziwe
100" > "12" // fałszywe ("100" to mniej niż "12" leksykograficznie!)
Kiedy jeden operand jest ciągiem znaków, a drugi liczbą, ciąg znaków jest konwertowany na liczbę przed porównaniem:
1' < 2 // true '3' > 2 // true true true > '2' // false (true implicitly converted to number, 1 < 2)
Gdy łańcuch jest niecyfrowy, konwersja numeryczna zwraca NaN (nie-a-numer). Porównanie z NaN zawsze zwraca false:
1 < 'abc' // false 1 > 'abc' // false
Należy jednak zachować ostrożność porównując wartość liczbową z wartościami null, undefined lub pustymi łańcuchami:
1 > '' // true 1 < '' // false 1 > null // true 1 < null // false 1 > undefined // false 1 < undefined // false
Kiedy jeden operand jest obiektem, a drugi liczbą, obiekt jest konwertowany na liczbę przed porównaniem.null jest więc szczególnym przypadkiem, ponieważ liczba (null);//0
nowa data(2015)< 1479480185280 // prawda zerowa > -1 //trawda ({doString:function(){return 123}})) > 122 //t prawda 

Sekcja 10.12: Nierówności
Operator != jest odwrotnością operatora ==. Zwróci prawdę, jeśli operandy nie są równe. Mechanizm JavaScript spróbuje przekonwertować oba operandy na pasujące typy, jeśli nie są one tego samego typu. Uwaga: jeśli oba operandy mają w pamięci wewnętrzne odnośniki diﬀerent, to zwrócony zostanie fałsz.
Próbka:
1 != '1' // false 1 != 2 // true
W powyższej próbie 1 != "1" jest fałszywe, ponieważ typ liczby prymitywnej jest porównywany z wartością znaku. Dlatego silnik JavaScript nie dba o typ danych wartości R.H.S.
Operator: !=== jest odwrotnością operatora ===. Zwróci prawdę jeśli operandy nie są równe lub jeśli ich typy nie pasują do siebie.
Przykład:
1 !=== '1' // true 1 !=== 2 // true 1 !== 1 // false

Sekcja 10.13: Wykaz operatorów porównujących
Przykład porównania operatora 
== Equal i == 0 
=== Equal Value and Type i === "5"
!= Not Equal i != 5 
!== Not Equal Value or Type i !== 5 
> Greater than i > 5 
< Less than i < 5 
>= Greater than or equal i >= 5
<= Less than or equal i <= 5

Sekcja 10.14: Grupowanie wielokrotnych oświadczeń logicznych
Możesz pogrupować wiele instrukcji logiki wspomagającej w nawiasy w celu stworzenia bardziej złożonej oceny logiki, szczególnie przydatnej w przypadku instrukcji.
if ((wiek >= 18 lat i wysokość >= 5.11) || (status === 'royalty' && hasInvitation)) { console.log('Możesz wejść do naszego klubu'); }
Moglibyśmy również przenieść logikę grupową do zmiennych, aby uczynić to stwierdzenie nieco krótszym i opisowym:
var isLegal = wiek >= 18 lat; 
var tall = wysokość >= 5.11; 
var suitable = isLegal && tall; 
var isRoyalty = status === 'royalty'; 
var specialCase = isRoyalty && hasInvitation; 
var canEnterOurBar = suitable || specialCase;
if (canEnterOurBar) console.log('Możesz wejść do naszego klubu');
Zauważ, że w tym konkretnym przykładzie (i wielu innych), grupowanie stwierdzeń nawiasami działa tak samo, jak gdybyśmy je usunęli, po prostu postępuj zgodnie z logiką liniową i uzyskasz ten sam wynik. Wolę używać nawiasów, ponieważ pozwalają mi one lepiej zrozumieć, co zamierzałem i mogą zapobiec błędom logicznym. 

Sekcja 10.15: Bit ma na celu optymalizację porównywania danych wielopaństwowych
Bit Feld jest zmienną, która utrzymuje różne stany boolean jako pojedyncze bity. Trochę dalej reprezentowałoby to prawdę, a oﬀ byłoby fałszywe. W przeszłości rutynowo używano bitów, ponieważ zapisywano w nich pamięć i zmniejszano obciążenie procesora. Chociaż potrzeba stosowania bit ﬁeld nie jest już tak ważna, to jednak nie są one już tak ważne jak oﬀer, to jednak niektóre z nich mogą uprościć wiele zadań obróbczych.
Na przykład wprowadzanie danych przez użytkownika. Po otrzymaniu danych wejściowych z klawiszy kierunkowych klawiatury w górę, w dół, w lewo, w prawo, można zakodować różne klawisze w jedną zmienną z przypisanymi bitami w każdym kierunku.
Przykładowy odczyt klawiatury przez bitﬁeld
var bitField = 0; // wartość do przytrzymywania bitów const KEY_BITS = [4,1,8,2]; // lewy w górę w dół w prawo KEY_MASKS = [0b1011,0b11,0b11,0b11,0b1101]; // lewy w górę w dół w prawo window.onkeydown = window.onkeyup = funkcja (e) { jeśli (e.keyCode >= 37 && e.keyCode <41){
       if(e.type === "keydown"){ bitField |= KEY_BITS[e.keyCode - 37]; }else{ bitField &= KEY_MASKS[e.keyCode - 37]; }    }    }
Przykładowy odczyt jako tablica
var directionState = [false,false,false,false,false,false,false]; window.onkeydown = window.onkeyup = funkcja (e) { if(e.keyCode >= 37 && e.keyCode <41){ directionState[e.keyCode - 37] = e.type === "keydown"; }    }
Aby włączyć bit użyj bitu lub | i wartości odpowiadającej bitowi. Więc jeśli chcesz ustawić 2-bitowe pole bitowe |= 0b10 włączy je. Jeśli chcesz włączyć bit oﬀ użyj bitów bitowych i & z wartością, która ma włączone wszystkie wymagane bity. Używając 4 bitów i przekręcając drugi bit oﬀ bitfield &= 0b1101;
Można powiedzieć, że powyższy przykład wydaje się o wiele bardziej złożony niż przypisywanie różnych stanów klawiszy do tablicy. Tak, jest to trochę bardziej skomplikowane do ustawienia, ale zaletą jest to, że jest to przydatne podczas przesłuchiwania stanu.
Jeśli chcesz sprawdzić, czy wszystkie klucze są włączone.
// jako pole bitowe jeśli(!bitfield) // brak klawiszy
// jako tablica testuj każdą pozycję w tablicy jeśli(!(directionState[0] && directionState[1] && directionState[2] & directionState[3])){
Możesz ustawić pewne stałe, aby ułatwić sobie życie
// postfix U,D,L,R dla lewego górnego 
const KEY_U = 1; 
const KEY_D = 2; 
const KEY_L = 4; 
const KEY_R = 8;
const KEY_UL = KEY_U + KEY_L; // lewy
const KEY_UR = KEY_U + KEY_R; // w górę prawy 
const KEY_DL = KEY_D + KEY_L; //  w dol lewy 
const KEY_DR = KEY_D + KEY_R // w dol prawy
Następnie można szybko przetestować wiele różnych stanów klawiatury
if ((bitfield & KEY_UL) === KEY_UL) { // jest w górę, a LEFT tylko wtedy, gdy (bitfield & KEY_UL) { // jest w dole, 
if ((bitfield & KEY_U) === KEY_U) { // jest w górę tylko wtedy, 
if (bitfield & KEY_U) { // jest w dole (jakikolwiek inny klucz może być w dół), 
if (!(bitfield & KEY_U)) { // jest w górę (dowolny inny klucz może być w dół),
if (!bitfield ) { // żaden klucz nie jest w dół, 
if (bitfield ) { // jeden lub więcej kluczy jest w dół
Wejście klawiaturowe jest tylko jednym z przykładów. Bitfile są przydatne, gdy masz różne stany, które muszą być połączone. JavaScript może używać do 32 bitów dla bitu ﬁeld. Użycie ich może oznaczać wzrost wydajności oﬀer Warto się z nimi zapoznać.

Rozdział 11: Warunki
Wyrażenia warunkowe, obejmujące słowa kluczowe, takie jak czy i inne, zapewniają programom JavaScript możliwość wykonywania akcji diﬀerent w zależności od warunku logicznego: true lub false. Ta sekcja obejmuje użycie warunków JavaScript, logiki logiki logiki logicznej i stwierdzeń trójdzielnych. 

Sekcja 11.1: Operatorzy trójczłonowi
Może być użyty do skrócenia operacji, jeśli/elastycznie. Jest to przydatne przy szybkim zwrocie wartości (np. w celu przypisania jej do innej zmiennej).
Na przykład:
var animal = "kitty"; 
var result = (zwierzę === "kitty") ? Cute" : "still nice";
W tym przypadku wynik otrzymuje wartość "słodki", ponieważ wartością zwierzęcia jest "kotek". Jeśli zwierzę miałoby inną wartość, wynik otrzymywałby wartość "wciąż miły".
Porównaj to z tym, co kod chciałby mieć z warunkami if/else.
var animal = "kitty"; 
var result = ''; if (zwierzę === "kitty") { result = "cute"; } else { result = "still nice"; }
Jeżeli lub inne warunki mogą mieć kilka operacji. W tym przypadku operator zwraca wynik ostatniego wyrażenia.
var a = 0;
var str = "nie a"; 
var b = ""; b = a === 0 ? (a = 1, str += ' test') : (a = 2);
Ponieważ a było równe 0, staje się 1, a str staje się "nie testem". Operacja, która dotyczyła str była ostatnia, więc b otrzymuje wynik operacji, który jest wartością zawartą w str, tj.
Operatorzy trójdzielni zawsze oczekują innych warunków, w przeciwnym razie dostaniesz błąd składni. Jako obejście można by zwrócić zero czegoś podobnego w innej gałęzi - to nie ma znaczenia, jeśli nie używamy wartości zwrotu, ale jedynie skracamy (lub próbujemy skrócić) operację.
var a = 1; a === 1 ? alert('Hey, to jest 1!') : 0;
Jak widzisz, jeśli (a === 1) alert('Hey, to jest 1! Byłby to po prostu dłuższy znak, ponieważ nie wymaga obowiązkowego warunku. Jeśli inny warunek byłby zastosowany, metoda trójdzielna byłaby znacznie czystsza.
a === 1 ? alert('Hej, to jest 1!') : alert('Dziwne, co to może być?'); jeśli (a ===1) alert('Hej, to jest 1!') alert('Dziwne, co to może być?');
Ternary mogą być zagnieżdżone, aby zawrzeć w nich dodatkową logikę. Na przykład
foo ? bar ? 1 : 2 : 3
// Aby było jasne, jest to oceniane od lewej do prawej // i może być bardziej jednoznacznie wyrażone jako:
foo ? (pasek ? 1 : 2) : 3
Jest to takie samo, jak w przypadku, gdy/else
if (foo) { if (bar) { 1 } else { 2 } } } else { 3 }
Stylistycznie powinno być to używane tylko z krótkimi nazwami zmiennych, ponieważ wielowierszowe trójwierszowe ternary mogą drastycznie zmniejszyć czytelność.
Jedynymi stwierdzeniami, których nie można używać w trójwierszach są stwierdzenia sterujące. Na przykład, nie można używać zwrotów ani zerwania z ternariami. Poniższe wyrażenie będzie nieważne.
var animal = 'kitty'; dla (var i = 0; i < 5; ++i) { (zwierzę === 'kitty') ? break:console.log(i); }
W przypadku deklaracji zwrotnych nieważne byłyby również następujące elementy
var animal = "kitty"; (zwierzę ==="kitty") ? zwrot "meow": zwrot "woof";
Aby to zrobić prawidłowo, należy zwrócić trójząb w następujący sposób:
var animal = "kitty"; powrót (zwierzę ==="kitty") ? Meow": "woof"; 

Sekcja 11.2: Przełącznik
Przełączniki porównują wartość wyrażenia z 1 lub większą ilością wartości i wykonują sekcje kodu diﬀerent w oparciu o to porównanie.
var value = 1; switch (wartość) { przypadek 1: console.log('I will always run'); break; przypadek 2: console.log('I will never run'); break; }

Stwierdzenie przerwy "wyłamuje" się z zestawienia przełącznika i zapewnia, że w zestawieniu przełącznika nie zostanie wykonany kolejny kod. W ten sposób definiowane są sekcje, co pozwala użytkownikowi na "przebijanie" przypadków.
Ostrzeżenie: brak instrukcji przerwania lub powrotu dla każdego przypadku oznacza, że program będzie kontynuował ocenę następnego przypadku, nawet jeśli kryteria przypadku nie są spełnione!
switch (wartość) { przypadek 1: console.log('Będę uruchamiał tylko jeśli wartość === 1'); // Tutaj kod "spadnie" i uruchomi kod w przypadku 2 przypadku 2: console.log('Będę uruchamiał jeśli wartość === 1 lub wartość === 2'); break; przypadek 3: console.log('Będę uruchamiał tylko jeśli wartość === 3'); break; }
Ostatni przypadek jest przypadkiem domyślnym. Ten z nich będzie działał, jeśli nie zostały wykonane żadne inne dopasowania.
 
