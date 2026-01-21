# III. Enum Tricks 🎭

> **Sumber:** [https://filamentphp.com/docs/5.x/advanced/enums](https://filamentphp.com/docs/5.x/advanced/enums)

---

## 🤔 Tentang Enums

PHP 8.1+ enums bisa digunakan dengan Filament untuk labels, colors, icons, dll.

---

## 🏷️ Enum Labels

```php
use Filament\Support\Contracts\HasLabel;

enum Status: string implements HasLabel
{
    case Draft = 'draft';
    case Published = 'published';
    case Archived = 'archived';

    public function getLabel(): ?string
    {
        return match ($this) {
            self::Draft => 'Draft',
            self::Published => 'Dipublikasikan',
            self::Archived => 'Diarsipkan',
        };
    }
}
```

### Penggunaan

```php
// Form select options otomatis
Select::make('status')
    ->options(Status::class)

// Table column
TextColumn::make('status')
    // Label otomatis dari enum

// Infolist entry
TextEntry::make('status')
    // Label otomatis
```

---

## 🎨 Enum Colors

```php
use Filament\Support\Contracts\HasColor;

enum Status: string implements HasLabel, HasColor
{
    case Draft = 'draft';
    case Published = 'published';
    case Archived = 'archived';

    public function getColor(): string|array|null
    {
        return match ($this) {
            self::Draft => 'gray',
            self::Published => 'success',
            self::Archived => 'warning',
        };
    }
}
```

### Penggunaan

```php
TextColumn::make('status')
    ->badge()
    // Color otomatis dari enum

ToggleButtons::make('status')
    ->options(Status::class)
    // Colors otomatis
```

---

## 🎯 Enum Icons

```php
use Filament\Support\Contracts\HasIcon;

enum Status: string implements HasLabel, HasColor, HasIcon
{
    case Draft = 'draft';
    case Published = 'published';
    case Archived = 'archived';

    public function getIcon(): ?string
    {
        return match ($this) {
            self::Draft => 'heroicon-o-pencil',
            self::Published => 'heroicon-o-check-circle',
            self::Archived => 'heroicon-o-archive-box',
        };
    }
}
```

---

## 📝 Enum Descriptions

```php
use Filament\Support\Contracts\HasDescription;

enum Priority: string implements HasLabel, HasDescription
{
    case Low = 'low';
    case Medium = 'medium';
    case High = 'high';

    public function getDescription(): ?string
    {
        return match ($this) {
            self::Low => 'Bisa ditunda',
            self::Medium => 'Perlu diperhatikan',
            self::High => 'Harus segera ditangani',
        };
    }
}
```

### Penggunaan

```php
Radio::make('priority')
    ->options(Priority::class)
    // Descriptions otomatis
```

---

## 💡 Contoh Lengkap

```php
use Filament\Support\Contracts\HasLabel;
use Filament\Support\Contracts\HasColor;
use Filament\Support\Contracts\HasIcon;

enum OrderStatus: string implements HasLabel, HasColor, HasIcon
{
    case Pending = 'pending';
    case Processing = 'processing';
    case Shipped = 'shipped';
    case Delivered = 'delivered';
    case Cancelled = 'cancelled';

    public function getLabel(): ?string
    {
        return match ($this) {
            self::Pending => 'Menunggu',
            self::Processing => 'Diproses',
            self::Shipped => 'Dikirim',
            self::Delivered => 'Diterima',
            self::Cancelled => 'Dibatalkan',
        };
    }

    public function getColor(): string|array|null
    {
        return match ($this) {
            self::Pending => 'warning',
            self::Processing => 'info',
            self::Shipped => 'primary',
            self::Delivered => 'success',
            self::Cancelled => 'danger',
        };
    }

    public function getIcon(): ?string
    {
        return match ($this) {
            self::Pending => 'heroicon-o-clock',
            self::Processing => 'heroicon-o-arrow-path',
            self::Shipped => 'heroicon-o-truck',
            self::Delivered => 'heroicon-o-check-badge',
            self::Cancelled => 'heroicon-o-x-circle',
        };
    }
}
```

---

## 🎯 Latihan Mandiri

Buat enum untuk:

- PaymentStatus dengan label, color, icon
- Priority dengan description
- UserRole dengan label dan color
