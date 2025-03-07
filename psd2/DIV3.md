# W jaki sposób wykorzystać PSD2 do rozwiązania problemu KYC i rozpowszechnienia koncepcji cyfrowej tożsamości?

Wersja 3.1 (05/04/2018)

**Proponujemy rozwiązanie w zakresie KYC, które bazując na legislacji PSD2 umożliwia wykorzystanie, będącej w posiadaniu banku, informacji o tożsamości klienta. Skalowanie procesu KYC uzyskujemy poprzez wykorzystanie kryptograficznego poświadczenia tożsamości klienta uzyskane od jego banku. Dzięki temu bank, oprócz świadczenia usług finansowych, jest w stanie radykalnie ułatwić swoim klientom proces weryfikacji KYC w sytuacji, gdy chcą oni skorzystać z usług innych podmiotów w branży FinTech (zarówno bankowych jak i niebankowych), a w dalszej konsekwencji, staje się dla nich generatorem ich cyfrowej tożsamości w internecie.**

## 1. Wprowadzenie

#### 1.1 Jak weryfikować tożsamość online?

Internetowa weryfikacja tożsamości to próba rozwiązania następującego problemu: w jaki sposób w warunkach online uzyskać pewność, że osoba (klient) podająca się jako K rzeczywiście jest tą osobą K?

Istotne jest tu to, że jest to sytuacja online, czyli *nie* w realu. W sytuacji kontaktu w realu dokument ze zdjęciem można uznać za wystarczająco dobry sposób weryfikacji tożsamości (mimo swoich oczywistych wad: jest kosztowny w produkcji i relatywnie łatwo może być podrobiony, zwłaszcza w przypadku, gdy nie wiemy jak dokładnie powinien wyglądać oryginalny dokument, np. dowód tożsamości obcokrajowca).

Z oczywistych powodów w warunkach online zdjęcie, które jest integralną częścią dokumentu tożsamości, przestaje być użyteczne, bo nie ma go z czym porównać. 

#### 1.2 Problem: nieskalowalność KYC

Wymogi KYC narzucają na firmy konieczność ustalenia tożsamości każdego nowego klienta.

Wszystkie obecne procedury KYC mają jedną istotną wadę: nie skalują się. Przy pozyskaniu nowego klienta każda firma, która podlega wymogom KYC, musi samodzielnie dokonać ustalenia jego tożsamości, co jest kosztowne i czasochłonne (dla obu stron: firmy i jej klienta). Tak więc w obecnie istniejącym paradygmacie ten sam kosztowny i czasochłonny proces musi być wykonywany wielokrotnie przez kolejne firmy.

Jedynym znanym nam sposobem na skalowanie KYC jest wykorzystanie procedury tzw. testowego przelewu, który polega na tym, że klient poświadcza swoją tożsamość poprzez wykonanie przelewu ze swojego rachunku w innym banku do banku, który chce dokonać weryfikacji KYC. Oczywiste są wady tego rozwiązania:

* nie rozwiązuje to problemu dla podmiotów niebankowych,
* nie skaluje się więcej niż raz (bo nie można w ten sposób potwierdzić tożsamości w kolejnym banku),
* wymaga to od klienta dodatkowego wysiłku.

Niemniej tego rodzaju kombinowanie (tj. używanie przelewu bankowego do innych celów niż cel finansowy) pokazuje, że problem nieskalowalności KYC rzeczywiście istnieje.

Warty podkreślenia jest fakt, że outsourcing procesu KYC do specjalistycznej firmy, która się tym zajmuje, nie rozwiązuje problemu skalowania KYC. Nawet jeśli podmiot specjalizujący się w KYC dostanie zlecenie weryfikacji klienta K, którego wcześniej weryfikował dla innej firmy, to i tak cały proces KYC będzie musiał być uruchomiony od nowa, bo nie ma żadnego formalnego dowodu, że w obu przypadkach jest to rzeczywiście ten sam klient K.

#### 1.3 Co chcemy osiągnąć?

Szukamy rozwiązania dla procesu KYC, które:

- umożliwi skalowanie procedury KYC, czyli wyeliminuje konieczność powtarzania tego procesu przez kolejne firmy,
- będzie działać dla wszystkich firm, które podlegają wymogom KYC (tj. nie tylko dla podmiotów bankowych),
- będzie miało realną szansę na masową adopcję, zarówno po stronie biznesów jak i ich klientów,
- otworzy drogę na inne niż KYC zastosowania, w szczególności do rozpowszechnienia koncepcji cyfrowej tożsamości.

## 2. Strategia dualnej funkcjonalności: skalowalny KYC na grzbiecie autoryzacji PSD2

#### 2.1 Rationale

Naszą intencją jest zbudowanie kanału mocnej autoryzacji transakcji bankowych w PSD2 poprzez zastosowanie kryptografii asymetrycznej, a następnie skorzystanie z faktu, że ten sam klucz prywatny (i mechanizm jego ochrony), który służy do autoryzacji w PSD2, może jednocześnie być użyty do skalowania procesu KYC, a także do wielu innym celów powiązanych z cyfrową tożsamością, np:

- kryptograficzna ochrona tożsamości i reputacji,
- kryptograficznie poświadczony stan faktyczny,
- kryptograficzne podpisywanie umowy cywilnoprawnej,
- internetowa kancelaria notarialna.

