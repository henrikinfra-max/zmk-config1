# Totem Keymap Reference — Mac Programmer Edition

> **macOS keyboard must be set to "Norwegian" (Bokmål).**
> All symbol keycodes in the Sym layer are Norwegian Mac keycodes.

---

## Key notation

| Symbol | Meaning |
|--------|---------|
| `⌘` | Cmd — hold home row key |
| `⌥` | Opt / Alt — hold home row key |
| `^` | Ctrl — hold home row key |
| `⇧` | Shift — hold home row key |
| `[N]` | Hold this key to enter layer N |
| `·` | Transparent — passes through to layer below |
| `Å / Ø / Æ` | Hold I / O / P for 250 ms |

---

## Physical key index

```
      ┌────┬────┬────┬────┬────┐                   ┌────┬────┬────┬────┬────┐
      │  0 │  1 │  2 │  3 │  4 │                   │  5 │  6 │  7 │  8 │  9 │
      ├────┼────┼────┼────┼────┤                   ├────┼────┼────┼────┼────┤
      │ 10 │ 11 │ 12 │ 13 │ 14 │                   │ 15 │ 16 │ 17 │ 18 │ 19 │
  ┌───┼────┼────┼────┼────┼────┤                   ├────┼────┼────┼────┼────┼───┐
  │20 │ 21 │ 22 │ 23 │ 24 │ 25 │                   │ 26 │ 27 │ 28 │ 29 │ 30 │31 │
  └───┴────┴────┴────┴────┴────┘                   └────┴────┴────┴────┴────┴───┘
              ┌────┬────┬────┐                   ┌────┬────┬────┐
              │ 32 │ 33 │ 34 │                   │ 35 │ 36 │ 37 │
              └────┴────┴────┘                   └────┴────┴────┘

  Left outer pinkies : 20 (bottom-left)  31 (bottom-right)
  Left thumbs        : 32 (inner)  33 (mid)  34 (outer)
  Right thumbs       : 35 (outer)  36 (mid)  37 (inner)
```

---

## Layer 0 · Base

```
      ┌────┬────┬────┬────┬────┐                   ┌────┬────┬──────┬──────┬──────┐
      │ Q  │ W  │ E  │ R  │ T  │                   │ Y  │ U  │ I/Å  │ O/Ø  │ P/Æ  │
      ├────┼────┼────┼────┼────┤                   ├────┼────┼──────┼──────┼──────┤
      │ A⌘ │ S⌥ │ D^ │ F⇧ │ G  │                   │ H  │ J⇧ │  K^  │  L⌥  │  ;⌘  │
  ┌───┼────┼────┼────┼────┼────┤                   ├────┼────┼──────┼──────┼──────┼───┐
  │ESC│ Z  │ X  │ C  │ V  │ B  │                   │ N  │ M  │  ,   │  .   │  -   │ ' │
  │[3]│    │    │    │    │    │                   │    │    │      │      │      │[4]│
  └───┴────┴────┴────┴────┴────┘                   └────┴────┴──────┴──────┴──────┴───┘
              ┌────┬─────┬────┐                   ┌───────┬─────┬────┐
              │Del │ Tab │Spc │                   │ Enter │ BSp │ =  │
              │ ⌘  │ [1] │    │                   │       │ [2] │    │
              └────┴─────┴────┘                   └───────┴─────┴────┘
```

### Layer 0 — Every key explained

**Top row  (positions 0–9)**

| Pos | Key | What it does |
|-----|-----|--------------|
| 0 | Q | Q |
| 1 | W | W |
| 2 | E | E |
| 3 | R | R |
| 4 | T | T |
| 5 | Y | Y |
| 6 | U | U |
| 7 | I / Å | Tap quickly → I.  Hold 250 ms → Å (sends LBKT, which Norwegian Mac maps to Å) |
| 8 | O / Ø | Tap quickly → O.  Hold 250 ms → Ø (sends SEMI, which Norwegian Mac maps to Ø) |
| 9 | P / Æ | Tap quickly → P.  Hold 250 ms → Æ (sends SQT, which Norwegian Mac maps to Æ) |

**Home row  (positions 10–19)**

