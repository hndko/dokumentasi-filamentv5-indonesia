# I. Upgrade Guide v4 ke v5 🔄

> **Sumber:** [https://filamentphp.com/docs/5.x/upgrade-guide](https://filamentphp.com/docs/5.x/upgrade-guide)

---

## 📋 Requirements Baru

| Requirement | Minimum |
| ----------- | ------- |
| PHP         | 8.2+    |
| Laravel     | 11.0+   |
| Livewire    | 3.0+    |

---

## 🚀 Automated Upgrade Script

Filament menyediakan script otomatis:

```bash
composer require filament/upgrade:"^3.2" --dev

vendor/bin/filament-v5
```

Script ini akan:

- Update `composer.json`
- Rename namespaces
- Update method signatures
- Fix breaking changes

---

## 🔄 Upgrade Livewire

Pastikan Livewire sudah v3:

```bash
composer require livewire/livewire:^3.0
```

---

## ⚠️ Breaking Changes Umum

### 1. Namespace Changes

```php
// v4
use Filament\Forms\Components\...

// v5
use Filament\Schemas\Components\...  // untuk layout
use Filament\Forms\Components\...    // untuk fields
```

### 2. Method Renames

```php
// v4
->schema([...])

// v5 (di beberapa tempat)
->components([...])
```

### 3. Form Schema ke Schemas

Forms dan Infolists sekarang berbagi "Schemas" package.

### 4. Panel Configuration

```php
// v4
->navigationGroups([...])

// v5
// Beberapa method mungkin berubah nama atau parameter
```

---

## 📝 Manual Steps Setelah Script

1. **Review semua file yang diubah**
2. **Test semua halaman**
3. **Cek custom components**
4. **Update published views**
5. **Test actions dan modals**

---

## 🔧 Common Fixes

### Fix: Class not found

```bash
composer dump-autoload
php artisan filament:clear-cached-components
```

### Fix: View not found

```bash
php artisan view:clear
php artisan cache:clear
```

### Fix: Assets outdated

```bash
php artisan filament:assets
```

---

## 📋 Upgrade Checklist

- [ ] Backup database dan code
- [ ] Update PHP ke 8.2+
- [ ] Update Laravel ke 11+
- [ ] Run `filament-v5` script
- [ ] Review changed files
- [ ] Test all resources
- [ ] Test all custom pages
- [ ] Test all widgets
- [ ] Clear all caches
- [ ] Deploy ke staging dulu
