# Strona pośrednia logowania - system magazynowy

Jedyny adres przekierowania aplikacji „System magazynowy” w Microsoft Entra ID: `https://nandig8.github.io/magazyn-logowanie/`.

Microsoft po zalogowaniu wraca tutaj z wynikiem w kotwicy adresu (`#code=…&state=…`), a strona od razu przekazuje go do programu
magazynowego pod adresem zapisanym przez program w `state` - **tylko do adresów w sieci lokalnej** (10.x, 172.16–31.x, 192.168.x,
nazwa komputera, `.local`, `.lan`, `.home`, `.internal`). Dzięki temu logowanie działa z każdego serwera i każdej sieci (zmienne IP
na budowach) bez dopisywania adresów w Entra ID.

- Strona nie zawiera żadnych tajnych danych, niczego nie zapisuje i nie wczytuje zewnętrznych skryptów (CSP z odciskiem skryptu).
- Kod logowania bez klucza tajnego klienta i PKCE serwera, który rozpoczął logowanie, jest bezużyteczny.
- Źródło i testy: prywatne repozytorium programu, `tools/logowanie-microsoft/index.html` i `web/tests/microsoftRelay.test.ts`
  (decyzja DEC-2026-10-23-07). Zmiana tylko razem z nim.
