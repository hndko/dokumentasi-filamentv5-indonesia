# III. Form Component 📝

> **Sumber:** [https://filamentphp.com/docs/5.x/components/form](https://filamentphp.com/docs/5.x/components/form)

---

## 🤔 Rendering Form di Blade

Gunakan form Filament di Livewire component custom.

---

## 🚀 Setup Livewire Component

```php
namespace App\Livewire;

use Filament\Forms\Concerns\InteractsWithForms;
use Filament\Forms\Contracts\HasForms;
use Filament\Forms\Form;
use Filament\Forms\Components\TextInput;
use Livewire\Component;

class CreatePost extends Component implements HasForms
{
    use InteractsWithForms;

    public ?array $data = [];

    public function mount(): void
    {
        $this->form->fill();
    }

    public function form(Form $form): Form
    {
        return $form
            ->schema([
                TextInput::make('title')
                    ->required(),
                TextInput::make('slug'),
            ])
            ->statePath('data');
    }

    public function create(): void
    {
        $data = $this->form->getState();

        Post::create($data);
    }

    public function render()
    {
        return view('livewire.create-post');
    }
}
```

---

## 🎨 Render di Blade

```blade
<form wire:submit="create">
    {{ $this->form }}

    <x-filament::button type="submit">
        Simpan
    </x-filament::button>
</form>
```

---

## 📦 Initialize dengan Data

```php
public function mount(): void
{
    $this->form->fill([
        'title' => 'Default Title',
    ]);
}
```

---

## 🔗 Form Model

```php
public Post $post;

public function form(Form $form): Form
{
    return $form
        ->schema([...])
        ->model($this->post)
        ->statePath('data');
}
```

---

## 📂 Multiple Forms

```php
public function contactForm(Form $form): Form {...}
public function addressForm(Form $form): Form {...}

protected function getForms(): array
{
    return [
        'contactForm',
        'addressForm',
    ];
}
```

---

## 🔄 Reset Form

```php
$this->form->fill();
```

---

## 🚀 Generate dengan CLI

```bash
php artisan make:livewire CreatePost
```