| Pos | Key | Tap | Hold |
|-----|-----|-----|------|
| 10 | A | a | ⌘ Cmd |
| 11 | S | s | ⌥ Opt |
| 12 | D | d | ^ Ctrl |
| 13 | F | f | ⇧ Shift |
| 14 | G | g | — |
| 15 | H | h | — |
| 16 | J | j | ⇧ Shift |
| 17 | K | k | ^ Ctrl |
| 18 | L | l | ⌥ Opt |
| 19 | ; | ; *(LS(COMMA) → semicolon on Norwegian Mac)* | ⌘ Cmd |

> **Why `;` on position 19?**  The SEMI keycode sends Ø on Norwegian Mac, so it's unusable for `;`.
> Instead this key sends Shift+Comma which Norwegian Mac interprets as `;`.
> Ø is still accessible by holding O (position 8).

**Home row mod timing**
- Tap (< 280 ms, no other key held) → letter or character
- Hold (≥ 280 ms) OR hold while pressing another key → modifier
- `require-prior-idle-ms = 150` — if a key was pressed within 150 ms before this one,
  the hold action is suppressed. This prevents accidental Cmd/Ctrl/etc while typing fast.

**Bottom row  (positions 20–31)**

| Pos | Key | What it does |
|-----|-----|--------------|
| 20 | ESC | Tap → Escape.  **Hold → Fun layer [3]** |
| 21 | Z | z |
| 22 | X | x |
| 23 | C | c |
| 24 | V | v |
| 25 | B | b |
| 26 | N | n |
| 27 | M | m |
| 28 | , | , |
| 29 | . | . |
| 30 | - | Sends SLASH → `-` *(Norwegian Mac maps SLASH position to minus)* |
| 31 | ' | Tap → `'` single quote *(NUHS → apostrophe on Norwegian Mac)*.  **Hold → Button layer [4]** |

**Thumb row  (positions 32–37)**

| Pos | Key | What it does |
|-----|-----|--------------|
| 32 | Del | Tap → Delete.  Hold → ⌘ Cmd (for ⌘+Del = delete word forward on Mac) |
| 33 | Tab | Tap → Tab.  **Hold → Nav layer [1]** |
| 34 | Space | Space |
| 35 | Enter | Enter |
| 36 | BSpc | Tap → Backspace.  **Hold → Sym layer [2]** |
| 37 | = | Sends LS(N0) → `=` *(Shift+0 on Norwegian Mac = equals)*  — most-used SQL operator on a thumb |

**Combos  (both keys must be pressed within 180 ms — only active on Base layer)**

| Keys | Output |
|------|--------|
| Z (21) + X (22) | Escape |
| N (26) + M (27) | Screenshot ⌘⇧4 |

---

## Layer 1 · Nav  `hold Tab (33)`

```
      ┌─────┬─────┬────┬──────┬─────┐                   ┌───┬───┬───┬───┬─────┐
      │ Tab │ Und │ ↑  │ Redo │ PgU │                   │ · │ 7 │ 8 │ 9 │ BSp │
      ├─────┼─────┼────┼──────┼─────┤                   ├───┼───┼───┼───┼─────┤
      │  ⌘  │  ←  │ ↓  │  →   │ PgD │                   │ · │ 4 │ 5 │ 6 │ Del │
  ┌───┼─────┼─────┼────┼──────┼─────┤                   ├───┼───┼───┼───┼─────┼───┐
  │ · │ Hom │  ·  │End │  ·   │  ·  │                   │ · │ 1 │ 2 │ 3 │  ·  │ · │
  └───┴─────┴─────┴────┴──────┴─────┘                   └───┴───┴───┴───┴─────┴───┘
              ┌───┬─────┬─────┐                   ┌───────┬───┬─────┐
              │ · │ [·] │ Spc │                   │ Enter │ 0 │  .  │
              └───┴─────┴─────┘                   └───────┴───┴─────┘
