# I. Components - Pengenalan 📦

> **Sumber:** [https://filamentphp.com/docs/5.x/components/overview](https://filamentphp.com/docs/5.x/components/overview)

---

## 🤔 Apa itu Components?

**Components** adalah Blade components reusable yang disediakan oleh Filament. Bisa digunakan di dalam maupun di luar panel.

---

## 📦 Package Components

Gunakan komponen Filament di Livewire component custom:

- **Action** - Tombol dengan modal/action
- **Form** - Form lengkap dengan validasi
- **Infolist** - Menampilkan data read-only
- **Notifications** - Toast notifications
- **Schema** - Layout components
- **Table** - Data table
- **Widget** - Dashboard widgets

---

## 🎨 Blade Components

UI components yang bisa dipakai langsung di Blade:

| Component         | Fungsi                     |
| ----------------- | -------------------------- |
| Avatar            | Gambar profil              |
| Badge             | Label status               |
| Breadcrumbs       | Navigation path            |
| Button            | Tombol                     |
| Checkbox          | Input checkbox             |
| Dropdown          | Dropdown menu              |
| Empty State       | Placeholder "data kosong"  |
| Fieldset          | Grouping form fields       |
| Icon Button       | Tombol dengan icon saja    |
| Input             | Text input                 |
| Input Wrapper     | Wrapper dengan label/error |
| Link              | Text link                  |
| Loading Indicator | Spinner loading            |
| Modal             | Popup modal                |
| Pagination        | Navigasi halaman           |
| Section           | Container dengan heading   |
| Select            | Dropdown select            |
| Tabs              | Tab navigation             |

---

## 🚀 Penggunaan

```blade
<x-filament::button color="primary">
    Klik Saya
</x-filament::button>

<x-filament::badge color="success">
    Aktif
</x-filament::badge>
```
