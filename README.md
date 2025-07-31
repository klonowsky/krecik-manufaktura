# README: Krecik Manufaktura – Platforma E‑Commerce z Duszą

## 🐾 Wprowadzenie

**Krecik Manufaktura** to cyfrowy dom rodzinnej manufaktury, w której tradycyjne rzemiosło spotyka nowoczesne technologie. Nasz sklep internetowy prezentuje ręcznie wytwarzane zabawki, dekoracje i upominki, a także historię rodziny stojącej za marką. Łączymy e‑commerce z opowieścią, aby każdy klient mógł poczuć się jak gość w naszej pracowni.

Ten plik README zawiera kluczowe informacje o strukturze projektu, użytych technologiach oraz głównych zasadach implementacji całego systemu.

---

## 📐 Architektura Systemu

Platforma została zaprojektowana w modelu headless, z podziałem na niezależne komponenty:

- **Frontend (Next.js + Tailwind CSS)** – renderowanie SSR/ISR, przyjazny SEO, pełna responsywność, przygotowany do internacjonalizacji (i18n), z elementami narracji o rodzinie.
- **Backend (Express.js + PostgreSQL)** – modularna architektura (produkty, zamówienia, użytkownicy, AI, treści), REST API, JWT-auth, ORM (Prisma lub Knex).
- **Baza Danych** – PostgreSQL z relacjami między produktami, wariantami, klientami, partnerami i zamówieniami oraz opcjonalnie partiami produkcyjnymi.
- **AI Agent System (Flowise)** – agenci wspierający klientów detalicznych i hurtowych, działający w wieloagentowej orkiestracji z retrieverami danych.
- **Panel Admina** – aplikacja w Next.js do zarządzania produktami, treściami, zamówieniami i użytkownikami z rozbudowanym systemem ról (Admin, Content, Logistics, Partner Manager).

---

## 🚀 Technologie

