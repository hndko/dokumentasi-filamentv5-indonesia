# V. Testing Actions ⚡

> **Sumber:** [https://filamentphp.com/docs/5.x/testing/testing-actions](https://filamentphp.com/docs/5.x/testing/testing-actions)

---

## 🔧 Calling Actions

```php
livewire(ListUsers::class)
    ->callAction('create');
```

---

## 📋 Testing Table Actions

```php
it('can delete user', function () {
    $user = User::factory()->create();

    livewire(ListUsers::class)
        ->callTableAction('delete', $user)
        ->assertSuccessful();

    $this->assertModelMissing($user);
});

it('can edit user', function () {
    $user = User::factory()->create();

    livewire(ListUsers::class)
        ->callTableAction('edit', $user, [
            'name' => 'New Name',
        ])
        ->assertHasNoActionErrors();
});
```

### Header Actions

```php
it('can call header action', function () {
    livewire(ListUsers::class)
        ->callTableAction('export');
});
```

### Bulk Actions

```php
it('can bulk delete', function () {
    $users = User::factory()->count(5)->create();

    livewire(ListUsers::class)
        ->callTableBulkAction('delete', $users);

    foreach ($users as $user) {
        $this->assertModelMissing($user);
    }
});
```

---

## 📝 Testing Action Forms

```php
it('can fill action form', function () {
    $user = User::factory()->create();

    livewire(ListUsers::class)
        ->callTableAction('updateStatus', $user, [
            'status' => 'active',
        ]);

    expect($user->fresh()->status)->toBe('active');
});

it('validates action form', function () {
    $user = User::factory()->create();

    livewire(ListUsers::class)
        ->callTableAction('updateStatus', $user, [
            'status' => null,
        ])
        ->assertHasActionErrors(['status' => 'required']);
});
```

---

## ✅ Testing Action Existence

```php
it('has delete action', function () {
    livewire(ListUsers::class)
        ->assertTableActionExists('delete');
});
```

---

## 👁️ Testing Action Visibility

```php
it('delete action is visible', function () {
    $user = User::factory()->create();

    livewire(ListUsers::class)
        ->assertTableActionVisible('delete', $user);
});

it('delete action hidden for admin', function () {
    $admin = User::factory()->create(['role' => 'admin']);

    livewire(ListUsers::class)
        ->assertTableActionHidden('delete', $admin);
});
```

---

## 🔒 Testing Disabled Actions

```php
it('edit disabled for locked user', function () {
    $user = User::factory()->create(['locked' => true]);

    livewire(ListUsers::class)
        ->assertTableActionDisabled('edit', $user);
});
```

---

## 🏷️ Testing Action Properties

```php
it('delete action has danger color', function () {
    livewire(ListUsers::class)
        ->assertTableActionHasColor('delete', 'danger');
});

it('edit action has correct icon', function () {
    livewire(ListUsers::class)
        ->assertTableActionHasIcon('edit', 'heroicon-o-pencil');
});
```

---

## ⛔ Testing Halted Actions

```php
it('action can be halted', function () {
    $user = User::factory()->create(['protected' => true]);

    livewire(ListUsers::class)
        ->callTableAction('delete', $user)
        ->assertActionHalted('delete');
});
```

---

## 🎯 Latihan Mandiri

Buat tests untuk:

- Delete action dengan confirmation
- Edit action dengan form validation
- Bulk delete action
- Action visibility berdasarkan role