Zbudowanie mechanizmu mocnej autoryzacji w PSD2 nie jest więc celem ostatecznym - bardziej pełni funkcję konia trojańskiego, który da użytkownikom istotny powód, żeby posiadali (i chronili) w swoim telefonie swój unikalny klucz prywatny, ściśle związany z ich tożsamością (i potencjalnie także z ich reputacją), podobnie jak PESEL - tyle że klucz prywatny jest z założenia niejawny.

Chcemy zatem wykorzystać dogodną sytuację, stworzoną przez PSD2, do wprowadzenia do powszechnego użycia mechanizmu ochrony klucza prywatnego po stronie użytkownika. Mając tego rodzaju mechanizm, masowo (i często) używany z racji PSD2, możemy wprowadzić skalowalny proces KYC, a także zacząć budować przeróżne produkty zmierzające do cyfryzacji "wszystkiego".

Oznacza to, że nasza aplikacja mobilna będzie miała dwie spokrewnione ze sobą funkcjonalności, obie bazujące na tym samym kluczu prywatnym:

- autoryzacja transakcji bankowych w PSD2,
- weryfikacja tożsamości dla potrzeb KYC.

Dzięki pełnieniu tej podwójnej roli, liczymy na to, że już w momencie uruchomienia nasz system KYC będzie obejmował znaczącą liczbę użytkowników pasywnych (tj. tych którzy są potencjalnym obiektem KYC), co jest krytycznie ważne dla uczynienia go realnie przydatnym dla użytkowników aktywnych (tj. firm które przeprowadzają KYC).

#### 2.2 Implementacja

Do wdrożenia naszego systemu autoryzacji w PSD2 na pewno potrzebne będzie partnerstwo z jakimś podmiotem bankowym.

Załóżmy, że jakiś bank uznałby, że nasz system spełnia jego wymogi w zakresie kanału mocnej autoryzacji w PSD2 i rekomenduje swoim klientom użycie naszej aplikacji mobilnej do tego celu.

Co się wtedy dzieje?

Partner bankowy dostaje od nas system mocnej autoryzacji (za darmo lub odpłatnie - jest to kwestia negocjacji), a w zamian, poprzez rozpowszechnienie naszego systemu autoryzacji PSD2 wśród swoich klientów, czyni naszą aplikację mobilną (i tym samym nasz system weryfikacji tożsamości) wysoce użytecznym narzędziem dla firm potrzebujących sprawnej i szybkiej weryfikacji KYC.

## 3. Autoryzacja w PSD2 poprzez kryptografię asymetryczną

#### 3.1 Istniejące rozwiązania

Obecne podejścia w zakresie mocnej autoryzacji transakcji bankowych są następujące:

- jesteś wypytywany o jakiś wcześniej ustalony przez obie strony sekret (np. nazwisko panieńskie matki),
- dostajesz esemesa z kodem,
- weryfikujesz się poprzez narzędzie typu Google Authenticator.

#### 3.2 Proponowane rozwiązanie

Do autoryzacji transakcji bankowej w PSD2 użyjemy kryptografii asymetrycznej, tj, kombinacji klucza prywatnego X i sprzężonego z nim klucza publicznego Y. Generalnie sprowadza się to do tego, że generujemy dla klienta K klucz prywatny X i w przyszłości uznajemy, że posiadanie klucza X jest tożsame z byciem klientem K.

