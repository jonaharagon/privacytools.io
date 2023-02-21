---
title: "פותרי DNS"
icon: material/dns
---

!!! האם להשתמש ב - DNS מוצפן?"

    יש להשתמש ב- DNS מוצפן עם שרתי צד שלישי רק כדי לעקוף את הבסיס [DNS blocking](https://en.wikipedia.org/wiki/DNS_blocking) כאשר אתה יכול להיות בטוח שלא יהיו השלכות. DNS מוצפן לא יעזור לך להסתיר את פעילות הגלישה שלך.
    
    [Learn more about DNS](advanced/dns-overview.md){ .md-button }

## ספקים מומלצים

| ספקי DNS                                                                        | מדיניות פרטיות                                                                                        | פרוטוקולים                                                                                 | תיעוד לוגים    | ECS        | סינון                                                                                                                           |
| ------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | -------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------- |
| [**AdGuard**](https://adguard.com/en/adguard-dns/overview.html)                 | [:octicons-link-external-24:](https://adguard.com/en/privacy/dns.html)                                | Cleartext <br> DoH <br> DoT <br> DNSCrypt                                | חלק[^1]        | לא         | מבוסס על בחירת שרת. רשימת סינון בשימוש ניתן למצוא כאן. [:octicons-link-external-24:](https://github.com/AdguardTeam/AdGuardDNS) |
| [**Cloudflare**](https://developers.cloudflare.com/1.1.1.1/setting-up-1.1.1.1/) | [:octicons-link-external-24:](https://developers.cloudflare.com/1.1.1.1/privacy/public-dns-resolver/) | Cleartext <br> DoH <br> DoT                                                    | חלק[^2]        | לא         | מבוסס על בחירת שרת.                                                                                                             |
| [**Control D**](https://controld.com/free-dns)                                  | [:octicons-link-external-24:](https://controld.com/privacy)                                           | Cleartext <br> DoH <br> DoT <br> DNSCrypt <br> DoQ <br> DoH3 | אופציונאלי[^3] | לא         | מבוסס על בחירת שרת.                                                                                                             |
| [**Mullvad**](https://mullvad.net/en/help/dns-over-https-and-dns-over-tls)      | [:octicons-link-external-24:](https://mullvad.net/en/help/no-logging-data-policy/)                    | DoH <br> DoT                                                                         | לא[^4]         | לא         | מבוסס על בחירת שרת. רשימת סינון בשימוש ניתן למצוא כאן. [:octicons-link-external-24:](https://github.com/mullvad/dns-adblock)    |
| [**NextDNS**](https://www.nextdns.io)                                           | [:octicons-link-external-24:](https://www.nextdns.io/privacy)                                         | Cleartext <br> DoH <br> DoT                                                    | אופציונאלי[^5] | אופציונאלי | מבוסס על בחירת שרת.                                                                                                             |
| [**Quad9**](https://quad9.net)                                                  | [:octicons-link-external-24:](https://quad9.net/privacy/policy/)                                      | Cleartext <br> DoH <br> DoT <br> DNSCrypt                                | חלק[^6]        | אופציונאלי | בהתבסס על בחירת השרת, תוכנות זדוניות חוסמות כברירת מחדל.                                                                        |

## תמיכה מקורית במערכת ההפעלה

**שים לב שאיננו קשורים לאף אחד מהפרויקטים שאנו ממליצים עליהם.** בנוסף [לקריטריונים הסטנדרטיים שלנו](about/criteria.md), פיתחנו סט ברור של דרישות כדי לאפשר לנו לספק המלצות אובייקטיביות. אנו מציעים לך להכיר את הרשימה הזו לפני שתבחר להשתמש בפרויקט, ולערוך מחקר משלך כדי להבטיח שזו הבחירה הנכונה עבורך.

אנדרואיד 9 ומעלה תומך ב - DNS מעל TLS. ניתן למצוא את ההגדרות ב: **הגדרות** &rarr; **רשת & אינטרנט** &rarr; **DNS פרטי**.

    `systemd -olved ', שבה משתמשים הפצות לינוקס רבות לביצוע בדיקות DNS, עדיין לא [support DoH]( https://github.com/systemd/systemd/issues/8639). אם ברצונך להשתמש ב - DoH, יהיה עליך להתקין פרוקסי כמו [dnscrypt-proxy](https://github.com/DNSCrypt/dnscrypt-proxy) ו - [configure it]( https://wiki.archlinux.org/title/Dnscrypt-proxy) כדי לקחת את כל שאילתות ה - DNS מפתרון המערכת ולהעביר אותן דרך HTTPS. ישנם גורמים רבים שנלקחים בחשבון ונדונים כאשר אנו ממליצים על פרויקט, ותיעוד כל אחד מהם הוא עבודה בתהליך.

- חייב לתמוך [DNSSEC](advanced/dns-overview.md#what-is-dnssec)
- [מזעור QNAME](advanced/dns-overview.md#what-is-qname-minimization).
- אפשר ל - [ECS](advanced/dns-overview.md#what-is-edns-client-subnet-ecs) להיות מנוטרל
- עדיף [Anycast](https://en.wikipedia.org/wiki/Anycast#Addressing_methods) תמיכה או תמיכה היגוי גיאוגרפי

## פרוקסי מוצפן של DNS

### אנדרואיד

הגרסאות העדכניות ביותר של iOS, ‏ iPadOS, ‏ tvOS ו - macOS, תומכות הן ב - DoT והן ב - DoH. שני הפרוטוקולים נתמכים באופן מקורי באמצעות פרופילי תצורה [](https://support.apple.com/guide/security/configuration-profile-enforcement-secf6fb9f053/web) או באמצעות API הגדרות DNS [](https://developer.apple.com/documentation/networkextension/dns_settings).

### מוצרי Apple

לאחר ההתקנה של פרופיל תצורה או אפליקציה המשתמשת ב - API של הגדרות DNS, ניתן לבחור את תצורת ה - DNS. אם VPN פעיל, הרזולוציה במנהרת ה - VPN תשתמש בהגדרות ה - DNS של ה - VPN ולא בהגדרות המערכת שלכם.

Apple אינה מספקת ממשק מקורי ליצירת פרופילי DNS מוצפנים. [יוצר פרופיל DNS](https://dns.notjakob.com/tool.html) מאובטח הוא כלי לא רשמי ליצירת פרופילי DNS מוצפנים משלך, אולם הם לא יהיו חתומים.

#### פרופילים חתומים

Apple אינה מספקת ממשק מקורי ליצירת פרופילי DNS מוצפנים. מידע פרופילים חתומים מועדפים; החתימה מאמתת את מקור הפרופיל ומסייעת להבטיח את שלמות הפרופילים. תווית "מאומת" ירוקה ניתנת לפרופילי תצורה חתומים. לקבלת מידע נוסף על חתימת קוד, ראה [אודות חתימת קוד](https://developer.apple.com/library/archive/documentation/Security/Conceptual/CodeSigningGuide/Introduction/Introduction.html). **פרופילים חתומים** מוצעים על ידי [AdGuard](https://adguard.com/en/blog/encrypted-dns-ios-14.html), [NextDNS](https://apple.nextdns.io), ו [Quad9](https://www.quad9.net/news/blog/ios-mobile-provisioning-profiles/).

תוכנת פרוקסי DNS מוצפנת מספקת פרוקסי מקומי עבור [ברזולוציית DNS](advanced/dns-overview.md#unencrypted-dns) לא מוצפנת להעברה. מידע

    'systemd-resolved', שבו הפצות לינוקס רבות משתמשות כדי לבצע את בדיקות ה- DNS שלהן, עדיין לא [תומך ב- DoH](https://github.com/systemd/systemd/issues/8639). אם ברצונך להשתמש ב- DoH, תצטרך להתקין פרוקסי כמו [dnscrypt-proxy](https://github.com/DNSCrypt/dnscrypt-proxy) ו[הגדר אותו](https://wiki.archlinux.org/title/Dnscrypt-proxy) כדי לקחת את כל שאילתות ה- DNS מפותר המערכת שלך ולהעביר אותן דרך HTTPS.

## שרתי Proxy מוצפנים של DNS

תוכנת פרוקסי DNS מוצפנת מספקת פרוקסי מקומי עבור [ברזולוציית DNS](advanced/dns-overview.md#unencrypted-dns) לא מוצפנת להעברה. בדרך כלל הוא משמש בפלטפורמות שאינן תומכות במקור [DNS מוצפן ](advanced/dns-overview.md#what-is-encrypted-dns).

### RethinkDNS

!!! recommendation

    ![dnscrypt-proxy logo](assets/img/dns/dnscrypt-proxy.svg){ align=right }
    
    **dnscrypt-proxy** הוא פרוקסי DNS עם תמיכה ב-[DNSCrypt](advanced/dns-overview.md#dnscrypt), [DNS-over-HTTPS](advanced/dns-overview.md#dns-over-https-doh), ו-[DNS אנונימי](https://github.com/DNSCrypt/dnscrypt-proxy/wiki/Anonymized-DNS).
    
    [:octicons-home-16: דף הבית](https://rethinkdns.com){ .md-button .md-button--primary }
    [:octicons-eye-16:](https://rethinkdns.com/privacy){ .card-link title="מדיניות פרטיות" }
    [:octicons-info-16:](https://docs.rethinkdns.com/){ .card-link title=תיעוד}
    [:octicons-code-16:](https://github.com/celzero/rethink-app){ .card-link title="קוד מקור" }
    
    ??? תכונת ה - DNS האנונימית [** לא**](Advanced/dns-overview.md#why-shouldnt-i - use - encrypted - dns) הופכת תעבורת רשת אחרת לאנונימית

### dnscrypt-proxy

!!! recommendation

    ![AdGuard Home לוגו](assets/img/dns/adguard-home.svg){ align=right }
    
    **AdGuard Home** הוא קוד פתוח [DNS-sinkhole](https://wikipedia.org/wiki/DNS_sinkhole) המשתמש ב-[סינון DNS](ניהול https://www.cloudflare.com/learning/access/מה-הוא-סינון-DNS/) כדי לחסום תוכן אינטרנט לא רצוי, כגון פרסומות.
    
    AdGuard Home כולל ממשק אינטרנט מלוטש כדי להציג תובנות ולנהל תוכן חסום. [:octicons-home-16: Homepage](https://adguard.com/adguard-home/overview.html){ .md-button .md-button--primary }
    [:octicons-eye-16:](https://adguard.com/privacy/home.html){ .card-link title="מדיניות פרטיות" }
    [:octicons-info-16:](https://github.com/AdguardTeam/AdGuardHome/wiki){ .card-link title=תיעוד}
    [:octicons-code-16:](https://github.com/AdguardTeam/AdGuardHome){ .card-link title="קוד מקור" }
    
    [:octicons-repo-16: מאגר](https://github.com/DNSCrypt/dnscrypt-proxy){ .md-button .md-button--primary }
    [:octicons-info-16:](https://github.com/DNSCrypt/dnscrypt-proxy/wiki){ .card-link title=תיעוד}
    [:octicons-code-16:](https://github.com/DNSCrypt/dnscrypt-proxy){ .card-link title="קוד מקור" }
    [:octicons-heart-16:](https://opencollective.com/dnscrypt/contribute){ .card-link title=לתרומה }
    
    ??? הורדות
    
    
        - [:simple-windows11: Windows](https://github.com/DNSCrypt/dnscrypt-proxy/wiki/Installation-Windows)
        - [:simple-apple: macOS](https://github.com/DNSCrypt/dnscrypt-proxy/wiki/Installation-macOS)
        - [:simple-linux: Linux](https://github.com/DNSCrypt/dnscrypt-proxy/wiki/Installation-linux)

## פתרונות באחסון עצמי

פתרון DNS באירוח עצמי שימושי לסינון בפלטפורמות מבוקרות, כגון טלוויזיות חכמות ומכשירי IoT אחרים, מכיוון שאין צורך בתוכנה בצד הלקוח.

### AdGuard Home

!!! recommendation

    ![Pi-hole לוגו](assets/img/dns/pi-hole.svg){ align=right }
    
    ** Pi - hole ** הוא מקור פתוח [DNS-sinkhole](https://wikipedia.org/wiki/DNS_sinkhole) המשתמש ב-[סינון DNS]( https://www.cloudflare.com/learning/access-management/what-is-dns-filtering/) כדי לחסום תוכן אינטרנט לא רצוי, כגון מודעות.
    
    Pi-hole מיועד להתארח ב-Raspberry Pi, אך הוא אינו מוגבל לחומרה כזו.
    
    התוכנה כוללת ממשק אינטרנט ידידותי כדי להציג תובנות ולנהל תוכן חסום.

### Pi-hole

!!! recommendation

    ![Pi-hole לוגו](assets/img/dns/pi-hole.svg){ align=right }
    
    
    **Pi-hole** הוא קוד פתוח [DNS-sinkhole](https://wikipedia.org/wiki/DNS_sinkhole) המשתמש ב[סינון DNS](https://www.cloudflare.com/learning/access-management/what-is-dns-filtering/) כדי לחסום תוכן אינטרנט לא רצוי, כגון פרסומות.
    
    Pi-hole מיועד להתארח ב-Raspberry Pi, אך הוא אינו מוגבל לחומרה כזו. התוכנה כוללת ממשק אינטרנט ידידותי כדי להציג תובנות ולנהל תוכן חסום.
    
    [:octicons-home-16: דף הבית](https://pi-hole.net/){ .md-button .md-button--primary }
    [:octicons-eye-16:](https://pi-hole.net/privacy/){ .card-link title="מדיניות פרטיות" }
    [:octicons-info-16:](https://docs.pi-hole.net/){ .card-link title=תיעוד}
    [:octicons-code-16:](https://github.com/pi-hole/pi-hole){ .card-link title="קוד מקור" }
    [:octicons-heart-16:](https://pi-hole.net/donate){ .card-link title=לתרומה }

[^1]: AdGuard מאחסן מדדי ביצועים מצטברים של שרתי ה-DNS שלו, כלומר מספר הבקשות המלאות לשרת מסוים, מספר הבקשות החסומות ומהירות עיבוד הבקשות. הם גם שומרים ומאחסנים את מסד הנתונים של הדומיינים המבוקשים במהלך 24 השעות האחרונות. "אנחנו צריכים את המידע הזה כדי לזהות ולחסום עוקבים ואיומים חדשים." "אנחנו גם מתעדים כמה פעמים גשש זה או אחר נחסם. אנחנו צריכים את המידע הזה כדי להסיר את הכללים המיושנים מהמסננים שלנו." [https://adguard.com/en/privacy/dns.html](https://adguard.com/en/privacy/dns.html)
[^2]: Cloudflare אוספת ומאחסנת רק את נתוני שאילתת ה - DNS המוגבלים הנשלחים לפתרון 1.1.1.1. שירות הפותר 1.1.1.1 אינו רושם נתונים אישיים, והחלק הנצבר של נתוני השאילתה המוגבלים שאינם מאפשרים זיהוי אישי מאוחסנים רק למשך 25 שעות. [https://developers.cloudflare.com/1.1.1.1/privacy/public-dns-resolver/](https://developers.cloudflare.com/1.1.1.1/privacy/public-dns-resolver/)
[^3]: Control D רק מתעדים עבור פותרי Premium עם פרופילי DNS מותאמים אישית. פותרים חינמיים אינם רושמים נתונים. [https://controld.com/privacy](https://controld.com/privacy)
[^4]: שירות ה - DNS של Mullvad זמין הן למנויים והן למי שאינם מנויים של Mullvad VPN. מדיניות הפרטיות שלהם טוענת במפורש שהם אינם רושמים בקשות DNS בכל דרך שהיא. [https://mullvad.net/en/help/no-logging-data-policy/](https://mullvad.net/en/help/no-logging-data-policy/)
[^5]: NextDNS יכולה לספק תובנות ותכונות רישום על בסיס הצטרפות. אתה יכול לבחור זמני שמירה ומיקומי אחסון יומן עבור כל יומנים שתבחר לשמור. אם זה לא מבוקש במיוחד, אין נתונים מתועדים. [https://nextdns.io/privacy](https://nextdns.io/privacy)
[^6]: Quad9 אוספת נתונים למטרות ניטור ותגובה לאיומים. לאחר מכן ניתן לבצע עירבוב ולשתף נתונים אלה, למשל לצורך מחקר אבטחה. Quad9 אינה אוספת או מתעדת כתובות IP או נתונים אחרים שהם רואים כניתנים לזיהוי אישי. [https://www.quad9.net/privacy/policy/](https://www.quad9.net/privacy/policy/)
