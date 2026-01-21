# IV. File Generation 🔧

> **Sumber:** [https://filamentphp.com/docs/5.x/advanced/file-generation](https://filamentphp.com/docs/5.x/advanced/file-generation)

---

## 🤔 Tentang File Generation

Filament menggunakan **class generators** untuk membuat file via artisan commands. Anda bisa mengkustomisasi output generator.

---

## 🏗️ Anatomy of Class Generator

Setiap generator terdiri dari:

- Properties (class properties)
- Methods (class methods)

---

## 🔄 Replacing a Class Generator

```php
use Filament\Support\Commands\Concerns\CanGenerateResources;

// Di AppServiceProvider
CanGenerateResources::resolveResourceClassGeneratorUsing(
    fn () => new CustomResourceClassGenerator(),
);
```

---

## 🔧 Customizing Property/Method

```php
use Filament\Commands\FileGenerators\Resources\ResourceClassGenerator;

ResourceClassGenerator::modifyPropertyUsing('navigationIcon', function ($property) {
    $property->setDefault("'heroicon-o-folder'");
    return $property;
});
```

---

## ➕ Adding New Property/Method

```php
ResourceClassGenerator::modifyClassBodyUsing(function ($class) {
    $class->addProperty(
        \Nette\PhpGenerator\Property::make('customProperty')
            ->setProtected()
            ->setStatic()
            ->setType('?string')
            ->setValue('custom value'),
    );

    return $class;
});
```

---

## 💡 Contoh: Custom Resource Generator

```php
// Di AppServiceProvider boot()

use Filament\Commands\FileGenerators\Resources\ResourceClassGenerator;

ResourceClassGenerator::modifyPropertyUsing('navigationIcon', function ($property) {
    $property->setDefault("'heroicon-o-rectangle-stack'");
    return $property;
});

ResourceClassGenerator::modifyPropertyUsing('navigationGroup', function ($property) {
    $property->setDefault("'Master Data'");
    return $property;
});
```

---

## 🎯 Latihan Mandiri

Kustomisasi generator untuk:

- Default navigation icon
- Default navigation group
- Tambah custom property
