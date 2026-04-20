# 📚 LibApp & ResApp — Kitap Rezervasyon Sistemi

---

## 🗂️ Proje Hakkında

Bu repo, birbirinden **ayrık iki ASP.NET Core uygulamasından** oluşan bir kitap rezervasyon sistemini içermektedir:

| Uygulama | Rol | Açıklama |
|----------|-----|----------|
| **LibApp** | Provider (Sağlayıcı) | Kitap kataloğunu barındıran ve verileri REST API üzerinden sunan ana kaynak uygulaması. |
| **ResApp** | Consumer (İstemci) | Kullanıcının etkileşime girdiği, rezervasyon işlemlerini yöneten ön yüz uygulaması. |

---

## 🏗️ Sistem Mimarisi

```
Kullanıcı
    │
    ▼ HTTP
┌─────────────────────────────────┐         ┌─────────────────────────────────┐
│           ResApp                │         │            LibApp               │
│  ┌──────────────────────────┐   │         │  ┌──────────────────────────┐   │
│  │  Presentation Katmanı    │   │         │  │  Presentation Katmanı    │   │
│  │  (MVC Controllers,       │   │         │  │  (MVC Admin UI +         │   │
│  │   Razor Pages, Views)    │   │  REST   │  │   REST API Controllers)  │   │
│  ├──────────────────────────┤   │◄──JSON──►  ├──────────────────────────┤   │
│  │  Servis Katmanı          │   │         │  │  Servis Katmanı          │   │
│  │  (IReservationService,   │   │         │  │  (IBookService)          │   │
│  │   IBookApiClientService) │   │         │  ├──────────────────────────┤   │
│  ├──────────────────────────┤   │         │  │  Veri Erişim Katmanı     │   │
│  │  Veri Erişim Katmanı     │   │         │  │  (AppDbContext)           │   │
│  │  (AppDbContext)           │   │         │  └──────────────────────────┘   │
│  └──────────────────────────┘   │         │                                 │
│           ▼                     │         │           ▼                     │
│        ResDb                    │         │        LibDb                    │
│  (Users, Reservations)          │         │  (Books, Authors, Categories)   │
└─────────────────────────────────┘         └─────────────────────────────────┘
```
---

## 📦 Teknoloji Yığını

- **.NET 9** / **ASP.NET Core 9.0**
- **Entity Framework Core** (Code-First yaklaşımı)
- **Microsoft SQL Server**
- **Bootstrap** 
- **Cookie-Based Authentication**
- **Dependency Injection**

---

## 🔐 Güvenlik

- **Cookie tabanlı kimlik doğrulama** (Secure, HTTP-Only)
- **Rol bazlı yetkilendirme** — `[Authorize]` ve `[Authorize(Roles = "Admin")]`
- **Parola hash'leme**

---