# Rule Provider

Kumpulan rule provider untuk Clash/Mihomo. Support HTTP & local mode.

## AdBlock Rules

| File | Rules | Source | Deskripsi |
|------|-------|--------|-----------|
| `custom-block.yaml` | Kosong | - | Isi manual sesuai kebutuhan |
| `lite-block.yaml` | ~16K | 2+ sources | Domain paling populer dari berbagai sumber |
| `medium-block.yaml` | ~325K | blackmatrix7 + StevenBlack | Coverage medium |
| `extreme-block.yaml` | ~334K | All sources | Coverage maksimal, semua sumber |

## Game Rules

| File | Isi | Deskripsi |
|------|-----|-----------|
| `games.yaml` | Domain game | Superset game (Blizzard, Steam, Epic, dll) |
| `battlenet.yaml` | Domain Blizzard/Battle.net | Dedicated rules |
| `steam.yaml` | Domain Steam | Dedicated rules |
| `epic-games.yaml` | Domain Epic Games | Dedicated rules |
| `game-ports.yaml` | Port game | Collapsed port ranges dari portgames + portingame |

## Social Media Rules

| File | Isi | Deskripsi |
|------|-----|-----------|
| `sosmed.yaml` | Multi-platform | Discord, TikTok, IG, WA, FB, Line, Telegram, Twitter, Spotify, Deezer, JOOX, Nodepay |
| `tiktok.yaml` | TikTok | Dedicated rules |
| `whatsapp.yaml` | WhatsApp | Dedicated rules |

## Streaming & Media

| File | Isi | Deskripsi |
|------|-----|-----------|
| `streaming.yaml` | Multi-platform | Netflix, YouTube, dll |
| `netflix.yaml` | Netflix | Dedicated rules |
| `youtube.yaml` | YouTube | Dedicated rules |

## Routing Rules

| File | Isi | Deskripsi |
|------|-----|-----------|
| `crypto.yaml` | Domain crypto/DeFi | Exchange, blockchain, DeFi (Binance, Coinbase, 1inch, dll) |
| `ewallet.yaml` | Domain e-wallet & banking | Gojek, OVO, Dana, ShopeePay, BCA, BRI, Mandiri, dll |
| `ai-gh.yaml` | AI & developer tools | ChatGPT, Claude, Gemini, GitHub, Huggingface, Cursor, dll |

## Blocking

| File | Isi | Deskripsi |
|------|-----|-----------|
| `porn.yaml` | Domain dewasa | Adult content blocker |

## Utility

| File | Isi | Deskripsi |
|------|-----|-----------|
| `meta.yaml` | Meta services | Facebook, Instagram, WhatsApp, Messenger, Oculus |
| `speedtest.yaml` | Speedtest | Ookla speedtest servers |
| `ldplayer.yaml` | LDPlayer | LDPlayer emulator |
| `mumu.yaml` | MuMu | MuMu emulator |

## Source

- [AdGuard adservers.txt](https://adguardteam.github.io/AdguardFilters/BaseFilter/sections/adservers.txt)
- [blackmatrix7/ios_rule_script](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/AdGuard/Advertising/Advertising.txt)
- [StevenBlack/hosts](https://raw.githubusercontent.com/StevenBlack/hosts/master/hosts)
- [StevenBlack/hosts - fakenews & gambling](https://raw.githubusercontent.com/StevenBlack/hosts/master/alternates/fakenews-gambling-only/hosts)

## Format

```yaml
payload:
 - DOMAIN-KEYWORD,keyword
 - DOMAIN-SUFFIX,domain.com
 - IP-CIDR,1.2.3.4/32
```

## Cara Pakai

Tambah ke config Clash/Mihomo:

```yaml
rule-providers:
  adblock-lite:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/user/repo/main/clash/rule_provider/lite-block.yaml"
    path: ./rules/adblock-lite.yaml
    interval: 86400

  adblock-extreme:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/user/repo/main/clash/rule_provider/extreme-block.yaml"
    path: ./rules/adblock-extreme.yaml
    interval: 86400
```

## Tier

- **Lite** -> domain yang muncul di 2+ sumber sekaligus. Cocok buat daily use tanpa banyak overhead.
- **Medium** -> gabungan blackmatrix7 + StevenBlack. Middle ground.
- **Extreme** -> semua sumber termasuk fakenews & gambling. Coverage paling lengkap tapi ukuran besar.
- **Custom** -> isi sendiri sesuai kebutuhan spesifik.