Chociaż do autoryzacji w PSD2 nie jest potrzebny blockchain, ze względu na dalsze potencjalne zastosowania naszego systemu, wygenerowane klucze będą kompatybilne z platformą smart-kontraktową [EOS](https://eos.io/).

Warte podkreślenia jest to, że:

- naszym zamiarem nie jest zbudowanie całego procesu autoryzacji w PSD2, a jedynie jednego z wymaganych dwóch niezależnych kanałów,
- bez problemu możemy wspierać autoryzację w wersji dynamicznej, tj. dodawać elementy łączące daną transakcję z określoną kwotą i określonym odbiorcą (np. ostatnie cyfry rachunku i kwota transakcji).

#### 3.3 Konfiguracja procesu autoryzacji

Konfiguracja (albo aktywacja) naszego procesu autoryzacji PSD2 dla nowego klienta wygląda następująco:

1. Klient K instaluje na swoim telefonie wykonaną przez nas aplikację mobilną, która generuje unikalną parę kluczy kryptograficznych: klucz prywatny X i klucz publiczny Y. 
2. Klucz prywatny X jest trzymany w telefonie i nigdy nikomu poza klientem K nie jest ujawniany (klucz prywatny jest chroniony PIN-em lub biometrycznie - być może da się tu sprytnie wykorzystać właściwości biometryczne EOSa).
3. Aplikacja przekazuje bankowi B klucz publiczny Y klienta K.

W wyniku powyższego procesu bank B może w swojej bazie danych przypisać tożsamość klienta K do jego klucza publicznego Y. Prawdopodobnie wymagało to będzie pewnego rodzaju procedury aktywacji (podobnie jak aktywujemy nowo otrzymaną kartę debetową), tak żeby bank B miał pewność, że wygenerowany przez naszą aplikację klucz publiczny rzeczywiście należy do klienta K.

#### 3.4 Działanie procesu autoryzacji

Zakładając że dla klienta K powyższa konfiguracja procesu została już przeprowadzona, autoryzacja transakcji bankowej w PSD2 wygląda wtedy następująco:

1. Poprzez aplikację mobilną bank B wysyła do klienta K propozycję przelewu bankowego (ze wszystkimi potrzebnymi szczegółami typu adresat płatności i kwota).
2. Klient K wyraża zgodę na tę propozycję (tj. autoryzuje tę transakcję) poprzez podpisanie jej swoim kluczem prywatnym X.

Autoryzacja sprowadza się zatem do potwierdzenia, że klient K dysponuje kluczem prywatnym X, który odpowiada kluczowi publicznemu Y. W ten sposób bank B ma pewność, że propozycja transakcji finansowej została zatwierdzona przez klienta K, bo tylko on może być posiadaczem klucza prywatnego X, który odpowiada kluczowi publicznemu Y, przypisanemu w banku B klientowi K.

#### 3.5 Odzyskiwanie klucza

Procedura odzyskiwania zgubionego / skradzionego klucza prywatnego może przebiegać na dwa sposoby:

1. Najprostszym rozwiązaniem wydaje się być wykorzystanie do tego celu banku i uruchomienie procedury analogicznej do odzyskiwania hasła w tradycyjnych systemach, tj. zablokowanie istniejącego klucza i aktywacja nowego. 
2. Alternatywnym sposobem jest wykorzystanie dość spektakularnych (jak na blockchain) możliwości EOSa w tym zakresie.

#### 3.6 Korzyści

Autoryzacja poprzez kryptografię asymetryczną na pewno jest rozwiązaniem niegorszym niż alternatywne metody (np. esemesy lub Google Authenticator). Dodatkowe korzyści są takie:

1. Dzięki EOSowej funkcjonalności *account permissions* staje się możliwe zbudowanie po stronie użytkownika dowolnie złożonej struktury delegacji uprawnień w zakresie autoryzacji transakcji finansowych. Przestaje być wtedy potrzebne często stosowane (szczególnie w sytuacjach biznesowych) "pożyczanie" haseł lub ich współdzielenie. W naszym paradygmacie użytkownik nigdy nie powinien mieć powodu aby ujawnić swój klucz prywatny komukolwiek - oczywiście o ile będą dostępne narzędzia do sprawnej delegacji uprawnień i ich odwoływania.
2. Bank B może łatwo uzyskać kryptograficzne potwierdzenie szczegółów transakcji podpisane kluczem prywatnym X klienta K - wtedy bank B ma oficjalny dowód na to, że klient K zgodził się na zaproponowaną mu transakcję. Według naszej wiedzy inne metody autoryzacji nie dają takiej możliwości.

## 4. Skalowalny proces KYC poprzez wykorzystanie kryptograficznego poświadczenia banku

#### 4.1 Koncepcja

Najogólniej mówiąc, skalowalny KYC polega na tym, że jeden podmiot (w naszym przypadku bank) przeprowadza weryfikację tożsamości danej osoby (klienta) K, a następnie wynik tej weryfikacji jest udostępniany innym podmiotom (bankowym i niebankowym).

Do konstrukcji skalowalnego KYC wykorzystujemy następujący zestaw założeń:

- (niemal) każdy dorosły człowiek ma konto w banku,
- każdy bank zna tożsamość każdego swojego klienta,
- każdy bank otworzy swoje API z racji PSD2, tak więc możliwe będzie wydobywanie z banku informacji, w tym także tych dotyczących tożsamości klienta,
- każdy bank dysponuje [kwalifikowanym podpisem elektronicznym](https://pl.wikipedia.org/wiki/Podpis_kwalifikowany).

Naturalną konsekwencją wydaje się zatem istnienie możliwości zrobienia użytku z informacji o tożsamości klientów bankowych (tj. informacji, które banki i tak posiadają) w celu radykalnego usprawnienia procesu KYC.

Idąc tym tropem, proponujemy mechanizm, który umożliwia klientowi K dostarczenie dowolnej firmie F podpisanego elektronicznie przez wiarygodny podmiot (w naszym przypadku bank B) certyfikatu poświadczającego jego (tj. klienta K) tożsamość.

**Skalowanie procesu KYC uzyskujemy więc poprzez wykorzystanie kryptograficznego poświadczenia tożsamości klienta uzyskane od jego banku.**

Oznacza to, że nasz pomysł w zakresie KYC sprowadza się *de facto* do tego: w kontrolowany sposób wyprowadzamy na zewnątrz informacje, które do tej pory leżały bezużytecznie (z perspektywy świata zewnętrznego) w systemie bankowym. Dzięki temu bank, oprócz świadczenia usług finansowych, staje się generatorem cyfrowej tożsamości swoich klientów.

#### 4.2 Wymagania

Żeby powyższy mechanizm KYC mógł funkcjonować potrzebne będzie spełnienie następujących warunków:

1. Integralną częścią naszej aplikacji musi być możliwość weryfikacji certyfikowanego podpisu elektronicznego, tak żeby firma F mogła w łatwy sposób uzyskać pewność, że otrzymane od banku B informacje na temat klienta K rzeczywiście zostały przez ten bank wygenerowane i nie zostały zmodyfikowane po ich podpisaniu. Jest to funkcjonalność podobna do tej, która jest oferowana przez powszechnie dostępne serwisy internetowe, np. [MadKom](https://madkom.pl/weryfikacja-podpisu-elektronicznego/).
2. Wymagane jest żeby nasz partner bankowy rozszerzył swoje API (które i tak będzie musiał publicznie udostępnić ze względu na PSD2) o funkcjonalność lekko wykraczającą poza wymagania PSD2: dostarczanie na życzenie TPP (Third Party Provider) kryptograficznie podpisanej informacji o tożsamości danego klienta. Zakładamy, że postulat ten relatywnie łatwo może być przez bank spełniony, gdyż nie wymaga on istotnych zmian technologicznych po stronie banku.
3. Ponieważ my, jako twórcy i operatorzy aplikacji mobilnej będącej w posiadaniu klienta K, pełnimy rolę TPP (Third Party Provider), musimy być podmiotem zarejestrowanym w KNF zgodnie z wymagami PSD2. Wydaje się, że licencja AIS (Account Information Service) w tym przypadku będzie wystarczająca.

#### 4.3 Proces podstawowy

Załóżmy, że firma F potrzebuje dokonać weryfikacji KYC klienta K i ma zaufanie do banku B, tj. podpisane elektronicznie oświadczenia banku B w zakresie tożsamości klienta K uznaje za prawdziwe.

Wtedy proces KYC, inicjowany przez firmę F, może wyglądać następująco:

1. Na prośbę firmy F nasza aplikacja mobilna wysyła do banku B zapytanie o podpisane elektronicznie przez bank B informacje dotyczące tożsamości klienta K (tj. wszystko co jest potrzebne do weryfikacji KYC: imię, nazwisko, PESEL, numer dowodu osobistego itp).
2. Następuje autoryzacja tego zapytania przez klienta K, zgodnie z wymogami PSD2 dla AIS.
3. Odpowiedź uzyskana od banku jest przesyłana do firmy F, która uzyskuje w ten sposób wiarygodne (bo kryptograficznie potwierdzone przez bank B) informacje na temat tożsamości klienta K.
4. Za pomocą naszej aplikacji firma F weryfikuje autentyczność i integralność otrzymanej informacji.

*Uwaga*: Ze względów bezpieczeństwa do podpisanego przez bank pakietu informacji dołączamy losowy ciąg znaków (tzw. *nonce*), który wcześniej (przed uruchomieniem tego całego procesu weryfikacji) dostarcza nam firma F. Tym sposobem firma F ma pewność, że otrzymana informacja została wygenerowana przez bank B specjalnie dla potrzeb tego konkretnego przypadku (a więc jest aktualna).

#### 4.4 Proces rozszerzony

Ponieważ bank B używa oferowanego przez nas wyżej opisanego kryptograficznego systemu autoryzacji transakcji, do otrzymywanego przez firmę F od banku B pakietu informacji z danymi KYC dla klienta K możemy też dołączyć informację o kluczu publicznym Y, z którym w banku B powiązana jest tożsamość klienta K.

Wtedy firma F:

* po standardowym zweryfikowaniu posiadania przez klienta K klucza prywatnego X uzyskuje dodatkową pewność co do tożsamości klienta K,
* a ponadto może, podobnie jak bank B, powiązać w swoim systemie tożsamość klienta K z tym kluczem publicznym i w przyszłości autoryzować klienta K poprzez nasz system, przyjmując założenie że posiadanie klucza prywatnego X jest tożsame z byciem klientem K.

#### 4.5 Korzyści

Firma F unika konieczności przeprowadzenia kosztownej i czasochłonnej procedury KYC, bo korzysta z wyników procedury KYC przeprowadzonej wcześniej przez bank B.

#### 4.6 Legislacja

Wymagania legislacyjne są następujące:

1. Ustawa musi zapewnić, że korzystanie z wyników weryfikacji KYC, wykonanej uprzednio przez inny podmiot, jest wiarygodną formą weryfikacji KYC. Możemy przyjąć, że obecne ustawodawstwo już temu sprzyja, bo legalne jest zlecenie przeprowadzenia KYC innej firmie (tj. outsource'owanie KYC).
2. Ustawa musi zapewnić, że podpisane kryptograficznie oświadczenie banku odnośnie tożsamości jego klienta jest wiarygodną formą weryfikacji KYC. Możemy wstępnie przyjąć, że będzie to możliwe, skoro już teraz wyżej opisany przelew testowy jest uznawany za wiarygodną formę weryfikacji KYC, a nasza metoda na pewno nie jest mniej wiarygodna.

## 5. Czym nasze rozwiązanie w zakresie KYC różni się od profilu zaufanego?

Wedle [dokumentacji](https://www.gov.pl/cyfryzacja/profil-zaufany-ego-) Ministerstwa Cyfryzacji profil zaufany to bezpłatna metoda potwierdzania tożsamości obywatela w systemach elektronicznej administracji.

> Profil zaufany działa jak odręczny podpis. Możesz dzięki niemu wysyłać przez internet dokumenty i wnioski do różnych urzędów (np. wnieść podanie, odwołanie, skargę). Profil zaufany potwierdza tożsamość obywatela  — podpis potwierdzony profilem zaufanym, podobnie jak kwalifikowany podpis elektroniczny, skutecznie zastępuje w kontaktach z podmiotami publicznymi podpis własnoręczny.

Na pierwszy rzut oka profil zaufany wygląda na rozwiązanie bardzo podobne do naszego. Co więcej, podobnie jak w naszym podejściu jednym z podmiotów zdolnych do wygenerowania takiego profilu dla użytkownika jest serwis bankowy. Kilka banków w Polsce oferuje taką usługę.

Jest jednak istotna różnica: zastosowanie profilu zaufanego jest ograniczone do serwisów państwowych. Ograniczenie to wynika ze sposobu działania tego systemu: polega on na tym, że po założeniu profilu zaufanego użytkownik uzyskuje dostęp do wspólnego dla systemów państwowych mechanizmu logowania, lecz nie jest to równoważne z uzyskaniem uniwersalnej cyfrowej tożsamości. Tak więc profil zaufany z założenia nie może być rozszerzony na sferę niepaństwową i tym samym nie rozwiązuje problemu KYC dla firm.

Niemniej porównanie naszego rozwiązania do profilu zaufanego wydaje się jak najbardziej uzasadnione. Można nawet powiedzieć, że nasz system oferuje biznesom rozwiązanie w zakresie KYC analogiczne do tego, jakie profil zaufany oferuje urzędom państwowym w zakresie mechanizmu logowania, tj. weryfikacji tożsamości obywatela w warunkach online.

## 6. Rozszerzenie 1: Kryptograficzna ochrona tożsamości i reputacji

#### 6.1 Kontekst

Coraz bardziej powszechna staje się delegacja autoryzacji użytkownika między różnymi serwisami internetowymi, tj. usługa typu *zaloguj się przez Facebook*. Usługa ta w swojej obecnej formie jest niczym innym niż wykorzystaniem reputacji (i/lub unikalnej tożsamości), którą dany użytkownik ma na jakimś znanym serwisie (typu Facebook, Twitter, Gmail, GitHub) do utworzenia unikalnej tożsamości (i w konsekwencji możliwości budowy reputacji wokół tej tożsamości) na jakimś innym, mniej popularnym serwisie S.

Przyczyna coraz większej popularności tego rodzaju mechanizmu jest oczywista: większa wygoda dla użytkownika sprawia, że łatwiejsze dla serwisu S staje się pozyskanie nowego klienta.

Warto podkreślić, że w tym przypadku potwierdzenie rzeczywistej (tj. zgodnej z realem) tożsamości użytkownika nie jest konieczne (tj. proces KYC może nie być wymagany). Liczy się tylko to, żeby serwis S mógł w swoim systemie przypisać nowego użytkownika do jakiegoś unikalnego identyfikatora dostarczonego przez serwis typu Facebook i żeby w przyszłości system logowania Facebooka autoryzował dostęp tego użytkownika do serwisu S.

#### 6.2 Problem

W obecnej formie działania mechanizm delegacji autoryzacji sprawia, że użytkownik w pełni powierza serwisowi typu Facebook swoją tożsamość na innych serwisach. Innymi słowy, tożsamość danego użytkownika na serwisie S nie należy do niego samego lecz do zewnętrznego podmiotu. Firma typu Facebook ma zatem pełną kontrolę na tą tożsamością i może zrobić dowolną rzecz uzurpując sobie tę tożsamość (w tym także kompletnie zniszczyć reputację danej osoby).

#### 6.3 Koncepcja

Wykorzystując fakt posiadania przez naszych użytkowników klucza prywatnego, łatwo nam będzie zaoferować im dobry substytut dla funkcjonalności typu *zaloguj się przez Facebook*. Mechanizm użycia kryptografii asymetrycznej do ochrony tożsamości i reputacji jest dobrze opisany w dokumentacji projektu [Jolocom](https://jolocom.com/).

#### 6.4 Korzyści

Przy użyciu klucza prywatnego do definiowania unikalnej tożsamości powyższy problem całkowicie znika. Właścicielem tożsamości jest zawsze właściciel klucza prywatnego i tylko on ma kontrolę nad reputacją związaną z tą tożsamością.

Co więcej, możliwe się staje dodatkowe zwiększenie bezpieczeństwa takiej cyfrowej tożsamości. Dostęp do serwisu S (i tym samym do reputacji tam zbudowanej) można uzależnić od spełnienia dwóch warunków jednocześnie:

* udowodnienie posiadania klucza prywatnego X,
* plus dodatkowo udowodnienie bycia klientem banku B z przypisanym tam kluczem publicznym Y, który odpowiada kluczowi prywatnemu X - można łatwo to uzyskać poprzez kryptograficzne poświadczenie uzyskane od banku B, podobne to tego, jakie proponujemy w zakresie KYC.

Powyższe podwójne zabezpieczenie chroni użytkownika w przypadku, gdy klucz prywatny zostanie mu skradziony - oczywiście przy założeniu że użytkownik zgłosi tę kradzież do swojego banku. Warto też zauważyć, że w tym układzie bank B pełni jedynie rolę strażnika tożsamości użytkownika, ale nigdy nie staje się jej właścicielem.

## 7. Rozszerzenie 2: Kryptograficznie poświadczony stan faktyczny

#### 7.1 Problem

Problemy są dwojakiego rodzaju:

1. Uzyskanie wiarygodnego zaświadczenia potwierdzającego stan faktyczny bywa trudne i czasochłonne, podobnie jak weryfikacja autentyczności takiego zaświadczenia.
2. W praktyce użytkownicy nie mają żadnej kontroli nad komercyjnym wykorzystaniem informacji na swój temat, w tym także swoich danych osobowych.

#### 7.2 Koncepcja

W aplikacji mobilnej klienta K posługującego się kluczem publicznym Y dokonujemy wpisów stwierdzających stan faktyczny, który wynika z dokumentów istniejących w formie tradycyjnej, np:

- *Posiadacz klucza publicznego Y jest pełnoletni.*
- *Posiadacz klucza publicznego Y ma wykupione ubezpieczenie OC w firmie F.*
- *Posiadacz klucza publicznego Y mieszka pod adresem A.*
- *Posiadacz klucza publicznego Y ukończył uczelnię U.*
- *Posiadacz klucza publicznego Y jest wspólnikiem w spółce S.*

Każdy taki wpis ma przypisaną datę kiedy został dokonany i jest podpisany certyfikowanym podpisem elektronicznym instytucji zaufania publicznego. W ten sposób instytucja ta gwarantuje prawdziwość informacji zawartej w tym wpisie.

#### 7.3 Proces

Proces udostępniania powyższych informacji firmie F przez klienta K może wyglądać następująco:

1. Za pomocą aplikacji mobilnej firma F uzyskuje zgodę klienta K na udostępnienie informacji na jego temat.
2. Aplikacja mobilna klienta K wysyła firmie F:
   * wymagane przez nią informacje podpisane kryptograficznie przez zaufaną instytucję,
   * dowód klienta K na posiadanie dostępu do klucza prywatnego X,
   * uzyskany od banku B dowód na związek pomiędzy kluczem publicznym Y a tożsamością klienta K.

#### 7.4 Korzyści

Uzyskujemy dwojakiego rodzaju korzyści:

1. Następuje migracja informacji zawartych w tradycyjnych dokumentach papierowych do formy cyfrowej, co oczywiście oznacza redukcję kosztów i możliwości fałszowania.
2. Następuje przejęcie pełnej kontroli nad informacją przez podmiot, do którego ona należy. W tym nowym paradygmacie każdorazowo gdy informacja jest przekazywana osobie trzeciej, musi się na to zgodzić jej właściciel, tj. posiadacz klucza prywatnego. Możliwe staje się też przekazywanie minimalnej informacji, jaka jest w danej sytuacji potrzebna, np. żeby udowodnić swoją pełnoletność nie trzeba przekazywać pełnej daty urodzenia, lecz tylko fakt bycia starszym niż dany próg wiekowy.
3. Pełna kontrola posiadacza klucza prywatnego nad informacją otwiera także możliwość świadomego sprzedawania własnych danych demograficznych (których prawdziwość jest poświadczona kryptograficznie) podmiotom zainteresowanym tego rodzaju danymi.

#### 7.5 Legislacja

Ustawa musi dać wsparcie dla wiarygodności tego typu dokumentów cyfrowych.

## 8. Rozszerzenie 3: Kryptograficzne podpisywanie umowy cywilnoprawnej

#### 8.1 Problem

Zawieranie umów cywilnoprawnych przez internet jest wysoce problematyczne. Firmy, które oferują rozwiązania w tym zakresie bez użycia kryptografii, np. [DocuSign](https://www.docusign.com), wbrew temu co jest głoszone w [ich materiałach marketingowych](https://www.docusign.com/videos/are-electronic-signatures-legally-binding), nie są w stanie dostarczyć metody, która byłaby prawnie wiążąca. Więcej szczegółów na ten temat można znaleźć w [tej publikacji](https://www.cryptomathic.com/news-events/blog/us-court-rejects-docusign-e-signatures-as-method-to-provide-digital-authorization).

Solidną alternatywą wobec DocuSign mogłoby być użycie certyfikowanego podpisu elektronicznego, lecz ze względu na koszty i wymagania dotyczące dodatkowego hardware'u, nie jest to metoda mająca szansę na masową adopcję.

#### 8.2 Koncepcja

Podobnie jak w przypadku skalowalnego KYC, kryptograficzne potwierdzenie uzyskane od banku B pozwala nam powiązać klucz prywatny X klienta K z jego tożsamością. Otwiera to możliwość wykorzystania klucza prywatnego X do podpisywania prawnie wiążących umów cywilnoprawnych, np. umowa NDA, umowa zlecenia, umowa o dzieło itp.

#### 8.3 Korzyści

Umowy podpisane uwiarygodnionym przez bank kluczem prywatnym stają się prawnie wiążące. Likwidujemy w ten sposób główną wadę rozwiązania oferowanego przez DocuSign.

#### 8.4 Legislacja

Zakładamy, że ustawa już obecnie uznaje kryptograficznie podpisane umowy za prawnie wiążące.

## 9. Rozszerzenie 4: Internetowa kancelaria notarialna

#### 9.1 Problem

Niektóre czynności prawne, zarówno jednostronne (np. udzielenie pełnomocnictwa) jak i wielostronne (np. umowa spółki) wymagają udziału notariusza. Korzystanie z usługi kancelarii notarialnej wciąż pociąga za sobą konieczność fizycznego stawienia się klienta w takiej kancelarii, mimo że oferuje ona usługę o charakterze czysto formalnym (tj. niematerialnym).

#### 9.2 Koncepcja

W większości przypadków jedynym istotnym powodem konieczności fizycznego pojawienia się u notariusza jest umożliwienie mu weryfikacji naszej tożsamości. Używając metody analogicznej do skalowalnego KYC notariusz jest w stanie dokonać skutecznej weryfikacji tożsamości online.

Gdybyśmy przyjęli, że taka weryfikacja tożsamości jest wystarczająco wiarygodna, rola notariusza mogłaby wtedy wyglądać następująco: weryfikuje on tożsamość swoich klientów online, a następnie poświadcza on swoim certyfikowanym podpisem elektronicznym autentyczność i zgodność z prawem ich oświadczeń woli.

#### 9.3 Korzyści

Otwieramy w ten sposób drogę dla internetowych kancelarii notarialnych, oferujących usługę notarialną bez konieczności organizacji fizycznego spotkania.

#### 9.4 Legislacja

Ustawa musi dać wsparcie dla wiarygodności tego typu nowej formy usług notarialnych.

## 10. Monetyzacja systemu

Warto zauważyć, że:

1. Istotą naszej aplikacji mobilnej jest ochrona klucza prywatnego, co oznacza, że pełni ona rolę analogiczną do portfela kryptowalutowego. Jest jednak istotna różnica: nasza aplikacja nie zajmuje się obsługą związanych z tym kluczem kryptowalut (tj. otrzymywanie i wysyłanie płatności), lecz obsługą związanych z tym kluczem danych osobowych i informacji. Klucz prywatny chroni zatem w naszym przypadku informację i tożsamość, a nie instrument finansowy.
2. Mimo że nasz generator kluczy kryptograficznych będzie od samego początku kompatybilny z blockchainem EOSa, żadna z wyżej opisanych propozycji nie wymaga interakcji z blockchainem. W przyszłości, gdy wymyślimy nowe funkcjonaliści, to się może zmienić, ale na razie warto postrzegać to jako zaletę: w okresie początkowym nie jesteśmy uzależnieni od konkretnej platformy technologicznej.
3. Przy sojuszu z dużym partnerem bankowym nasza aplikacja mobilna ma realne szanse na dość masową adopcję - chociażby ze względu na jej rolę w zakresie autoryzacji PSD2.

Najprostszą metodą monetyzacji naszego systemu wydaje się komercjalizacja bardziej zaawansowanych funkcjonalności naszej aplikacji mobilnej (np. delegacja uprawnień związanych z danym kluczem prywatnym, podejmowanie decyzji poprzez głosowanie, raportowanie, backup danych itp.), albo pójście w kierunku funkcjonalości oferowanych przez system [Factom](https://www.factom.com/), tj. publikowanie hashy dokumentów na blockchainie EOSa celem udowodnienia ich istnienia w danym czasie i/lub zawierania konkretnej treści.

Można też spekulować, że w przyszłości zaczną powstawać podmioty biznesowe, które będą specjalizować się w przechowywaniu, ochronie i selektywnym udostępnianiu osobom trzecim informacji dotyczących danego klienta - podobnie jak teraz banki przechowują jego prawa majątkowe. Nasza aplikacja, traktowana jako sejf dla klucza prywatnego, wydaje się dobrym zalążkiem dla interfejsu użytkownika w takim nowym paradygmacie.

Alternatywną opcją jest rozbudowa naszej aplikacji mobilnej w kierunku obsługi finansowej tokenów EOSa i interakcji ze zdecentralizowanymi aplikacjami budowanymi przez inne biznesy na tej platformie. Korzystając z naszej kompatybilności z blockchainem EOSa, wystarczy zarejestrować klucze prywatne naszych użytkowników na tym blockchainie żeby otworzyć im dostęp do bogatego ekosystemu przeróżnych aplikacji, jakie (miejmy nadzieję) w przyszłości tam powstaną. Wówczas dobrą formą finansowania naszego systemu może być dochód z puli inflacyjnej EOSa - oczywiście przy założeniu, że nasz system będzie postrzegany jako *pro publico bono*.

## 11. Szerszy kontekst: Digital Identity

Propozycje opisane w niniejszym dokumencie to podzbiór większego zagadnienia znanego jako [Cyfrowa Tożsamość](http://di.com.pl/cyfrowa-tozsamosc-56607) (Digital Identity) albo, w przypadku użycia systemów rozproszonych, Zdecentralizowana Weryfikacja Tożsamości (Decentralized Identity Verification, w skrócie DIV).

W zakresie DIV pierwsze próby podjęcia tego tematu sięgają 2013 roku, kiedy to Daniel Larimer (*nota bene* twórca EOSa) wystąpił z pomysłem systemu zdecentralizowanej tożsamości o nazwie [Keyhotee](https://www.youtube.com/watch?v=3pZaTdEtK-8). Ten system nigdy nie powstał, ale jego idea wydaje się całkiem słuszna.

Obecnie istnieje [spora liczba projektów blockchainowych](https://github.com/peacekeeper/blockchain-identity), które podejmują rożne aspekty cyfrowej tożsamości i jej weryfikacji. Najważniejsze naszym zdaniem są te dwa:

- [Civic](https://www.civic.com/) ([whitepaper)](https://tokensale.civic.com/CivicTokenSaleWhitePaper.pdf)
- [Decentralized Identity](https://decentralized.id/) ([whitepaper biznesowy](https://decentralized.id/docs/DID-whitepaper.pdf), [whitepaper techniczny](https://decentralized.id/docs/DID-tech.pdf))

Dostępna jest dość wiarygodna [recenzja](https://www.scottbrady91.com/Blockchain-Identity/Technical-Review-of-Civics-Secure-Identity-Platform) systemu Civic. Jest ona całkiem pozytywna - główny zarzut sprowadza się do krytyki odstąpienia od używania standardów na rzecz swoich własnych wynalazków:

> Civic really should have used OAuth and OpenID Connect, instead of rolling their own authentication protocol.

Tak więc pomysł jest oceniany jako bardzo dobry, ale wykonanie jako dość niefortunne. Dodatkowym minusem jest fakt, że Civic bazuje na platformie [RootStock](https://www.rsk.co/), co oznacza, że będzie się zmagał ze wszystkimi problemami, jakie ma w sobie Bitcoin.

W przypadku projektu Decentralized Identity, też jest ciekawa sytuacja, bo wygląda na to, że jego twórcy doszli do ściany w zakresie możliwości Ethereum:

> We found Ethereum smart contracts unfit for computations that go beyond than the basics. While we understand that the technology is just growing up, we found that not being able to do computations (like hashing) on the Blockchain is a major drawback. The global computational power isn’t available for Dapps yet.

W kontekście możliwości EOSa, ta deklaracja też jest intrygująca:

> At the time of writing, there exists no blockchain that is truly public and stateless. All current blockchain technologies intend to store data. We just want to store the receipt of an ID transfer; not the data. In the matter of transferring an ID token/nugget, we only require a decentralised transfer of data. The data structures used by current blockchain technologies is restrictive and do not allow for expansion or abstraction. We call for a new, stateless, public Blockchain.

## 12. Pozycja konkurencyjna

Nasza pozycja konkurencyjna wygląda dość korzystnie ponieważ:

- Działamy w cieniu firm dużo większych od nas (np. Civic, Decentralized Identity) - one już wykonały sporo roboty za nas i dodatkowo uwiarygadniają sensowność naszego przedsięwzięcia.
- Mamy precyzyjną specyfikację (ich kod źródłowy) i relatywnie małe zadanie (bo w pierwszym etapie zajmujemy się tylko KYC), więc dokładnie wiadomo co trzeba robić i nie tracimy czasu i kapitału na eksperymentowanie.
- Mamy technologię (platforma EOS), która jest wyraźnie lepsza od tej, którą wybrali inni, bo jest pozbawiona istotnych ograniczeń (np. opłaty transakcyjne, niewydolność i powolność procesowania transakcji), a dodatkowo zawiera sprzyjające nam funkcjonalności (np. procedura odzyskiwania skradzionego / zgubionego klucza prywatnego i jego biometrycza ochrona).
- Tego rodzaju tematy jak cyfrowa tożsamość mają specyfikę lokalną, więc nasze położenie geograficzne daje nam przewagę w tym rejonie Europy. Możemy też podpatrzyć z kim Civic zawarł alianse biznesowe w USA i zrobić podobne układy lokalnie.


## 13. Proponowana nazwa systemu

Nazwa powinna nawiązywać do czegoś, co jest unikalne dla danego użytkownika i służy do potwierdzania jego tożsamości i autoryzacji różnego rodzaju działań. Najlepiej coś kojarzącego się z podpisem.

Dodatkowym warunkiem jest dobre funkcjonowanie nazwy zarówno w języku polskim jak i angielskim.

Proponujemy nazwę *Sygnet* i domenę *sygnet.eu*. Spełnia ona wszystkie powyższe postulaty, a dodatkowo jej końcówka *net* sugeruje coś związanego z internetem.

> Signet - a small seal, especially one set in a ring, used instead of or with a signature to give authentication to an official document.

## 14. Disclaimer

Niniejszy dokument jest tylko wstępnym zarysem pomysłu (można go potraktować jako tekst wizjonerski). W swojej obecnej formie nie wyczerpuje on wszystkich tematów, które będą wymagać analizy zanim zdecydujemy się na pójście z propozycją do potencjalnego partnera bankowego i ostatecznie uznamy, że opisane rozwiązanie jest warte wdrożenia.

W aspekcie biznesowym brakuje nam analizy w zakresie:

- Jakie podmioty w Polsce (i Europie) potrzebują weryfikować swoich klientów w zakresie KYC? Jak dużo ich jest?
- Jakie koszty ponoszą podmioty (zarówno bankowe jak i niebankowe) w związku z KYC?
- Jak powszechne jest korzystanie z usług finansowych oferowanych przez firmy zagraniczne (z UE i spoza UE)?
- Jak dużym problemem jest przeprowadzanie KYC dla klientów z innych niż siedziba firmy krajów?
- W jakim kierunku będzie się zmieniać zapotrzebowanie na KYC w przyszłości?

W aspekcie prawnym brakuje nam analizy w zakresie:

- Jakie dokładnie są wymogi KYC finansowego w Polsce (i Europie)? Jakie są wymogi w przypadku stosowania outsourcingu KYC?
- Jakie są wymogi w zakresie KYC dla klientów zagranicznych (z UE i spoza UE)?

W aspekcie technologicznym brakuje nam analizy w zakresie:

- Jak trudna dla nas jest implementacja naszego rozwiązania?
- Jak trudna dla banku jest adaptacja do proponowanego przez nas rozwiązania?