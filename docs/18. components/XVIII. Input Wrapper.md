# XVIII. Input Wrapper 📝

> **Sumber:** [https://filamentphp.com/docs/5.x/components/input-wrapper](https://filamentphp.com/docs/5.x/components/input-wrapper)

---

## 🤔 Apa itu Input Wrapper?

Wrapper untuk input dengan label, hint, dan error message.

---

## 🚀 Penggunaan

```blade
<x-filament::input.wrapper label="Nama">
    <x-filament::input wire:model="name" />
</x-filament::input.wrapper>
```

---

## ❌ Error State

```blade
<x-filament::input.wrapper
    label="Email"
    :valid="! $errors->has('email')"
>
    <x-filament::input wire:model="email" />
</x-filament::input.wrapper>
```

---

## 🔒 Disabled

```blade
<x-filament::input.wrapper label="ID" disabled>
    <x-filament::input wire:model="id" disabled />
</x-filament::input.wrapper>
```

---

## 📝 Affix Text

```blade
<x-filament::input.wrapper
    label="Domain"
    prefix="https://"
    suffix=".com"
>
    <x-filament::input wire:model="domain" />
</x-filament::input.wrapper>
```

---

## 🎯 Affix Icons

```blade
<x-filament::input.wrapper
    label="Email"
    prefix-icon="heroicon-o-envelope"
>
    <x-filament::input wire:model="email" />
</x-filament::input.wrapper>

<x-filament::input.wrapper
    label="Search"
    suffix-icon="heroicon-o-magnifying-glass"
>
    <x-filament::input wire:model="search" />
</x-filament::input.wrapper>
```
