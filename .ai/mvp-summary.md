# Aplikacja - MentorConnect (MVP)

## Główny problem

Użytkownicy mają dostęp do ogromnej ilości informacji z różnych źródeł (AI, internet, książki, kursy), ale potrzebują szybkiego dostępu do ekspertów, którzy mogą:
- Zweryfikować ich pomysły przed wdrożeniem
- Pomóc w rozwiązaniu konkretnych problemów poprzez mentoring
- Potwierdzić lub skorygować wiedzę zdobytą z różnych źródeł
- Udzielić szybkiej porady w kluczowych momentach

Platforma ma umożliwić szybkie połączenie z odpowiednim ekspertem, aby użytkownicy mogli sprawdzić swoje pomysły, zweryfikować wiedzę i otrzymać wsparcie w rozwiązywaniu problemów.

## Najmniejszy zestaw funkcjonalności

### Autentykacja i konta
- Rejestracja, logowanie, wylogowanie użytkowników
- Odzyskiwanie hasła
- Jeden profil użytkownika z możliwością bycia zarówno użytkownikiem jak i ekspertem

### Profile ekspertów
- Tworzenie i edycja profilu eksperta
- Wyświetlanie profilu z informacjami: imię, kategorie, opis doświadczenia, portfolio, kontakt
- Przypisywanie eksperta do wielu kategorii

### System kategorii
- Płaskie kategorie (5-7 głównych: Prawo i Finanse, Zdrowie i Medycyna, Technologia, Edukacja i Rozwój, Biznes, Inne)
- Filtrowanie ekspertów po kategoriach (jedna kategoria na raz)

### Wyszukiwanie i przeglądanie ekspertów
- Lista wszystkich ekspertów
- Wyszukiwarka ekspertów (po imieniu, kategorii, opisie)
- Filtrowanie po kategoriach
- Wyświetlanie szczegółów eksperta

### Rezerwacja sesji
- Wybór eksperta i terminu (data i godzina)
- Podanie informacji o potrzebie
- Wyświetlanie danych kontaktowych po rezerwacji (email i telefon dla obu stron)
- Wyświetlanie rezerwacji w dashboardach (użytkownik i ekspert)
- Anulowanie rezerwacji

### Dashboard
- Dla użytkownika: moje rezerwacje, przełącznik widoku (szukam eksperta / jestem ekspertem)
- Dla eksperta: moje rezerwacje, mój profil eksperta

## Co NIE wchodzi w zakres MVP

1. System płatności - wszystkie sesje są darmowe w MVP
2. System ocen i recenzji - rating ekspertów będzie dodany później
3. Zintegrowane video call - sesje odbywają się przez email/telefon
4. System komunikacji (Chat) - komunikacja przez email/telefon, chat będzie dodany później
5. Zaawansowane rekomendacje - tylko proste filtrowanie i wyszukiwanie
6. Powiadomienia push/email - podstawowe powiadomienia w aplikacji (opcjonalnie)
7. Panel administracyjny - zarządzanie kategoriami przez seed data
8. Zaawansowane statystyki - podstawowe statystyki dla ekspertów (opcjonalnie)
9. Hierarchiczne drzewo kategorii - w MVP kategorie są płaskie (bez podkategorii)
10. Mobilna aplikacja - tylko aplikacja webowa (responsive design)
11. CI/CD (GitHub Actions) - będzie zaimplementowany później w ramach MVP

## Kryteria sukcesu

MVP będzie uznane za sukces, jeśli w ciągu 4 tygodni po uruchomieniu zostaną spełnione następujące kryteria:

### Kryteria ilościowe:
- Minimum 10 ekspertów utworzy profile w różnych kategoriach
- Minimum 3 ekspertów w każdej z 5 głównych kategorii
- Minimum 20 użytkowników zarejestruje się
- Minimum 10 sesji zostanie zarezerwowanych
- Minimum 5 sesji zostanie zrealizowanych (sesje z przeszłymi datami)
- Współczynnik konwersji: minimum 30% zarejestrowanych użytkowników zarezerwuje przynajmniej jedną sesję

### Kryteria jakościowe:
- Platforma działa stabilnie bez krytycznych błędów (zero krytycznych błędów w produkcji)
- Wszystkie główne funkcje działają zgodnie z PRD:
  - Rejestracja i logowanie
  - Tworzenie i edycja profili ekspertów
  - Wyszukiwanie i filtrowanie ekspertów
  - Rezerwacja sesji z wyświetlaniem danych kontaktowych
  - Wyświetlanie rezerwacji w dashboardach
  - Anulowanie rezerwacji
- Użytkownicy mogą znaleźć ekspertów, zarezerwować sesje i skontaktować się przez email/telefon

### Kryteria techniczne:
- Czas ładowania strony < 2 sekundy (dla 90% requestów)
- Dostępność systemu > 99%
- Zero krytycznych błędów w produkcji
- Minimum 2 kluczowe testy e2e przechodzą (rejestracja/logowanie, rezerwacja sesji)
- Wszystkie testy manualne głównych scenariuszy zakończone sukcesem
- Aplikacja jest wdrożona i dostępna publicznie na Vercel
- SSL/HTTPS działa poprawnie