```

### Layer 1 — Every key explained

**Left side — navigation** *(left thumb holds Tab to activate this layer)*

| Pos | Key | What it does |
|-----|-----|--------------|
| 0 | Tab | Tab |
| 1 | Undo | ⌘Z — undo |
| 2 | ↑ | Arrow Up |
| 3 | Redo | ⌘⇧Z — redo |
| 4 | PgUp | Page Up |
| 10 | ⌘ | Left Cmd — hold then tap arrows for word-jump (⌘←/⌘→), line start/end |
| 11 | ← | Arrow Left |
| 12 | ↓ | Arrow Down |
| 13 | → | Arrow Right |
| 14 | PgDn | Page Down |
| 20 | · | transparent (passes ESC from base) |
| 21 | Home | Jump to start of line / document |
| 22 | · | transparent |
| 23 | End | Jump to end of line / document |
| 24–25 | · | transparent |

**Right side — numpad**

| Pos | Key | What it does |
|-----|-----|--------------|
| 5 | · | transparent |
| 6 | 7 | Number 7 |
| 7 | 8 | Number 8 |
| 8 | 9 | Number 9 |
| 9 | BSp | Backspace |
| 15 | · | transparent |
| 16 | 4 | Number 4 |
| 17 | 5 | Number 5 |
| 18 | 6 | Number 6 |
| 19 | Del | Delete |
| 26–30 | · | transparent |
| 31 | · | transparent |

**Thumbs**

| Pos | Key | What it does |
|-----|-----|--------------|
| 32 | · | transparent (Del from base) |
| 33 | [·] | held — activates layer |
| 34 | Space | Space |
| 35 | Enter | Enter |
| 36 | 0 | Number 0 |
| 37 | . | Decimal point |

---

## Layer 2 · Sym  `hold BSpc (36)`

```
      ┌────┬────┬────┬────┬────┐                   ┌─────┬────┬────┬────┬────┐
      │ !  │ @  │ #  │ $  │ %  │                   │  ^  │ [  │ ]  │ {  │ }  │
      ├────┼────┼────┼────┼────┤                   ├─────┼────┼────┼────┼────┤
      │ |  │ :  │ =  │ (  │ )  │                   │  &  │ *  │ +  │ ;  │ "  │
  ┌───┼────┼────┼────┼────┼────┤                   ├─────┼────┼────┼────┼────┼───┐
  │ · │ ~  │ `  │ <  │ >  │ \  │                   │  _  │ -  │ '  │ ?  │ /  │ · │
  └───┴────┴────┴────┴────┴────┘                   └─────┴────┴────┴────┴────┴───┘
              ┌─────┬─────┬─────┐                   ┌───────┬─────┬───┐
              │ Del │ Tab │ Spc │                   │ Enter │ [·] │ · │
              └─────┴─────┴─────┘                   └───────┴─────┴───┘
```

### Layer 2 — Every key explained

All keycodes are Norwegian Mac.  Right thumb holds BSpc to activate.
Left hand is primary — it is fully free while right thumb is held.

**Top row**

| Pos | Key | Norwegian Mac keycode | Notes |
|-----|-----|-----------------------|-------|
| 0 | ! | LS(N1) | Shift+1 |
| 1 | @ | RA(N2) | AltGr+2 |
| 2 | # | LS(N3) | Shift+3 |
| 3 | $ | RA(N4) | AltGr+4 |
| 4 | % | LS(N5) | Shift+5 |
| 5 | ^ | LS(RBKT) | Shift+Å-next-key; test if wrong |
| 6 | [ | RA(N8) | AltGr+8 |
| 7 | ] | RA(N9) | AltGr+9 |
| 8 | { | RA(N7) | AltGr+7 |
| 9 | } | RA(N0) | AltGr+0 |

**Home row** ← SQL priority zone

| Pos | Key | Norwegian Mac keycode | Why here |
|-----|-----|-----------------------|---------|
| 10 | \| | RA(NUBS) | AltGr+< — pipe/OR — left pinky, easy hold |
| 11 | : | LS(DOT) | Shift+. — schema.table colon |
| 12 | = | LS(N0) | Shift+0 — equals, left middle finger |
| 13 | ( | LS(N8) | Shift+8 — open paren, left index finger |
| 14 | ) | LS(N9) | Shift+9 — close paren, left index stretch |
| 15 | & | LS(N6) | Shift+6 — AND / bitwise |
| 16 | * | LS(NUHS) | Shift+NUHS-key — SELECT * wildcard |
| 17 | + | MINUS | The +? key on Norwegian (MINUS position → +) |
| 18 | ; | LS(COMMA) | Shift+, — statement terminator |
| 19 | " | LS(N2) | Shift+2 — double quote string |

**Bottom row**

