# How to Define Foreign Keys in Laravel

## There are several ways to define foreign keys in a Laravel migration file. Here are three of the most common methods:
1. Using the foreignId method:
```php
   Schema::create('orders', function (Blueprint $table) {
        $table->id();
        $table->foreignId('customer_id')->constrained();
    });
```
2. Using the references method:
```php
   Schema::table('orders', function (Blueprint $table) {
        $table->unsignedBigInteger('customer_id');
        $table->foreign('customer_id')->references('id')->on('customers');
    });
```
3. Using the constrained method:
```php
   Schema::create('orders', function (Blueprint $table) {
    $table->id();
    $table->unsignedBigInteger('customer_id');
    $table->date('order_date');
    $table->foreign('customer_id')
          ->references('id')
          ->on('customers')
          ->onUpdate('cascade')
          ->onDelete('restrict');
});
// LaravelTips.io
// IG: @Laravel.Tips
```