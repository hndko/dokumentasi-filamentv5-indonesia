# II. Testing Resources 📋

> **Sumber:** [https://filamentphp.com/docs/5.x/testing/testing-resources](https://filamentphp.com/docs/5.x/testing/testing-resources)

---

## 🔑 Authenticating

```php
use App\Models\User;

$user = User::factory()->create();

$this->actingAs($user);
```

---

## 📋 Testing List Page

```php
use function Pest\Livewire\livewire;
use App\Filament\Resources\UserResource\Pages\ListUsers;

it('can render list page', function () {
    $this->actingAs(User::factory()->create());

    livewire(ListUsers::class)
        ->assertSuccessful();
});

it('can list users', function () {
    $users = User::factory()->count(10)->create();

    livewire(ListUsers::class)
        ->assertCanSeeTableRecords($users);
});
```

---

## ➕ Testing Create Page

```php
use App\Filament\Resources\UserResource\Pages\CreateUser;

it('can render create page', function () {
    livewire(CreateUser::class)
        ->assertSuccessful();
});

it('can create user', function () {
    $newData = User::factory()->make();

    livewire(CreateUser::class)
        ->fillForm([
            'name' => $newData->name,
            'email' => $newData->email,
            'password' => 'password',
        ])
        ->call('create')
        ->assertHasNoFormErrors();

    $this->assertDatabaseHas(User::class, [
        'name' => $newData->name,
        'email' => $newData->email,
    ]);
});

it('validates required fields', function () {
    livewire(CreateUser::class)
        ->fillForm([
            'name' => null,
        ])
        ->call('create')
        ->assertHasFormErrors(['name' => 'required']);
});
```

---

## ✏️ Testing Edit Page

```php
use App\Filament\Resources\UserResource\Pages\EditUser;

it('can render edit page', function () {
    $user = User::factory()->create();

    livewire(EditUser::class, ['record' => $user->getRouteKey()])
        ->assertSuccessful();
});

it('can update user', function () {
    $user = User::factory()->create();
    $newData = User::factory()->make();

    livewire(EditUser::class, ['record' => $user->getRouteKey()])
        ->fillForm([
            'name' => $newData->name,
            'email' => $newData->email,
        ])
        ->call('save')
        ->assertHasNoFormErrors();

    $this->assertDatabaseHas(User::class, [
        'id' => $user->id,
        'name' => $newData->name,
    ]);
});
```

---

## 👁️ Testing View Page

```php
use App\Filament\Resources\UserResource\Pages\ViewUser;

it('can render view page', function () {
    $user = User::factory()->create();

    livewire(ViewUser::class, ['record' => $user->getRouteKey()])
        ->assertSuccessful();
});
```

---

## 🔗 Testing Relation Managers

```php
use App\Filament\Resources\UserResource\RelationManagers\OrdersRelationManager;

it('can list orders', function () {
    $user = User::factory()
        ->has(Order::factory()->count(3))
        ->create();

    livewire(OrdersRelationManager::class, [
        'ownerRecord' => $user,
        'pageClass' => EditUser::class,
    ])
        ->assertCanSeeTableRecords($user->orders);
});
```

---

## 🎯 Latihan Mandiri

Buat tests untuk:

- UserResource list, create, edit
- Validation errors
- Relation manager
