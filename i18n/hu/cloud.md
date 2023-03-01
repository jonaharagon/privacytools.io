---
title: "Felhőtárhely"
icon: material/file-cloud
---

Sok felhőalapú tárhelyszolgáltatónak elvárása a teljes bizalmad abban, hogy nem fogják megnézni a fájljaidat. Az lent felsorolt alternatívák kiküszöbölik a bizalom szükségességét azáltal, hogy a te kezedbe helyezik az adataid fölötti kontrollt, vagy E2E titkosítást valósítanak meg.

Ha ezek az alternatívák nem felelnek meg az igényeidnek, javasoljuk, hogy tekintsd meg a [Titkosítási Szoftverek](encryption.md) részt.

??? question "A Nextcloud-ot keresed?"

    A Nextcloud [továbbra is egy ajánlott eszköz](productivity.md) egy fájlkezelő csomag saját üzemeltetéséhez, azonban jelenleg nem ajánljuk a harmadik féltől származó Nextcloud tárolási szolgáltatóit, mivel a Nextcloud beépített E2EE funkcióit nem ajánljuk otthoni felhasználóknak.

## Proton Drive

!!! recommendation

    ![Proton Drive logo](assets/img/cloud/protondrive.svg){ align=right }
    
    A **Proton Drive** egy E2EE általános fájltároló szolgáltatás a népszerű titkosított e-mail szolgáltatótól a [Proton Mail](https://proton.me/mail)-től.
    
    [:octicons-home-16: Honlap](https://proton.me/drive){ .md-button .md-button--primary }
    [:octicons-eye-16:](https://proton.me/legal/privacy){ .card-link title="Adatvédelmi Nyilatkozat" }
    [:octicons-info-16:](https://proton.me/support/drive){ .card-link title=Dokumentáció}
    [:octicons-code-16:](https://github.com/ProtonMail/WebClients){ .card-link title="Forráskód" }
    
    ??? downloads
    
        - [:simple-googleplay: Google Play](https://play.google.com/store/apps/details?id=me.proton.android.drive)
        - [:simple-appstore: App Store](https://apps.apple.com/app/id1509667851)

A Proton Drive mobil kliensei 2022 decemberében jelentek meg, és még nem nyílt forráskódúak. Proton szokás szerint a forráskód közzétételét a termék első kiadásának utánra halasztja, és [a terveik szerint](https://www.reddit.com/r/ProtonDrive/comments/zf14i8/comment/izdwmme/?utm_source=share&utm_medium=web2x&context=3) 2023 végére teszi közzé a forráskódot. A Proton Drive asztali kliensek még fejlesztés alatt állnak.

## Követelmények

**Tartsd figyelemben, hogy nem állunk kapcsolatban az általunk ajánlott projektek egyikével sem.** A [szabványos kritériumaink mellett](about/criteria.md), egyértelmű követelményrendszert dolgoztunk ki, hogy objektív ajánlásokat tudjunk tenni. Javasoljuk, hogy ismerkedj meg ezzel a listával, mielőtt kiválasztanál egy projektet, és végezz saját kutatásokat, hogy megbizonyosodj arról, hogy ez a megfelelő választás számodra.

!!! example "Ez a szakasz új"

    Azon dolgozunk, hogy meghatározott követelményeket állapítsunk meg az oldalunk minden egyes szakaszára vonatkozóan, és ez még változhat. Ha bármilyen kérdésed van a követelményinkkel kapcsolatban, kérjük, [kérdezz a fórumon](https://discuss.privacyguides.net/latest), és ne feltételezd, hogy valamit nem vettünk figyelembe az ajánlásaink elkészítésekor, ha az nem szerepel itt. There are many factors considered and discussed when we recommend a project, and documenting every single one is a work-in-progress.

### Minimum Requirements

- Végponttól végpontig terjedő titkosítást kell érvényesítenie.
- Ingyenes csomagot vagy próbaidőszakot kell kínálnia a teszteléshez.
- Támogatnia kell TOTP vagy FIDO2 többfaktoros hitelesítés használatát, vagy Passkey bejelentkezéseket.
- Olyan webes felületet kell kínálnia, amely támogat alapvető fájlkezelési funkciókat.
- Lehetővé kell tennie az összes fájl/dokumentum egyszerű exportálását.
- Szabványos, felülvizsgált titkosítást kell használnia.

### Best-Case

Our best-case criteria represents what we would like to see from the perfect project in this category. Our recommendations may not include any or all of this functionality, but those which do may rank higher than others on this page.

- A klienseknek nyílt forráskódúnak kell lenniük.
- A klienseket teljes egészükben független harmadik félnek kell felülvizsgálnia.
- Natív klienseket kell kínálnia Linux, Android, Windows, macOS és iOS rendszerekre.
    - Ezeknek a klienseknek integrálódniuk kell natív operációs rendszer eszközökkel, amik felhőtárhely szolgáltatóknak lettek létrehozva, például a Files alkalmazás integrációjával iOS-en, vagy a DocumentsProvider funkcióval Androidon.
- Támogatnia kell az egyszerű fájlmegosztást más felhasználókkal.
- Legalább alapvető fájlelőnézeti és szerkesztési funkciókat kell kínálnia a webes felületen.

--8<-- "includes/abbreviations.hu.txt"
