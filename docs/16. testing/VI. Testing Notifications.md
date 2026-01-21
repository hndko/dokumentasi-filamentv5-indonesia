# VI. Testing Notifications 🔔

> **Sumber:** [https://filamentphp.com/docs/5.x/testing/testing-notifications](https://filamentphp.com/docs/5.x/testing/testing-notifications)

---

## 🔔 Testing Session Notifications

```php
use Filament\Notifications\Notification;

it('shows success notification after create', function () {
    livewire(CreateUser::class)
        ->fillForm([
            'name' => 'John Doe',
            'email' => 'john@example.com',
            'password' => 'password',
        ])
        ->call('create')
        ->assertNotified();
});
```

---

## 🏷️ Testing Notification Title

```php
it('shows correct notification title', function () {
    livewire(CreateUser::class)
        ->fillForm([...])
        ->call('create')
        ->assertNotified('User berhasil dibuat');
});
```

---

## 🎨 Testing Notification Object

```php
it('shows success notification', function () {
    livewire(CreateUser::class)
        ->fillForm([...])
        ->call('create')
        ->assertNotified(
            Notification::make()
                ->title('User berhasil dibuat')
                ->success()
        );
});
```

---

## ❌ Testing No Notification

```php
it('does not show notification on validation error', function () {
    livewire(CreateUser::class)
        ->fillForm([
            'name' => '',
        ])
        ->call('create')
        ->assertNotNotified();
});
```

---

## 💡 Contoh Lengkap

```php
use function Pest\Livewire\livewire;
use Filament\Notifications\Notification;

describe('User Notifications', function () {
    beforeEach(function () {
        $this->actingAs(User::factory()->create());
    });

    it('shows success on create', function () {
        livewire(CreateUser::class)
            ->fillForm([
                'name' => 'John',
                'email' => 'john@test.com',
                'password' => 'password',
            ])
            ->call('create')
            ->assertNotified('User berhasil dibuat');
    });

    it('shows success on update', function () {
        $user = User::factory()->create();

        livewire(EditUser::class, ['record' => $user->getRouteKey()])
            ->fillForm(['name' => 'Updated'])
            ->call('save')
            ->assertNotified('User berhasil diperbarui');
    });

    it('shows warning on soft delete', function () {
        $user = User::factory()->create();

        livewire(ListUsers::class)
            ->callTableAction('delete', $user)
            ->assertNotified(
                Notification::make()
                    ->title('User dihapus')
                    ->warning()
            );
    });
});
```

---

## 🎯 Latihan Mandiri

Buat tests untuk notifications:

- Success setelah create
- Success setelah update
- Warning setelah delete
- Error jika gagal
