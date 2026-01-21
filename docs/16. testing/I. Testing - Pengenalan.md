# I. Testing - Pengenalan 🧪

> **Sumber:** [https://filamentphp.com/docs/5.x/testing/overview](https://filamentphp.com/docs/5.x/testing/overview)

---

## 🤔 Tentang Testing

Filament menyediakan helper methods untuk testing menggunakan Laravel's testing tools dan Livewire::test().

---

## 📋 Testing Guides

| Guide                 | Topik                          |
| --------------------- | ------------------------------ |
| Testing Resources     | List, Create, Edit, View pages |
| Testing Tables        | Columns, filters, actions      |
| Testing Schemas       | Forms, infolists               |
| Testing Actions       | Semua jenis actions            |
| Testing Notifications | Session notifications          |

---

## 🔧 Livewire Component

Setiap halaman Filament adalah Livewire component:

```php
use Livewire\Livewire;

Livewire::test(ListUsers::class)
    ->assertSuccessful();
```

### Resource Pages

```php
// List page
Livewire::test(ListUsers::class)

// Create page
Livewire::test(CreateUser::class)

// Edit page
Livewire::test(EditUser::class, ['record' => $user->id])

// View page
Livewire::test(ViewUser::class, ['record' => $user->id])
```

---

## 🔑 Test Setup

```php
use Tests\TestCase;
use Illuminate\Foundation\Testing\RefreshDatabase;

class UserResourceTest extends TestCase
{
    use RefreshDatabase;

    protected function setUp(): void
    {
        parent::setUp();

        // Login sebagai user
        $this->actingAs(User::factory()->create());
    }
}
```

---

## 🎯 Latihan Mandiri

Setup testing dengan:

- Test case base class
- Factory untuk User
- Basic assertion untuk list page
