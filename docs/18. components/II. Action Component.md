# II. Action Component ⚡

> **Sumber:** [https://filamentphp.com/docs/5.x/components/action](https://filamentphp.com/docs/5.x/components/action)

---

## 🤔 Rendering Action di Livewire

Action bisa dirender di Livewire component custom.

---

## 🚀 Setup Livewire Component

```php
namespace App\Livewire;

use Filament\Actions\Action;
use Filament\Actions\Concerns\InteractsWithActions;
use Filament\Actions\Contracts\HasActions;
use Filament\Forms\Concerns\InteractsWithForms;
use Filament\Forms\Contracts\HasForms;
use Livewire\Component;

class MyComponent extends Component implements HasForms, HasActions
{
    use InteractsWithForms;
    use InteractsWithActions;

    public function createAction(): Action
    {
        return Action::make('create')
            ->label('Buat Baru')
            ->action(fn () => $this->create());
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
    {{ $this->createAction }}

    <x-filament-actions::modals />
</div>
```

---

## 📦 Passing Arguments

```php
public function deleteAction(): Action
{
    return Action::make('delete')
        ->action(function (array $arguments) {
            $id = $arguments['id'];
            // Delete logic
        });
}
```

```blade
{{ $this->deleteAction(['id' => $item->id]) }}
```

---

## 👁️ Hiding Actions

```blade
{{ $this->createAction->visible($canCreate) }}
```

---

## 📂 Grouping Actions

```blade
<x-filament-actions::group :actions="[
    $this->editAction,
    $this->deleteAction,
]" />
```

---

## 🔗 Chaining Actions

```php
Action::make('confirm')
    ->action(function (Action $action) {
        // Do something
        $action->replaceMountedAction('success');
    })
```

---

## ⚡ Trigger Programmatically

```php
$this->mount('create');
```
