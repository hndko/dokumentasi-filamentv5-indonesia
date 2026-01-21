# IV. Infolist Component 📋

> **Sumber:** [https://filamentphp.com/docs/5.x/components/infolist](https://filamentphp.com/docs/5.x/components/infolist)

---

## 🤔 Rendering Infolist di Blade

Tampilkan data read-only dengan Infolist di Livewire component.

---

## 🚀 Setup Livewire Component

```php
namespace App\Livewire;

use Filament\Infolists\Concerns\InteractsWithInfolists;
use Filament\Infolists\Contracts\HasInfolists;
use Filament\Infolists\Infolist;
use Filament\Infolists\Components\TextEntry;
use Livewire\Component;

class ViewPost extends Component implements HasInfolists
{
    use InteractsWithInfolists;

    public Post $post;

    public function postInfolist(Infolist $infolist): Infolist
    {
        return $infolist
            ->record($this->post)
            ->schema([
                TextEntry::make('title'),
                TextEntry::make('author.name'),
                TextEntry::make('created_at')
                    ->dateTime(),
            ]);
    }

    public function render()
    {
        return view('livewire.view-post');
    }
}
```

---

## 🎨 Render di Blade

```blade
<div>
    {{ $this->postInfolist }}
</div>
```

---

## 📦 Passing Data

```php
public function postInfolist(Infolist $infolist): Infolist
{
    return $infolist
        ->record($this->post)
        ->schema([...]);
}
```

Atau dengan array:

```php
public function postInfolist(Infolist $infolist): Infolist
{
    return $infolist
        ->state([
            'title' => 'My Post',
            'author' => ['name' => 'John'],
        ])
        ->schema([...]);
}
```
