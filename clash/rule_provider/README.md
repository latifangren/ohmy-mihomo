# Rule Provider - AdBlock Rules

Kumpulan rule provider untuk adblocking di Clash/Mihomo.

## Files

| File | Rules | Source | Deskripsi |
|------|-------|--------|-----------|
| `custom-block.yaml` | Kosong | - | Buat isi manual sesuai kebutuhan |
| `lite-block.yaml` | ~16K | 2+ sources | Domain paling populer, muncul di banyak sumber |
| `medium-block.yaml` | ~325K | blackmatrix7 + StevenBlack | Coverage medium dari 2 sumber utama |
| `extreme-block.yaml` | ~334K | All sources | Semua sumber digabung, coverage maksimal |

## Source

- [AdGuard adservers.txt](https://adguardteam.github.io/AdguardFilters/BaseFilter/sections/adservers.txt)
- [blackmatrix7/ios_rule_script](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/AdGuard/Advertising/Advertising.txt)
- [StevenBlack/hosts](https://raw.githubusercontent.com/StevenBlack/hosts/master/hosts)
- [StevenBlack/hosts - fakenews & gambling](https://raw.githubusercontent.com/StevenBlack/hosts/master/alternates/fakenews-gambling-only/hosts)

## Format

```yaml
Payload:
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
