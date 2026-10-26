# Problémy, které jsem řešil

## Chyba repozitáře `cz.archive.ubuntu.com` při updatu (1. 4.)
**Příznak:** `apt update` na Ubuntu Serveru hlásil chybu při stahování z českého zrcadla.
**Příčina:** Chyba byla na straně zrcadla, jejich servery měly výpadek. Moje konfigurace byla v pořádku.
**Řešení:** Přepnul jsem na mezinárodní zrcadlo.
**Poučení:** Než začnu ladit vlastní systém, ověřím, jestli problém není na straně služby.

## `lightdm` a XFCE na Debianu (5. 6.)
**Příznak:** XFCE nenaběhlo, hláška `Failed to connect to session manager: SESSION_MANAGER environment variable not defined`.
**Příčina:** Přesnou příčinu jsem nezjistil, session manager se nepřipojil a XFCE po přihlášení nenaběhlo.
**Řešení:** Přeinstaloval jsem display manager.
**Poučení:** Přeinstalace display manageru je rychlý způsob, jak vyloučit poškozenou konfiguraci. Příště bych se kromě toho podíval do logů (`journalctl -b`, `~/.xsession-errors`), abych příčinu opravdu našel.

## Arch: `failed to mount /boot` (20. 7.)
**Příznak:** Systém po startu nenamountoval `/boot`.
**Příčina:** Přerušil jsem aktualizaci `pacman` uprostřed a pak jsem počítač vypnul. Zůstal nekonzistentní stav, kernel a initramfs nebyly kompletní.
**Řešení:** Provedl jsem rollback a aktualizaci pacmanu jsem pak dokončil bez přerušení.
**Poučení:** Aktualizaci na rolling distribuci nepřerušovat. Pokud se musí, nechat ji doběhnout.

## NixOS: `failed to load kernel modules` při instalaci (4. 8.)
**Příznak:** Grafický instalátor NixOS nenabootoval, chyba při načítání kernel modulů.
**Příčina:** Způsobil to Ventoy, přes který jsem ISO spouštěl. Se samotným ISO problém nebyl.
**Řešení:** Zapsal jsem celý `.iso` soubor na flashku přímo pomocí `dd`.
**Poučení:** Když instalátor selže, nejdřív vyloučit nástroj kolem něj (jiný způsob zápisu ISO), než hledat chybu v distribuci.
