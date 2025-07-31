# README – Krecik Manufaktura Platform

## Opis Projektu
Krecik Manufaktura to rodzinna marka oparta na tradycji i rzemiośle, rozwijana z myślą o skalowaniu w modelu B2C i B2B. Platforma e-commerce została zaprojektowana jako system headless, z oddzielonym frontendem (Next.js) i backendem (Express.js + PostgreSQL), aby zapewnić elastyczność, skalowalność i głębokie zintegrowanie z realnym modelem produkcji rodzinnego warsztatu.

---

## Zawartość Projektu

### 1. Frontend – Next.js (React)
- **Routing**: Strony statyczne i dynamiczne (produkty, blog, panel partnera, itp.)
- **Renderowanie**: SSR / ISR dla optymalizacji SEO i szybkości
- **Komponenty**: Modularne (ProductCard, ProductGallery, CheckoutForm itp.)
- **UX**: Dostosowanie dla klientów detalicznych i hurtowych
- **Design**: Styl rustykalny, responsywny, przystępny dla osób starszych
- **SEO**: Metadata, schema.org, lazy loading, optymalizacja obrazów

### 2. Backend – Express.js (Node.js) + PostgreSQL
- **API REST**: `/api/v1/` – podział na produkty, zamówienia, użytkowników, itd.
- **Struktura**: MVC lub services-router pattern
- **Baza danych**: PostgreSQL (tabele: Users, Products, Orders, Partners, Inventory, ProductionBatches)
- **Obsługa B2C/B2B**: Logika zamówień hurtowych, obsługa palet, statusy produkcji

### 3. Panel Administracyjny
- **Zamówienia**: Podział na detaliczne/hurtowe, śledzenie statusów
- **Produkty**: Dodawanie, edycja, zdjęcia, opis, warianty
- **Treści**: Edycja strony O nas, bloga, bannerów
- **CRM**: Partnerzy, notatki, statusy, historia
- **Zdarzenia**: Logi systemowe, kontrola działań użytkowników
- **Sprzedaż offline**: Wprowadzanie zamówień telefonicznych, z targów, itp.

### 4. System Ról i Autoryzacji
- **Role**: Klient, Partner (hurt), Admin, Logistyk
- **Uprawnienia**: Panel partnera, edycja produktów, dostęp do danych
- **Flow**: Rejestracja, zatwierdzanie partnerów, ograniczenie API po roli

### 5. Płatności
- **Stripe** (P24, BLIK, karty kredytowe)
- **PayPal** (opcjonalnie)
- **Płatność przy odbiorze** (dla lokalnych / B2B)
- **Faktury dla B2B**: Zamówienia z terminem płatności (manualne oznaczanie zapłaty)

### 6. Moduł Dostaw i Transportu
- **Lokalne dostawy**: Planowanie tras, przypisywanie dat
- **Zewnętrzni kurierzy**: Śledzenie, etykiety, linki
- **Wydruki**: Checklisty do pakowania, faktury, etykiety
- **Odbiór osobisty**: Statusy: gotowe do odbioru, odebrane

### 7. Integracja AI (Flowise)
- **Wholesale Support Bot**: Statusy zamówień, zapytania o dostępność
- **Partner Onboarding Bot**: Zbieranie leadów, FAQ, pomoc przy rejestracji
- **Supervisor Agent**: Przekierowania między agentami wg intencji
- **Toolsy AI**: Dostęp do API, bazy wiedzy, funkcje (np. kalkulator cen)

### 8. Wdrożenie
- **Architektura**: Oddzielny VPS frontend/backend + PostgreSQL
- **Reverse proxy**: Nginx z SSL i przekierowaniami
- **Zarządzanie procesami**: PM2 + auto-restart + monitoring
- **CI/CD**: Git + skrypty wdrożeniowe
- **Backupy**: Cron + kopie bazy + kopie plików

### 9. Bezpieczeństwo i Zgodność
- **GDPR**: Przetwarzanie danych, anonimizacja, prawo do bycia zapomnianym
- **Zabezpieczenia**: JWT, ograniczenia ról, rate limiting, logowanie zmian
- **Szyfrowanie**: HTTPS wszędzie, hasła bcrypt
- **Compliance**: Regulamin, polityka prywatności, zwroty EU

### 10. Rozszerzalność
- **Kalendarz produkcji**: Planowanie zadań i surowców
- **Śledzenie materiałów**: Tabele materiałów + zużycie na produkt
- **Tłumaczenia**: Wielojęzyczność (PL/EN) – i18n
- **Aplikacja mobilna**: API gotowe do integracji
- **Portal Partnera**: Faktury, analizy, szybkie zamówienia
- **AI CRM**: Maile po zakupie, przypomnienia, aktualizacje statusów

---

## Autorzy i Właściciel
**Krecik Manufaktura Sp. z o.o.** – ul. Bielska 47, Mikołów 43-190, NIP: 6351865585  
Prowadzenie IT i AI: *Mateusz Klonowski (@klonowsky)*

---

## Status
Projekt w trakcie realizacji – aktywnie rozwijany.  
Kontakt: [kontakt@krecikmanufaktura.pl]

---

## Licencja
Wszelkie prawa zastrzeżone © 2025 Krecik Manufaktura

