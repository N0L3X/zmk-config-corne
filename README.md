# Corne V3 QWERTZ Keymap - Ergonomisch & Effizient

Diese ZMK-Firmware-Konfiguration ist für eine **Corne V3 Tastatur (42 Tasten)** optimiert. Sie basiert auf einem deutschen **QWERTZ-Layout** und legt den Fokus auf ergonomisches Tippen durch den Einsatz von Home-Row-Mods, Layer-Taps und nützlichen Combos/Makros.

## Hauptmerkmale

* **QWERTZ-Basislayout**
* **4 Ebenen (Layer):**
    * `DEF`: Standard-Ebene mit Buchstaben und Home-Row-Mods.
    * `SYM`: Ebene für Zahlen und häufig genutzte Symbole.
    * `NAV`: Ebene für Navigation, F-Tasten und Makros.
    * `SYS`: Systemebene für Bluetooth-Steuerung und Reset-Funktionen.
* **Home-Row-Mods (HRM):** Modifikatortasten (Shift, Ctrl, Alt, GUI) auf der Grundreihe, die bei Halten aktiviert werden, während kurzes Tippen den Buchstaben sendet. Mit Positions-Trigger, um das Verhalten zu optimieren.
* **Layer-Taps auf Daumentasten:** Schneller Zugriff auf die `SYM`- und `NAV`-Layer durch Halten der inneren Daumentasten (die bei kurzem Tippen Space bzw. Enter sind).
* **Klammer-Combos:** Einfache Eingabe von `()`, `[]` und `{}` durch gleichzeitiges Drücken von zwei benachbarten Tasten auf der Grundebene.
* **Tap-Dance Backspace:** Einmal Tippen löscht ein Zeichen, Doppeltipp löscht ein ganzes Wort.
* **Nützliche Makros:** Für häufige Terminal-Befehle und Code-Snippets.
* **System-Layer über Combo:** Sicherer Zugriff auf Systemfunktionen.
* **Kein RGB:** Diese Konfiguration ist für Cornes ohne RGB-Beleuchtung ausgelegt.

## Tastenpositions-Referenz

Die Tasten sind von 0 bis 41 durchnummeriert, wie im Code definiert:


/* Key Positions
╭────────────────────────╮ ╭────────────────────────╮
│  0   1   2   3   4   5 │ │  6   7   8   9  10  11 │
│ 12  13  14  15  16  17 │ │ 18  19  20  21  22  23 │
│ 24  25  26  27  28  29 │ │ 30  31  32  33  34  35 │
╰───────────╮ 36  37  38 │ │ 39  40  41 ╭───────────╯
╰────────────╯ ╰────────────╯
*/
// #define LEFT_POSITIONS  0 1 2 3 4 5 12 13 14 15 16 17 24 25 26 27 28 29 36 37 38
// #define RIGHT_POSITIONS 6 7 8 9 10 11 18 19 20 21 22 23 30 31 32 33 34 35 39 40 41
// Wichtiger Hinweis: Die ZMK-interne Zählung für key-positions (z.B. in Combos) ist fortlaufend von 0 bis 41.
// Linke Hand: Tasten 0-20 (Finger 0-17, Daumen 18-20)
// Rechte Hand: Tasten 21-41 (Finger 21-38, Daumen 39-41)
// Die #defines oben sind für die hold-trigger-key-positions der Home Row Mods gedacht und verwenden eine andere, gruppierte Zählweise, die im Behavior selbst aufgelöst wird. Für Combos verwenden wir die direkte ZMK-Zählung.




## Layer-Erklärungen

### Ebene 0: `DEF` (Standard QWERTZ-Layout)

Dies ist deine Hauptebene für das tägliche Tippen.

* **Zugriff:** Standardmäßig aktiv.
* **Layout:**
    ```
    // Linke Hälfte                                      // Rechte Hälfte
    ┌───────┬───────┬───────┬───────┬───────┬───────┐   ┌───────┬───────┬───────┬───────┬───────┬─────────┐
    │  TAB  │   Q   │   W   │   E   │   R   │   T   │   │   Y   │   U   │   I   │   O   │   P   │ BSPC(TD)│
    ├───────┼───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┼─────────┤
    │ LCTRL │A(LGUI)│S(LALT)│D(LCTL)│F(LSFT)│   G   │   │   H   │J(RSFT)│K(RCTL)│L(RALT)│ Ö(RGUI) │   '     │
    ├───────┼───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┼─────────┤
    │ LSHFT │   Z   │   X   │   C   │   V   │   B   │   │   N   │   M   │   ,   │   .   │   -   │  RSHFT  │
    └───────┴───────┴───────┴───┬───┼───┬───┴───────┘   └───────┴───┬───┼───┬───┴───────┴───────┴─────────┘
                                │ LGUI│SYM(Spc)│ LALT│           │ RCTRL │NAV(Ent)│  RGUI │
                                └─────┴────────┴─────┘           └─────┴────────┴───────┘
    ```
