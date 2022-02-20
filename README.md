# e-Deklaracje pod Linuxem w 2022 roku

Czy możliwe jest elektroniczne złożenie polskiego formularza podatkowego PIT bez użycia systemu Windows? W 2022 roku, po [zamknięciu](https://www.gov.pl/web/finanse/aplikacja-e-deklaracje-desktop-dostepna-tylko-do-konca-2021-roku) usługi [e-Deklaracje Desktop](https://www.podatki.gov.pl/e-deklaracje/aplikacja-e-deklaracje-desktop/)? Bez użycia komercyjnego oprogramowania podatkowego typu [e-pity](https://www.e-pity.pl/pobierz-darmowy-program-linux/) albo [ograniczeń](https://www.podatki.gov.pl/pit/twoj-e-pit/pytania-i-odpowiedzi/) usługi [Twój e-PIT](https://www.podatki.gov.pl/pit/twoj-e-pit/)?

**Tak!** Możesz po prostu wypełnić udostępniony przez Ministerstwo Finansów [formularz interaktywny](https://www.podatki.gov.pl/pit/e-deklaracje-pit/) i wysłać go [elektronicznie](https://www.podatki.gov.pl/e-deklaracje/wtyczka-do-podpisywania-i-przesylania-danych-xml-z-interaktywnych-formularzy-pdf/), po czym pobrać Urzędowe Potwierdzenie Odbioru. Jak? Czytaj dalej!

## Linux? A co z innymi systemami jak MacOS?

Możesz skorzystać z otwartego oprogramowania do wirtualizacji takiego jak [VirtualBox](https://www.virtualbox.org/). Pobierz dowolną dystrybucję Linuxa taką jak [Ubuntu](https://ubuntu.com/download/desktop) i zainstaluj ją. Dla oszczędności czasu i miejsca możesz pobrać [minimalną wersję](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso).

## W skrócie

* Zainstaluj Wine i Winetricks
* Zainstaluj mspatcha oraz Segue UI
* Zainstaluj 32-bitowy Adobe Reader 11.0.08 (instalatorem dystrybucyjnym)
* Zainstaluj wtyczkę e-Deklaracje
* Skonfiguruj locale
* Pobierz formularze, wypełniaj, podpisuj, wysyłaj
