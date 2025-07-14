# PLAN


---

### **Plan Implementacji Projektu: PrawoAsystent AI**
**Stan na dzień: 14.07.2025**

## 1. Cel Projektu

Stworzenie wiodącej na rynku platformy SaaS dla branży prawniczej, która wykorzystuje AI do inteligentnej analizy dokumentów. Kluczowe filary produktu to:
*   **Asystent AI (RAG):** Bezpieczna analiza dokumentów na podstawie prywatnej bazy wiedzy kancelarii.
*   **Inteligentne Snippety:** Automatyzacja tworzenia i zarządzania fragmentami pism i umów.
*   **Portal Klienta:** Bezpieczna komunikacja i wymiana plików z klientami końcowymi.
*   **Panel Administratora:** Centralne zarządzanie platformą i jej użytkownikami.

## 2. Fazy Rozwoju i Status Zadań

### **Faza 1: Fundament (Tygodnie 1-4)**
**Priorytet:** Krytyczny | **Status:** 🔄 **W trakcie**

#### 1.1 Konfiguracja Podstawowa i Prototyping
*   [x] Pierwsze spotkanie i omówienie prototypów (24.06.2025)
*   [x] Inicjalizacja projektu React + TypeScript, konfiguracja Vite
*   [x] Konfiguracja Tailwind CSS + shadcn/ui jako bazowego systemu designu
*   [x] Konfiguracja projektu Supabase (Baza Danych, Auth, Storage)
*   [ ] Implementacja podstawowego routingu i struktury aplikacji (React Router)

#### 1.2 System Autoryzacji Użytkowników
*   [ ] Komponenty i logika logowania/rejestracji
*   [ ] Zarządzanie sesjami użytkowników (JWT z mechanizmem odświeżania)
*   [ ] Implementacja chronionych tras (Protected Routes)
*   [ ] Stworzenie podstawowej, ale funkcjonalnej strony profilu użytkownika

### **Faza 2: Core Features - Rdzeń AI (Tygodnie 5-7)**
**Priorytet:** Krytyczny | **Status:** ⏳ **Planowana**

#### 2.1 Przesyłanie i Przetwarzanie Dokumentów
*   [ ] Komponent drag & drop do przesyłania plików z wizualizacją postępu
*   [ ] Walidacja typów i rozmiarów plików (klient/serwer)
*   [ ] Integracja z usługą OCR (np. poprzez Edge Function) do ekstrakcji tekstu
*   [ ] Bezpieczny zapis przetworzonych plików i tekstu w Supabase (Storage & DB)

#### 2.2 Rdzeń Asystenta AI
*   [ ] Implementacja interfejsu czatu (UI)
*   [ ] Stworzenie mikroserwisu AI (Python/Flask) do komunikacji z Google Gemini
*   [ ] Wdrożenie procesu ingestii RAG: embedding tekstu i zapis wektorów w Pinecone
*   [ ] Zarządzanie kontekstem konwersacji i historią czatu

### **Faza 3: Funkcjonalności Zaawansowane (Tygodnie 8-10)**
**Priorytet:** Wysoki | **Status:** ⏳ **Planowana**

#### 3.1 Funkcje Multimodalne (Głos)
*   [ ] Integracja z API Speech-to-Text (natywnie w Gemini lub usługa zewnętrzna)
*   [ ] Komponent do nagrywania głosu w interfejsie czatu
*   [ ] Opcjonalnie: implementacja syntezy mowy (Text-to-Speech) dla odpowiedzi AI

#### 3.2 System Płatności i Subskrypcji
*   [ ] Integracja z API Stripe dla obsługi płatności cyklicznych
*   [ ] Logika zarządzania planami subskrypcyjnymi (upgrade/downgrade)
*   [ ] Stworzenie portalu klienta do zarządzania fakturami i metodami płatności

### **Faza 4: Logika Biznesowa i Zarządzanie (Tygodnie 11-13)**
**Priorytet:** Średni | **Status:** ⏳ **Planowana**

#### 4.1 Panele Zarządzania
*   [ ] Implementacja Panelu Klienta (wgląd w sprawy, bezpieczna komunikacja)
*   [ ] Implementacja Panelu Administratora (osobne logowanie, zarządzanie użytkownikami)
*   [ ] Dashboard analityczny (statystyki użycia, kluczowe metryki)

#### 4.2 Multi-Brand Support (Opcjonalnie, w zależności od strategii)
*   [ ] Mechanizm przełączania marek i motywów
*   [ ] Możliwość konfiguracji brand-specific assets (logo, kolory)

