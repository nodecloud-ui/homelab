# :house_with_garden: Homelab :test_tube:

Prywatne repozytorium dokumentacji, procedur wdrożeniowych i ściągawek mojego środowiska domowego.

## :frame_with_picture: Środowisko i Architektura

Całe środowisko aplikacyjne zostało skonsolidowane na jednym fizycznym hoście **Proxmox VE** i odizolowane w bezpiecznej, dedykowanej sieci sterowanej przez kontroler **UniFi**.

!!! note "Ważna zasada dotycząca uprawnień"
    Wszystkie polecenia wykonywane bezpośrednio wewnątrz kontenerów LXC in Proxmoxie są uruchamiane z poziomu konta `root`, dlatego używanie przedrostka `sudo` przed komendami nie jest wymagane.

!!! info "Filozofia infrastruktury (LXC vs Docker)"
    Podobnie jak wielu zaawansowanych twórców homelabów, kluczowe, wymagające wysokiej wydajności aplikacje (takie jak **Immich** czy **Nextcloud**) wdrażam jako dedykowane, odizolowane kontenery LXC (często posiłkując się sprawdzonymi skryptami automatyzacyjnymi ze społeczności *Proxmox VE Helper-Scripts*). 
    
    Z kolei mniejsze narzędzia oraz usługi pomocnicze konsoliduję wewnątrz środowiska Docker zarządzanego centralnie przez webowy panel **Dockge (LXC 103)**.

---

## 🗒️ Podręczna Mapa Adresacji IP i Usług

Poniższa tabela stanowi szybki punkt odniesienia do kluczowych zasobów sieciowych w podsieci `10.0.30.0/24`:

| Usługa / Kontener | Adres IP / URL | Rola w Środowisku |
| :--- | :--- | :--- |
| **Proxmox Host** | `10.0.30.2` | Hypervisor Proxmox VE (Węzeł: `proxmox`) |
| **Proxmox LXC 103** | `10.0.30.3` | Docker Host, Panel Dockge (`:5001`), Rclone |
| **Immich Server** | `10.0.30.41` / `nodecloud.uk` | Centralna galeria zdjęć i wideo (Multikonta) |
| **Nextcloud App** | `10.0.30.44` / `nodecloud.uk` | Private cloud (sebastian) |
| **Wiki.js** | `10.0.30.45` / `nodecloud.uk` | Centralna baza wiedzy |
| **Homelab Docs** | `10.0.30.46` / GitHub | Niniejszy notatnik (Silnik Zensical) |

---

## :hammer_and_wrench: Zarządzanie i Bezpieczeństwo

*   **Zarządzanie Kluczami:** Wszystkie klucze API, sekrety oraz tokeny środowiskowe są bezpiecznie odizolowane i ładowane centralnie na hoście Docker z pliku eksportu znajdującego się pod ścieżką `/root/.api_keys`.
*   **Segmentacja Sieciowa:** Wszystkie kontenery produkcyjne posiadają bezpośrednie adresy IP w sieci LAN dzięki implementacji sterownika **macvlan** (`unifi_servers30`), co pozwala na pełną kontrolę ruchu z poziomu firewalla UniFi.

## :pencil: Autor
Projekt bazy wiedzy rozwijany i utrzymywany przez **[nodecloud-ui](https://github.com)** za pomocą automatycznego wdrażania CI/CD przez GitHub Actions.
