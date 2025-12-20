# Plan iteracyjny rozwoju MVP - MentorConnect

## Przegląd

Plan podzielony na 6 tygodni pracy (1 godzina dziennie = 6 godzin tygodniowo). Każda iteracja kończy się pokazywalną wersją aplikacji z działającymi funkcjami.

## Iteracja 1: Podstawy projektu (Tydzień 1)

### Cel
Przygotowanie środowiska, konfiguracja projektu i podstawowa infrastruktura.

### Zadania

1. Konfiguracja Supabase
   - Utworzenie projektu Supabase
   - Konfiguracja połączenia z aplikacją
   - Setup zmiennych środowiskowych (.env.example)

2. Schemat bazy danych - podstawy
   - Tabela users (rozszerzenie auth.users Supabase)
   - Tabela profiles (podstawowe informacje o użytkownikach)
   - Tabela categories (płaskie kategorie - bez hierarchii dla MVP)
   - Seed data dla kategorii (5-7 głównych kategorii)

3. Autentykacja - podstawy
   - Konfiguracja Supabase Auth
   - Strona logowania (podstawowy UI)
   - Strona rejestracji (podstawowy UI)
   - Podstawowa logika logowania/rejestracji

4. Layout i nawigacja
   - Główny layout aplikacji
   - Podstawowa nawigacja (menu)
   - Responsive design (mobile-first)

### Definicja "Done"
- Użytkownik może zarejestrować się i zalogować
- Podstawowa nawigacja działa
- Baza danych jest skonfigurowana z podstawowymi tabelami
- Kategorie są w bazie (seed data)

### Pokazywalne
- Strona logowania/rejestracji działająca
- Podstawowy layout aplikacji
- Dashboard po zalogowaniu (pusty, ale działający)

---

## Iteracja 2: Autentykacja i profile użytkowników (Tydzień 2)

### Cel
Ukończenie autentykacji i podstawowe profile użytkowników.

### Zadania

1. Autentykacja - ukończenie
   - Wylogowanie
   - Odzyskiwanie hasła
   - Obsługa błędów autentykacji
   - Zabezpieczenie tras (protected routes)

2. Profile użytkowników
   - Wyświetlanie podstawowego profilu użytkownika
   - Edycja podstawowych danych (imię, avatar opcjonalnie)
   - Integracja z Supabase Auth

3. Dashboard użytkownika
   - Podstawowy dashboard po zalogowaniu
   - Sekcja "Moje konto"
   - Przygotowanie miejsca na przyszłe sekcje

4. UI Components
   - Podstawowe komponenty UI (button, input, card)
   - Stylowanie z Tailwind
   - Podstawowe komponenty z shadcn/ui

### Definicja "Done"
- Pełna autentykacja działa (logowanie, rejestracja, wylogowanie, reset hasła)
- Użytkownik może edytować swój podstawowy profil
- Dashboard jest funkcjonalny
- Podstawowe komponenty UI są gotowe

### Pokazywalne
- Pełny flow autentykacji
- Edycja profilu użytkownika
- Dashboard z podstawowymi sekcjami

---

## Iteracja 3: Profile ekspertów i kategorie (Tydzień 3)

### Cel
System profili ekspertów i zarządzanie kategoriami.

### Zadania

1. Profile ekspertów - tworzenie
   - Formularz tworzenia profilu eksperta
   - Flaga is_expert w profilu użytkownika
   - Przypisywanie eksperta do kategorii (many-to-many)
   - Walidacja formularza

2. Profile ekspertów - wyświetlanie
   - Strona szczegółów eksperta
   - Wyświetlanie kategorii eksperta
   - Wyświetlanie doświadczenia i portfolio

3. Edycja profilu eksperta
   - Formularz edycji profilu
   - Aktualizacja kategorii
   - Aktualizacja opisu i doświadczenia

4. System kategorii (uproszczony - płaskie kategorie)
   - Wyświetlanie listy kategorii (bez hierarchii)
   - Filtrowanie ekspertów po kategoriach (jedna kategoria na raz)
   - Komponent wyboru kategorii (multi-select dla przypisania eksperta do kategorii)

5. Przełącznik widoku użytkownik/ekspert
   - Logika przełączania widoku w dashboardzie
   - Różne widoki dla użytkownika i eksperta

### Definicja "Done"
- Użytkownik może utworzyć profil eksperta
- Ekspert może edytować swój profil
- Eksperci są przypisani do kategorii (płaskie kategorie)
- Lista kategorii jest wyświetlana i działa filtrowanie po jednej kategorii

### Pokazywalne
- Tworzenie profilu eksperta
- Wyświetlanie profilu eksperta z kategoriami
- Filtrowanie ekspertów po kategoriach

---

## Iteracja 4: Lista ekspertów i wyszukiwanie (Tydzień 4)

### Cel
Przeglądanie i wyszukiwanie ekspertów.

### Zadania