### **Faza 5: Dopracowanie i Wdrożenie (Tygodnie 14-15)**
**Priorytet:** Średni | **Status:** ⏳ **Planowana**

#### 5.1 Optymalizacja UI/UX
*   [ ] Pełna optymalizacja pod kątem urządzeń mobilnych (Responsive Design)
*   [ ] Wdrożenie standardów dostępności (WCAG)
*   [ ] Implementacja stanów ładowania (skeletons), animacji i obsługi błędów

#### 5.2 Testowanie i Wdrożenie
*   [ ] Konfiguracja i pisanie testów jednostkowych (np. Vitest)
*   [ ] Implementacja testów E2E (np. Cypress, Playwright) dla kluczowych przepływów
*   [ ] Konfiguracja środowiska produkcyjnego i wdrożenie (CI/CD)

## 3. Metodologia Pracy

### Agile/Scrum
*   **Sprinty:** 1-tygodniowe cykle deweloperskie.
*   **Ceremonie:**
    *   **Standups:** Krótkie spotkania w celu synchronizacji.
    *   **Sprint Review:** Tygodniowa prezentacja postępów i demo nowych funkcji.
    *   **Retrospektywa:** Spotkanie po każdej zakończonej fazie w celu usprawnienia procesów.

### Definition of Done (DoD)
Zadanie jest uznane za **ukończone**, gdy:
*   [ ] Kod został sprawdzony i zatwierdzony w procesie Code Review.
*   [ ] Testy jednostkowe i integracyjne zostały napisane i pomyślnie przechodzą.
*   [ ] Związana z funkcją dokumentacja techniczna została zaktualizowana.
*   [ ] Funkcjonalność została przetestowana na środowisku stagingowym.
*   [ ] Interfejs jest w pełni responsywny i zgodny z wytycznymi dostępności.

## 4. Zarządzanie Ryzykiem (Risk Management)

### Wysokie Ryzyko
*   **Dokładność i "halucynacje" AI:**
    *   **Mitygacja:** Rygorystyczne stosowanie architektury RAG, cytowanie źródeł w odpowiedziach AI, ciągłe doskonalenie promptów i mechanizm feedbacku od użytkowników.
*   **Bezpieczeństwo i Poufność Danych:**
    *   **Mitygacja:** Implementacja Row Level Security w Supabase od pierwszego dnia, szyfrowanie danych "at-rest" i "in-transit", regularne audyty bezpieczeństwa.

### Średnie Ryzyko
*   **Koszty Operacyjne Usług AI:**
    *   **Mitygacja:** Wykorzystanie tańszych modeli (Gemini Flash) do prostszych zadań, cache'owanie odpowiedzi, optymalizacja procesów ingestii danych.
*   **Wydajność Aplikacji przy Dużym Obciążeniu:**
    *   **Mitygacja:** Stosowanie dobrych praktyk (code splitting, lazy loading), optymalizacja zapytań do bazy danych, architektura oparta na skalowalnych usługach serverless.

## 5. Mierniki Sukcesu (Success Metrics)

### Techniczne
*   **Czas ładowania strony (LCP):** < 2.5 sekundy
*   **Czas odpowiedzi API (P95):** < 300ms (dla operacji CRUD)
*   **Dostępność usługi (Uptime):** > 99.9%
*   **Współczynnik błędów:** < 0.1%

### Biznesowe i Produktowe
*   **Dokładność odpowiedzi Asystenta AI (oceniana przez ekspertów):** > 95%
*   **Satysfakcja klienta (CSAT):** > 4.5/5
*   **Współczynnik adopcji kluczowych funkcji (np. Snippets, Analiza Audio):** > 60% aktywnych użytkowników
*   **Współczynnik konwersji (z wersji próbnej na płatną):** > 15%

## 6. Następne Kroki (Next Steps)

1.  **Dokończenie Fazy 1:** Finalizacja routingu i pełna integracja z Supabase.
2.  **Rozpoczęcie Fazy 2:** Priorytetem jest funkcjonalność przesyłania dokumentów jako podstawa dla modułu AI.
3.  **Ciągłe doskonalenie UI/UX:** Zbieranie feedbacku na temat wczesnych komponentów i iteracyjne ich ulepszanie.
4.  **Konfiguracja Monitoringu:** Wdrożenie narzędzi do śledzenia błędów (np. Sentry) i analityki produktowej (np. PostHog) na wczesnym etapie.
