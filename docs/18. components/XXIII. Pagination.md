# XXIII. Pagination 📄

> **Sumber:** [https://filamentphp.com/docs/5.x/components/pagination](https://filamentphp.com/docs/5.x/components/pagination)

---

## 🤔 Apa itu Pagination?

Navigasi halaman untuk data banyak.

---

## 🚀 Penggunaan

```blade
<x-filament::pagination :paginator="$posts" />
```

---

## 🔢 Per Page Options

```blade
<x-filament::pagination
    :paginator="$posts"
    :page-options="[10, 25, 50, 100]"
/>
```

---

## ↔️ First/Last Links

```blade
<x-filament::pagination
    :paginator="$posts"
    :extreme-links="true"
/>
```
