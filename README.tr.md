# Codex ve Claude Code için AugeLab

Tek bir `augelab` becerisi, çalışan AugeLab Studio'nun mevcut MCP araçlarına bağlanır.
Studio'nun blok kataloğu ve iş akışları plugin içinde kopyalanmaz.

**0.1.0 beta:** Codex yerel kurulumu doğrulandı. Canlı Studio iş akışı ve Claude
Code çalışma testi henüz tamamlanmadı.

## Önce Studio

Studio ve ajan aynı bilgisayarda çalışmalı. Studio'da **Chat > Settings > MCP**
bölümünden sunucuyu başlatın. Varsayılan adres `http://127.0.0.1:8765/mcp`.
Plugin, Studio uygulamasını veya lisansını içermez.

## Codex kurulumu

Depo `AugelabTech/augelab-codex-claude-plugin` adresinde yayınlandıktan sonra:

```sh
codex plugin marketplace add AugelabTech/augelab-codex-claude-plugin
codex plugin add augelab@augelab-plugins
```

Yeni bir yerel sohbet açın:

> $augelab Studio'nun bağlantısını kontrol et; hiçbir projeyi değiştirme veya çalıştırma.

## Claude Code kurulumu

Claude Code içinde:

```text
/plugin marketplace add AugelabTech/augelab-codex-claude-plugin
/plugin install augelab@augelab-plugins
```

Yeni oturumda `/augelab:augelab` kullanın. Bu paket Claude Code içindir;
Claude Desktop'ın ayrı sohbet bağlantı ayarları için değildir.

## Yerel ZIP kurulumu

`augelab-marketplace-0.1.0.zip` arşivini çıkarın. Codex için çıkarılan klasörde
`codex plugin marketplace add .`, ardından `codex plugin add augelab@augelab-plugins`
çalıştırın. Claude Code için `claude plugin marketplace add .`, ardından
`claude plugin install augelab@augelab-plugins` kullanın.

Studio farklı port gösteriyorsa yerel kopyadaki `plugins/augelab/.mcp.json` adresini
güncelleyin ve plugini yeniden kurun. Kayıtlı port yerine **aktif portu** esas alın.
Aynı isimli yerel ve Git marketplace kaynaklarını birlikte eklemeyin.

[Ayrıntılı rehber](README.md) · [Canlı test adımları](docs/smoke-test.md)
