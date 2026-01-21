# XVI. Fieldset 📦

> **Sumber:** [https://filamentphp.com/docs/5.x/components/fieldset](https://filamentphp.com/docs/5.x/components/fieldset)

---

## 🤔 Apa itu Fieldset?

Container untuk grouping form fields.

---

## 🚀 Penggunaan

```blade
<x-filament::fieldset label="Alamat">
    <div class="space-y-4">
        <x-filament::input.wrapper label="Jalan">
            <x-filament::input wire:model="street" />
        </x-filament::input.wrapper>

        <x-filament::input.wrapper label="Kota">
            <x-filament::input wire:model="city" />
        </x-filament::input.wrapper>
    </div>
</x-filament::fieldset>
```