| Pos | Key | Norwegian Mac keycode | Notes |
|-----|-----|-----------------------|-------|
| 20 | · | transparent | ESC from base |
| 21 | ~ | RA(RBKT) | AltGr+Å-next-key — test; try RA(NUBS) if wrong |
| 22 | ` | GRAVE | Backtick — may be a dead key on Norwegian Mac, test |
| 23 | < | NUBS | The ISO `<>` key |
| 24 | > | LS(NUBS) | Shift+`<>` key |
| 25 | \ | BSLH | Backslash — test; try EQUAL if wrong |
| 26 | _ | LS(SLASH) | Shift+- key (SLASH pos → _) |
| 27 | - | SLASH | The `-_` key on Norwegian (SLASH position → -) |
| 28 | ' | NUHS | Single quote — same key as base layer pos 31 |
| 29 | ? | LS(MINUS) | Shift+`+?` key (MINUS pos → ?) |
| 30 | / | LS(N7) | Shift+7 — division / SQL comment start |
| 31 | · | transparent |  |

**Thumbs**

| Pos | Key | What it does |
|-----|-----|--------------|
| 32 | Del | Delete |
| 33 | Tab | Tab |
| 34 | Space | Space |
| 35 | Enter | Enter |
| 36 | [·] | held — activates layer |
| 37 | · | transparent |

---

## Layer 3 · Fun  `hold ESC (20)`

```
      ┌────┬────┬────┬────┬────┐                   ┌────┬────┬────┬────┬─────┐
      │ F1 │ F2 │ F3 │ F4 │ F5 │                   │ F6 │ F7 │ F8 │ F9 │ F10 │
      ├────┼────┼────┼────┼────┤                   ├────┼────┼────┼────┼─────┤
      │F11 │F12 │ ·  │ ·  │ ·  │                   │ ·  │Hom │PgD │PgU │ End │
  ┌───┼────┼────┼────┼────┼────┤                   ├────┼────┼────┼────┼─────┼───┐
  │[·]│ ·  │ ·  │ ·  │ ·  │ ·  │                   │Ins │Del │Pau │ScL │ Cap │ · │
  └───┴────┴────┴────┴────┴────┘                   └────┴────┴────┴────┴─────┴───┘
              ┌───┬───┬───┐                   ┌───┬───┬───┐
              │ · │ · │ · │                   │ · │ · │ · │
              └───┴───┴───┘                   └───┴───┴───┘
```

### Layer 3 — Every key explained

| Pos | Key | What it does |
|-----|-----|--------------|
| 0–4 | F1–F5 | Function keys 1–5 |
| 5–9 | F6–F10 | Function keys 6–10 |
| 10 | F11 | Function key 11 |
| 11 | F12 | Function key 12 |
| 12–14 | · | transparent |
| 15 | · | transparent |
| 16 | Home | Start of line/document |
| 17 | PgDn | Page Down |
| 18 | PgUp | Page Up |
| 19 | End | End of line/document |
| 20 | [·] | held — activates layer |
| 21–25 | · | transparent |
| 26 | Ins | Insert key |
| 27 | Del | Delete |
| 28 | Pause | Pause/Break |
| 29 | ScLk | Scroll Lock |
| 30 | Caps | Caps Lock |
| 31 | · | transparent |
| 32–37 | · | all thumbs transparent |

---

## Layer 4 · Button  `hold ' (31)`

```
      ┌───────┬───┬───┬───┬──────┐                   ┌───┬───┬───┬──────┬───┐
      │ BtClr │ · │ · │ · │ Bt0  │                   │ · │ · │ · │ Boot │ · │
      ├───────┼───┼───┼───┼──────┤                   ├───┼───┼───┼──────┼───┤
      │  ⌘    │ ⌥ │ ^ │ ⇧ │ Bt1  │                   │ · │ ⇧ │ ^ │  ⌥   │ ⌘ │
  ┌───┼───────┼───┼───┼───┼──────┤                   ├───┼───┼───┼──────┼───┼───┐
  │Bt!│  EP   │ · │ · │ · │ Bt2  │                   │ · │ · │ · │  ·   │ · │ · │
  └───┴───────┴───┴───┴───┴──────┘                   └───┴───┴───┴──────┴───┴───┘
              ┌───┬───┬───┐                   ┌───────┬──────┬───────┐
              │ · │ · │ · │                   │  ◀◀   │ ▶/▌  │  ▶▶   │
              └───┴───┴───┘                   └───────┴──────┴───────┘
```

### Layer 4 — Every key explained

