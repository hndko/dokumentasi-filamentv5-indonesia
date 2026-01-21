# IV. Testing Schemas 📝

> **Sumber:** [https://filamentphp.com/docs/5.x/testing/testing-schemas](https://filamentphp.com/docs/5.x/testing/testing-schemas)

---

## 📝 Filling Form

```php
livewire(CreateUser::class)
    ->fillForm([
        'name' => 'John Doe',
        'email' => 'john@example.com',
    ]);
```

---

## 🔍 Testing Field State

```php
it('has correct initial state', function () {
    $user = User::factory()->create();

    livewire(EditUser::class, ['record' => $user->getRouteKey()])
        ->assertFormFieldExists('name')
        ->assertFormFieldState('name', $user->name);
});
```

---

## ✅ Testing Validation

```php
it('validates required name', function () {
    livewire(CreateUser::class)
        ->fillForm([
            'name' => '',
        ])
        ->call('create')
        ->assertHasFormErrors(['name' => 'required']);
});

it('validates email format', function () {
    livewire(CreateUser::class)
        ->fillForm([
            'email' => 'not-an-email',
        ])
        ->call('create')
        ->assertHasFormErrors(['email' => 'email']);
});

it('validates unique email', function () {
    User::factory()->create(['email' => 'taken@example.com']);

    livewire(CreateUser::class)
        ->fillForm([
            'email' => 'taken@example.com',
        ])
        ->call('create')
        ->assertHasFormErrors(['email' => 'unique']);
});
```

---

## 📋 Testing Form Exists

```php
it('has form', function () {
    livewire(CreateUser::class)
        ->assertFormExists();
});
```

---

## 📋 Testing Field Exists

```php
it('has name field', function () {
    livewire(CreateUser::class)
        ->assertFormFieldExists('name');
});
```

---

## 👁️ Testing Field Visibility

```php
it('name field is visible', function () {
    livewire(CreateUser::class)
        ->assertFormFieldIsVisible('name');
});

it('admin fields hidden for non-admin', function () {
    $this->actingAs(User::factory()->create(['is_admin' => false]));

    livewire(CreateUser::class)
        ->assertFormFieldIsHidden('admin_notes');
});
```

---

## 🔒 Testing Disabled Fields

```php
it('email is disabled on edit', function () {
    $user = User::factory()->create();

    livewire(EditUser::class, ['record' => $user->getRouteKey()])
        ->assertFormFieldIsDisabled('email');
});
```

---

## 🔄 Testing Repeater

```php
it('can add repeater item', function () {
    livewire(EditUser::class, ['record' => $user->getRouteKey()])
        ->callFormComponentAction('addresses', 'add')
        ->assertFormFieldExists('addresses.0.street');
});
```

---

## 🧙 Testing Wizard

```php
it('can navigate wizard', function () {
    livewire(CreateUser::class)
        ->fillForm(['name' => 'John'])
        ->call('nextStep')
        ->assertFormFieldExists('email');
});
```

---

## 🎯 Latihan Mandiri

Buat tests untuk:

- Validasi required, email, unique
- Field visibility berdasarkan role
- Repeater items