* **Besonderheiten:**
    * **`BSPC(TD)`:** Tap-Dance Backspace. Einmal tippen = Backspace, zweimal schnell tippen = Strg+Backspace (Wort löschen).
    * **Home-Row-Mods:**
        * Linke Hand: `A` (LGUI halten), `S` (LALT halten), `D` (LCTRL halten), `F` (LSHFT halten).
        * Rechte Hand: `J` (RSHFT halten), `K` (RCTRL halten), `L` (RALT halten), `O` (RGUI halten, für `Ö`).
        Kurzes Tippen sendet den Buchstaben.
    * **Daumentasten:**
        * Links Innen: `SYM(Spc)` = Leertaste tippen, `SYM`-Layer halten.
        * Rechts Innen: `NAV(Ent)` = Enter tippen, `NAV`-Layer halten.

### Ebene 1: `SYM` (Symbole & Zahlen)

* **Zugriff:** Linke innere Daumentaste (`Space`) gedrückt halten.
* **Layout:**
    ```
    // Linke Hälfte                                      // Rechte Hälfte
    ┌───────┬───────┬───────┬───────┬───────┬───────┐   ┌───────┬───────┬───────┬───────┬───────┬───────┐
    │  ESC  │   1   │   2   │   3   │   4   │   5   │   │   6   │   7   │   8   │   9   │   0   │   +   │
    ├───────┼───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┼───────┤
    │ &trans│   !   │   @   │   #   │   $   │   %   │   │   ^   │   &   │   * │   (   │   )   │   \   │
    ├───────┼───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┼───────┤
    │ &trans│   ~   │   `   │ LC(Z) │ LC(X) │ LC(C) │   │   {   │   }   │   [   │   ]   │   |   │ LC(V) │
    └───────┴───────┴───────┴───┬───┼───┬───┴───────┘   └───────┴───┬───┼───┬───┴───────┴───────┴───────┘
                                │&trans│&trans │&trans │           │&trans │&trans │&trans │
                                └─────┴───────┴─────┘           └─────┴───────┴─────┘
    ```
* **Inhalt:** Zahlenreihe oben, darunter häufige Symbole. Klammern `[] {} ()` sind auch über Combos auf dem `DEF`-Layer erreichbar. `LC(Z)` etc. sind Undo/Cut/Copy/Paste.

### Ebene 2: `NAV` (Navigation, F-Tasten & Makros)

* **Zugriff:** Rechte innere Daumentaste (`Enter`) gedrückt halten.
* **Layout:**
    ```
    // Linke Hälfte                                      // Rechte Hälfte
    ┌───────┬───────┬───────┬───────┬───────┬───────┐   ┌───────┬───────┬───────┬───────┬───────┬───────┐
    │  F1   │  F2   │  F3   │  F4   │  F5   │  F6   │   │  F7   │  F8   │  F9   │  F10  │  F11  │  F12  │
    ├───────┼───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┼───────┤
    │ &trans│ M_SUDO│  M_CD │ M_GIT │ M_LS  │ M_PIPE│   │ M_AND │ LEFT  │ DOWN  │  UP   │ RIGHT │  DEL  │
    ├───────┼───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┼───────┤
    │ &trans│M_SQOT │M_DQOT │M_ARROW│ &trans│ &trans│   │M_ARROW│ HOME  │ PG_DN │ PG_UP │  END  │ &trans│
    └───────┴───────┴───────┴───┬───┼───┬───┴───────┘   └───────┴───┬───┼───┬───┴───────┴───────┴───────┘
                                │&trans│&trans │&trans │           │&trans │&trans │&trans │
                                └─────┴───────┴─────┘           └─────┴───────┴─────┘
    ```
* **Inhalt:** Funktionstasten (F1-F12), Pfeiltasten, Navigationsbefehle (Home, End etc.) und deine definierten Makros.

### Ebene 3: `SYS` (Systemfunktionen)

* **Zugriff:** Die beiden innersten Daumentasten (`Space/SYM` und `Enter/NAV`) **gleichzeitig kurz drücken** (Combo: Tastenpositionen 20 und 41).
* **Layout:**
    ```
    // Linke Hälfte                                      // Rechte Hälfte
    ┌───────┬───────┬───────┬───────┬───────┬───────┐   ┌───────┬───────┬───────┬───────┬───────┬───────┐
    │OUT_USB│ BT_S0 │ BT_S1 │ BT_S2 │ BT_S3 │ BT_S4 │   │ &trans│ &trans│ &trans│ &trans│ &trans│ &trans│
    ├───────┼───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┼───────┤
    │ &trans│ &trans│ &trans│ &trans│ &trans│ &trans│   │ &trans│ &trans│ &trans│ &trans│ &trans│ &trans│
    ├───────┼───────┼───────┼───────┼───────┼───────┤   ├───────┼───────┼───────┼───────┼───────┼───────┤
    │ &trans│ &trans│ &trans│ &trans│ &trans│BT_CLRA│   │ &trans│ &trans│RESET_ZMK│BTLOAD │ &trans│ &trans│
    └───────┴───────┴───────┴───┬───┼───┬───┴───────┘   └───────┴───┬───┼───┬───┴───────┴───────┴───────┘
                                │&trans│&trans │&trans │           │&trans │&trans │&trans │
                                └─────┴───────┴─────┘           └─────┴───────┴─────┘
    ```
* **Inhalt:**
    * `OUT_USB` / `OUT_BLE` (um zwischen USB- und Bluetooth-Ausgabe zu wechseln - `OUT_BLE` ist auf `function_layer` in deinem Original-Glove80 Code, hier nur `OUT_USB` als Beispiel platziert, `OUT_BLE` kannst du hinzufügen).
    * Bluetooth-Profilauswahl (`BT_S0` bis `BT_S4`).
    * `BT_CLRA`: Alle Bluetooth-Pairings löschen.
    * `RESET_ZMK`: ZMK neustarten (Soft Reset).
    * `BTLOAD`: Tastatur in den Bootloader-Modus versetzen (zum Flashen).
    * **ACHTUNG:** Sei vorsichtig mit den Reset- und Bootloader-Tasten!

## Spezielle Funktionen erklärt

### Homerow Mods (HRM)

* **Konzept:** Die Tasten A, S, D, F (linke Hand) und J, K, L, O (rechte Hand) fungieren als Modifikatortasten (GUI, ALT, CTRL, SHIFT), wenn sie gehalten und eine andere Taste gedrückt wird. Bei kurzem Tippen senden sie ihren normalen Buchstaben.
* **Konfiguration:**
    * Linke Hand: `A`=LGUI, `S`=LALT, `D`=LCTRL, `F`=LSHFT
    * Rechte Hand: `J`=RSHFT, `K`=RCTRL, `L`=RALT, `O`=RGUI
* **`hold-trigger-key-positions`:** Diese Eigenschaft optimiert das HRM-Verhalten, sodass der "Hold"-Modus (z.B. Shift) eher ausgelöst wird, wenn die nächste Taste auf der *anderen* Hand gedrückt wird. Das verhindert ungewollte Modifikator-Aktivierungen bei schnellem Tippen auf derselben Hand.

### Layer Taps (`&lt;LAYER> <KEY>`)

* **Linke innere Daumentaste:**
    * Kurz tippen: `SPACE` (Leertaste)
    * Gedrückt halten: Aktiviert den `SYM`-Layer
* **Rechte innere Daumentaste:**
    * Kurz tippen: `RET` (Enter)
    * Gedrückt halten: Aktiviert den `NAV`-Layer
* **`flavor = "hold-preferred"`:** Sorgt dafür, dass bei unklarer Eingabe eher der Layer-Wechsel (Hold) als die Tipp-Aktion priorisiert wird.

### Klammer-Combos (auf `DEF`-Layer)

Durch gleichzeitiges Drücken zweier benachbarter Tasten werden Klammern erzeugt:
* `(` : `S` + `D` (linke Hand)
* `)` : `K` + `L` (rechte Hand)
* `[` : `A` + `S` (linke Hand)
* `]` : `L` + `Ö` (Taste neben L, rechte Hand)
* `{` : `Q` + `W` (linke Hand)
* `}` : `I` + `O` (rechte Hand)
* **Timeout:** `50ms`. Die Tasten müssen innerhalb dieser Zeitspanne gedrückt werden.

### Tap-Dance (`&td_bspc`)

* Zugewiesen zur Backspace-Taste.
* 1x Tippen: `BSPC` (Backspace)
* 2x Schnell Tippen: `LCTRL(BSPC)` (Strg + Backspace = Wort löschen)

### Makros (Beispiele auf `NAV`-Layer)

* `&m_sudo`: `sudo `
* `&m_cd`: `cd `
* `&m_ls`: `ls -la `
* `&m_git`: `git `
* `&m_pipe`: ` | `
* `&m_and`: ` && `
* `&m_arrow`: `->`
* `&m_dquote`: `""` (Cursor in der Mitte)
* `&m_squote`: `''` (Cursor in der Mitte)

## Anpassung

Diese Keymap ist ein Startpunkt. Zögere nicht, die `config/corne.keymap`-Datei zu bearbeiten, um Tastenbelegungen, Layer oder Makros nach deinen Wünschen zu verändern. Nach jeder Änderung muss die Firmware neu gebaut und geflasht werden.

Viel Spaß mit deiner Corne!
