# ohmy-mihomo

Proyek rule provider adblock untuk Clash/Mihomo. Menggabungkan beberapa sumber blocklist terpercaya jadi rule file siap pakai dalam format Clash.

## Source

| Sumber | Format | Domain |
|--------|--------|--------|
| [AdGuard adservers](https://adguardteam.github.io/AdguardFilters/BaseFilter/sections/adservers.txt) | AdGuard | ~1K |
| [blackmatrix7 Advertising](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/AdGuard/Advertising/Advertising.txt) | AdGuard | ~256K |
| [StevenBlack/hosts](https://raw.githubusercontent.com/StevenBlack/hosts/master/hosts) | Hosts | ~84K |
| [StevenBlack fakenews+gambling](https://raw.githubusercontent.com/StevenBlack/hosts/master/alternates/fakenews-gambling-only/hosts) | Hosts | ~8K |

## Output

```
clash/rule_provider/
├── custom-block.yaml      # Kosong, isi manual
├── lite-block.yaml        # ~16K rules - domain di 2+ sumber
├── medium-block.yaml      # ~325K rules - blackmatrix7 + StevenBlack
├── extreme-block.yaml     # ~334K rules - semua sumber
└── README.md
```

## Tier

| Tier | Criteria | Use Case |
|------|----------|----------|
| **Lite** | Domain muncul di 2+ sumber | Daily use, ringan |
| **Medium** | blackmatrix7 + StevenBlack | Middle ground |
| **Extreme** | Semua sumber termasuk fakenews & gambling | Coverage maksimal |
| **Custom** | Isi manual | Kebutuhan spesifik |

## Cara Kerja

1. `source.txt` - daftar URL sumber blocklist
2. Script PowerShell parse tiap format (AdGuard `||domain^`, Hosts `0.0.0.0 domain`)
3. Domain diekstrak, dideduplikasi, di-sort per tier
4. Output dalam format Clash rule provider (`DOMAIN-SUFFIX,domain.com`)

## Penggunaan

Tambah ke config Clash/Mihomo:

```yaml
rule-providers:
  adblock-lite:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/<user>/ohmy-mihomo/main/clash/rule_provider/lite-block.yaml"
    path: ./rules/adblock-lite.yaml
    interval: 86400
```
