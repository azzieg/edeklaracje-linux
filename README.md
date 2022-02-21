# e-Deklaracje pod Linuxem w 2022 roku

Czy możliwe jest elektroniczne złożenie polskiego formularza podatkowego PIT bez użycia systemu Windows? W 2022 roku, po [zamknięciu](https://www.gov.pl/web/finanse/aplikacja-e-deklaracje-desktop-dostepna-tylko-do-konca-2021-roku) usługi [e-Deklaracje Desktop](https://www.podatki.gov.pl/e-deklaracje/aplikacja-e-deklaracje-desktop/)? Bez użycia komercyjnego oprogramowania podatkowego typu [e-pity](https://www.e-pity.pl/pobierz-darmowy-program-linux/) albo [ograniczeń](https://www.podatki.gov.pl/pit/twoj-e-pit/pytania-i-odpowiedzi/) usługi [Twój e-PIT](https://www.podatki.gov.pl/pit/twoj-e-pit/)?

**Tak!** Możesz po prostu wypełnić udostępniony przez Ministerstwo Finansów [formularz interaktywny](https://www.podatki.gov.pl/pit/e-deklaracje-pit/) i wysłać go [elektronicznie](https://www.podatki.gov.pl/e-deklaracje/wtyczka-do-podpisywania-i-przesylania-danych-xml-z-interaktywnych-formularzy-pdf/), po czym pobrać Urzędowe Potwierdzenie Odbioru. Jak? Czytaj dalej!

### Linux? A co z innymi systemami jak MacOS?

Możesz skorzystać z oprogramowania do wirtualizacji takiego jak [VirtualBox](https://www.virtualbox.org/). Pobierz dowolną dystrybucję Linuxa taką jak [Ubuntu](https://ubuntu.com/download/desktop) i [zainstaluj ją](https://www.download.net.pl/jak-zainstalowac-linuxa-na-virtualbox-dowolna-dystrybucja/n/15416/). Dla oszczędności czasu i miejsca możesz pobrać [minimalną wersję](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso). Instalacja Ubuntu Minimal Desktop powinna w zupełności wystarczyć.

### Linux? A co jest nie tak z Windowsem?

Windows to komercyjny system operacyjny który wymaga uiszczenia opłat licencyjnych. Wymaganie by podatnicy instalowali płatne oprogramowanie, a nawet jakiekolwiek komercyjne bądź zamknięte oprogramowanie, pokazuje że polska administracja i skarbówka nadal traktują obywateli i podatników z buta. Co prawda w wirtualnych maszynach można zainstalować [edycje developerskie](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/) systemu Windows, ale mogą być one aktywne jedynie przez 90 dni.

## W skrócie

* Zainstaluj Wine i Winetricks.
* Zainstaluj mspatcha oraz Segue UI.
* Zainstaluj 32-bitowy Adobe Reader 11.0.08 (instalatorem dystrybucyjnym).
* Zainstaluj wtyczkę e-Deklaracje.
* Skonfiguruj locale.
* Pobierz formularze, wypełniaj, podpisuj, wysyłaj.

### Ale to nie jest wolne oprogramowanie!

Niestety. Zarówno Adobe Reader jak i wtyczka e-Deklaracje są zamkniętym oprogramowaniem. Instalowanie zamkniętego oprogramowania dostarczonego przez kogolowiek wymaga znacznej dozy zaufania w stosunku do dostawcy tego oprogramowania. Szczególnie w przypadku administracji państwowej i skarbowej, ja takiego zaufania nie mam. Dlatego polecam instalację wyżej wymienionego oprogramowania w dedykowanej maszynie wirtualnej (patrz [wyżej](#linux-a-co-z-innymi-systemami-jak-macos)).