1. Lista ekspertów
   - Strona z listą wszystkich ekspertów
   - Wyświetlanie podstawowych informacji (imię, kategorie, krótki opis)
   - Paginacja (jeśli potrzeba)
   - Sortowanie ekspertów

2. Wyszukiwarka ekspertów
   - Pole wyszukiwania
   - Wyszukiwanie po imieniu, kategorii, opisie
   - Wyświetlanie wyników wyszukiwania
   - Obsługa braku wyników

3. Filtrowanie po kategoriach
   - Filtrowanie po jednej kategorii (uproszczenie dla MVP)
   - Czyszczenie filtrów
   - Kombinacja wyszukiwania + filtrowania

4. Strona szczegółów eksperta
   - Pełny profil eksperta
   - Wszystkie informacje (doświadczenie, portfolio, kontakt)
   - Przycisk "Zarezerwuj sesję" (przygotowanie)

### Definicja "Done"
- Użytkownik może przeglądać listę ekspertów
- Wyszukiwarka działa i znajduje ekspertów
- Filtrowanie po kategoriach działa
- Szczegóły eksperta są wyświetlane

### Pokazywalne
- Lista ekspertów z filtrowaniem i wyszukiwaniem
- Szczegóły profilu eksperta
- Pełny flow: wyszukiwanie -> filtrowanie -> szczegóły

---

## Iteracja 5: Rezerwacje sesji (Tydzień 5)

### Cel
System rezerwacji sesji mentoringowych.

### Zadania

1. Model rezerwacji
   - Tabela reservations w bazie danych
   - Relacje: user -> expert -> reservation
   - Statusy rezerwacji (uproszczone): nadchodząca, przeszła, anulowana
   - Automatyczne oznaczenie jako "przeszła" po dacie sesji

2. Formularz rezerwacji
   - Wybór daty (kalendarz)
   - Wybór godziny (dostępne sloty)
   - Pole z opisem potrzeby
   - Walidacja formularza

3. Logika dostępności terminów
   - Sprawdzanie dostępności terminu
   - Blokowanie zajętych terminów
   - Komunikat błędu jeśli termin zajęty (bez sugerowania alternatyw w MVP)

4. Wyświetlanie rezerwacji z danymi kontaktowymi
   - Dashboard użytkownika: "Moje rezerwacje"
   - Dashboard eksperta: "Rezerwacje do mnie"
   - Filtrowanie (nadchodzące/przeszłe)
   - Szczegóły rezerwacji
   - Wyświetlanie danych kontaktowych:
     - Dla użytkownika: email i telefon eksperta
     - Dla eksperta: email i telefon użytkownika

5. Anulowanie rezerwacji
   - Przycisk anulowania
   - Dialog potwierdzenia
   - Aktualizacja statusu rezerwacji
   - Powiadomienie drugiej strony (w aplikacji)

### Definicja "Done"
- Użytkownik może zarezerwować sesję z ekspertem
- System sprawdza dostępność terminów
- Rezerwacje są wyświetlane w dashboardach z danymi kontaktowymi
- Użytkownik i ekspert widzą dane kontaktowe drugiej strony po potwierdzeniu rezerwacji
- Możliwość anulowania rezerwacji

### Pokazywalne
- Pełny flow rezerwacji: wybór eksperta -> wybór terminu -> potwierdzenie -> wyświetlanie danych kontaktowych
- Dashboard z rezerwacjami (użytkownik i ekspert) z danymi kontaktowymi
- Anulowanie rezerwacji

---

## Iteracja 6: Finalizacja MVP (Tydzień 6)

### Cel
Polish, optymalizacja i finalizacja MVP.

### Zadania

1. Polish UI/UX
   - Poprawki wizualne
   - Spójność designu
   - Ulepszenia użyteczności
   - Responsive design improvements

2. Obsługa błędów
   - Komunikaty błędów dla użytkownika
   - Walidacja formularzy
   - Obsługa edge cases
   - Error boundaries

3. Loading states i feedback
   - Loading indicators
   - Success messages
   - Confirmation dialogs
   - Disabled states podczas operacji

4. Optymalizacja wydajności
   - Optymalizacja zapytań do bazy danych
   - Lazy loading gdzie możliwe
   - Caching jeśli potrzeba
   - Sprawdzenie czasu ładowania

5. Testy automatyczne (uproszczone - tylko kluczowe)
   - Konfiguracja frameworka testowego (Playwright dla e2e)
   - Instalacja i setup Playwright
   - Konfiguracja testów e2e
   - Napisanie 2 kluczowych testów e2e (minimum dla MVP):
     a. Test rejestracji i logowania (US-001, US-002) - podstawowa funkcjonalność
     b. Test rezerwacji sesji (US-011) - najważniejszy flow biznesowy
   - Pozostałe testy (tworzenie profilu eksperta, wyszukiwanie) można dodać później
   - Uruchomienie testów przed deploymentem
   - Skrypty testowe w package.json (npm run test:e2e)