| Pos | Key | What it does |
|-----|-----|--------------|
| 0 | BtClr | Clear the paired device on the current Bluetooth profile |
| 1–3 | · | transparent |
| 4 | Bt0 | Switch to Bluetooth profile 0 |
| 5 | · | transparent |
| 6–7 | · | transparent |
| 8 | Boot | Enter bootloader — keyboard appears as USB drive, drop firmware .uf2 here |
| 9 | · | transparent |
| 10 | ⌘ | Left Cmd |
| 11 | ⌥ | Left Opt |
| 12 | ^ | Left Ctrl |
| 13 | ⇧ | Left Shift |
| 14 | Bt1 | Switch to Bluetooth profile 1 |
| 15 | · | transparent |
| 16 | ⇧ | Right Shift |
| 17 | ^ | Right Ctrl |
| 18 | ⌥ | Right Opt |
| 19 | ⌘ | Right Cmd |
| 20 | Boot | Bootloader (left side) |
| 21 | EP | Toggle external power (enable/disable the keyboard's power output) |
| 22–24 | · | transparent |
| 25 | Bt2 | Switch to Bluetooth profile 2 |
| 26–30 | · | transparent |
| 31 | [·] | held — activates layer |
| 32–34 | · | transparent |
| 35 | ◀◀ | Media: Previous track |
| 36 | ▶/▌ | Media: Play / Pause |
| 37 | ▶▶ | Media: Next track |

---

## Norwegian Mac keycode reference

On Norwegian Mac, the ZMK keycode sent does **not** match what appears on your screen.
The OS remaps based on the Norwegian layout.  Key mapping:

| ZMK keycode | Output on Norwegian Mac |
|-------------|------------------------|
| SLASH | `-` (minus) |
| LS(SLASH) | `_` (underscore) |
| MINUS | `+` (plus) |
| LS(MINUS) | `?` (question mark) |
| LS(N0) | `=` (equals) |
| LS(N1) | `!` |
| LS(N2) | `"` (double quote) |
| RA(N2) | `@` |
| LS(N3) | `#` |
| RA(N4) | `$` |
| LS(N5) | `%` |
| LS(N6) | `&` |
| LS(N7) | `/` (forward slash) |
| LS(N8) | `(` |
| LS(N9) | `)` |
| RA(N7) | `{` |
| RA(N8) | `[` |
| RA(N9) | `]` |
| RA(N0) | `}` |
| LBKT | `Å` |
| SEMI | `Ø` |
| SQT | `Æ` |
| NUHS | `'` (single quote) |
| LS(NUHS) | `*` (asterisk) |
| NUBS | `<` |
| LS(NUBS) | `>` |
| RA(NUBS) | `\|` (pipe) |
| LS(COMMA) | `;` |
| LS(DOT) | `:` |
| LS(RBKT) | `^` |
| RA(RBKT) | `~` *(needs testing)* |
| BSLH | `\` *(needs testing — try EQUAL if wrong)* |
| GRAVE | `` ` `` *(may be a dead key — test)* |

---

## SQL quick-reference

| What you need | How to type it |
|---------------|----------------|
| `=` | Base layer — right inner thumb (pos 37) |
| `;` | Base layer — right home pinky tap (pos 19) |
| `'string'` | Base layer — outer right pinky tap (pos 31) |
| `-` (minus) | Base layer — bottom row right (pos 30) |
| `,` | Base layer — pos 28 |
| `.` (for table.col) | Base layer — pos 29 |
| `--` comment | Tap pos 30 twice (`-` `-`) |
| `(` | Sym layer — F key (pos 13) |
| `)` | Sym layer — G key (pos 14) |
| `*` wildcard | Sym layer — J key (pos 16) |
| `\|` pipe / OR | Sym layer — A key (pos 10) |
| `!=` | Sym layer: ! (pos 0) then base = (thumb 37) |
| `<>` not-equal | Sym layer: < (pos 23) and > (pos 24) |
| `>=` | Sym layer: > (pos 24) then base = (thumb 37) |
| `NULL` | Type normally on base |
| Screenshot | Combo N+M |
| Extra Escape | Combo Z+X |
| Å | Hold I (pos 7) for 250 ms |
| Ø | Hold O (pos 8) for 250 ms  — or tap home row right pinky (pos 19 gives Ø if SEMI used... but here pos 19 = ; — Ø only via O hold) |
| Æ | Hold P (pos 9) for 250 ms |