- **Frontend:** Next.js, React, Tailwind CSS, React Internationalization (react-i18next), Headless UI
- **Backend:** Express.js, TypeScript, PostgreSQL, JWT, bcrypt, yup/joi do walidacji
- **AI Integration:** Flowise, OpenAI API (lub lokalne LLM), wektorowa baza danych (np. ChromaDB)
- **CMS / Treści:** Własny moduł CMS w Express (z opcją rozszerzenia o Strapi)
- **Payments:** Stripe z obsługą Przelewy24, BLIK, kart płatniczych; obsługa płatności przy odbiorze i faktur dla B2B
- **Notifications:** Nodemailer / Mailchimp, Webhooks, powiadomienia SMS/WhatsApp (opcjonalnie)
- **Deployment:** VPS (Ubuntu), Nginx, SSL (Let's Encrypt), Docker/PM2, GitHub Actions do CI/CD

---

## 📁 Struktura Projektu

krecik-manufaktura/
├── frontend/ # Aplikacja Next.js
│ ├── app/ # App Router i strony
│ ├── components/ # Komponenty UI (katalogi produktów, karty, layout)
│ ├── styles/ # Tailwind config i style globalne
│ ├── i18n/ # Pliki tłumaczeń (pl, en)
│ └── public/ # Zasoby statyczne (logo, zdjęcia)
│
├── backend/ # Aplikacja Express.js
│ ├── src/
│ │ ├── controllers/ # Logika biznesowa (produkty, zamówienia, płatności)
│ │ ├── routes/ # Definicje tras API
│ │ ├── middleware/ # Uwierzytelnianie, role, walidacje
│ │ ├── models/ # Schematy ORM
│ │ └── utils/ # Funkcje pomocnicze (np. obsługa Stripe)
│ └── prisma/ # Schematy i migracje (jeśli używany Prisma)
│
├── ai/ # Konfiguracje agentów Flowise
├── nginx/ # Konfiguracja reverse proxy
├── docker/ # Pliki Docker i Compose
├── scripts/ # Skrypty wdrożeniowe i utrzymaniowe
└── README.md # Ten dokument


---

## 🧠 AI Agenci (Flowise)

- **Retail Support Agent** – chatbot dla klientów detalicznych, odpowiadający na pytania o produkty, status zamówienia, zwroty i rekomendacje.
- **Wholesale Partner Agent** – asystent dla partnerów hurtowych: sprawdza stany magazynowe, ceny hurtowe, minimalne ilości, pomaga w składaniu zamówień.
- **Onboarding & Content Agent** – pomaga nowym partnerom założyć konto, przygotowuje teksty marketingowe, artykuły na blog i social media.
- **Supervisor Agent** – koordynuje zapytania i deleguje je do odpowiedniego agenta w modelu multi-agent.

---

## 🛒 Funkcje E‑commerce

- Katalog produktów z kategoriami, filtrami i wyszukiwarką
- Strony produktu z obszernymi opisami, galerią zdjęć, informacją o dostępnych wariantach i czasach produkcji
- Koszyk z podsumowaniem zamówienia, obsługą kuponów rabatowych i kodów partnerskich
- Checkout dla gości i zarejestrowanych użytkowników, integracja z systemem płatności (Stripe) i opcją zapłaty przy odbiorze
- Program partnerski i opcja składania zamówień hurtowych
- Możliwość zapisania się na newsletter i subskrypcje specjalnych edycji produktów

---

## 🛠 Panel Administracyjny

- Zarządzanie produktami: dodawanie, edycja, warianty, zdjęcia, dostępność, opisy
- Panel zamówień: podgląd i filtrowanie zamówień, aktualizacja statusów, generowanie faktur i list pakunkowych
- Moduł treści: tworzenie artykułów, aktualności, sekcji „O nas” za pomocą edytora Markdown/WYSIWYG
- CRM partnerów: rejestracja nowych partnerów, zatwierdzanie kont, ustawianie rabatów i warunków sprzedaży
- Role i uprawnienia: Admin (pełen dostęp), Content Manager (treści), Logistics (dostawy), Partner Manager (hurt)
- Historia aktywności, logi, możliwość eksportu danych i narzędzia GDPR (anonimizacja, eksport danych)

---

## 📬 Powiadomienia i Messaging

- Automatyczne maile transakcyjne (potwierdzenie zamówienia, zmiana statusu, wysyłka)
- Integracja z Mailchimp: listy mailingowe, segmentacja, kampanie newsletterowe
- Możliwość wysyłania powiadomień przez SMS/WhatsApp (np. odbiór zamówienia)
- Webhooki do systemów zewnętrznych (Slack, CRM, narzędzia analityczne)

---

## 🔒 Bezpieczeństwo & RODO

- Pełne szyfrowanie komunikacji dzięki HTTPS/SSL
- Uwierzytelnianie JWT, bezpieczne przechowywanie haseł (bcrypt), zapobieganie atakom XSS, CSRF, SQL injection
- Rozbudowany system uprawnień i logowania działań w panelu admin
- Zgodność z RODO: możliwość eksportu/usunięcia danych użytkowników, zgoda na zapisy marketingowe, minimalizacja zbieranych danych
- Ograniczenie rate limit na wrażliwych endpointach i monitoring bezpieczeństwa

---

## 🌍 Przyszłościowość

- Obsługa wielu języków (PL/EN) z możliwością dodawania kolejnych
- Integracje z marketplace’ami (Etsy, Allegro, Amazon) i systemami POS
- Łatwe skalowanie (różne instancje backendu, frontendu, osobne serwery dla AI)
- Przygotowanie pod aplikację mobilną (PWA i/lub React Native)
- Możliwość dodawania nowych agentów AI (np. do rekomendacji produktów, personalizowanych kampanii)
- Integracja kalendarza produkcji i zarządzania materiałami

---

## ⚙️ Deployment

- VPS/Chmura z podziałem na frontend, backend i bazę danych
- Docker/PM2 do utrzymania aplikacji i łatwego skalowania
- Nginx jako reverse proxy z certyfikatami SSL (Let’s Encrypt)
- CI/CD z GitHub Actions: testy, budowanie obrazów, automatyczny deploy na serwer
- Regularne backupy (bazy danych i przesłanych plików), monitoring stanu usług i alerty

---

## 📎 Kontakt i Licencja

Platforma rozwijana przez rodzinę Krecików. Domeny: **krecikmanufaktura.pl** / **krecik.pl**.  
Licencja: **Proprietary / Internal Use Only** (do użytku wewnętrznego firmy Krecik Manufaktura).

---

> *„Krecik Manufaktura to nie tylko sklep – to opowieść o pasji, tradycji i dbałości o każdy detal. Z nami technologie pomagają pielęgnować rodzinne rzemiosło.”*
