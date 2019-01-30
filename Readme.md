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
//<body> <h1> //Dodawanie elementu </ h1> </ body>
W naszym JavaScriptu tworzymy nowy znacznik <p> z właściwością textContent i dodajemy go na końcu treści html:
var element = document.createElement ("p"); element.textContent = "Hello, World"; document.body.appendChild (element); // dodaj nowo utworzony element do DOM
To zmieni twój korpus HTML na:
//< body> <h1> Dodawanie elementu </ h1> <p> Hello, World </ p> </ body>
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

Rozdział 4: Uwagi

Sekcja 4.1: Korzystanie z komentarzy
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
 var animal = 'Lion'; switch (animal) {case 'Dog': console.log ("Nie będę biec od zwierzęcia! ==" Pies ""); złamać; case "Cat": console.log ("Nie będę uciekać od zwierzęcia! ==" Cat ""); złamać; default: console.log ("Będę uruchamiany, ponieważ zwierzę nie pasuje do żadnego innego przypadku"); }
Należy zauważyć, że wyrażenie przypadku może być dowolnym rodzajem wyrażenia. Oznacza to, że możesz używać porównań, wywołań funkcji itp. Jako wartości wielkości liter.
function john () {return 'John'; }
function jacob () {return 'Jacob'; }
switch (name) {case john (): // Porównaj nazwę z wartością zwracaną przez john () (name == "John") console.log ('Uruchomę, jeśli name === "John"'); złamać; case 'Ja' + 'ne': // Połącz ciągi razem, a następnie porównaj (name == "Jane") console.log ('Uruchomę, jeśli nazwa === "Jane"'); złamać; case john () + '' + jacob () + 'Jingleheimer Schmidt': console.log ("Jego imię jest równe nazwie!"); złamać; } Wielokrotne kryteria dotyczące przypadków
Ponieważ przypadki "spadają" bez instrukcji "przerwa lub zwrot", możesz użyć tego do utworzenia wielu kryteriów obejmujących:
var x = "c" switch (x) {case "a": case "b": case "c": console.log ("Wybrano a, b lub c."); złamać; case "d": console.log ("Wybrano tylko d."); złamać; default: console.log ("Nie znaleziono żadnego przypadku."); złamać; // przerwa zapobiegawcza w przypadku zmiany kolejności spraw} Sekcja 11.3: Jeśli / Else If / Else Control
W najprostszej postaci warunek if może być użyty w następujący sposób:
var i = 0;
if (i <1) {console.log ("i jest mniejsze niż 1"); }
Warunek i <1 jest oceniany, a jeśli ma wartość true, wykonywany jest poniższy blok. Jeśli wartość jest fałszywa, blok jest pomijany.
Warunek if może zostać rozszerzony o blok else. Warunek jest sprawdzany raz, jak wyżej, a jeśli wynik jest fałszywy, zostanie wykonany blok wtórny (który zostałby pominięty, gdyby warunek był prawdziwy). Przykład:
if (i <1) {console.log ("i jest mniejsze niż 1"); } else {console.log ("nie byłem mniejszy niż 1"); }
Przypuśćmy, że blok else zawiera wyłącznie blok inny (z opcjonalnym blokiem else) podobny do poniższego:
if (i <1) {console.log ("i jest mniejsze niż 1"); } else {if (i <2) {console.log ("i jest mniejsze niż 2"); } else {console.log ("żaden z poprzednich warunków nie był prawdziwy"); }}
Istnieje również inny sposób zapisu, który zmniejsza zagnieżdżanie:
if (i <1) {console.log ("i jest mniejsze niż 1"); } else if (i <2) {console.log ("i jest mniejsze niż 2"); } else {console.log ("żaden z poprzednich warunków nie był prawdziwy");
}
Kilka ważnych przypisów dotyczących powyższych przykładów:
Jeśli którykolwiek z warunków zostanie oceniony jako prawdziwy, żaden inny warunek w tym łańcuchu bloków nie zostanie oceniony, a wszystkie odpowiednie bloki (łącznie z blokiem else) nie zostaną wykonane.
Liczba pozostałych części jest praktycznie nieograniczona. Ostatni przykład powyżej zawiera tylko jeden, ale możesz mieć tyle, ile chcesz.
Warunek wewnątrz instrukcji if może być wszystkim, co można wymusić na wartości logicznej, zobacz temat logiki boolowskiej, aby uzyskać więcej szczegółów;
Drabina if-else-if wychodzi przy pierwszym sukcesie. Oznacza to, że w powyższym przykładzie, jeśli wartość i wynosi 0,5, wówczas wykonywana jest pierwsza gałąź. Jeśli warunki nakładają się, wykonywane są pierwsze kryteria występujące w strumieniu wykonania. Inny warunek, który również może być prawdziwy, jest ignorowany.
Jeśli masz tylko jedną instrukcję, nawiasy klamrowe w tej instrukcji są opcjonalne technicznie, np. Jest to:
jeśli (i <1) console.log ("i jest mniejsze niż 1");
I to też będzie działać:
jeśli (i <1) console.log ("i jest mniejsze niż 1");
Jeśli chcesz wykonać wiele instrukcji wewnątrz bloku if, wówczas nawiasy klamrowe wokół nich są obowiązkowe. Tylko za pomocą wcięcia nie wystarczy. Na przykład poniższy kod:
jeśli (i <1) console.log ("i jest mniejsze niż 1"); console.log ("spowoduje to NIEZALEŻNIE od warunku"); // Ostrzeżenie, patrz tekst!
jest równa:
if (i <1) {console.log ("i jest mniejsze niż 1"); } console.log ("uruchomi to BEZ WZGLĘDU na warunek");
Sekcja 11.4: Strategia
Wzorzec strategii może być w wielu przypadkach użyty w JavaScript w celu zastąpienia instrukcji switch. Jest to szczególnie przydatne, gdy liczba warunków jest dynamiczna lub bardzo duża. Dzięki niemu kod każdego warunku może być niezależny i oddzielnie testowany.
Obiekt strategii jest prostym obiektem o wielu funkcjach, reprezentującym każdy odrębny warunek. Przykład:
const AnimalSays = {pies () {return 'woof'; },
    cat () {return "meow"; },
    lion () {return "ryk"; },
    // ... inne zwierzęta
    default () {return "moo"; }};
Powyższy obiekt może być używany w następujący sposób:
function makeAnimalSpeak (animal) {// Dopasuj zwierzę według typu const speak = AnimalSays [animal] || AnimalSays.default;
console.log (animal + 'says' + speak ()); }
Wyniki:
makeAnimalSpeak ("pies") // => "pies mówi" "makeAnimalSpeak" ("cat") // => "cat mówi" mow "makeAnimalSpeak (" lew ") // => 'lew mówi' ryk 'makeAnimalSpeak (' snake ' ) // => 'snake says moo'
W ostatnim przypadku nasza domyślna funkcja obsługuje wszystkie brakujące zwierzęta. Rozdział 11.5: Używanie || i && krótkie spięcie
Operatory Boolean || and && "zwiąże obwód" i nie oceni drugiego parametru, jeśli pierwsza jest odpowiednio prawdą lub fałszem. Może to być użyte do napisania krótkich warunków, takich jak:
var x = 10
x == 10 && alert ("x to 10") x == 10 || alert ("x to nie 10")

Rozdział 12: Tablice Sekcja 12.1: Przekształcanie obiektów podobnych do macierzy w tablice
Czym są obiekty podobne do tablic?
JavaScript ma "obiekty podobne do macierzy", które są obiektowymi reprezentacjami tablic o właściwości length. Na przykład:
var realArray = ["a", "b", "c"]; var tablicaLike = {0: "a", 1: "b", 2: "c", długość: 3};
Typowymi przykładami obiektów typu Array są obiekty argumentów w funkcjach i obiekty HTMLCollection lub NodeList zwrócone przez metody takie jak document.getElementsByTagName lub document.querySelectorAll.
Jednak jedną kluczową różnicą między tablicami i obiektami podobnymi do macierzy jest to, że obiekty podobne do macierzy dziedziczą z Object.prototype zamiast z Array.prototype. Oznacza to, że obiekty podobne do macierzy nie mają dostępu do typowych metod prototypowych Array, takich jak forEach (), push (), map (), filter () i slice ():
var parent = document.getElementById ('myDropdown'); var desiredOption = parent.querySelector ('option [value = "desired"]'); var domList = parent.children;
domList.indexOf (desiredOption); // Błąd! indexOf nie jest zdefiniowany. domList.forEach (function () {arguments.map (/ * Tutaj tutaj * /) // Błąd! mapa nie jest zdefiniowana.}); // Błąd! forEach nie jest zdefiniowany.
function func () {console.log (argumenty); } func (1, 2, 3); // → [1, 2, 3] Konwertuj obiekty podobne do tablic do tablic w ES6
Array.od: 1.
Version ≥ 6 const arrayLike = {0: 'Value 0', 1: 'Value 1', length: 2}; arrayLike.forEach (value => {/ * Zrób coś * /}); // Błędy const realArray = Array.from (arrayLike); realArray.forEach (value => {/ * Zrób coś * /}); // Prace
dla ... z: 2.
Wersja ≥ 6 var realArray = []; dla (const element z arrayLike) {realArray.append (element); }
Operator rozrzutu: 3.
Wersja ≥ 6 [... arrayLike]
Wartości obiektu: 4.
Wersja ≥ 7 var realArray = Object.values ​​(arrayLike);
Object.keys: 5.
Wersja ≥ 6 var realArray = Object .keys (arrayLike) .map ((key) => arrayLike [key]); Konwertuj obiekty podobne do tablic do tablic w ≤ ES5
Użyj Array.prototype.slice jak poniżej:
var tablicaLike = {0: 'Wartość 0', 1: 'Wartość 1', długość: 2}; var realArray = Array.prototype.slice.call (arrayLike); realArray = [] .slice.call (arrayLike); // Krótsza wersja
realArray.indexOf ("Wartość 1"); // Łał! to działa
Możesz także użyć Function.prototype.call, aby wywołać metody Array.prototype na obiektach podobnych do Array bezpośrednio, bez ich konwertowania:
Wersja ≥ 5.1 var domList = document.querySelectorAll ("# myDropdown opcja");
domList.forEach (function () {// Do stuff}); // Błąd! forEach nie jest zdefiniowany.
Array.prototype.forEach.call (domList, function () {// Do stuff}); // Łał! to działa
Możesz również użyć [] .method.bind (arrayLikeObject), aby wypożyczyć metody tablicowe i przyjrzeć je obiektowi:
Wersja ≥ 5.1 tablica varLike = {0: 'Wartość 0', 1: 'Wartość 1', długość: 2};
arrayLike.forEach (function () {// Do stuff}); // Błąd! forEach nie jest zdefiniowany.
[] .forEach.bind (arrayLike) (function (val) {// Rób rzeczy z val
}); // Łał! to działa Modyfikowanie elementów podczas konwersji
W ES6, podczas korzystania z Array.from, możemy określić funkcję map, która zwraca zmapowaną wartość dla tworzonej nowej tablicy.
Wersja ≥ 6 Array.from (domList, element => element.tagName); // Tworzy tablicę tagName
Zobacz Array są obiekty do szczegółowej analizy. Punkt 12.2: Zmniejszanie wartości
Wersja ≥ 5.1
Metoda reduce () stosuje funkcję względem akumulatora i każdej wartości tablicy (od lewej do prawej), aby zredukować ją do pojedynczej wartości.
Array Suma
Tej metody można użyć do skondensowania wszystkich wartości tablicy w pojedynczej wartości:
[1, 2, 3, 4] .reduce (funkcja (a, b) {return a + b;}); // → 10
Opcjonalny drugi parametr można przekazać do funkcji reduce (). Jego wartość zostanie wykorzystana jako pierwszy argument (określony jako a) dla pierwszego wywołania zwrotnego (wyspecyfikowanego jako funkcja (a, b)).
[2] .reduce (funkcja (a, b) {console.log (a, b); // drukuje: 1 2 return a + b;}, 1); // → 3
Wersja ≥ 5.1 Spłaszczaj tablicę obiektów
Poniższy przykład pokazuje, jak sprowadzić tablicę obiektów do jednego obiektu.
var tablica = [{klucz: 'jeden', wartość: 1}, {klucz: 'dwa', wartość: 2}, {klucz: 'trzy', wartość: 3}]; Wersja ≤ 5.1 array.reduce (function (obj, current) {obj [current.key] = current.value; return obj;}, {});
Wersja ≥ 6 array.reduce ((obj, current) => Obj
ect.assign (obj, {[current.key]: current.value}), {}); Wersja ≥ 7 array.reduce ((obj, current) => ({... obj, [current.key]: current.value}), {});
Zwróć uwagę, że Właściwości Spoczynku / Rozkładu nie ma na liście gotowych propozycji ES2016. Nie jest obsługiwany przez ES2016. Ale możemy użyć babel plugin babel-plugin-transform-object-rest-spread, aby go wspierać.
Wszystkie powyższe przykłady dla Flatten Array dają:
{jeden: 1, dwa: 2, trzy: 3}
Wersja ≥ 5.1 Mapa Używanie skrótu
Jako kolejny przykład użycia parametru wartości początkowej rozważ zadanie wywoływania funkcji na tablicy elementów, zwracając wyniki w nowej tablicy. Ponieważ tablice są zwykłymi wartościami, a łączenie list jest zwykłą funkcją, możemy użyć polecenia "zmniejszyć", aby zebrać listę, co ilustruje następujący przykład:
function map (list, fn) {return list.reduce (function (newList, item) {return newList.concat (fn (element));}, []); }
// Użycie: map ([1, 2, 3], function (n) {return n * n;}); // → [1, 4, 9]
Zauważ, że jest to tylko ilustracja (z parametru wartości początkowej), użyj natywnej mapy do pracy z transformacjami list (zobacz Mapowanie wartości dla szczegółów).
Wersja ≥ 5.1 Znajdź wartość minimalną lub maksymalną
Możemy również użyć akumulatora do śledzenia elementu tablicy. Oto przykład użycia tego do znalezienia wartości min:
var arr = [4, 2, 1, -10, 9]
arr.reduce (function (a, b) {return a <b? a: b}, Infinity); // → -10 Wersja ≥ 6 Znajdź unikalne wartości
Oto przykład, który używa funkcji zmniejszenia, aby zwrócić unikalne liczby do tablicy. Pusta tablica jest przekazywana jako drugi argument i jest przywoływana przez prev.
var arr = [1, 2, 1, 5, 9, 5];
arr.reduce ((prev, number) => {if (prev.indexOf (number) === -1) {prev.push (number);} return prev;}, []); // → [1, 2, 5, 9] Rozdział 12.3: Odwzorowywanie wartości
Często konieczne jest wygenerowanie nowej tablicy na podstawie wartości istniejącej macierzy.
Na przykład, aby wygenerować tablicę długości łańcuchów z tablicy łańcuchów:
Wersja ≥ 5.1 ["jeden", "dwa", "trzy", "cztery"]. Map (funkcja (value, index, arr) {return value.length;}); // → [3, 3, 5, 4] Wersja ≥ 6 ["jeden", "dwa", "trzy", "cztery"]. Map (value => value.length); // → [3, 3, 5, 4]
W tym przykładzie funkcja anonimowa jest dostarczana do funkcji map (), a funkcja map wywoła ją dla każdego elementu w tablicy, podając następujące parametry w następującej kolejności:
Sam element Indeks elementu (0, 1 ...) Cała tablica
Dodatkowo map () zapewnia opcjonalny drugi parametr w celu ustawienia wartości tego w funkcji mapowania. W zależności od środowiska wykonawczego domyślna wartość może się różnić:
W przeglądarce domyślną wartością tego okna jest zawsze:
['jeden', 'dwa']. map (funkcja (wartość, indeks, arr) {console.log (this); // okno (domyślna wartość w przeglądarkach) zwraca value.length;});
Możesz go zmienić na dowolny niestandardowy obiekt, taki jak ten:
['jeden', 'dwa']. map (funkcja (value, index, arr) {console.log (this); // Object {documentation: "randomObject"} return value.length;}, {documentation: 'randomObject "}); Rozdział 12.4: Filtrowanie tablic obiektów
Metoda filter () akceptuje funkcję testową i zwraca nową tablicę zawierającą tylko elementy oryginalnej tablicy, które pomyślnie przeszły test.
// Załóżmy, że chcemy uzyskać liczbę nieparzystą w tablicy: var numbers = [5, 32, 43, 4]; Wersja ≥ 5.1 var odd = numbers.filter (function (n) {return n% 2! == 0;}); Wersja ≥ 6 niech nieparzysta = liczba.filtr (n => n% 2! == 0); // można skrócić do (n => n% 2)
nieparzysty zawierałby następującą tablicę: [5, 43].
Działa również na tablicy obiektów:
var people = [{id: 1, nazwa: "John", wiek: 28}, {id: 2, imię: "Jane", wiek: 31}, {id: 3, imię: "Peter", wiek: 55 }]; Wersja ≥ 5.1 var young = people.filter (function (person) {return person.age <35;}); Wersja ≥ 6 niech młody = ludzie.filtr (osoba => osoba.raga <35);
młody zawierałby następującą tablicę:
[{id: 1, nazwa: "John", wiek: 28}, {id: 2, imię: "Jane", wiek: 31}]
Możesz przeszukiwać całą tablicę pod kątem takiej wartości:
var young = people.filter ((obj) => {var flag = false; Object.values ​​(obj) .forEach ((val) => {if (String (val) .indexOf ("J")> -1) {flag = true; return;}}); if (flag) return obj;});
To zwraca:
[{id: 1, nazwa: "John", wiek: 28}, {id: 2, imię: "Jane", wiek: 31}] 

Sekcja 12.5: Sortowanie tablic
Metoda .sort () sortuje elementy tablicy. Domyślna metoda posortuje tablicę zgodnie z ciągami znaków kodu Unicode. Aby posortować tablicę numerycznie, metoda .sort () musi mieć przekazany do niej parametr compareFunction.
Uwaga: Metoda .sort () jest nieczysta. .sort () będzie sortować tablicę w miejscu, tj. zamiast tworzyć posortowaną kopię oryginalnej tablicy, zmieni kolejność oryginalnej tablicy i zwróci ją.
Sortowanie domyślne
Sortuje tablicę w kolejności UNICODE.
['s', 't', 'a', 34, 'K', 'o',
"v", "E", "r", "2", "4", "o", "W", -1, "-4"]. sort ();
Prowadzi do:
[-1, "-4", "2", 34, "4", "E", "K", "W", "a", "l", "o", "o", "r" , 's', 't', 'v']
Uwaga: Wielkie litery zostały przeniesione nad małymi literami. Tablica nie jest w porządku alfabetycznym, a liczby nie są w porządku liczbowym.
Sortuj alfabetycznie
['s', 't', 'a', 'c', 'K', 'o', 'v', 'E', 'r', 'f', 'l', 'W', ' 2 ',' 1 ']. Sort ((a, b) => {return a.localeCompare (b);});
Prowadzi do:
["1", "2", "a", "c", "E", "f", "K", "l", "o", "r", "s", "t", " v ',' W ']
Uwaga: Powyższy sort spowoduje błąd, jeśli elementy tablicy nie są ciągami. Jeśli wiesz, że tablica może zawierać elementy, które nie są ciągami, użyj bezpiecznej wersji poniżej.
['s', 't', 'a', 'c', 'K', 1, 'v', 'E', 'r', 'f', 'l', 'o', 'W' ] .sort ((a, b) => {return a.toString (). localeCompare (b);});
Sortowanie według długości (najdłuższe pierwsze)
["zebras", "psy", "słonie", "pingwiny"]. sort (funkcja (a, b) {return b.length - a.length;});
Prowadzi do
["słonie", "pingwiny", "zebras", "psy"];
Sortowanie według długości (najkrótsze pierwsze)
["zebras", "psy", "słonie", "pingwiny"]. sort (funkcja (a, b) {return a.length - b.length;});
Prowadzi do
["psy", "zebras", "pingwiny", "słonie"];
Sortowanie numeryczne (rosnąco)
[100, 1000, 10, 10000, 1] .sort (funkcja (a, b) {return a - b;});
Prowadzi do:
[1, 10, 100, 1000, 10000]
Sortowanie numeryczne (malejące)
[100, 1000, 10, 10000, 1] .sort (funkcja (a, b) {return b - a;});
Prowadzi do:
[10000, 1000, 100, 10, 1]
Sortowanie tablicy według liczb parzystych i nieparzystych
[10, 21, 4, 15, 7, 99, 0, 12] .sort (funkcja (a, b) {return (a & 1) - (b & 1) || a - b;});
Prowadzi do:
[0, 4, 10, 12, 7, 15, 21, 99]
Sortowanie według daty (malejąco)
var dates = [nowa data (2007, 11, 10), nowa data (2014, 2, 21),
  nowa data (2009, 6, 11), nowa data (2016, 7, 23)];
date.sort (function (a, b) {if (a> b) return -1; if (a <b) return 1; return 0;});
// obiekty daty mogą również sortować według różnicy // w ten sam sposób, w jaki tablica liczb sortuje date.sort (function (a, b) {return b-a;});
Prowadzi do:
["Wto 23 sierpnia 2016 00:00:00 GMT-0600 (MDT)", "Fri 21 marca 2014 00:00:00 GMT-0600 (MDT)", "Sob 11 lipca 2009 00:00:00 GMT-0600 (MDT) "," poniedziałek 10 2007 00:00:00 GMT-0700 (MST) "] Sekcja 12.6: Iteracja
Tradycyjna pętla for
Tradycyjna pętla for ma trzy składniki:
Inicjalizacja: wykonywana przed uruchomieniem bloku look po raz pierwszy1. Warunek: sprawdza warunek za każdym razem przed wykonaniem bloku pętli i zamyka pętlę, jeśli false2. Uwagi: wykonywane za każdym razem po wykonaniu bloku pętli3.
Te trzy składniki są oddzielone od siebie przez a; symbol. Treść każdego z tych trzech składników jest opcjonalna, co oznacza, że ​​następujące elementy są najbardziej ograniczone do możliwych pętli:
for (;;) {// Rób rzeczy}
Oczywiście będziesz musiał podać if (warunek === true) {break; } lub if (warunek === true) {return; } gdzieś w tej pętli for, aby zatrzymać jej działanie.
Zwykle inicjalizacja służy do zadeklarowania indeksu, warunek jest używany do porównania tego indeksu z wartością minimalną lub maksymalną, a do przemnożenia indeksu używana jest dodatkowa myśl:
dla (var i = 0, długość = 10; i <długość; i ++) {console.log (i); }
Używanie tradycyjnej pętli for do przechodzenia przez macierz
Tradycyjny sposób przechodzenia przez macierz to:
dla (var i = 0, length = myArray.length; i <length; i ++) {
    console.log (myArray [i]); }
Lub, jeśli wolisz pętlę wstecz, wykonaj następujące czynności:
dla (var i = myArray.length - 1; i> -1; i--) {console.log (myArray [i]); }
Istnieje jednak wiele możliwych wariantów, na przykład ta:
for (klucz var = 0, wartość = myArray [klucz], długość = mojaArray.length; klucz <długość; wartość = mojaArray [klucz_ ++]) {console.log (wartość); }
... albo ten ...
var i = 0, length = myArray.length; for (; i <length;) {console.log (myArray [i]); i ++; }
... albo ten:
klucz var = 0, wartość; for (; value = myArray [key ++];) {console.log (wartość); }
To, co działa najlepiej, jest w dużej mierze kwestią zarówno osobistego gustu, jak i konkretnego zastosowania, które stosujesz.
Pamiętaj, że każda z tych odmian jest obsługiwana przez wszystkie przeglądarki, w tym bardzo stare!
Pętla while
Jedną z alternatyw dla pętli for jest pętla while. Aby przechwycić tablicę, możesz to zrobić:
klawisz var = 0; while (value = myArray [key ++]) {console.log (wartość); }
Podobnie jak w przypadku tradycyjnych pętli, pętle są obsługiwane przez nawet najstarsze przeglądarki.
Zwróć też uwagę, że każda pętla while może zostać przepisana jako pętla for. Na przykład powyższa pętla while zachowuje się dokładnie tak samo, jak ta pętla for:
for (klawisz var = 0; value = myArray [key ++];) {console.log (wartość); }
dla w
W JavaScript możesz również:
for (i in myArray) {console.log (myArray [i]); }
Powinno się z tym jednak ostrożnie korzystać
s nie zachowuje się tak samo jak tradycyjna pętla for we wszystkich przypadkach i istnieją potencjalne skutki uboczne, które należy wziąć pod uwagę. Zobacz "Dlaczego używasz" for ... in "w iteracji tablicowej jako zły pomysł? po więcej szczegółów.
dla ...
W ES 6 pętla for-of jest zalecanym sposobem wykonywania iteracji na wartościach tablicy:
Wersja ≥ 6 pozwól myArray = [1, 2, 3, 4]; for (let value of myArray) {let twoValue = wartość * 2; console.log ("2 * wartość to:% d", dwie wartości); }
Poniższy przykład pokazuje różnicę między pętlą for ... a pętlą for ... in:
Wersja ≥ 6 pozwól myArray = [3, 5, 7]; myArray.foo = "cześć";
dla (var i in myArray) {console.log (i); // logs 0, 1, 2, "foo"}
dla (var i of myArray) {console.log (i); // logi 3, 5, 7}
Array.prototype.keys ()
Metodę Array.prototype.keys () można użyć do iteracji nad takimi indeksami:
Wersja ≥ 6 pozwól myArray = [1, 2, 3, 4]; for (let i of myArray.keys ()) {let twoValue = myArray [i] * 2; console.log ("2 * wartość to:% d", dwie wartości); }
Array.prototype.forEach ()
Metoda .forEach (...) jest opcją w ES 5 i nowszych. Jest obsługiwany przez wszystkie nowoczesne przeglądarki, a także Internet Explorer 9 i nowsze.
Wersja ≥ 5 [1, 2, 3, 4] .forEach (funkcja (wartość, indeks, arr) {var twoValue = wartość * 2; console.log ("2 * wartość to:% d", dwie wartości);}) ;
Porównując z tradycyjną pętlą for, nie możemy wyskoczyć z pętli w .forEach (). W takim przypadku użyj pętli for lub użyj częściowej iteracji przedstawionej poniżej.
We wszystkich wersjach JavaScript możliwe jest iterowanie poprzez indeksy tablicy przy użyciu tradycyjnej pętli for-C.
var myArray = [1, 2, 3, 4]; dla (var i = 0; i <myArray.length; ++ i) {var twoValue = myArray [i] * 2; console.log ("2 * wartość to:% d", dwie wartości); }
Możliwe jest również użycie pętli while:
var myArray = [1, 2, 3, 4], i = 0, suma = 0; while (i ++ <myArray.length) {sum + = i; } console.log (suma);
Array.prototype.every
Od wersji ES5, jeśli chcesz przerobić na część tablicy, możesz użyć Array.prototype.every, który iteruje do momentu, aż zwrócony zostanie false:
Wersja ≥ 5 // [] .every () zatrzymuje się, gdy znajdzie fałszywy wynik // w ten sposób ta iteracja zatrzyma się na wartości 7 (od 7% 2! == 0) [2, 4, 7, 9]. Everyry (function (value, index, arr) {console.log (value); return value% 2 === 0; // iteruje aż do znalezienia nieparzystej liczby});
Odpowiednik w dowolnej wersji JavaScript:
var arr = [2, 4, 7, 9]; dla (var i = 0; i <arr.length && (arr [i]% 2! == 0); i ++) {// iteruje aż do znalezienia nieparzystej liczby console.log (arr [i]); }
Array.prototype.some
Array.prototype.some iteruje, aż zwrócimy true:
Wersja ≥ 5 // [] .some zatrzymuje się po znalezieniu fałszywego wyniku // w ten sposób ta iteracja zatrzyma się na wartości 7 (od 7% 2! == 0) [2, 4, 7, 9] .some (function (wartość, indeks, arr) {console.log (wartość); zwracana wartość === 7; // iteruj, dopóki nie znajdziemy wartości 7});
Odpowiednik w dowolnej wersji JavaScript:
Biblioteki
Wreszcie, wiele bibliotek narzędziowych ma również własną odmianę foreach. Trzy z najbardziej popularnych to:
jQuery.each (), w jQuery:
$ .each (myArray, funkcja (klucz, wartość) {console.log (value);});
_.each (), w pliku Underscore.js:
_.each (myArray, function (value, key, myArray) {console.log (value);});
_.forEach (), w Lodash.js:
_.forEach (myArray, function (value, key) {console.log (value);});
Zobacz także następujące pytanie dotyczące SO, w którym duża część tych informacji została pierwotnie opublikowana:
Pętla w tablicy w sekcji JavaScript w sekcji 12.7: Destrukturyzacja tablicy
Wersja ≥ 6
Tablica może zostać zniszczona, gdy jest przypisana do nowej zmiennej.
const triangle = [3, 4, 5]; const [długość, wysokość, przeciwprostokątna] = trójkąt;
długość === 3; // → true height === 4; // → true hypanticuse === 5; // → true
Elementy można pominąć
const [, b, c] = [1, 2, 3, 4];
console.log (b, c); // → 2, 4
Można również użyć operatora odpoczynku
const [b, c, ... xs] = [2, 3, 4, 5]; console.log (b, c, xs); // → 2, 3, [4, 5]
Tablica może również zostać zniszczona, jeśli jest argumentem funkcji.
obszar funkcyjny ([długość, wysokość]) {powrót (długość * wysokość) / 2; }
const triangle = [3, 4, 5];
obszar (trójkąt); // → 6
Zauważ, że trzeci argument nie jest wymieniony w funkcji, ponieważ nie jest potrzebny.
Dowiedz się więcej o destrukcji składni.
Punkt 12.8: Usuwanie duplikatów elementów
Począwszy od wersji ES5.1 można użyć natywnej metody Array.prototype.filter do przechodzenia przez tablicę i pozostawienia tylko tych pozycji, które przekazują daną funkcję zwrotną.
W poniższym przykładzie nasze wywołanie zwrotne sprawdza, czy podana wartość występuje w tablicy. Jeśli tak, jest to duplikat i nie zostanie skopiowany do wynikowej tablicy.
Wersja ≥ 5.1 var uniqueArray = ['a', 1, 'a', 2, '1', 1] .filtr (funkcja (wartość, indeks, self) {return self.indexOf (value) === index;} ); // zwraca ["a", 1, 2, "1"]
Jeśli twoje środowisko obsługuje ES6, możesz również nas
e obiekt Set. Ten obiekt umożliwia przechowywanie unikatowych wartości dowolnego typu, niezależnie od tego, czy są to wartości pierwotne, czy odwołania do obiektów:
Wersja ≥ 6 var uniqueArray = [... new Set (['a', 1, 'a', 2, '1', 1])]; Punkt 12.9: Porównanie tablic
Do prostego porównywania macierzy można użyć string stringów JSON i porównać ciągi wyjściowe:
JSON.stringify (array1) === JSON.stringify (array2)
Uwaga: działa to tylko wtedy, gdy oba obiekty są serializowane i nie zawierają cyklicznych odniesień. Może rzucić TypeError: Konwersja struktury kołowej do JSON
Możesz użyć funkcji rekursywnej, aby porównać tablice.
funkcja compareArrays (array1, array2) {var i, isA1, isA2; isA1 = Array.isArray (tablica1); isA2 = Array.isArray (array2);
 
  if (isA1 !== isA2) {// jest jedną tablicą, a drugą nie? return false; // tak, nie może być takie samo} if (! (isA1 && isA2)) {// Czy obie tablice nie zwracają array1 === array2; // return strict equality} if (array1.length! == array2.length) {// jeśli długości różnią się, to nie mogą być tym samym błędem return; } // iteruj tablice i porównaj je (i = 0; i <array1.length; i + = 1) {
    if (! compareArrays (tablica1 [i], array2 [i])) {// Porównywanie rekurencji elementów z rekursywnie zwraca false; }} return true; // musi być równy}
OSTRZEŻENIE: Używanie powyższej funkcji jest niebezpieczne i powinno być opakowane w próbę catch, jeśli podejrzewasz, że istnieje szansa, że ​​tablica ma odniesienia cykliczne (odniesienie do tablicy zawierającej odniesienie do niej)
a = [0]; a [1] = a; b = [0, a]; compareArrays (a, b); // throws RangeError: Przekroczono maksymalny rozmiar stosu wywołań
Uwaga: Funkcja używa operatora ścisłej równości === do porównywania elementów nieszablonowych {a: 0} === {a: 0} jest fałszywe

Sekcja 12.10: Odwracanie tablic
.reverse służy do odwrócenia kolejności elementów wewnątrz tablicy.
Przykład dla .reverse:
[1, 2, 3, 4] .reverse ();
Prowadzi do:
[4, 3, 2, 1]
Uwaga: Zwróć uwagę, że .reverse (Array.prototype.reverse) spowoduje odwrócenie tablicy w miejscu. Zamiast zwracania odwróconej kopii, zwróci tę samą tablicę, odwróconą.
var arr1 = [11, 22, 33]; var arr2 = arr1.reverse (); console.log (arr2); // [33, 22, 11] console.log (arr1); // [33, 22, 11]
Możesz również odwrócić tablicę "głęboko" przez:
function deepReverse (arr) {arr.reverse (). forEach (elem => {if (Array.isArray (elem)) {deepReverse (elem);}}); return arr; }
Przykład deepReverse:
var arr = [1, 2, 3, [1, 2, 3, ["a", "b", "c"]]];
deepReverse (arr);
Prowadzi do:
arr // -> [[['c', 'b', 'a'], 3, 2, 1], 3, 2, 1] Rozdział 12.11: Płytkie klonowanie tablicy
Czasami musisz pracować z tablicą, upewniając się, że nie modyfikujesz oryginału. Zamiast metody klonowania tablice mają metodę wycinania, która umożliwia wykonanie płytkiej kopii dowolnej części tablicy. Pamiętaj, że to tylko klony pierwszego poziomu. Działa to dobrze z typami pierwotnymi, takimi jak liczby i łańcuchy, ale nie obiektami.
Aby płytko klonować tablicę (tj. Mieć nową instancję tablicy, ale z tymi samymi elementami), można użyć następującej jednolinijki:
var clone = arrayToClone.slice ();
Wywołuje to wbudowaną metodę JavaScript Array.prototype.slice. Jeśli przekazujesz argumenty do wycinania, możesz uzyskać bardziej skomplikowane zachowania, które tworzą płytkie klony tylko części tablicy, ale dla naszych celów samo wywołanie slice () stworzy płytką kopię całej tablicy.
Wszystkie metody używane do konwertowania macierzy jak obiektów do tablicy mają zastosowanie do klonowania tablicy:
Wersja ≥ 6 arrayToClone = [1, 2, 3, 4, 5]; clone1 = Array.from (arrayToClone); clone2 = Array.of (... arrayToClone); clone3 = [... arrayToClone] // najkrótsza wersja Version ≤ 5.1 arrayToClone = [1, 2, 3, 4, 5]; clone1 = Array.prototype.slice.call (arrayToClone); clone2 = [] .slice.call (arrayToClone); Sekcja 12.12: Łączenie tablic
Dwie tablice
var array1 = [1, 2]; var array2 = [3, 4, 5]; Wersja ≥ 3 tablice var3 = tablica1.concat (tablica2); // zwraca nową tablicę Version ≥ 6 var array3 = [... array1, ... array2]
Wyniki w nowej tablicy:
[1, 2, 3, 4, 5]
Wiele tablic
var tablica1 = ["a", "b"], tablica2 = ["c", "d"], tablica3 = ["e", "f"], tablica4 = ["g", "h"];
Wersja ≥ 3
Podaj więcej argumentów tablicowych w tablicy array.concat ()
var arrConc = array1.concat (array2, array3, array4); Wersja ≥ 6
Podaj więcej argumentów []
var arrConc = [... tablica1, ... tablica2, ... tablica3, ... tablica4]
Wyniki w nowej tablicy:
["a", "b", "c", "d", "e", "f", "g", "h"]
Bez kopiowania pierwszej tablicy
var longArray = [1, 2, 3, 4, 5, 6, 7, 8], shortArray = [9, 10]; Wersja ≥ 3
Podaj elementy shortArray jako parametry do wypchnięcia przy użyciu Function.prototype.apply
longArray.push.apply (longArray, shortArray); Wersja ≥ 6
Użyj operatora rozprzestrzeniania, aby przekazać elementy shortArray jako oddzielne argumenty do przekazania
longArray.push (... shortArray)
Wartość longArray jest teraz:
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
Zauważ, że jeśli druga tablica jest zbyt długa (> 100 000 wpisów), ty
może uzyskać błąd przepełnienia stosu (z powodu sposobu działania działa). Aby być bezpiecznym, możesz zamiast tego iterować:
shortArray.forEach (function (elem) {longArray.push (elem);});
Wartości tablicowe i nieszablonowe
var array = ["a", "b"]; Wersja ≥ 3 var arrConc = array.concat ("c", "d"); Wersja ≥ 6 var arrConc = [... array, "c", "d"]
Wyniki w nowej tablicy:
["a", "b", "c", "d"]
Możesz także mieszać tablice z tablicami innymi niż tablice
var arr1 = ["a", "b"]; var arr2 = ["e", "f"];
var arrConc = arr1.concat ("c", "d", arr2);
Wyniki w nowej tablicy:
["a", "b", "c", "d", "e", "f"] 

Sekcja 12.13: Scal dwie tablice jako parę wartości klucza
Kiedy mamy dwie osobne tablice i chcemy utworzyć parę wartości klucza z tej dwóch tablic, możemy użyć funkcji zmniejszania tablicy jak poniżej:
var columns = ["Date", "Number", "Size", "Location", "Age"]; var rows = ["2001", "5", "Big", "Sydney", "25"]; var result = rows.reduce (funkcja (wynik, pole, indeks) {wynik [kolumny [indeks]] = pole, wynik powrotu;}, {})
console.log (wynik);
Wydajność:
{Data: "2001", Numer: "5", Rozmiar: "Duże", Lokalizacja: "Sydney", Wiek: "25"} Punkt 12.14: Rozkład / rozkład szyku
Operator rozrzutu Wersja ≥ 6
W ES6 możesz używać spreadów do rozdzielania poszczególnych elementów na składnię rozdzielaną przecinkami:
niech arr = [1, 2, 3, ... [4, 5, 6]]; // [1, 2, 3, 4, 5, 6]
// w ES <6, powyższe operacje są równoważne arr = [1, 2, 3]; arr.push (4, 5, 6);
Operator rozdzielający działa również na ciągi, oddzielając każdy indywidualny znak na nowy element łańcucha. Dlatego, używając funkcji tablicowej do konwersji tych liczb na liczby całkowite, tablica utworzona powyżej jest równoważna poniższej:
niech arr = [1, 2, 3, ... [... "456"]. map (x => parseInt (x))]; // [1, 2, 3, 4, 5, 6]
Lub, używając pojedynczego ciągu znaków, można to uprościć do:
niech arr = [... "123456"]. map (x => parseInt (x)); // [1, 2, 3, 4, 5, 6]
Jeśli mapowanie nie zostanie wykonane, wówczas:
niech arr = [... "123456"]; // ["1", "2", "3", "4", "5", "6"]
Operator rozprzestrzeniania może również służyć do rozprzestrzeniania argumentów w funkcji:
function myFunction (a, b, c) {} let args = [0, 1, 2];
myFunction (... args);
// w ES <6, byłby to odpowiednik: myFunction.apply (null, args); Operator odpoczynku
Operator odpoczynku robi przeciwieństwo operatora rozprzestrzeniania poprzez koalescencję kilku elementów w jeden
[a, b, ... rest] = [1, 2, 3, 4, 5, 6]; // reszta jest przypisana [3, 4, 5, 6]
Zbierz argumenty funkcji:
function myFunction (a, b, ... rest) {console.log (reszta); }
myFunction (0, 1, 2, 3, 4, 5, 6); // rest to [2, 3, 4, 5, 6] Rozdział 12.15: Filtrowanie wartości
Metoda filter () tworzy tablicę wypełnioną wszystkimi elementami tablicy, które przechodzą test dostarczony jako funkcja.
Wersja ≥ 5.1 [1, 2, 3, 4, 5] .filtr (funkcja (wartość, indeks, arr) {wartość powrotu> 2;}); Wersja ≥ 6 [1, 2, 3, 4, 5] .filtr (wartość => wartość> 2);
Wyniki w nowej tablicy:
[3, 4, 5] Filtruj wartości falsjowe Wersja ≥ 5.1 zmienione filtrowane = [0, niezdefiniowane, {}, puste, "", prawda, 5] .filtr (Boolean);
Ponieważ Boolean jest natywną funkcją / konstruktorem JavaScript, który pobiera [jeden opcjonalny parametr], a metoda filtru przyjmuje również funkcję i przekazuje mu bieżący element tablicy jako parametr, można go odczytać w następujący sposób:
Boolean (0) zwraca false1. Boolean (undefined) zwraca wartość false2. Boolean ({}) zwraca wartość true, co oznacza, że ​​należy ją przekazać do zwróconej tablicy3. Boolean (null) zwraca false4. Boolean ('') zwraca false5. Boolean (true) zwraca wartość true, co oznacza, że należy ją przekazać do zwróconej tablicy6. Boolean (5) zwraca wartość true, co oznacza, że ​​należy ją przekazać do zwróconej tablicy7.
więc ogólny proces zakończy się
[{}, prawda, 5]
Kolejny prosty przykład
Ten przykład wykorzystuje tę samą koncepcję przekazywania funkcji, która przyjmuje jeden argument
Uruchomi się wersja ≥ 5.1WithLetterA (str) {if (str && str [0] .toLowerCase () == 'a') {return true} return false; }
var str = 'Ponieważ Boolean jest natywną funkcją / konstruktorem javascript, który pobiera [jeden opcjonalny parametr], a metoda filtru przyjmuje również funkcję i przekazuje mu bieżący element tablicy jako parametr, można go odczytać w następujący sposób: "; var strArray = str.split (""); var wordsStartsWithA = strArray.filter (startsWithLetterA); // ["a", "i", "również", "a", "i", "tablica", "jako"] Rozdział 12.16: Wyszukiwanie tablicy
Zalecanym sposobem (od wersji ES5) jest użycie Array.prototype.
let people = [{name: "bob"}, {nazwa: "john"}];
niech bob = people.find (person => person.name === "bob");
// Lub bardziej szczegółowe niech bob = people.find (function (person) {return person.name === "bob";});
W dowolnej wersji JavaScript można również użyć standardowej pętli for:
dla (var i = 0; i <people.length; i ++) {if (people [i] .name === "bob") {break; // znaleźliśmy boba}}
FindIndex
Metoda fi ndIndex () zwraca indeks w tablicy, jeśli element w tablicy spełnia zapewnioną funkcję testowania. W przeciwnym razie zwracane jest -1.
array = [{wartość: 1}, {wartość: 2}, {wartość: 3}, {wartość
e: 4}, {wartość: 5}
]; var index = array.findIndex (item => item.value === 3); // 2 var index = array.findIndex (item => item.value === 12); // -1 

Sekcja 12.17: Konwertuj ciąg na tablicę
Metoda .split () dzieli ciąg znaków na tablicę podłańcuchów. Domyślnie .split () przerwie łańcuch na podciągi na spacje (""), co jest równoważne wywołaniu .split ("").
Parametr przekazany do .split () określa znak lub wyrażenie regularne, które ma być użyte do podziału ciągu znaków.
Aby podzielić ciąg znaków na wywołanie tablicy .split z pustym ciągiem znaków (""). Ważna uwaga: działa to tylko wtedy, gdy wszystkie twoje postacie znajdują się w niższym zakresie znaków Unicode, który obejmuje większość języków angielskich i większości europejskich. W przypadku języków wymagających 3 i 4 bajtowych znaków Unicode, slice ("") rozdzieli je.
var strArray = "StackOverflow" .split (""); // strArray = ["S", "t", "a", "c", "k", "O", "v", "e", "r", "f", "l", " o "," w "] Wersja ≥ 6
Za pomocą operatora rozprzestrzeniania (...) konwertować ciąg znaków do tablicy.
var strArray = [... "niebo jest niebieskie"]; // strArray = ["s", "k", "y", "", "i", "s", "", "b", "l", "u", "e"] Rozdział 12.18: Usuwanie elementów z tablicy
Przesunięcie
Użyj .shift, aby usunąć pierwszy element tablicy.
Na przykład:
var array = [1, 2, 3, 4]; array.shift ();
tablica wyników:
[2, 3, 4]
Muzyka pop
Dalej .pop służy do usuwania ostatniego elementu z tablicy.
Na przykład:
var array = [1, 2, 3]; array.pop ();
tablica wyników:
[1, 2]
Obie metody zwracają usunięty element;
Splatać
Użyj .splice (), aby usunąć szereg elementów z tablicy. Funkcja .splice () akceptuje dwa parametry, indeks początkowy i opcjonalną liczbę elementów do usunięcia. Jeśli drugi parametr zostanie pominięty, funkcja .splice () usunie wszystkie elementy z indeksu początkowego przez koniec tablicy.
Na przykład:
var array = [1, 2, 3, 4]; array.splice (1, 2);
pozostawia tablicę zawierającą:
[1, 4]
Zwrot tablicy array.splice () jest nową tablicą zawierającą usunięte elementy. Dla powyższego przykładu, zwrot byłby następujący:
[2, 3]
Zatem pominięcie drugiego parametru skutecznie dzieli tablicę na dwie tablice, z oryginalnym zakończeniem przed wyspecyfikowanym indeksem:
var array = [1, 2, 3, 4]; array.splice (2);
... pozostawia tablicę zawierającą [1, 2] i zwraca [3, 4].
Kasować
Użyj delete, aby usunąć element z tablicy bez zmiany długości tablicy:
var array = [1, 2, 3, 4, 5]; console.log (array.length); // 5 usuń tablicę [2]; console.log (tablica); // [1, 2, niezdefiniowane, 4, 5] console.log (array.length); // 5
Array.prototype.length
Przypisanie wartości do długości tablicy zmienia długość na podaną wartość. Jeśli nowa wartość jest mniejsza niż długość tablicy, elementy zostaną usunięte z końca wartości.
array = [1, 2, 3, 4, 5]; array.length = 2; console.log (tablica); // [1, 2] 

Sekcja 12.19: Usuwanie wszystkich elementów
var arr = [1, 2, 3, 4]; Metoda 1
Tworzy nową tablicę i zastępuje istniejące odniesienie do tablicy nową.
arr = [];
Należy zachować ostrożność, ponieważ nie spowoduje to usunięcia żadnych elementów z oryginalnej tablicy. Tablica mogła zostać zamknięta po przejściu do funkcji. Tablica pozostanie w pamięci przez całe życie tej funkcji, choć możesz tego nie wiedzieć. Jest to powszechne źródło wycieków pamięci.
Przykład wycieku pamięci wynikającego ze złego wyczyszczenia tablicy:
var count = 0;
function addListener (arr) {// arr jest zamknięty przez var b = document.body.querySelector ("# foo" + (count ++)); b.addEventListener ("click", funkcja (e) {// to odwołanie do funkcji utrzymuje // aktualny czas zamknięcia, gdy // zdarzenie jest aktywne // zrobić coś, ale nie potrzebuje arr}); }
arr = ["big data"]; var i = 100; while (i> 0) {addListener (arr); // tablica jest przekazywana do funkcji arr = []; // usuwa odwołanie, oryginalna tablica pozostaje array.push ("niektóre duże dane"); // przydzielono więcej pamięci i--; } // istnieje teraz 100 tablic zamkniętych, każda odwołująca się do innej tablicy // nie usunięto pojedynczego elementu
Aby zapobiec ryzyku wycieku pamięci, użyj jednej z poniższych 2 metod, aby opróżnić tablicę w pętli while w powyższym przykładzie.
Metoda 2
Ustawienie właściwości length powoduje usunięcie całego elementu tablicy z nowej długości tablicy do starej długości tablicy. Jest to najbardziej efektywny sposób usuwania i dereferencji wszystkich elementów w tablicy. Zachowuje odniesienie do oryginalnej tablicy
arr.length = 0; Metoda 3
Podobne do metody 2, ale zwraca nową tablicę zawierającą usunięte elementy. Jeśli nie potrzebujesz tych elementów, ta metoda jest niewystarczająca, ponieważ nowa tablica jest nadal tworzona tylko po to, aby zostać natychmiast dereferencjonowana.
arr.splice (0); // nie powinno być używane, jeśli nie chcesz usunąć usuniętych elementów // używaj tej metody, jeśli wykonasz następujące polecenie keepArr = arr.splice (0); // opróżnia tablicę i tworzy nową tablicę zawierającą // usunięte elementy


Punkt 12.20: Znajdowanie minimalnego lub maksymalnego elementu
Jeśli twoja tablica lub obiekt podobny do tablicy ma wartości numeryczne, to znaczy, jeśli wszystkie jego elementy są liczbami, możesz użyć Math.min.apply lub Math.max.apply, przekazując wartość null jako pierwszy argument, a twoja tablica jako druga.
var myArray = [1, 2, 3, 4];
Math.min.apply (null, myArray); // 1
Math.max.apply (null, myArray); // 4 Wersja ≥ 6
W ES6 możesz użyć operatora ... do rozłożenia tablicy i podjęcia minimalnego lub maksymalnego elementu.
var myArray = [1, 2, 3, 4, 99, 20];
var maxValue = Math.max (... myArray); // 99 var minValue = Math.min (... myArray); // 1
W poniższym przykładzie użyto pętli for:
var maxValue = myArray [0]; dla (var i = 1; i <myArray.length; i ++) {var currentValue = myArray [i]; if (currentValue> maxValue) {maxValue = currentValue; }} Wersja ≥ 5.1
W poniższym przykładzie użyto metody Array.prototype.reduce () w celu znalezienia minimum lub maksimum:
var myArray = [1, 2, 3, 4];
myArray.reduce (function (a, b) {return Math.min (a, b);}); // 1
myArray.reduce (funkcja (a, b) {return Math.max (a, b);}); // 4 Wersja ≥ 6
lub użycie funkcji strzałek:
myArray.reduce ((a, b) => Math.min (a, b)); // 1 myArray.reduce ((a, b) => Math.max (a, b)); // 4 Wersja ≥ 5.1
Aby uogólnić wersję, musielibyśmy przekazać wartość początkową, aby pokryć pusty przypadek listy:
redufunction myMax (array) {return array.reduce (function (maxSoFar, element) {return Math.max (maxSoFar, element);}, -Infinity); }
myMax ([3, 5]); // 5 myMax ([]); // -Infinity Math.max.apply (null, []); // -Infinity
Aby uzyskać szczegółowe informacje na temat prawidłowego używania opcji zmniejszenia, zobacz Pomniejszanie wartości.

Sekcja 12.21: Inicjalizacja standardowych tablic
Istnieje wiele sposobów tworzenia tablic. Najczęstsze są użycie literałów tablicowych lub konstruktora Array:
var arr = [1, 2, 3, 4]; var arr2 = new Array (1, 2, 3, 4);
Jeśli konstruktor Array jest używany bez argumentów, tworzona jest pusta tablica.
var arr3 = new Array ();
wyniki w:
[]
Zauważ, że jeśli jest używany z dokładnie jednym argumentem, a argumentem jest liczba, zamiast tego zostanie utworzona tablica o tejdługości ze wszystkimi niezdefiniowanymi wartościami:
samejvar arr4 = new Array (4);
wyniki w:
[niezdefiniowane, niezdefiniowane, niezdefiniowane, niezdefiniowane]
To nie ma zastosowania, jeśli pojedynczy argument jest:
nieliczbowyvar arr5 = new Array ("foo");
wyniki w:
["foo"] Wersja ≥ 6
Podobnie do literału tablicowego, Array.of może być użyty do stworzenia nowej instancji Array z uwzględnieniem kilku argumentów:
Array.of (21, "Hello", "World");
wyniki w:
[21, "Hello", "World"]
W przeciwieństwie do konstruktora Array, utworzenie tablicy z pojedynczą liczbą, taką jak Array.of (23), utworzy nową tablicę [23], a nie Array z długość 23.
Innym sposobem utworzenia i zainicjowania tablicy będzie Array.od
var newArray = Array.from ({length: 5}, (_, index) => Math.pow (index, 4));
będzie wynik:
[0, 1, 16, 81, 256] 

Sekcja 12.22: Łączenie elementów tablicy w łańcuchu
Aby połączyć wszystkie elementy tablicy w łańcuch, możesz użyć metody join:
console.log (["Hello", "", "świat"]. join ("")); // "Witaj świecie"
console.log ([1, 800, 555, 1234] .join ("-")); // "1-800-555-1234"
Jak widać w drugim wierszu, elementy, które nie są ciągami, zostaną najpierw przekonwertowane. Rozdział 12.23: Usuwanie / dodawanie elementów za pomocą splice ()
Metoda splice () może być używana do usuwania elementów z tablicy. W tym przykładzie usuwamy pierwsze 3 z tablicy.
var values ​​= [1, 2, 3, 4, 5, 3]; var i = values.indexOf (3); if (i> = 0) {values.splice (i, 1); } // [1, 2, 4, 5, 3]
Metoda splice () może być również używana do dodawania elementów do tablicy. W tym przykładzie wstawimy liczby 6, 7 i 8 na końcu tablicy.
var values ​​= [1, 2, 4, 5, 3]; var i = values.length + 1; values.splice (i, 0, 6, 7, 8); // [1, 2, 4, 5, 3, 6, 7, 8]
Pierwszym argumentem metody splice () jest indeks do usuwania / wstawiania elementów. Drugi argument to liczba elementów do usunięcia. Trzeci argument i dalej to wartości wstawiane do tablicy. Sekcja 12.24: Metoda entries () Metoda
entries () zwraca nowy obiekt Iterator tablicy, który zawiera pary klucz / wartość dla każdego indeksu w tablicy.
Wersja ≥ 6 liter var = ["a", "b", "c"];
dla (const [index, element] letters. centries ()) {console.log (index, element); }
result
0 "a" 1 "b" 2 "c"
Uwaga: Ta metoda nie jest obsługiwana w przeglądarce Internet Explorer.
Fragmenty tej zawartości z Array.prototype.entries autorstwa Mozilla Contributors objęte licencją CC-by-SA 2.5 

Sekcja 12.25: Usuwanie wartości z tablicy
Gdy potrzebujesz usunąć konkretną wartość z tablicy, możesz użyć poniższej jednolinijki do utworzenia tablica kopiowania bez podanej wartości:
array.filter (function (val) {return val! == to_remove;});
Lub jeśli chcesz zmienić samą tablicę bez tworzenia kopii (na przykład, jeśli napiszesz funkcję, która pobiera tablicę jako funkcję i manipulujesz nią), możesz użyć tego fragmentu:
while ( index = tablica.indexOf (3)! == -1) {tablica.splice (indeks, 1); }
A jeśli chcesz usunąć tylko pierwszą znalezioną wartość, usuń pętlę while:
var index = array.indexOf (to_remove); if (index! == -1) {tablica.splice (indeks, 1); } Rozdział 12.26: Spłaszczanie tablicTablice
2wymiarowe Version ≥ 6
W ES6 możemy rozwinąć tablicę przez operatora rozprzestrzeniania ...:
function flattenES6 (arr) {return [] .concat (... arr); }
var arrL1 = [1, 2, [3, 4]]; console.log (flattenES6 (arrL1)); // [1, 2, 3, 4] Wersja ≥ 5
W ES5 możemy to osiągnąć przez .apply ():
function flatten (arr) {return [] .concat.apply ([], arr); }
var arrL1 = [1, 2, [3, 4]]; console.log (spłaszczyć (arrL1)); // [1, 2, 3, 4] Tablice o wyższych wymiarach
Biorąc pod uwagę głęboko zagnieżdżoną tablicę, tak więc
var deeplyNested = [4, [5,6, [7,8], 9]];
Można go użyć z tą magiczną konsolą.log
(String (deeplyNested) .split (','). Map (Number); # => [4,5,6,7,8,9]
Lub
const flatten = deepoldNested. toString (). split (','). map (Number) console.log (flatten); # => [4,5,6,7,8,9]
Obie powyższe metody działają tylko wtedy, gdy tworzona jest tablica . wyłącznie z liczb a wielowymiarowa tablica obiektów nie można FL attened tą metodą12.27.
Sekcja  szt Dołącz / prepend do array
unshift
Zastosowanie .unshift aby dodać jeden lub więcej elementów w początek tablicy,
na przykład:
var tablica = [3, 4, 5, 6]; array.unshift (1, 2),
tablica wyniki:
[1, 2, 3, 4, 5, 6]
Push
Dalej. push służy do dodawania elementów po ostatniej aktualnie istniejącej pozycji,
na przykład:
tablica var = [1, 2, 3]; array.push (4, 5, 6),
tablica wyników:
[1, 2, 3, 4 , 5, 6]
Obie metody zwracają nową długość tablicy.

Sekcja 12.28: Klucze i wartości obiektów do tablicy
var object = {key1: 10, key2: 3, key3: 40, key4: 20};
var array = []; dla (var ludzie w obiekcie) {array.push ([ludzie, obiekt [ludzie]]); }
Teraz tablica to
[["klucz1", 10], ["klucz2", 3], ["klucz3", 40], ["klucz4", 20]]

Rozdział 12.29: Logiczne połączenie wartości
Wersja ≥ 5.1
.some i .every pozwala na logiczne powiązanie wartości Array.
Podczas gdy .some łączy wartości zwracane z OR, .every łączy je z AND.
Przykłady dla .some
[false, false] .some (function (value) {return value;}); // Wynik: false
[false, true] .some (function (value) {return value;}); // Wynik: true
[true, true] .some (function (value) {return value;}); // Wynik: true
I przykłady dla .every
[false, false] .every (function (value) {return value;}); // Wynik: false
[false, true] .every (function (value) {return value;}); // Wynik: false
[true, true] .every (function (value) {return value;}); // Wynik: true Punkt 12.30: Sprawdzanie, czy obiekt jest
tablicą Array.isArray (obj) zwraca wartość true, jeśli obiekt jest tablicą, w przeciwnym wypadku wartość false.
Array.isArray ([]) // true Array.isArray ([1, 2, 3]) // true Array.isArray ({}) // false Array.isArray (1) // false
W większości przypadków można wykonać instanceof aby sprawdzić, czy obiekt jest tablicą.
[] instanceof Array; // true {} instanceof Array; // false
Array.isArray ma tę przewagę nad wykorzystaniem sprawdzania instancji, że nadal zwróci true, nawet jeśli prototyp tablicy został zmieniony i zwróci wartość false, jeśli prototyp bez tablic został zmieniony na Array
var arr = []; Object.setPrototypeOf (arr, null); Array.isArray (arr); // true arr instanceof Array; // false 

Sekcja 12.31: Wstawianie elementu do tablicy w określonym indeksie
Proste wstawienie elementu można wykonać za pomocą metody:
Array.prototype.splicearr.splice (indeks, 0, element);
Bardziej zaawansowany wariant z wieloma argumentami i obsługą łańcucha:
/ * Składnia: array.insert (index, value1, value2, ..., valueN) * /
Array.prototype.insert = function (index) {this.splice.apply (this , [index, 0] .concat (Array.prototype.slice.call (argumenty, 1))); zwróć to; };
["a", "b", "c", "d"]. insert (2, "X", "Y", "Z"). slice (1, 6); // ["b", "X", "Y", "Z", "c"]
A także z łączeniem argumentów tablicowych i obsługą łańcuchów:
/ * Składnia: array.insert (index, value1, value2, .. ., valueN) * /
Array.prototype.insert = function (index) {index = Math.min (index, this.length); arguments.length> 1 && this.splice.apply (this, [index, 0] .concat ([]. pop.call (arguments))) && this.insert.apply (this, arguments); zwróć to; };
["a", "b", "c", "d"]. insert (2, "V", ["W", "X", "Y"], "Z") .łącz ("-" ); // "abVWXYZcd" Rozdział 12.32: Sortowanie wielowymiarowych tablic
Biorąc pod uwagę tablicę
var array = [["klucz1", 10], ["klucz2", 3], ["klucz3", 40], ["klucz4", 20] ];
Możesz sortować sortowanie według numeru (drugi indeks)
array.sort (funkcja (a, b) {return a [1] - b [1];})
Wersja ≥ 6 tablic .sort ((a, b) => a [1] - b [1]);
To wyświetli
[[klucz2 ", 3], [" klucz1 ", 10], [" klucz4 ", 20], [" klucz3 ", 40]]
Należy pamiętać, że metoda sortowania działa na macierzy w miejscu. Zmienia tablicę. Większość innych metod tablicowych zwraca nową tablicę, pozostawiając pierwotną nienaruszoną. Jest to szczególnie ważne, jeśli korzystasz z funkcjonalnego stylu programowania i oczekujesz, że funkcje nie będą mieć efektów ubocznych. Sekcja 12.33: Testowanie wszystkich elementów tablicy pod kątem równości
Metoda .every sprawdza, czy wszystkie elementy tablicowe przechodzą zapewniony test predykatów.
Aby przetestować wszystkie obiekty pod kątem równości, można użyć następujących fragmentów kodu.
[1, 2, 1]. Everyry (funkcja (element, i, list) {return item === list [0];}); // false [1, 1, 1] .every (function (item, i, list) {return item === list [0];}); // true Wersja ≥ 6 [1, 1, 1]. everyry ((pozycja, i, lista) => pozycja === lista [0]); // true
Poniższe fragmenty kodu testują równość właściwości
niech dane = [{nazwa: "alicja", id: 111}, {nazwa: "alicja", id: 222}];
data.every (function (element, i, list) {return item === list [0];}); // false data.every (function (element, i, list) {return item.name === list [0] .name;}); // true Version ≥ 6 data.every ((pozycja, i, lista) => item.name === lista [0] .name); // true Sekcja 12.34: Kopiowanie części tablicy
Metoda slice () zwraca kopię części tablicy.
Trwa dwa parametry arr.slice ([rozpocząć [, end]]):
zaczynają
indeksu od zera, która na początku ekstrakcji.
end
Zero-based index, czyli koniec ekstrakcji, cięcie do tego indeksu, ale nie jest uwzględnione.
Jeśli koniec jest liczbą ujemną, end = arr.length + end.
Przykład 1
// Załóżmy, że mamy tablicę alfabetów var arr = ["a", "b", "c", "d" ...];
// Chcę tablicy pierwszych dwóch alfabetów var newArr = arr.slice (0, 2); // newArr === ["a", "b"] Przykład 2 // Powiedzmy, że mamy tę tablicę liczb // i nie wiem, że to koniec var arr = [0, 1, 2, 3, 4 , 5, 6, 7, 8, 9 ...];
// Chcę wyciąć tę tablicę zaczynając od // liczba 5 na jej koniec var newArr = arr.slice (4); // newArr === [5, 6, 7, 8, 9 ...]
Rozdział 13: Obiekty
Właściwość Opis value Wartość do przypisania do właściwości. writable Czy wartość nieruchomości może zostać zmieniona czy nie. enumerable Określa, czy właściwość zostanie wyliczona w for w pętli, czy nie. konfigurowalne Czy możliwe będzie ponowne określenie deskryptora właściwości, czy nie. get Funkcja, która zostanie wywołana, która zwróci wartość właściwości. set Funkcja, która ma zostać wywołana, gdy właściwość ma przypisaną wartość. Sekcja 13.1: Płytkie klonowanie
Wersja ≥ 6
Funkcja Object.assign () ES6 może być używana do kopiowania wszystkich przeliczalnych właściwości z istniejącej instancji obiektu do nowej.
const existing = {a: 1, b: 2, c: 3};
const clone = Object.assign ({}, existing);
Obejmuje to właściwości Symbol oprócz String.
Zatrzymywanie obiektów / rozkładanie spreadu, które jest obecnie propozycją etapu 3, zapewnia jeszcze prostszy sposób tworzenia płytkich klonów instancji Object:
const existing = {a: 1, b: 2, c: 3};
const {... clone} = istniejący;
Jeśli potrzebujesz obsługi starszych wersji JavaScript, najbardziej kompatybilnym sposobem klonowania obiektu jest ręczne iterowanie po jego właściwościach i filtrowanie dziedziczonych obiektów przy użyciu metody .hasOwnProperty ().
var existing = {a: 1, b: 2, c: 3};
var clone = {}; dla (var prop w istniejącym) {if (existing.hasOwnProperty (prop)) {clone [prop] = existing [prop]; }} Rozdział 13.2: Object.freeze
Wersja ≥ 5
Object.freeze czyni obiekt niezmiennym, zapobiegając dodawaniu nowych właściwości, usuwaniu istniejących właściwości i modyfikacji możliwości przeliczania, kon fi gurowalności i zdolności do zapisywania istniejących właściwości. Zapobiega to również zmianie wartości istniejących właściwości. Jednak nie działa rekursywnie, co oznacza, że ​​obiekty podrzędne nie są automatycznie zamrożone i mogą ulec zmianie.
Operacje następujące po zamrożeniu nie powiedzie się po cichu, chyba że kod działa w trybie ścisłym. Jeśli kod jest w trybie ścisłym
, zostanie wygenerowany TypeError.
var obj = {foo: 'foo', bar: [1, 2, 3], baz: {foo: 'zagnieżdżony-foo'}};
Object.freeze (obj);
// Nie można dodać nowych właściwości obj.newProperty = true;
// Nie można modyfikować istniejących wartości lub ich deskryptorów: obj.foo = 'not foo'; Object.defineProperty (obj, 'foo', {writable: true});
// Nie można usunąć istniejących właściwości delete obj.foo;
// Zagnieżdżone obiekty nie są zamrożone obj.bar.push (4); obj.baz.foo = 'new foo'; 

Sekcja 13.3: Klonowanie obiektów
Gdy chcesz kompletną kopię obiektu (np. Właściwości obiektu i wartości wewnątrz tych właściwości, itp.), Nazywa się to głębokim klonowaniem.
Wersja ≥ 5.1
Jeśli obiekt można serializować do JSON, możesz utworzyć jego głęboki klon za pomocą kombinacji JSON.parse i JSON.stringify:
var existing = {a: 1, b: {c: 2}}; var copy = JSON.parse (JSON.stringify (istniejący)); existing.bc = 3; // copy.bc nie ulegnie zmianie
Zwróć uwagę, że JSON.stringify konwertuje obiekty Date na reprezentacje ciągów w formacie ISO, ale JSON.parse nie przekształci łańcucha z powrotem w Date.
W JavaScript nie ma wbudowanej funkcji tworzenia głębokich klonów, a generalnie nie jest możliwe tworzenie głębokich klonów dla każdego obiektu z wielu powodów. Na przykład
obiekty mogą mieć nieprzeliczalne i ukryte właściwości, których nie można wykryć. obiekty pobierające i ustawiające obiekty nie mogą być kopiowane. obiekty mogą mieć strukturę cykliczną. właściwości funkcji mogą zależeć od stanu w ukrytym zakresie.
Zakładając, że masz "ładny" obiekt, którego właściwości zawierają tylko prymitywne wartości, daty, tablice lub inne "ładne" obiekty, to następująca funkcja może być użyta do tworzenia głębokich klonów. Jest to funkcja rekursywna, która może wykrywać obiekty o strukturze cyklicznej i będzie zgłaszać błędy w takich przypadkach.
function deepClone (obj) {function clone (obj, traversedObjects) {var copy; // typy pierwotne if (obj === null || typeof obj! == "object") {return obj; }
// wykryj cykle dla (var i = 0; i <traversedObjects.length; i ++) {if (traversedObjects [i] === obj) {throw new Error ("Nie można sklonować okrągłego obiektu."); }}
// datuje if (obj wystąpienie Date) {copy = new Date (); copy.setTime (obj.getTime ()); kopia zwrotna; } // tablice if (obj instanceof Array) {copy = []; dla (var i = 0; i <obj.length; i ++) {copy.push (clone (obj [i], traversedObjects.concat (obj))); } return copy; } // proste obiekty if (obj instanceof Object) {copy = {}; for (klucz var w obj) {if (obj.hasOwnProperty (key)) {copy [key] = clone (obj [key], traversedObjects.concat (obj)); }} return copy; } throw new Error ("Nie jest obiektem klonującym."); }
return clone (obj, []); } 

Rozdział 13.4: Iteracja właściwości obiektu
Możesz uzyskać dostęp do każdej właściwości należącej do obiektu z tą pętlą
dla (właściwość var ​​w obiekcie) {// zawsze sprawdź, czy obiekt ma właściwość if (object.hasOwnProperty (właściwość)) {// rób rzeczy}}
Powinieneś dołączyć dodatkowe sprawdzenie dla hasOwnProperty, ponieważ obiekt może mieć właściwości odziedziczone z klasy bazowej obiektu. Niewykonanie tej kontroli może spowodować błędy.
Wersja ≥ 5
Można również użyć funkcji Object.keys, która zwraca tablicę zawierającą wszystkie właściwości obiektu, a następnie można przechodzić przez tę tablicę za pomocą funkcji Array.map lub Array.forEach.
var obj = {0: 'a', 1: 'b', 2: 'c'};
Object.keys (obj) .map (function (key) {console.log (key);}); // output: 0, 1, 2 

Section 13.5: Object.assign
Metoda Object.assign () służy do kopiowania wartości wszystkich przeliczalnych właściwości z jednego lub więcej obiektów źródłowych do obiektu docelowego. Zwróci obiekt docelowy.
Użyj go, aby przypisać wartości do istniejącego obiektu:
var user = {firstName: "John"};
Object.assign (user, {lastName: "Doe", age: 39}); console.log (użytkownik); // Dzienniki: {firstName: "John", lastName: "Doe", wiek: 39}
Lub utworzyć płytką kopię obiektu:
var obj = Object.assign ({}, user);
console.log (obj); // Logi: {firstName: "John", lastName: "Doe", wiek: 39}
Lubwiele właściwości z wielu obiektów do jednego:
łączvar obj1 = {a: 1}; var obj2 = {b: 2}; var obj3 = {c: 3}; var obj = Object.assign (obj1, obj2, obj3);
console.log (obj); // Logi: {a: 1, b: 2, c: 3} console.log (obj1); // Logi: {a: 1, b: 2, c: 3}, sam obiekt docelowy jest zmieniony
Prymitywy zostaną opakowane, wartość null i unde fizostaną zignorowane:
nowanevar var_1 = 'abc'; var var_2 = true; var var_3 = 10; var var_4 = Symbol ("foo");
var obj = Object.assign ({}, var_1, null, var_2, undefined, var_3, var_4); console.log (obj); // kłody: { "0", "a", "1", "b", "2", "C"}
Uwaga tylko łańcuch owijki mogą mieć własne właściwości przeliczalnego
użytkowania jako reduktor: (łączy tablicę z obiektem)
zwraca users.reduce ((result, user) => Object.assign ({}, {[user.id]: user}) 

Sekcja 13.6: Reszta obiektu / spread (. ..)
Wersja> 7
Rozsiewanie obiektów jest po prostu syntaktycznym cukrem dla Object.assign ({}, obj1, ..., objn);
Wykonuje się to za pomocą operatora:
let obj = {a: 1};
let obj2 = {... obj, b: 2, c: 3};
console.log (obj2); // {a: 1, b: 2, c: 3};
jako Object.assign robi płytkie scalanie, a nie głębokie przejmowane2};}.
pozwoli obj3 = {... obj b: {C:
console.log (obj3) // {a 1 b: {C: 2};}
UWAGA: Specyfikacji jest aktualnie etap 3

Sekcja 13.7: Object.de fi neProperty
Wersja ≥ 5
Pozwala nam na zdefiniowanie właściwości w istniejącym obiekcie za pomocą deskryptora właściwości
var obj = {};
Object.defineProperty (obj, 'foo', {value: 'foo'} );
konsola.log (obj.foo);
Wyjście konsoli
foo
Object.de FineProperty można wywołać za pomocą następujących opcji:
Object.defineProperty (obj, 'nameOfTheProperty', {value: valueOfTheProperty, writable: true, // jeśli false, właściwość jest konfigurowalna tylko do odczytu: true, // true oznacza, że ​​właściwość może zmień później wyliczalne: true // true oznacza, że ​​właściwość można wyliczyć tak jak w pętli for..in});
Object.defineProperties pozwala na definiowanie wielu właściwości naraz.
var obj = {};
Object.defineProperties (obj, {property1: {wartość: true, zapisywalny: true}, property2: {wartość: "Hello", zapisywalny: false}}); Rozdział 13.8: Właściwości dostępu (get i set)
Wersja ≥ 5
Traktuj właściwość jako kombinację dwóch funkcji, jedną, aby uzyskać wartość od niej, a drugą, aby ustawić w niej wartość.
Właściwość get deskryptora właściwości jest funkcją, która zostanie wywołana w celu pobrania wartości z właściwości.
Ustawiona właściwość jest również funkcją, zostanie wywołana, gdy właściwość ma przypisaną wartość, a nowa wartość zostanie przekazana jako argument.
Nie możesz przypisać wartości lub zapisu do deskryptora, który otrzymał lub ustaw
var person = {imię i nazwisko: "John", nazwisko: "Doe"}; Object.defineProperty (person, 'fullName', {get: function () {return this.name + "" + this.surname;}, set: function (value) {[this.name, this.surname] = value. rozdzielać(" "); } });
console.log (person.fullName); // -> "John Doe"
person.surname = "Hill"; console.log (person.fullName); // -> "John Hill"
person.fullName = "Mary Jones"; console.log (person.name) // -> "Mary"

Rozdział 13.9: Dynamiczne / zmienne nazwy właściwości
Czasami nazwa właściwości musi być zapisana w zmiennej. W tym przykładzie pytamy użytkownika, jakie słowo należy wyszukać, a następnie podajemy wynik z obiektu, który nazwałem słownikiem.
var dictionary = {sałata: "wegetarianin", banan: "owoc", pomidor: "to zależy od kogo pytasz", jabłko: "owoc", jabłko: "Steve Jobs kołysze!" // wielkość liter ma znaczenie)}
var word = prompt ("Jakie słowo chcesz dzisiaj wyszukać?") var definition = dictionary [word]
alert (word + '\ n \ n "+ definicja)
Zwróć uwagę, w jaki sposób używamy notacji nawiasów klamrowych [], aby spojrzeć na zmienną o nazwie słowo; gdybyśmy używali tradycyjnych. notacja, to dosłownie przyjąłby wartość, stąd:
console.log (dictionary.word) // nie działa, ponieważ słowo jest brane dosłownie, a słownik nie ma pola o nazwie `word` console.log (dictionary.apple) // to działa! ponieważ jabłko jest brane dosłownie
console.log (słownik [word]) // to działa! ponieważ słowo jest zmienną, a użytkownik wpisał jedno ze słów z naszego słownika po wyświetleniu zachęty console.log (słownik [jabłko]) // błąd! jabłko nie jest zdefiniowane (jako zmienna)
Można również napisać wartości literowe z notacją [], zastępując słowo zmienne ciągiem "jabłko". Zobacz przykład [Właściwości ze znakami specjalnymi lub słowami zastrzeżonymi].
Możesz także ustawić właściwości dynamiczne za pomocą składni nawiasów:
var property = "test"; var obj = {[właściwość] = 1; };
console.log (obj.test); // 1
Robi to samo, co:
var property = "test"; var obj = {}; obj [właściwość] = 1; 

Rozdział 13.10: Tablice są obiektami
Uwaga: Tworzenie obiektów podobnych do tablic nie jest zalecane. Warto jednak zrozumieć, w jaki sposób działają, szczególnie podczas pracy z DOM. To wyjaśni, dlaczego regularne operacje na tablicach nie działają na obiektach DOM zwróconych z wielu funkcji dokumentu DOM. (querySelectorAll, form.elements)
Przypuśćmy, że stworzyliśmy następujący obiekt, który ma pewne właściwości, które można zobaczyć w tablicy.
var anObject = {foo: 'bar', length: 'interesting', '0': "zero!", "1": "jeden!" };
Następnie utworzymy tablicę.
var anArray = ["zero.", "jeden."];
Teraz zwróć uwagę, jak możemy kontrolować zarówno obiekt, jak i tablicę w ten sam sposób.
console.log (anArray [0], anObject [0]); // wyniki: zero. zero! console.log (anArray [1], anObject [1]); // wyniki: jeden. jeden! console.log (anArray.length, anObject.length); // wyniki: 2 interesujące
console.log (anArray.foo, anObject.foo); // output: undefined bar
Ponieważ anArray jest w rzeczywistości obiektem, podobnie jak anObject, możemy nawet dodać niestandardowe właściwości wordy do anArray
Disclaimer: Tablice z niestandardowymi właściwościami zazwyczaj nie są zalecane, ponieważ mogą być mylące, ale mogą być przydatne w zaawansowanych przypadkach gdzie potrzebujesz zoptymalizowanych funkcji tablicy. (tj. obiekty jQuery)
anArray.foo = 'to działa!'; console.log (anArray.foo);
Możemy nawet uczynić obiekt anObject obiektem typu tablicowym, dodając długość.
anObject.length = 2;
Następnie możesz użyć pętli w stylu C do iterowania przez obiekt anObject, tak jakby był to Array. Patrz: Tablica Iteracja
Zauważ, że anObject jest tylko obiektem tablicowym. (znany również jako lista) Nie jest prawdziwą tablicą. Jest to ważne, ponieważ funkcje takie jak push i forEach (lub dowolna wygodna funkcja znaleziona w Array.prototype) nie będą działać domyślnie na obiektach podobnych do tablic.
Wiele funkcji dokumentu DOM zwróci listę (np. QuerySelectorAll, form.elements), która jest podobna do anObject, który stworzyliśmy powyżej. Zobacz Konwertowanie obiektów podobnych do tablicowych na tablice
console.log (typeof anArray == 'object', typeof anObject == 'object'); // output: true true console.log (anArray instanceof Object, anObject instanceof Object); // output: true true console.log (anArray instanceof Array, anObject instanceof Array); // output: true false console.log (Array.isArray (anArray), Array.isArray (anObject)); // wyniki: true false Sekcja 13.11: Object.seal
Wersja ≥ 5
Object.seal zapobiega dodawaniu lub usuwaniu właściwości z obiektu. Po zapieczętowaniu obiektu jego deskryptory właściwości nie mogą zostać przekonwertowane na inny typ. W przeciwieństwie do Object.freeze pozwala na edycję właściwości.
Próby wykonania tych operacji na zamkniętym obiekcie nie powiedzie się po cichu
var obj = {foo: 'foo', bar: function () {return 'bar "; }};
Object.seal (obj)
obj.newFoo = 'newFoo'; obj.bar = function () {return 'foo'};
obj.newFoo; // undefined obj.bar (); // 'foo'
// Nie można uczynić foo własnością dostępową Object.defineProperty (obj, 'foo', {get: function () {return 'newFoo';}}); // TypeError
// Ale możesz uczynić go tylko do odczytu Object.defineProperty (obj, 'foo', {
write: false}); // TypeError
obj.foo = 'newFoo'; obj.foo; // 'bla';
W trybie ścisłym te operacje spowodują TypeError
(function () {'use strict';
    var obj = {foo: 'foo'};
    Object.seal (obj);
    obj.newFoo = 'newFoo'; // TypeError} ( )); Rozdział 13.12: Konwertuj wartości obiektu na tablicę
Biorąc pod uwagę ten obiekt:
var obj = {a: "hello", b: "to jest", c: "javascript!",};
Możesz przekonwertować jego wartości do tablicy, wykonując:
var tablica = Object.keys (obj) .map (function (key) {return obj [key];});
console.log (tablica); // ["cześć", "to jest", "javascript!"] Rozdział 13.13: Pobieranie właściwości z obiektu
Charakterystyka właściwości:
Właściwości, które mogą być pobrane z obiektu, mogą mieć następujące cechy:
Enumerable Non - Enumerable own przy
tworzeniu właściwości za pomocą Object.de fi neProperty (y) możemy ustawić jego charakterystykę z wyjątkiem "własnych". Właściwości, które są dostępne na poziomie bezpośrednim, nie na poziomie prototypu (__proto__) obiektu, są nazywane własnymi właściwościami.
A właściwości dodane do obiektu bez użycia Object.defindProperty (y) nie będą miały swojej przeliczalnej cechy. Oznacza to, że uważa się to za prawdziwe.
Cel wymienialności:
Głównym celem ustawienia właściwości przeliczalnych dla właściwości jest udostępnienie konkretnej właściwości obiektu
dostępności podczas pobierania jej z obiektu, przy użyciu różnych metod programowych. Te różne metody zostaną omówione głęboko poniżej.
Metody pobierania właściwości:
Właściwości z obiektu można odzyskać za pomocą następujących metod dla
pętli w .l.
Pętla ta jest bardzo użyteczna przy pobieraniu wyliczalnych właściwości z obiektu. Dodatkowo, ta pętla pobierze wyliczalne własne właściwości, jak również zrobi to samo pobieranie przez przechodzenie przez prototypowy łańcuch, dopóki nie zobaczy prototypu jako wartości zerowej.
// Przykład 1: Proste dane var x = {a: 10, b: 3}, rekwizyty = [];
dla (prop in x) {props.push (prop); }
console.log (rekwizyty); // ["a", "b"]
// Przykład 2: Dane z właściwościami przeliczalnymi w łańcuchu prototypów var x = {a: 10, __proto__: {b: 10}}, props = [];
dla (prop in x) {props.push (prop); }
console.log (rekwizyty); // ["a", "b"]
// Przykład 3: Dane z nielicznymi właściwościami var x = {a: 10}, props = []; Object.defineProperty (x, "b", {wartość: 5, wyliczalna: false});
dla (prop in x) {props.push (prop); }
console.log (rekwizyty); // ["a"]
Object.keys () function2.
Ta funkcja została zaprezentowana jako część ECMAScript 5. Służy do pobierania własnych właściwości z obiektu. Przed jego wydaniem ludzie używali do pobierania własnych właściwości z obiektu, łącząc pętlę for..in i Object.prototype.hasOwnProperty ().
// Przykład 1: Proste dane var x = {a: 10, b: 3}, rekwizyty;
rekwizyty = Object.keys (x);
console.log (rekwizyty); // ["a", "b"]
// Przykład 2: Dane z właściwościami przeliczalnymi w łańcuchu prototypów var x = {a: 10, __proto__: {b: 10}}, rekwizyty;
rekwizyty = Object.keys (x);
console.log (rekwizyty); // ["a"]
// Przykład 3: Dane z nielicznymi właściwościami var x = {a: 10}, rekwizyty; Object.defineProperty (x, "b", {wartość: 5, wyliczalna: false});
rekwizyty = Object.keys (x);
console.log (rekwizyty); // ["a"]
Object.getOwnProperties () function3.
Ta funkcja pobierze zarówno przeliczalne, jak i nieprzeliczalne, własne właściwości z obiektu. Został również wydany jako część ECMAScript 5.
// Ex 1: Simple data var x = {a: 10, b: 3}, rekwizyty;
props = Object.getOwnPropertyNames (x);
console.log (rekwizyty); // ["a", "b"]
// Przykład 2: Dane z właściwościami przeliczalnymi w łańcuchu prototypów var x = {a: 10, __proto__: {b: 10}}, rekwizyty;
props = Object.getOwnPropertyNames (x);
console.log (rekwizyty); // ["a"]
// Przykład 3: Dane z nielicznymi właściwościami var x = {a: 10}, rekwizyty; Object.defineProperty (x, "b", {wartość: 5, wyliczalna: false});
props = Object.getOwnPropertyNames (x);
console.log (rekwizyty); // ["a", "b"]
Różne:
Poniżej przedstawiono technikę pobierania wszystkich właściwości (własna,,, wszystkie prototypowe) z obiektu,
wyliczalnanieliczalnafunkcja getAllProperties (obj, props = []) {return obj == null? rekwizyty: getAllProperties (Object.getPrototypeOf (obj), props.concat (Object.getOwnPropertyNames (obj))); }
var x = {a: 10, __proto__: {b: 5, c: 15}};
// dodanie nieprzewidywalnej właściwości do prototypu pierwszego poziomu Object.defineProperty (x .__ proto__, "d", {wartość: 20, przeliczalne: false});
console.log (getAllProperties (x)); ["a", "b", "c", "d", "... inne domyślne rekwizyty rdzenia ..."]
A to będzie obsługiwane przez przeglądarki obsługujące ECMAScript 5.
Rozdział 13.14: Właściwość Tylko do odczytu
Wersja ≥ 5
Używając deskryptorów właściwości możemy dokonać tylko odczytu właściwości, a każda próba zmiany jej wartości nie powiedzie się po cichu, wartość nie zostanie zmieniona i nie zostanie zgłoszony błąd.
Zapisywalna właściwość w deskryptorze właściwości wskazuje, czy tę właściwość można zmienić, czy też nie.
var a = {};
Object.defineProperty (a, 'foo', {value: 'original', writable: false});
a.foo = "nowy";
console.log (a.foo);
Console output
original

Section 13.15: Nieprzeliczalna właściwość
Version ≥ 5
Możemy uniknąć pojawienia się właściwości dla pętli (... w ...)
Właściwość przeliczalna deskryptora właściwości określa, czy ta właściwość zostanie wyliczona podczas przechodzenia przez pętlę właściwości obiektu.

var obj = {};
Object.defineProperty (obj, "foo", {wartość: "pokaż", wyliczalne: true}); Object.defineProperty (obj, "bar", {wartość: "ukryj", wyliczalna: false});
dla (var prop w obj) {console.log (obj [prop]); }
Wyjście konsoli
Pokaż
Sekcja 13.16: Opis właściwości blokady
Wersja ≥ 5
Deskryptor właściwości może zostać zablokowany, więc nie można w nim wprowadzać żadnych zmian. W dalszym ciągu możliwe będzie normalne korzystanie z właściwości, przypisywanie i pobieranie wartości z niej, ale każda próba jej ponownego wyrzucenia spowoduje zgłoszenie wyjątku.
Konfigurowalna właściwość deskryptora właściwości służy do blokowania dalszych zmian deskryptora.
var obj = {};
// Zdefiniuj "foo" jako tylko do odczytu i zablokuj obiekt Object.defineProperty (obj, "foo", {wartość: "oryginalna wartość", zapis: false, konfigurowalny: false});
 
Object.defineProperty (obj, "foo", {writable: true});
Ten błąd zostanie:
zgłoszonyTypeError: Can not rede fi ne property: foo
A właściwość będzie nadal tylko do odczytu.
obj.foo = "nowa wartość"; console.log (foo);
wyjściowa w konsoli
WartośćWartość
13.17: Object.getOwnPropertyDescriptor
Pobierz opis określonej właściwości w obiekcie.
var sampleObject = {hello: 'world'};
Object.getOwnPropertyDescriptor (sampleObject, 'hello'); // Object {value: "world", writable: true, enumerable: true, configurable: true} Rozdział 13.18: Deskryptory i nazwane właściwości
Właściwości są członkami obiektu. Każda nazwana właściwość to para (nazwa, deskryptor). Nazwa jest łańcuchem, który umożliwia dostęp (za pomocą notacji obiektu object.propertyName lub obiektu notacji nawiasów kwadratowych ['propertyName']). Deskryptor jest zapisem pól definiujących właściwości obiektu, gdy jest on dostępny (co dzieje się z własnością i jaka jest wartość zwrócona z dostępu do niej). Ogólnie właściwość wiąże nazwę z zachowaniem (możemy myśleć o zachowaniu jako czarnej skrzynki).
Istnieją dwa typy nazwanych właściwości: właściwość
data: nazwa właściwości jest powiązana z wartością 1. właściwość accessor: nazwa właściwości jest powiązana z jedną lub dwiema funkcjami akcesora.2.
Demonstracja:
obj.propertyName1 = 5; // tłumaczy za kulisami do // przypisanie 5 do pola wartości *, jeśli jest to właściwość danych // lub wywołanie funkcji set z parametrem 5, jeśli właściwość accessorokreśla,
// * faktycznieczy przypisanie ma mieć miejsce w przypadek właściwości danych // zależy również od obecności i wartości zapisywalnego pola - od tego późniejpola
Typ właściwości jest określony przezjej deskryptora, a właściwość nie może być obu typów.
Deskryptory danych 
Wymagane pola: wartość lub zapisywalny lub oba pola opcjonalne: konfigurowalne, przeliczalne
Próbka:
{wartość: 10, zapisywalna: prawdziwa; }
Deskryptory Accessora 
Wymagane pola: get or set lub oba pola opcjonalne: konfigurowalne, przeliczalne
Przykład:
{get: function () {return 10; }, enumerable: true}
znaczenie pól i ich wartości domyślne konfigurowalne, przeliczalne i zapisywalne: Wszystkie
te klucze mają wartość domyślną false. konfigurowalna ma wartość true wtedy i tylko wtedy, gdy typ tego deskryptora właściwości może zostać zmieniony i właściwość może zostać usunięta z odpowiedniego obiektu. przeliczalne jest prawdziwe wtedy i tylko wtedy, gdy ta właściwość pojawia się podczas wyliczania właściwości na odpowiednim obiekcie. zapisywalny jest prawdziwy wtedy i tylko wtedy, gdy wartość powiązana z właściwością może zostać zmieniona za pomocą operatora przypisania.
get i set:
te klucze są domyślnie niezdefiniowane. get jest funkcją, która służy jako getter dla właściwości, lub nieokreśloną, jeśli nie ma żadnego gettera. Zwrot funkcji zostanie użyty jako wartość właściwości. set to funkcja, która służy jako seter dla właściwości lub nieokreślona, ​​jeśli nie ma ustawnika. Funkcja otrzyma jako jedyny argument nową wartość przypisaną do właściwości.
value:
ten klucz jest domyślnie niezdefiniowany. Wartość powiązana z właściwością. Może to być dowolna poprawna wartość JavaScript (numer, obiekt, funkcja itp.).
Przykład:
    var obj = {propertyName1: 1}; // ta para jest faktycznie ('propertyName1', {wartość: 1, // zapisywalny: true, // przeliczalny: true, // konfigurowalny: true}) Object.defineProperty (obj, 'propertyName2', {get: function ( ) {console.log ("to będzie rejestrowane" + "za każdym razem, gdy uzyskuje się dostęp do właściwości nazwa_domeny2, aby uzyskać jej wartość");}, ustaw: function () {console.log ("i będzie rejestrowane" + "za każdym razem, gdy właściwość nazwa2 \ 's wartość jest próbowana być ustawione ") // będzie traktowane tak, jak ma przeliczalne: false, konfigurowalne: false}}); // właściwośćNazwa1 to nazwa właściwości danych obiektu //, ato nazwa właściwości programu korzystającego
nazwa_właściwości2obj.propertyName1 = 3; console.log (obj.propertyName1); // 3
obj.propertyName2 = 3; // i to będzie rejestrowane za każdym razem, gdy próbujemy ustawić wartość właściwości propertyName2 na console.log (obj.propertyName2); // to będzie rejestrowane za każdym razem, gdy uzyskuje się dostęp do właściwości NazwaNazwa2, aby uzyskać jej wartość Sekcja 13.19: Object.keys
Wersja ≥ 5
Object.keys (obj) zwraca tablicę kluczy danego obiektu.
var obj = {a: "cześć", b: "to jest", c: "javascript!" };
var keys = Object.keys (obj);
console.log (klucze); // ["a", "b", "c"] Rozdział 13.20: Właściwości ze znakami specjalnymi lub słowami zastrzeżonymi
Podczas gdy notacja właściwości obiektu jest zwykle zapisywana jako myObject.property, dozwolone będą tylko znaki normalnie występujące w nazwach zmiennych JavaScript , czyli głównie litery, cyfry i podkreślenie (_).
Jeśli potrzebujesz znaków specjalnych, takich jak spacja, ☺ lub treść dostarczona przez użytkownika, jest to możliwe za pomocą notacji nawiasów [].
myObject ['special property ☺'] = 'to działa!' console.log (myObject ['specjalna właściwość ☺']) All-digit properties:
Oprócz znaków specjalnych, nazwy właściwości, które są pełnymi cyframi będą wymagały zapisu nawiasów. Jednak w tym przypadku właściwość nie musi być zapisywana jako ciąg znaków.
myObject [123] = "cześć!" // liczba 123 jest automatycznie konwertowana na ciąg konsolowy.log (myObject ['123']) // zauważ, jak za pomocą ciągu 123 utworzono ten sam wynik console.log (myObject ['12 '+' 3 ']) // string concatenation console.log (myObject [120 + 3]) // arytmetyczna, nadal daje 123 i produkuje ten sam wynik console.log (myObject [123.0]) // to też działa, ponieważ 123.0 ocenia do 123 console.log (myObject [ '123.0']) // to NIE działa, ponieważ '123'! = '123.0'początkowe
Jednakzera nie są zalecane, ponieważ są interpretowane jako notacja dziesiętna. (TODO, powinniśmy utworzyć i połączyć się z przykładem opisującym notację ósemkową, szesnastkową i wykładniczą)
Zobacz także: Przykład [Tablice są obiektami]. Rozdział 13.21: Tworzenie obiektu
Iterable Wersja ≥ 6 var myIterableObject = {}; // Obiekt Iterable musi definiować metodę znajdującą się przy kluczu Symbol.iterator: myIterableObject [Symbol.iterator] = function () {// Iterator powinien zwracać return obiektu Iterator {// Obiekt Iterator musi implementować metodę, następnie () next: function () {// next musi sam zwrócić obiekt IteratorResult, jeśli (! this.iterated) {this.iterated = true; // Obiekt IteratorResult ma dwie właściwości return {//, czy iteracja jest zakończona, i wykonane: false, // wartość bieżącej wartości iteracji: 'Jeden'}; } return {// Po zakończeniu iteracji wystarczy wykonać właściwość done done: true}; }, iterowane: false}; };
dla (var c of myIterableObject) {console.log (c); }
Wyjście konsoli
Jedna
sekcja 13.22: Iterowanie po obiektach - Object.entries ()
Wersja ≥ 8
Proponowana metoda Object.entries () zwraca tablicę par klucz / wartość dla danego obiektu. Nie zwraca on iteratora takiego jak Array.prototype.entries (), ale tablica zwrócona przez Object.entries () może być iterowana
niezależnie.
const obj = {one: 1, two: 2, three: 3};
Object.entries (obj);
Wyniki w:
[["jeden", 1], ["dwa", 2], ["trzy", 3]]
Jest to przydatny sposób na iterację par klucz / wartość obiektu:
dla (const [key , value] z Object.entries (obj)) {console.log (key); // "jeden", "dwa" i "trzy" console.log (wartość); // 1, 2 i 3} Rozdział 13.23: Object.values ​​()
Wersja ≥ 8
Metoda Object.values ​​() zwraca tablicę własnych wyliczalnych wartości właściwości danego obiektu, w tej samej kolejności, w jakiej dostarczono dla obiektu .. .in loop (różnica jest taka, że ​​pętla for-in wylicza również właściwości w łańcuchu prototypów).
var obj = {0: 'a', 1: 'b', 2: 'c'}; console.log (Object.values ​​(obj)); // ['a', 'b', 'c']
Uwaga:
Aby uzyskać wsparcie dla przeglądarki, odsyłamy do tego łącza

Rozdział 14: Arytmetyka (matematyka) Rozdział 14.1: Stałe
Stałe Opis Przybliżona Math.E Podstawa logarytmu naturalnego e 2.718 Math.LN10 Logarytm naturalny z 10 2.302 Math.LN2 Logarytm naturalny z 2 0.693 Math.LOG10E Logarytm Base 10 o 0.434 Math.LOG2E Logarytm Base 2 o 1.442 Math.PI Pi: stosunek obwodu koła do średnicy (π) 3.14 Math.SQRT1_2 Pierwiastek kwadratowy z 1/2 0,707 Math.SQRT2 Pierwiastek kwadratowy z 2 1,414
Liczba.EPSILON Różnica
między jedną a najmniejszą wartością większą niż jedna reprezentowana jako liczba
2.2204460492503130808472633361816E-16
Number.MAX_SAFE_INTEGER
Największa liczba całkowita n taka, że ​​n n + 1 są dokładnie przedstawiane jako liczba
2 ^ 53 - 1
Number.MAX_VALUE Największa pozytywna, pełna wartość Number 1.79E + 308
Number.MIN_SAFE_INTEGER
Najmniejsza liczba całkowita n taka, że ​​n i n - 1 są dokładnie reprezentowane jako liczba
- ( 2 ^ 53 - 1)
Number.MIN_VALUE Najmniejsza wartość dodatnia dla N umber 5E-324 Number.NEGATIVE_INFINITY Wartość ujemnej nieskończoności (-∞) Liczba POSITIVE_INFINITY Wartość dodatniej nieskończoności (∞) Nieskończoność Wartość dodatniej nieistotności (∞) Sekcja 14.2: Reszta / moduł (%)
Reszta / operator modulus (%) zwraca resztę po dzieleniu (całkowitym).
console.log (42% 10); // 2 console.log (42% -10); // 2 console.log (-42% 10); // -2 console.log (-42% -10); // -2 console.log (-40% 10); // -0 console.log (40% 10); // 0
Ten operator zwraca resztę pozostałą, gdy jeden operand jest podzielony przez drugi operand. Gdy pierwszy operand jest wartością ujemną, wartość zwracana zawsze będzie ujemna i odwrotnie dla wartości dodatnich.
W powyższym przykładzie, 10 można odjąć cztery razy od 42, zanim nie będzie już wystarczająco dużo, aby odjąć ponownie bez zmiany znaku. Pozostała część jest następująca: 42 - 4 * 10 = 2.
Operator pozostały może być przydatny dla następujących problemów:
Sprawdź, czy liczba całkowita jest (nie) podzielna przez inny numer: 1.
 x% 4 == 0 // prawda, jeśli x jest podzielna przez 4 x% 2 == 0 // prawda, jeśli x jest liczbą parzystą
      - 130
 x% 2! = 0 // prawda, jeśli x jest liczbą nieparzystą
Od 0 === -0, to również działa dla x <= -0.
Zaimplementuj cykliczne zwiększanie / zmniejszanie wartości w ramach przedziału [0, n).
Załóżmy, że musimy zwiększyć wartość całkowitą z 0 do (ale nie włączając) n, więc następna wartość po n-1 wynosi 0. Można to zrobić za pomocą takiego pseudokod:
var n = ...; // podane n var i = 0; function inc () {i = (i + 1)% n; } while (true) {inc (); // zaktualizuj coś za pomocą i}
Teraz uogólnij powyższy problem i załóżmy, że musimy zezwolić zarówno na zwiększanie, jak i zmniejszanie tej wartości od 0 do (nie wliczając) n, więc następna wartość po n-1 wynosi 0, a poprzednia wartość przed 0 to n-1.
var n = ...; // podane n var i = 0; function delta (d) {// d - dowolna liczba całkowita ze znakiem i = (i + d + n)% n; // dodajemy n do (i + d), aby zapewnić, że suma jest dodatnia}
Teraz możemy wywołać funkcję delta () przekazującą dowolną liczbę całkowitą, zarówno dodatnią, jak i ujemną, jako parametr delta.
Użycie modułu do uzyskania ułamkowej części liczby var myNum = 10/4; // 2.5 var fraction = myNum% 1; // 0,5 myNum = -20 / 7; // -2.857142857142857 fraction = myNum% 1; // -0.857142857142857 Rozdział 14.3: Zaokrąglanie w
zaokrągleniu
Math.round () będzie zaokrąglało wartość do najbliższej liczby całkowitej za pomocą półokrągła do zerwania więzi.
var a = Math.round (2.3); // a jest teraz 2 var b = Math.round (2.7); // b jest teraz 3 var c = Math.round (2.5); // c jest teraz 3
Ale
var c = Math.round (-2.7); // c jest teraz -3 var c = Math.round (-2,5); // c jest teraz -2
Zwróć uwagę, że -2,5 jest zaokrąglone do -2. Dzieje się tak dlatego, że wartości połowy są zawsze zaokrąglane w górę, to znaczy są zaokrąglane do liczby całkowitej z następną wyższą wartością.
Zaokrąglenie
Math.ceil () spowoduje zaokrąglenie wartości do góry.
var a = Math.ceil (2.3); // a jest teraz 3 var b = Math.ceil (2.7); // b jest teraz 3
stropem, a liczba ujemna zaokrągli się w kierunku zera
var c = Math.ceil (-1.1); // c jest teraz 1
Zaokrąglanie w dół
Math.floor () zaokrągla wartość w dół.
var a = Math.floor (2.3); // a jest teraz 2 var b = Math.floor (2.7); // b to teraz 2
piętra, a liczba ujemna zaokrągli ją do zera.
var c = Math.floor (-1.1); // c jest teraz -1
Skasuj
zastrzeżenia: używanie operatorów bitowych (z wyjątkiem >>>) dotyczy tylko numerów od -2147483649 do 2147483648.
2.3 | 0; // 2 (podłoga) -2.3 | 0; // -2 (ceil) NaN | 0; // 0 Wersja ≥ 6
Math.trunc ()
Math.trunc (2.3); // 2 (podłoga) Math.trunc (-2,3); // -2 (ceil) Math.trunc (2147483648.1); // 2147483648 (piętro) Math.trunc (-2147483649.1); // -2147483649 (ceil) Math.trunc (NaN); // NaN
Zaokrąglanie do miejsc dziesiętnych
Math.floor, Math.ceil () i Math.round () mogą być użyte do zaokrąglenia do liczby miejsc po przecinku
Aby zaokrąglić do 2 miejsc dziesiętnych:
 var myNum = 2/3; // 0.6666666666666666 mnożnik var = 100; var a = Math.round (multiplikator myNum *) / mnożnik; // 0.67 var b = Math.ceil (mnożnik myNum *) / mnożnik; // 0.67 var c = Math.floor (mnożnik myNum *) / mnożnik; // 0.66
Możesz także zaokrąglić do liczby cyfr:
 var myNum = 10000/3; // 3333.3333333333335 multiplikator var = 1/100; var a = Math.round (multiplikator myNum *) / mnożnik; // 3300
 var b = Math.ceil (multiplikator myNum *) / mnożnik; // 3400 var c = Math.floor (mnożnik myNum *) / mnożnik; // 3300
Jako bardziej użyteczna funkcja:
 // wartość jest wartością zaokrąglenia // miejsca, jeśli dodatnia liczba miejsc po przecinku do zaokrąglonych do // miejsc, jeśli jest ujemna liczba cyfr do zaokrąglenia do funkcji roundTo (wartość, miejsca) { var power = Math.pow (10, miejsca); return Math.round (wartość * moc) / moc; } var myNum = 10000/3; // 3333.3333333333335 roundTo (myNum, 2); // 3333.33 roundTo (myNum, 0); // 3333 roundTo (myNum, -2); // 3300
A warianty dla sufitu i podłogi:
 funkcja ceilTo (value, places) {var power = Math.pow (10, miejsca); return Math.ceil (wartość * moc) / moc; } function floorTo (value, places) {var power = Math.pow (10, miejsca); return Math.floor (wartość * moc) / moc; } Rozdział 14.4: Trygonometria
Wszystkie kąty poniżej są w radianach. Kąt w radianach ma miarę 180 * r / Math.PI w stopniach.
Sine Math.sin (r);
To zwróci sinus r, wartość między -1 a 1.
Math.asin (r);
To zwróci arcus sinus (rewers sinusa) r.
Math.asinh (r)arcus sinusę
To zwróci hiperbolicznąr.
Cosine Math.cos (r);
To zwróci cosinus r, wartość pomiędzy -1 i 1
Math.acos (r);
To zwróci arccosine (odwrotność cosinusa) r.
Math.acosh (r);
To zwróci hiperboliczną arkcosynę r.
Tangent Math.tan (r);
To zwróci styczną r.
Math.atan (r);
To zwróci arcus tangens (odwrotność stycznej) r. Zwróć uwagę, że zwróci kąt w radianach od -π / 2 do π / 2.
Math.atanh (r);
Spowoduje to powrót hiperbolicznego arcus tangensa r.
Math.atan2 (x, y);
To zwróci wartość kąta od (0, 0) do (x, y) w radianach. Zwróci wartość między -π a π, nie włączając π. 

Sekcja 14.5: Operatory bitowe
Należy pamiętać, że wszystkie operacje bitowe działają na 32-bitowych liczbach całkowitych, przekazując dowolne operandy do wewnętrznej funkcji ToInt32.
Bitowy lub var a; a = 0b0011 | 0b1010; // a === 0b1011 // tabela prawdy // 1010 | (lub) // 0011 // 1011 (wynik) Bitowy i a = 0b0011 i 010010; // a === 0b0010 // tabela prawdy // 1010 & (i) // 0011 // 0010 (wynik) Bitwise not a = 0b0011; // a === 0b1100 // tabela prawdy // 10 ~ (nie) // 01 (wynik) Bitowe xor (wyłączne lub) a = 0b1010 ^ 0b0011; // a === 0b1001 // tabela prawdy // 1010 ^ (xor) // 0011 // 1001 (wynik) Bitowe przesunięcie lewe a = 0b0001 << 1; // a === 0b0010 a = 0b0001 << 2; // a === 0b0100 a = 0b0001 << 3; // a === 0b1000
Przesunięcie w lewo jest równoważne liczbie całkowitej mnożonej przez Math.pow (2, n). Podczas wykonywania matematyki całkowitej zmiana może znacznie poprawić szybkość niektórych operacji matematycznych.
var n = 2; var a = 5,4; var result = (a << n) === Math.floor (a) * Math.pow (2, n); // wynik jest prawdziwy a = 5.4 << n; // 20 Bitowe przesunięcie w prawo >> (Przesunięcie propagujące znak) >>> (Zero- lll right shift) a = 0b1001 >> 1; // a === 0b0100 a = 0b1001 >> 2; // a === 0b0010 a = 0b1001 >> 3; // a === 0b0001
a = 0b1001 >>> 1; // a === 0b0100 a = 0b1001 >>> 2; // a === 0b0010 a = 0b1001 >>> 3; // a === 0b0001
Ujemna wartość 32-bitowa zawsze ma włączony lewy bit:
a = 0b11111111111111111111111111110111 | 0; console.log (a); // -9 b = a >> 2; // Najdalszy bit jest przesunięty o 1 w prawo, a nowy lewy najbardziej ustawiony jest na on (1) console.log (b); // -3 b = a >>> 2; // Najdalszy bit jest przesunięty o 1 w prawo. nowy lewy najwyższy bit jest ustawiony na off (0) console.log (b); // 2147483643
Wynik operacji >>> zawsze jest dodatni. Wynik >> jest zawsze tym samym znakiem co zmieniona wartość.
Prawe przesunięcie na liczbach dodatnich jest równoznaczne z dzieleniem przez Math.pow (2, n) i przepuszczaniem wyniku:
a = 256,67; n = 4; result = (a >> n) === Math.floor (Math.floor (a) / Math.pow (2, n)); // wynik jest prawdziwy a = a >> n; // 16
result = (a >>> n) === Math.floor (Math.floor (a) / Math.pow (2, n)); // wynik jest prawdziwy a = a >>> n; // 16
Prawe przesunięcie zero fi ll (>>>) na liczbach ujemnych jest różne. Ponieważ JavaScript nie konwertuje na unsigned ints podczas wykonywania operacji bitowych nie ma operacyjnego odpowiednika:
a = -256.67; result = (a >>> n) === Math.floor (Math.floor (a) / Math.pow (2, n)); // wynik jest fałszywy Operatory przypisania bitowego
Z wyjątkiem nie (~) wszystkie powyższe operatory bitowe mogą być używane jako operatory przypisania:
a | = b; // tak samo jak: a = a | b; a ^ = b; // tak samo jak: a = a ^ b; a & = b; // tak samo jak: a = a & b; a >> = b; // tak samo jak: a = a >> b; a >>> = b; // tak samo jak: a = a >>> b; a << = b; // tak samo jak: a = a << b;
Ostrzeżenie: JavaScript używa Big Endian do przechowywania liczb całkowitych. To nie zawsze będzie pasowało do Endian urządzenia / systemu operacyjnego. W przypadku korzystania z tablic maszynowych o długościach bitów większych niż 8 bitów przed zastosowaniem operacji bitowych należy sprawdzić, czy środowisko to Little Endian lub Big Endian.
Ostrzeżenie: Operatory bitowe, takie jak & i | nie są takie same jak operatory logiczne && (and) i || (lub). Dostarczą niepoprawne wyniki, jeśli są używane jako operatory logiczne. Operator ^ nie jest operatorem mocy (ab). Punkt 14.6: Inkrementacja (++)
Operator inkrementacji (++) zwiększa swój operand o jeden.
Jeśli użyto go jako post-x, to zwraca wartość przed inkrementacją. W przypadku użycia jako prefiksu, zwraca wartość po inkrementacji.
// postfix var a = 5, // 5 b = a ++, // 5 c = a // 6
W tym przypadku wartość a jest zwiększana po ustawieniu b. Zatem b będzie 5, a c będzie 6.
// przedrostek var a = 5, // 5 b = ++ a, // 6 c = a // 6
W tym przypadku wartość a jest zwiększana przed ustawieniem b. Zatem b będzie 6, a c będzie 6.
Operatory inkrementacji i dekrementacji są powszechnie używane w pętlach, na przykład:
dla (var i = 0; i <42; ++ i) {// zrobić coś niesamowitego! }
Zwróć uwagę, w jaki sposób używany jest wariant wstępny. Zapewnia to, że zmienna tymczasowa nie jest niepotrzebnie tworzona (aby zwrócić wartość przed operacją). Rozdział 14.7: Potęgowanie (Math.pow () lub **)
Potęgowanie powoduje, że drugi operand jest potęgą pierwszego operandu (ab).
var a = 2, b = 3, c = Math.pow (a, b);
c będzie teraz8
wersjąWersja> 6
Stopień 3 ES2016 (ECMAScript 7) Wniosek:
niech a = 2, b = 3,
    c = a ** b;
c będzie teraz 8
Użyj Math.pow, aby znaleźć n-ty pierwiastek liczby.
Znalezienie n-tego korzenia jest odwrotnością podniesienia do n-tej siły. Na przykład 2 do potęgi 5 wynosi 32. Piąty korzeń z 32 wynosi 2.
Math.pow (v, 1 / n); // gdzie v jest dowolną dodatnią liczbą rzeczywistą //, a n jest dowolną dodatnią liczbą całkowitą
var a = 16; var b = Math.pow (a, 1/2); // zwraca pierwiastek kwadratowy z 16 = 4 var c = Math.pow (a, 1/3); // zwraca podstawową kostkę 16 = 2,5198420997897464 var d = Math.pow (a, 1/4); // zwraca czwarty katalog główny z 16 = 2 Rozdział 14.8: Losowe liczby całkowite i zmienne
var a = Math.random ();
Przykładowa wartość: 0.21322848065742162 Math.random
() zwraca losową liczbę między 0 (włącznie) i 1 (wyłączną)
funkcją getRandom () {return Math.random (); }
Aby użyć Math.random (), aby uzyskać liczbę z dowolnego zakresu (nie [0,1), użyj tej funkcji, aby uzyskać liczbę losową między min (włącznie) a maks. (Wyłączną): przedział [min, max]
function getRandomArbitrary (min, max) {return Math.random () * (max - min) + min; }
Aby użyć Math.random () do uzyskania liczby całkowitej z dowolnego zakresu (nie [0,1)), użyj tej funkcji, aby uzyskać liczbę losową między min (włącznie) a maks. (Wyłączną): przedział [min, max]
function getRandomInt (min, max) {return Math.floor (Math.random () * (max - min)) + min; }
Aby użyć Math.random (), aby uzyskać liczbę całkowitą z dowolnego zakresu (nie [0,1), użyj tej funkcji, aby uzyskać liczbę losową między min (włącznie) a maks. (Włącznie): przedział [min, max]
funkcja getRandomIntInclusive (min, max) {return Math.floor (Math.random () * (max - min + 1)) + min; }
Funkcje zaczerpnięte z https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random
Rozdział 14.9: Dodawanie (+)
Operator dodawania (+) dodaje liczby.
var a = 9, b = 3, c = a + b;
c będzie teraz 12
Ten operand może być również użyty wiele razy w jednym zadaniu:
var a = 9, b = 3, c = 8, d = a + b + c;
d będzie teraz mieć wartość 20.
Obydwa operandy są konwertowane na typy pierwotne. Następnie, jeśli jeden z nich jest ciągiem znaków, oba są konwertowane na ciągi i łączone. W przeciwnym razie oba są konwertowane na liczby i dodawane.
null + null; // 0 null + undefined; // NaN null + {}; // "null [object Object]" null + ''; // "null"
Jeśli operandy są ciągiem i liczbą, liczba jest konwertowana na ciąg znaków, a następnie są one łączone, co może prowadzić do nieoczekiwanych wyników podczas pracy z ciągami, które wyglądają na liczbowe.
"123" + 1; // "1231" (nie 124)
Jeśli wartość boolowska jest podana zamiast dowolnej wartości liczbowej, wartość logiczna jest konwertowana na liczbę (0 dla fałszu, 1 dla prawdziwej) przed obliczeniem sumy:
prawda + 1 ; // 2 false + 5; // 5 null + 1; // 1 undefined + 1; // NaN
Jeśli wartość boolowska jest podana wraz z wartością ciągu, wartość boolowska jest konwertowana na ciąg znaków:
true + "1"; // "true1" false + "bar"; // "falsebar" Rozdział 14.10: Little / Big endian dla tablic maszynowych przy użyciu operatorów bitowych
Aby wykryć endian urządzenia
var isLittleEndian = true; (() => {var buf = new ArrayBuffer (4); var buf8 = new Uint8ClampedArray (buf);
    var data = new Uint32Array (buf); data [0] = 0x0F000000; if (buf8 [0] == = 0x0f) {isLittleEndian = false;}}) ();  
Little-Endian przechowuje większość znaczących bajtów od prawej do lewej.
Big-Endian przechowuje większość znaczących bajtów od lewej do prawej.
var myNum = 0x11223344 | 0; // 32-bitowa liczba całkowita ze znakiem var buf = new ArrayBuffer (4); var data8 = new Uint8ClampedArray (buf); var data32 = new Uint32Array (buf); data32 [0] = myNum; // przechowuj numer w tablicy 32Bit
Jeśli system używa Little-Endian, to wartościamibędą
8bitowymikonsole console.log (data8 [0] .toString (16)); // 0x44 console.log (data8 [1] .toString (16)); // 0x33 console.log (data8 [2] .toString (16)); // 0x22 console.log (data8 [3] .toString (16)); // 0x11
Jeśli system używa Big-Endian, wówczas wartościami 8-bajtowymi będą
console.log (data8 [0] .toString (16)); // 0x11 console.log (data8 [1] .toString (16)); // 0x22 console.log (data8 [2] .toString (16)); // 0x33 console.log (data8 [3] .toString (16)); // 0x44
Przykład, gdzie typ Endian jest ważny
var canvas = document.createElement ("canvas"); var ctx = canvas.getContext ("2d"); var imgData = ctx.getImageData (0, 0, canvas.width, canvas.height); // Aby przyspieszyć odczyt i zapis z bufora obrazu, możesz utworzyć widok bufora, który będzie // 32-bitowy, pozwalając na odczyt / zapis piksela w pojedynczej operacji var buf32 = new Uint32Array (imgData.data.buffer); // Maskuj kanały Red i Blue var mask = 0x00FF00FF; // bigEndianskie kanały pikseli Czerwony, zielony, niebieski, alfa, jeśli (isLittleEndian) {maska ​​= 0xFF00FF00; // małe estetyczne kanały pikseli Alpha, Blue, Green, Red} var len = buf32.length; var i = 0; while (i <len) {// Maskuj wszystkie piksele buf32 [i] & = mask; // Maskuj czerwony i niebieski} ctx.putImageData (imgData); Sekcja 14.11: Losuj między dwiema liczbami
Zwraca losową liczbę całkowitą między min i maks:
funkcja randomBetween (min, max) {return Math.floor (Math.random () * (max - min + 1) + min); }
Przykłady:
// randomBetween (0, 10); Math.floor (Math.random () * 11);
// randomBetween (1, 10); Math.floor (Math.random () * 10) + 1;
// randomBetween (5, 20); Math.floor (Math.random () * 16) + 5;
// randomBetween (-10, -2); Math.floor (Math.random () * 9) - 10; 

Rozdział 14.12: Symulowanie zdarzeń z różnymi prawdopodobieństwami
Czasami możesz potrzebować tylko symulować zdarzenie z dwoma wynikami, być może z różnymi prawdopodobieństwami, ale możesz znaleźć się w sytuacji, która wymaga wielu możliwych wyników z różnymi prawdopodobieństwami. Wyobraźmy sobie, że chcesz symulować zdarzenie, które ma sześć równie prawdopodobnych wyników. To jest całkiem proste.
function simulateEvent (numEvents) {var event = Math.floor (numEvents * Math.random ()); wydarzenie powrotne; }
// symulacja fair konsoli console.log ("Rolled a" + (simulateEvent (6) +1)); // Zwinięte 2
Jednak nie możesz chcieć równie prawdopodobnych wyników. Załóżmy, że masz listę trzech wyników przedstawionych jako tablica prawdopodobieństw w procentach lub wielokrotnościach prawdopodobieństwa. Taki przykład może być ważoną kością. Możesz przepisać poprzednią funkcję, aby zasymulować takie zdarzenie.
function simulateEvent (szanse) {var sum = 0; chance.forEach (function (chance) {sum + = chance;}); var rand = Math.random (); var chance = 0; dla (var i = 0; i <szansa.length; i ++) {szansa + = szanse [i] / suma; if (rand <chance) {return i; }} // nigdy nie powinno być osiągnięte, chyba że suma prawdopodobieństw jest mniejsza niż 1 //, ponieważ wszystkie są równe zeru lub niektóre są ujemnymi prawdopodobieństwami return -1; }
// symuluj ważone kości, gdzie 6 jest dwa razy bardziej prawdopodobne niż jakakolwiek inna twarz // używając wielokrotności prawdopodobieństwa console.log ("Rolled a" + (simulateEvent ([1,1,1,1,1,2]) + 1 )); // Przetoczenie 1
// przy użyciu prawdopodobieństwa console.log ("Zwinięte" + (simulateEvent ([1 / 7,1 / 7,1 / 7,1 / 7,1 / 7,2 / 7]) + 1) ); // Zwinięte 6
Jak zapewne zauważyłeś, funkcje te zwracają indeks, więc możesz mieć bardziej opisowe wyniki przechowywane w tablicy. Oto przykład.
var rewards = ["złota moneta", "srebrna moneta", "diament", "bożek miecz"]; var likelihoods = [5,9,1,0]; // najmniej prawdopodobne, że zdobędziesz miecza bożego (0/15 = 0%, nigdy), // najprawdopodobniej dostaniesz srebrną monetę (9/15 = 60%, więcej niż połowę czasu)
// symulacja zdarzenia, nagroda z dziennika console.log ("Otrzymasz" + nagrody [simulateEvent (likelihoods)]); // Otrzymujesz srebrną monetę Sekcja 14.13: Odejmowanie (-)
Operator odejmowania (-) odejmuje liczby.
var a = 9; var b = 3; var c = a - b;
c będzie teraz 6
Jeśli zamiast wartości liczbowej zostanie podany łańcuch lub wartość logiczna, zostanie ona przekształcona na liczbę przed obliczeniem różnicy (0 dla fałszu, 1 dla prawdziwej):
"5" - 1; // 4 7 - "3"; // 4 "5" - prawda; // 4
Jeśli nie można przekształcić wartości ciągu w liczbę, wynikiem będzie NaN:
"foo" - 1; // NaN 100 - "bar"; // NaN

Sekcja 14.14: Mnożenie (*)
Operator mnożenia (*) wykonuje mnożenie arytmetyczne na liczbach (literałach lub zmiennych).
console.log (3 * 5); // 15 console.log (-3 * 5); // -15 console.log (3 * -5); // -15 console.log (-3 * -5); // 15 

Sekcja 14.15: Maksymalne i minimalne
Funkcja Math.max () zwraca największą liczbę zero lub więcej.
Math.max (4, 12); // 12 Math.max (-1, -15); // -1
Funkcja Math.min () zwraca najmniejszą z zera lub więcej liczb.
Math.min (4, 12); // 4 Math.min (-1, -15); // -15
Uzyskiwanie maksimum i minimum z tablicy: var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9], max = Math.max.apply (Math, arr), min = Math.min.apply (Math, arr);
console.log (max); // Logi: 9 console.log (min); // Logi: 1
operator rozprzestrzeniania ECMAScript 6, uzyskanie maksimum i minimum tablicy:
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9], max = Math.max (.. .arr), min = Math.min (... arr);
console.log (max); // Logi: 9 console.log (min); // Logi: 1 

Sekcja 14.16: Ograniczanie liczby do zakresu Min / Max
Jeśli potrzebujesz zacisnąć liczbę, aby utrzymać ją w specyficznym ogranicznikuzakresu
funkcji(min, max, val) {return Math.min (Math.max (min , + val), max); }
console.log (clamp (-10, 10, "4,30")); // 4.3 console.log (clamp (-10, 10, -8)); // -8 console.log (zacisk (-10, 10, 12)); // 10 console.log (clamp (-10, 10, -15)); // -10
Przykład użycia przypadku (jsFiddle) Punkt 14.17: Sufit i sufit
()
Metoda ceil () zaokrągla liczbę w górę do najbliższej liczby całkowitej i zwraca wynik.
Składnia:
Math.ceil (n);
Przykład:
console.log (Math.ceil (0.60)); // 1 console.log (Math.ceil (0.40)); // 1 console.log (Math.ceil (5.1)); // 6 console.log (Math.ceil (-5.1)); // -5 console.log (Math.ceil (-5.9)); // -5
floor ()
Metoda floor () zaokrągla liczbę w dół do najbliższej liczby całkowitej i zwraca wynik.
Składnia:
Math.floor (n);
Przykład:
console.log (Math.ceil (0.60)); // 0 console.log (Math.ceil (0.40)); // 0 console.log (Math.ceil (5.1)); // 5 console.log (Math.ceil (-5.1)); // -6 console.log (Math.ceil (-5.9)); // -6 Rozdział 14.18: Pobieranie pierwiastka z liczby
Pierwiastek kwadratowy
Użyj Math.sqrt (), aby znaleźć pierwiastek kwadratowy liczby
Math.sqrt (16) # => 4
Korzeń Cube
Aby znaleźć pierwiastek z liczby, użyj Funkcja Math.cbrt ()
Wersja ≥ 6 Math.cbrt (27) # => 3 Znajdowanie n-roots
Aby znaleźć n-root, użyj funkcji Math.pow () i podaj wykładnik cząstkowy.
Math.pow (64, 1/6) # => 2 

Sekcja 14.19: Losowo z rozkładem gaussowskim
Funkcja Math.random () powinna dawać liczby losowe, które mają odchylenie standardowe zbliżone do 0. Podczas wybierania z talii kart lub symulacji rzut kostką to jest to, czego chcemy.
Ale w większości sytuacji jest to nierealistyczne. W świecie rzeczywistym przypadkowość ma tendencję do gromadzenia się wokół wspólnej wartości normalnej. Jeśli zostanie narysowany na wykresie, otrzymasz klasyczną krzywą dzwonową lub rozkład gaussowski.
W tym celu przy pomocy funkcji Math.random () jest względnie prosta.
var randNum = (Math.random () + Math.random ()) / 2; var randNum = (Math.random () + Math.random () + Math.random ()) / 3; var randNum = (Math.random () + Math.random () + Math.random () + Math.random ()) / 4;
Dodanie losowej wartości do ostatniej zwiększa wariancję liczb losowych. Dzielenie przez liczbę dodawanych wynikówwynik do zakresu 0-1.
normalizuje Dodanie więcej niż kilku random jest kłopotliwe, prosta funkcja pozwoli ci wybrać wariancję, którą chcesz.
// v to liczba losowań zsumowanych i powinna być większa niż> = 1 // zwracana liczba losowa między 0-1 wyłączną funkcją randomG (v) {var r = 0; dla (var i = v; i> 0; i -) {r + = Math.random ();
    } return r / v; }
Obrazek pokazuje rozkład losowych wartości dla różnych wartości v. Górny lewy jest standardowym pojedynczym poleceniem Math.random (), dolny prawy jest Math.random () zsumowany 8 razy. Jest to 5 000 000 próbek za pomocą Chrome.
Ta metoda jest najbardziej skuteczna przy v <5 

Sekcja 14.20: Math.atan2 w celu znalezienia kierunku
Jeśli pracujesz z wektorami lub liniami, na pewnym etapie będziesz chciał uzyskać kierunek wektora lub linii. Lub kierunek od punktu do innego punktu.
