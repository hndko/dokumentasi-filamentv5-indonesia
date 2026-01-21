# VII. Table Component 🗃️

> **Sumber:** [https://filamentphp.com/docs/5.x/components/table](https://filamentphp.com/docs/5.x/components/table)

---

## 🤔 Rendering Table di Blade

Gunakan table Filament di Livewire component custom.

---

## 🚀 Setup Livewire Component

```php
namespace App\Livewire;

use App\Models\Post;
use Filament\Tables\Concerns\InteractsWithTable;
use Filament\Tables\Contracts\HasTable;
use Filament\Tables\Table;
use Filament\Tables\Columns\TextColumn;
use Illuminate\Database\Eloquent\Builder;
use Livewire\Component;

class PostList extends Component implements HasTable
{
    use InteractsWithTable;

    public function table(Table $table): Table
    {
        return $table
            ->query(Post::query())
            ->columns([
                TextColumn::make('title')
                    ->searchable(),
                TextColumn::make('author.name'),
                TextColumn::make('created_at')
                    ->dateTime(),
            ])
            ->filters([...])
            ->actions([...]);
    }

    public function render()
    {
        return view('livewire.post-list');
    }
}
```

---

## 🎨 Render di Blade

```blade
<div>
    {{ $this->table }}
</div>
```

---

## 🔗 Relationship Table

```php
public function table(Table $table): Table
{
    return $table
        ->relationship(fn () => $this->author->posts())
        ->columns([...]);
}
```

---

## 🚀 Generate dengan CLI

```bash
php artisan make:livewire PostList
```

---

## 🔧 Auto Generate Columns

```bash
php artisan make:livewire PostList --generate
```
