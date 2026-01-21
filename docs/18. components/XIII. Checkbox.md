# XIII. Checkbox ✅

> **Sumber:** [https://filamentphp.com/docs/5.x/components/checkbox](https://filamentphp.com/docs/5.x/components/checkbox)

---

## 🤔 Apa itu Checkbox?

Blade component untuk input checkbox.

---

## 🚀 Penggunaan

```blade
<x-filament::checkbox
    wire:model="isActive"
/>
```

---

## ❌ Error State

```blade
<x-filament::checkbox
    wire:model="terms"
    :valid="! $errors->has('terms')"
/>
```
