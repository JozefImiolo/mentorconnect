# Plan testów automatycznych - MentorConnect MVP

## Framework testowy

**Playwright** - testy end-to-end (e2e)
- Dobra integracja z Astro
- Wsparcie dla różnych przeglądarek
- Możliwość testowania SSR
- Szybkie i niezawodne

## Kluczowe testy e2e do zaimplementowania (MVP - minimum 2 testy)

### Priorytet WYSOKI (musi być w MVP):

### Test 1: Rejestracja i logowanie użytkownika
**Odpowiada historyjkom: US-001, US-002**

Scenariusz:
1. Użytkownik wchodzi na stronę główną
2. Klika "Zarejestruj się"
3. Wypełnia formularz rejestracji (email, hasło, potwierdzenie hasła)
4. Klika "Zarejestruj"
5. Weryfikuje przekierowanie do dashboardu
6. Weryfikuje, że jest zalogowany
7. Wylogowuje się
8. Loguje się ponownie z tymi samymi danymi
9. Weryfikuje przekierowanie do dashboardu

Kryteria akceptacji:
- Rejestracja działa poprawnie
- Użytkownik jest automatycznie zalogowany po rejestracji
- Logowanie działa poprawnie
- Przekierowania działają poprawnie

### Test 2: Rezerwacja sesji (najważniejszy flow)
**Odpowiada historyjce: US-011**

Scenariusz:
1. Użytkownik jest zalogowany
2. Wchodzi na stronę szczegółów eksperta
3. Klika "Zarezerwuj sesję"
4. Wybiera datę z kalendarza
5. Wybiera godzinę z dostępnych slotów
6. Wypełnia pole z opisem potrzeby
7. Klika "Potwierdź rezerwację"
8. Weryfikuje, że rezerwacja jest zapisana
9. Weryfikuje, że dane kontaktowe eksperta są wyświetlone
10. Przechodzi do dashboardu
11. Weryfikuje, że rezerwacja jest w sekcji "Moje rezerwacje"
12. (Opcjonalnie) Loguje się jako ekspert i weryfikuje, że rezerwacja jest w "Rezerwacje do mnie"

Kryteria akceptacji:
- Formularz rezerwacji działa
- Walidacja daty/godziny działa
- Rezerwacja jest zapisywana w bazie danych
- Dane kontaktowe są wyświetlane po rezerwacji
- Rezerwacja pojawia się w dashboardach obu stron

## Struktura testów

```
tests/
├── e2e/
│   ├── auth.spec.ts          # Test 1: Rejestracja i logowanie (MUSI być w MVP)
│   ├── reservation.spec.ts   # Test 2: Rezerwacja sesji (MUSI być w MVP)
│   ├── expert-profile.spec.ts # Test 3: Tworzenie profilu eksperta (opcjonalnie)
│   └── search.spec.ts         # Test 4: Wyszukiwanie ekspertów (opcjonalnie)
├── fixtures/
│   └── test-data.ts          # Dane testowe (użytkownicy, eksperci)
└── helpers/
    └── setup.ts              # Setup i helper functions
```

## Konfiguracja

### package.json - dodane skrypty:
```json
{
  "scripts": {
    "test:e2e": "playwright test",
    "test:e2e:ui": "playwright test --ui",
    "test:e2e:headed": "playwright test --headed"
  }
}
```

### playwright.config.ts:
- Konfiguracja dla różnych przeglądarek (Chrome, Firefox)
- Base URL: localhost:3000 (dev) / production URL
- Timeout settings
- Screenshots on failure

## Dane testowe

- Test user 1: użytkownik do testów rezerwacji
- Test user 2: ekspert do testów
- Test kategorie: przynajmniej 2 kategorie z ekspertami

## Uruchamianie testów

### Lokalnie (przed commit):
```bash
npm run test:e2e
```

### Uruchamianie testów:
- Lokalnie przed commitem: `npm run test:e2e`
- W CI/CD (GitHub Actions) - będzie zaimplementowany później w ramach MVP:
  - Testy uruchamiane automatycznie przed deploymentem na Vercel
  - Pipeline CI/CD obejmuje:
    - Lint i format check
    - Build aplikacji
    - Testy e2e (Playwright)
    - TypeScript type check
  - Wszystkie kroki muszą przejść, żeby deployment się udał
  - Deployment na Vercel następuje automatycznie po przejściu wszystkich testów
- Testy powinny przechodzić przed każdym deploymentem

### Priorytet ŚREDNI (można dodać później, po MVP):

### Test 3: Tworzenie profilu eksperta
**Odpowiada historyjce: US-005**

Scenariusz:
1. Użytkownik jest zalogowany
2. Przechodzi do dashboardu
3. Klika "Jestem ekspertem" (przełącznik widoku)
4. Klika "Utwórz profil eksperta"
5. Wypełnia formularz:
   - Krótki opis doświadczenia
   - Doświadczenie/portfolio
   - Kontakt (email/telefon)
   - Wybór kategorii (co najmniej jedna)
6. Klika "Zapisz"
7. Weryfikuje, że profil jest utworzony
8. Weryfikuje, że ekspert pojawia się w liście ekspertów

Kryteria akceptacji:
- Formularz tworzenia profilu działa
- Walidacja działa poprawnie
- Profil jest zapisywany w bazie danych
- Ekspert pojawia się w liście ekspertów

### Test 4: Wyszukiwanie i filtrowanie ekspertów
**Odpowiada historyjkom: US-007, US-008, US-009**

Scenariusz:
1. Użytkownik (niezalogowany lub zalogowany) wchodzi na stronę z listą ekspertów
2. Weryfikuje, że lista ekspertów jest wyświetlona
3. Używa wyszukiwarki - wpisuje frazę
4. Weryfikuje, że wyniki są filtrowane
5. Czyści wyszukiwanie
6. Wybiera kategorię z filtru
7. Weryfikuje, że lista jest filtrowana po kategorii
8. Czyści filtr
9. Klika na eksperta z listy
10. Weryfikuje, że szczegóły eksperta są wyświetlone

Kryteria akceptacji:
- Lista ekspertów jest wyświetlana
- Wyszukiwarka działa poprawnie
- Filtrowanie po kategorii działa
- Szczegóły eksperta są wyświetlane

## Priorytetyzacja

**Wysoki priorytet (MUSI być w MVP - minimum 2 testy):**
- Test 1: Rejestracja i logowanie
- Test 2: Rezerwacja sesji

**Średni priorytet (warto mieć, ale można dodać po MVP):**
- Test 3: Tworzenie profilu eksperta
- Test 4: Wyszukiwanie ekspertów

## Uwagi

- Testy będą pisane w iteracji 6 (finalizacja MVP)
- Testy mogą wymagać testowej bazy danych Supabase
- Testy powinny być idempotentne (można je uruchamiać wielokrotnie)
- Testy powinny czyścić dane testowe po sobie (lub używać izolowanych danych)

## Rozszerzenie w przyszłości

Po MVP można dodać:
- Więcej testów e2e dla pozostałych scenariuszy
- Testy jednostkowe (Vitest) dla utility functions
- Testy integracyjne dla API endpoints
- Testy wydajnościowe
- Testy dostępności (a11y)

