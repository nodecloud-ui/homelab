# :house_with_garden: Homelab :test_tube:

[![strona](https://shields.io)](https://nodecloud.uk)
[![ci](https://shields.io)](https://github.com)

Prywatne repozytorium na moje pliki konfiguracyjne i notatki z homelabu.

---

## :book: Dokumentacja

Pełną i interaktywną wersję bazy wiedzy znajdziesz pod adresem **[docs.nodecloud.uk][1]**.

---

## :framed_picture: Opis Środowiska

Chcę udokumentować i podzielić się konfiguracją mojego domowego homelabu oraz zebranymi doświadczeniami.

Moje obecne środowisko składa się z głównego hosta **Proxmox VE** działającego na architekturze AMD64. Kluczowe i najbardziej wymagające aplikacje (takie jak **Immich** czy **Nextcloud**) działają w dedykowanych kontenerach, natomiast pozostałe usługi pomocnicze są konsolidowane w środowisku Docker za pomocą webowego panelu **Dockge** na maszynie **LXC 103**. Wszystkie usługi posiadają bezpośrednie adresy IP w sieci domowej dzięki sterownikowi sieciowemu **macvlan** w dedykowanym **VLAN 30** pod kontrolą systemu **UniFi**.

W infrastrukturze pracują również urządzenia pomocnicze, w tym **Intel NUC**, **Raspberry Pi 5 16GB** oraz **Raspberry Pi 4 8GB**.

---

## :hammer_and_wrench: Konfiguracja i Utrzymanie

Całe środowisko aplikacyjne jest wdrażane w zorganizowany sposób. Wszystkie wrażliwe tokeny oraz klucze API są centralnie odizolowane i ładowane na serwerze z pliku `/root/.api_keys`, co pozwala na bezpieczne prowadzenie publicznej dokumentacji na GitHubie.

---

## :construction: Rozwój

Więcej informacji o strukturze oraz planach rozwoju znajdziesz na stronie [Development](./about/development.md).

---

## :balance_scale: Licencja

​[MIT License](https://githubusercontent.com)

---

## :pencil:​ Autor

Ten projekt bazy wiedzy został zaadaptowany i uruchomiony w 2026 roku przez **[nodecloud-ui][2]**.: <https://nodecloud.uk>: <https://github.com>
