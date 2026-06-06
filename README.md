# TRON Revoke

TRON ağındaki TRC20 **approve** yetkilerini iptal etmek için tek sayfalık web aracı.
İmzalama tamamen **TronLink** içinde olur — private key bu sayfaya hiç girmez.

🔗 Canlı: https://yasinqurban.github.io/tron-revoke/

## Nasıl çalışır?

1. Link `token` ve `spender` parametreleriyle açılır
2. Sayfa TronLink'i algılar (yoksa "TronLink'te Aç" deep-link sunar)
3. Cüzdan bağlanır, `approve(spender, 0)` işlemi hazırlanır
4. TronLink onay popup'ı çıkar → onayla → revoke zincire gider

## URL Formatı

```
https://yasinqurban.github.io/tron-revoke/?token=<TOKEN>&spender=<SPENDER>&symbol=<SEMBOL>&label=<AD>&owner=<CÜZDAN>
```

| Parametre | Zorunlu | Açıklama |
|-----------|---------|----------|
| `token` | ✅ | TRC20 token kontrat adresi (T…) |
| `spender` | ✅ | Yetki verilen adres (T…) |
| `symbol` | — | Token sembolü (gösterim için, örn. USDT) |
| `label` | — | Spender adı (örn. "JustLend jUSDT") |
| `owner` | — | Beklenen cüzdan adresi (uyuşmazlık uyarısı için) |

### Örnek

```
https://yasinqurban.github.io/tron-revoke/?token=TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t&spender=TXJgMdjVX5dKiQaUi9QobwNxtSQaFqccvd&symbol=USDT&label=JustLend%20jUSDT
```

## Güvenlik

- Sayfa **statiktir** — backend yok, veri toplamaz
- Private key / secret **içermez**, görmez
- Tüm işlem TronLink cüzdanının onayından geçer
- Kaynak kod tamamen açık (bu repo)

## Geliştirme

Tek dosya: `index.html`. Yerel test için tarayıcıda aç (TronLink extension gerekir)
veya GitHub Pages'e push'la.
