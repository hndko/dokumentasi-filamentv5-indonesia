# XIX. Input ⌨️

> **Sumber:** [https://filamentphp.com/docs/5.x/components/input](https://filamentphp.com/docs/5.x/components/input)

---

## 🤔 Apa itu Input?

Basic text input component.

---

## 🚀 Penggunaan

```blade
<x-filament::input wire:model="name" />
```

---

## 📝 Dengan Wrapper

```blade
<x-filament::input.wrapper label="Nama">
    <x-filament::input
        type="text"
        wire:model="name"
        placeholder="Masukkan nama"
    />
</x-filament::input.wrapper>
```

---

## 📋 Types

```blade
<x-filament::input type="text" />
<x-filament::input type="email" />
<x-filament::input type="password" />
<x-filament::input type="number" />
<x-filament::input type="tel" />
<x-filament::input type="url" />
```