6. Testy manualne
   - Testy wszystkich funkcji
   - Testy na różnych urządzeniach
   - Testy różnych scenariuszy
   - Sprawdzenie edge cases

7. Dokumentacja i deployment
   - Aktualizacja README z instrukcjami
   - Dokumentacja API (jeśli potrzeba)
   - Konfiguracja Vercel adaptera
   - Setup zmiennych środowiskowych w Vercel
   - Deployment na Vercel (ręczny/CLI w pierwszej wersji)
   - Weryfikacja działania aplikacji w produkcji
   - Konfiguracja domeny (opcjonalnie)
   - CI/CD (GitHub Actions) - będzie zaimplementowany później w ramach MVP, ale nie w pierwszej iteracji

### Definicja "Done"
- Wszystkie główne funkcje MVP działają stabilnie
- UI/UX jest spójne i użyteczne
- Błędy są obsługiwane poprawnie
- Minimum 2 kluczowe testy e2e są napisane i przechodzą (rejestracja/logowanie, rezerwacja sesji)
- Testy manualne wszystkich funkcji są wykonane
- Aplikacja jest wdrożona i dostępna publicznie na Vercel
- Wszystkie zmienne środowiskowe są skonfigurowane w Vercel
- SSL/HTTPS działa poprawnie
- Aplikacja jest gotowa do pokazania i użycia
- Dokumentacja jest kompletna

### Pokazywalne
- Pełny MVP:
  - Rejestracja/logowanie
  - Tworzenie profilu eksperta
  - Wyszukiwanie i filtrowanie ekspertów (płaskie kategorie)
  - Rezerwacja sesji z wyświetlaniem danych kontaktowych
  - Komunikacja przez email/telefon (dane dostępne po rezerwacji)
- Aplikacja działa stabilnie
- Wszystkie główne scenariusze są zrealizowane
- Aplikacja jest wdrożona na Vercel i dostępna publicznie
- Aplikacja jest gotowa do użycia przez realnych użytkowników

---

## Podsumowanie iteracji

### Tydzień 1-2: Fundamenty
- Autentykacja
- Baza danych
- Podstawowy UI
- Profile użytkowników

### Tydzień 3-4: Core Features
- Profile ekspertów
- System kategorii
- Lista i wyszukiwanie ekspertów

### Tydzień 5-6: Funkcjonalności i Polish
- Rezerwacje sesji z danymi kontaktowymi
- Finalizacja, polish i testy

## Metryki postępu

Po każdej iteracji sprawdź:
- Czy wszystkie zadania z iteracji są ukończone
- Czy definicja "Done" jest spełniona
- Czy aplikacja jest pokazywalna zgodnie z opisem

## Plan B - Jeśli zabraknie czasu

Jeśli w trakcie implementacji okaże się, że 6 tygodni to za mało, oto plan minimalnego MVP (must-have):

### Co MUSI być w MVP (absolutne minimum):
1. Autentykacja (rejestracja, logowanie, wylogowanie)
2. Profile ekspertów (tworzenie, wyświetlanie)
3. Lista ekspertów z podstawowym filtrowaniem po kategoriach
4. Rezerwacja sesji (wybór terminu, zapisanie, wyświetlanie danych kontaktowych)
5. Dashboard (wyświetlanie rezerwacji dla użytkownika i eksperta)
6. Deployment na Vercel (działająca aplikacja w produkcji)

### Co można uprościć/pominąć w Planie B:
1. Wyszukiwarka ekspertów - można zacząć od prostej listy z filtrowaniem
2. Anulowanie rezerwacji - można dodać później
3. Testy e2e - można ograniczyć do 1 testu (rezerwacja) lub pominąć w MVP
4. Polish UI/UX - podstawowy design wystarczy
5. Odzyskiwanie hasła - można dodać później
6. Przełącznik widoku użytkownik/ekspert - można uprościć do osobnych sekcji
7. Edycja profilu eksperta - można dodać później

### Priorytetyzacja w Planie B:
- Tydzień 1-2: Autentykacja + podstawowa baza danych (MUSI być)
- Tydzień 3-4: Profile ekspertów + lista ekspertów (MUSI być)
- Tydzień 5: Rezerwacje (MUSI być - najważniejsza funkcja)
- Tydzień 6: Deployment + minimum polish (MUSI być)

### Definicja sukcesu Planu B:
- Użytkownik może zarejestrować się i zalogować
- Ekspert może utworzyć profil
- Użytkownik może znaleźć eksperta i zarezerwować sesję
- Dane kontaktowe są dostępne po rezerwacji
- Aplikacja działa w produkcji

## Następne kroki po MVP

Po ukończeniu MVP można rozważyć:
1. System komunikacji (Chat) w aplikacji
2. Hierarchiczne drzewo kategorii (podkategorie)
3. System płatności
4. Rating i recenzje ekspertów
5. Zintegrowane video call
6. Powiadomienia email
7. Panel administracyjny
8. Zaawansowane statystyki
9. Aplikacja mobilna

