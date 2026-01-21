# III. Testing Tables 🗃️

> **Sumber:** [https://filamentphp.com/docs/5.x/testing/testing-tables](https://filamentphp.com/docs/5.x/testing/testing-tables)

---

## 📋 Testing Table Render

```php
it('can render table', function () {
    livewire(ListUsers::class)
        ->assertSuccessful();
});
```

---

## 📊 Testing Columns

### Column State

```php
it('can display user name', function () {
    $user = User::factory()->create();

    livewire(ListUsers::class)
        ->assertTableColumnStateSet('name', $user->name, $user);
});
```

### Column Exists

```php
it('has name column', function () {
    livewire(ListUsers::class)
        ->assertTableColumnExists('name');
});
```

### Column Visibility

```php
it('name column is visible', function () {
    livewire(ListUsers::class)
        ->assertTableColumnVisible('name');
});

it('secret column is hidden', function () {
    livewire(ListUsers::class)
        ->assertTableColumnHidden('secret');
});
```

---

## 🔍 Testing Search

```php
it('can search by name', function () {
    $users = User::factory()->count(10)->create();
    $searchUser = $users->first();

    livewire(ListUsers::class)
        ->searchTable($searchUser->name)
        ->assertCanSeeTableRecords([$searchUser])
        ->assertCanNotSeeTableRecords($users->skip(1));
});
```

---

## ↕️ Testing Sort

```php
it('can sort by name', function () {
    $users = User::factory()->count(5)->create();

    livewire(ListUsers::class)
        ->sortTable('name')
        ->assertCanSeeTableRecords($users->sortBy('name'), inOrder: true);

    livewire(ListUsers::class)
        ->sortTable('name', 'desc')
        ->assertCanSeeTableRecords($users->sortByDesc('name'), inOrder: true);
});
```

---

## 🔍 Testing Filters

```php
it('can filter by active status', function () {
    $activeUsers = User::factory()->count(3)->create(['is_active' => true]);
    $inactiveUsers = User::factory()->count(2)->create(['is_active' => false]);

    livewire(ListUsers::class)
        ->filterTable('is_active', true)
        ->assertCanSeeTableRecords($activeUsers)
        ->assertCanNotSeeTableRecords($inactiveUsers);
});

it('can reset filters', function () {
    livewire(ListUsers::class)
        ->filterTable('is_active', true)
        ->resetTableFilters()
        ->assertCanSeeTableRecords(User::all());
});
```

### Filter Exists

```php
it('has active filter', function () {
    livewire(ListUsers::class)
        ->assertTableFilterExists('is_active');
});
```

---

## 📊 Testing Summaries

```php
it('shows total count', function () {
    User::factory()->count(10)->create();

    livewire(ListUsers::class)
        ->assertTableColumnSummarySet('id', 'count', 10);
});
```

---

## 🎯 Latihan Mandiri

Buat tests untuk:

- Kolom name, email, created_at
- Search by email
- Filter by status
- Sort by created_at
