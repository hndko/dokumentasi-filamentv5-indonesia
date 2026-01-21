# VI. Schema Component 🧩

> **Sumber:** [https://filamentphp.com/docs/5.x/components/schema](https://filamentphp.com/docs/5.x/components/schema)

---

## 🤔 Rendering Schema di Blade

Schema adalah layout components tanpa form behavior.

---

## 🚀 Setup Livewire Component

```php
namespace App\Livewire;

use Filament\Schemas\Concerns\InteractsWithSchemas;
use Filament\Schemas\Contracts\HasSchemas;
use Filament\Schemas\Schema;
use Filament\Schemas\Components\Section;
use Filament\Schemas\Components\TextEntry;
use Livewire\Component;

class MyComponent extends Component implements HasSchemas
{
    use InteractsWithSchemas;

    public function schema(Schema $schema): Schema
    {
        return $schema
            ->schema([
                Section::make('Info')
                    ->schema([
                        // Components here
                    ]),
            ]);
    }

    public function render()
    {
        return view('livewire.my-component');
    }
}
```

---

## 🎨 Render di Blade

```blade
<div>
    {{ $this->schema }}
</div>
```
