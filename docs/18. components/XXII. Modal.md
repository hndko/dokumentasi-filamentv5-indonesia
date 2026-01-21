# XXII. Modal 🪟

> **Sumber:** [https://filamentphp.com/docs/5.x/components/modal](https://filamentphp.com/docs/5.x/components/modal)

---

## 🤔 Apa itu Modal?

Popup modal component.

---

## 🚀 Penggunaan

```blade
<x-filament::modal>
    <x-slot name="trigger">
        <x-filament::button>
            Buka Modal
        </x-filament::button>
    </x-slot>

    Konten modal di sini.
</x-filament::modal>
```

---

## 🎮 Control dari JavaScript

```blade
<x-filament::modal id="my-modal">
    Konten modal
</x-filament::modal>

<button x-on:click="$dispatch('open-modal', { id: 'my-modal' })">
    Buka
</button>
```

---

## 📝 Heading

```blade
<x-filament::modal heading="Konfirmasi">
    Apakah Anda yakin?
</x-filament::modal>
```

---

## 📝 Description

```blade
<x-filament::modal
    heading="Hapus Item"
    description="Tindakan ini tidak dapat dibatalkan."
>
    ...
</x-filament::modal>
```

---

## 🎯 Icon

```blade
<x-filament::modal icon="heroicon-o-exclamation-triangle" icon-color="danger">
    Peringatan!
</x-filament::modal>
```

---

## 📦 Footer

```blade
<x-filament::modal>
    Konten

    <x-slot name="footer">
        <x-filament::button>Simpan</x-filament::button>
    </x-slot>
</x-filament::modal>
```

---

## 📍 Alignment

```blade
<x-filament::modal alignment="center">
    ...
</x-filament::modal>
```

---

## 📱 Slide Over

```blade
<x-filament::modal slide-over>
    Slide dari samping
</x-filament::modal>
```

---

## 📌 Sticky Header/Footer

```blade
<x-filament::modal sticky-header sticky-footer>
    Long content...
</x-filament::modal>
```

---

## 📏 Width

```blade
<x-filament::modal width="md">...</x-filament::modal>
<x-filament::modal width="lg">...</x-filament::modal>
<x-filament::modal width="xl">...</x-filament::modal>
<x-filament::modal width="2xl">...</x-filament::modal>
```

---

## ⚙️ Options

```blade
{{-- Disable close on click away --}}
<x-filament::modal :close-by-clicking-away="false">

{{-- Disable close on escape --}}
<x-filament::modal :close-by-escaping="false">

{{-- Hide close button --}}
<x-filament::modal :close-button="false">

{{-- Disable autofocus --}}
<x-filament::modal :autofocus="false">
```
