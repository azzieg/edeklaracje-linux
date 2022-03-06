# e-Deklaracje pod Linuxem w 2022 roku

Czy możliwe jest elektroniczne złożenie polskiego formularza podatkowego PIT bez użycia systemu Windows? W 2022 roku, po [zamknięciu](https://www.gov.pl/web/finanse/aplikacja-e-deklaracje-desktop-dostepna-tylko-do-konca-2021-roku) usługi [e-Deklaracje Desktop](https://www.podatki.gov.pl/e-deklaracje/aplikacja-e-deklaracje-desktop/)? Bez użycia komercyjnego oprogramowania podatkowego typu [e-pity](https://www.e-pity.pl/pobierz-darmowy-program-linux/) albo [ograniczeń](https://www.podatki.gov.pl/pit/twoj-e-pit/pytania-i-odpowiedzi/) usługi [Twój e-PIT](https://www.podatki.gov.pl/pit/twoj-e-pit/)?

**Tak!** Możesz po prostu wypełnić udostępniony przez Ministerstwo Finansów [formularz interaktywny](https://www.podatki.gov.pl/pit/e-deklaracje-pit/) i wysłać go [elektronicznie](https://www.podatki.gov.pl/e-deklaracje/wtyczka-do-podpisywania-i-przesylania-danych-xml-z-interaktywnych-formularzy-pdf/), po czym pobrać Urzędowe Potwierdzenie Odbioru. Jak? Czytaj dalej!

### Linux? A co z innymi systemami jak MacOS?

Możesz skorzystać z oprogramowania do wirtualizacji takiego jak [VirtualBox](https://www.virtualbox.org/). Pobierz dowolną dystrybucję Linuxa taką jak [Ubuntu](https://ubuntu.com/download/desktop) i [zainstaluj ją](https://www.download.net.pl/jak-zainstalowac-linuxa-na-virtualbox-dowolna-dystrybucja/n/15416/). Dla oszczędności czasu i miejsca możesz pobrać [minimalną wersję](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso). Instalacja Ubuntu Minimal Desktop powinna w zupełności wystarczyć.

### Linux? A co jest nie tak z Windowsem?

Windows to komercyjny system operacyjny który wymaga uiszczenia opłat licencyjnych. Wymaganie by podatnicy instalowali płatne oprogramowanie, a nawet jakiekolwiek komercyjne bądź zamknięte oprogramowanie, pokazuje że polska administracja i skarbówka nadal traktują obywateli i podatników z buta. Co prawda w wirtualnych maszynach można zainstalować [edycje developerskie](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/) systemu Windows, ale mogą być one aktywne jedynie przez 90 dni.

## W skrócie

* Zainstaluj Wine i Winetricks.
* Zainstaluj mspatcha.dll oraz czcionkę Segoe UI.
* Zainstaluj 32-bitowy Adobe Reader 11.0.08 (instalatorem dystrybucyjnym).
* Zainstaluj wtyczkę e-Deklaracje.
* Skonfiguruj locale.
* Pobierz formularze, wypełniaj, podpisuj, wysyłaj.

### Ale to nie jest wolne oprogramowanie!

Niestety. Zarówno Adobe Reader jak i wtyczka e-Deklaracje są zamkniętym oprogramowaniem. Instalowanie zamkniętego oprogramowania dostarczonego przez kogolowiek wymaga znacznej dozy zaufania w stosunku do dostawcy tego oprogramowania. Szczególnie w przypadku administracji państwowej i skarbowej, ja takiego zaufania nie mam. Dlatego polecam instalację wyżej wymienionego oprogramowania w dedykowanej maszynie wirtualnej (patrz [wyżej](#linux-a-co-z-innymi-systemami-jak-macos)).

## Wine i Winetricks

Zainstaluj [Wine](https://wiki.winehq.org/Main_Page), oprogramowanie które pozwala uruchamiać oprogramowanie dla Windows pod Linuxem, oraz [Winetricks](https://wiki.winehq.org/Winetricks), które pozwala z łatwością instalować niezbędne dodatki. Na przykład pod Ubuntu:

```shell
sudo apt install wine winetricks
```

Zgodnie z [wymaganiami e-Deklaracji](https://www.podatki.gov.pl/e-deklaracje/wtyczka-do-podpisywania-i-przesylania-danych-xml-z-interaktywnych-formularzy-pdf), potrzebujemy Adobe Readera w wersji 32-bitowej. Najlepiej będzie więc skonfigurować środowisko Wine w wersji 32-bitowej korzystając ze zmiennej środowiskowej `WINEARCH`. Jeśli korzystamy już ze środowiska 64-bitowego w standardowej lokalizacji (`~/.wine`), można użyć `WINEPREFIX` by [wybrać inną lokalizację](https://newsblog.pl/jak-tworzyc-nowe-prefiksy-wine-w-systemie-linux/).

Zakładając że dopiero zaczynamy naszą przygodę z Wine:

```shell
WINEARCH=win32 winecfg
```

Po pojawieniu się okna konfiguracji można sobie poklikać ustawienia, albo od razu je zamknąć.

## mspatcha.dll i Segoe UI

Instalator potrzebuje biblioteki to łatania aplikacji, a sam Adobe Reader potrzebuje czcionki o nazwie Segoe UI.

Pierwsze możemy łatwo zorganizować przy pomocy Winetricks:

```shell
winetricks mspatcha
```

Po dłuższej chwili odpowiednia biblioteka powinna zostać zainstalowana.

Z czcionką Segoe UI jest trudniej, ale można odnaleźć odpowiednie pliki `segoeui*.ttf` i `segui*.ttf` w zasobach Internetu. Po pobraniu plików należy umieścić je w katalogu `~/.fonts`:

```shell
wget https://github.com/mrbvrz/segoe-ui-linux/archive/refs/heads/master.zip -O segoe.zip
unzip -j segoe.zip '*.ttf' -d ~/.fonts
```

## Adobe Reader

Pierwsza przeszkoda w instalacji Adobe Readera (od czasu do czasu zwanego też Acrobat Readerem) polega na tym, że instalator sieciowy nie działa dobrze z Wine. Aby temu zaradzić, trzeba pobrać instalator klasyczny, zwany przez Adobe "biznesowym" (czy też "enterprise"). Jak zwał tak zwał, grunt że można taki instalator pobrać z [dedykowanej strony](https://get.adobe.com/reader/enterprise/), albo [serwera FTP](https://community.adobe.com/t5/acrobat-reader-discussions/adobe-reader-older-version-offline-download/td-p/11549016) Adobe.

Najnowsza wersja Adobe Readera  to DC. Niestety, wersja ta wydaje się być przeładowana niepotrzebną funkcjonalnością i podczas moich prób nie działała stabilnie z wtyczką e-Deklaracje. Dlatego też polecam wersję 11 (XI), ostatnią dostępną dla Windows XP i wciąż dostępną na stronach producenta. Niestety, polska wersja nie doczekała się aktualizacji poza 11.0, która to wersja też nie działała w moim przypadku. Na szczęście angielska wersja 11.0.08 sprawuje się wyśmienicie.

Po pobraniu możemy uruchomić instalator w Wine:

```shell
wine AdbeRdr11008_en_US.exe
```

Jeśli wszystko zrobiliśmy prawidłowo, to instalator będzie chciał umieścić Adobe Readera w `C:\Program Files` (wersja 32-bitowa) a nie `C:\Program Files (x86)` (wersja 64-bitowa). W innym przypadku patrz [wyżej](#wine-i-winetricks).

Najlepiej od razu wyłączyć automatyczne aktualizacje odpowiednią opcją przy instalacji i jeśli nie zapomnieliśmy zainstalować `mspatcha.dll`, to instalacja powinna się zakończyć sukcesem. Jeśli zapomnieliśmy, to patrz [wyżej](#mspatchadll-i-segoe-ui)

## Wtyczka e-Deklaracje

Ze [strony Ministerstwa Finansów](https://www.podatki.gov.pl/e-deklaracje/wtyczka-do-podpisywania-i-przesylania-danych-xml-z-interaktywnych-formularzy-pdf/) można pobrać wytyczkę (plug-in) do Adobe Readera, służącą do podpisywania i przesyłania danych XML z interaktywnych formularzy PDF. Po pobraniu instalatora (pliku MSI) wtyczki, możemy zainstalować ją przy użyciu Wine:

```shell
wine msiexec /i e-deklaracje-wtyczka_v9-0-0.msi
```

Po uruchomieniu instalatora możemy zainstalować wtyczkę zarówno dla Adobe Reader jak i Adobe Acrobat (ustawienie domyślne), bądź w naszym przypadku wybrać tylko Adobe Reader.
