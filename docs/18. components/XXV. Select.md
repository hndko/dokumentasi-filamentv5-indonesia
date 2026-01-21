# XXV. Select 📋

> **Sumber:** [https://filamentphp.com/docs/5.x/components/select](https://filamentphp.com/docs/5.x/components/select)

---

## 🤔 Apa itu Select?

Basic native select component.

---

## 🚀 Penggunaan

```blade
<x-filament::input.wrapper label="Kategori">
    <x-filament::input.select wire:model="category">
        <option value="">Pilih kategori</option>
        <option value="news">Berita</option>
        <option value="tutorial">Tutorial</option>
    </x-filament::input.select>
</x-filament::input.wrapper>
```
