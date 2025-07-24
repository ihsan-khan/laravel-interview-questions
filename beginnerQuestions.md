# 100-laravel-interview-questions

# Lavavel-100-objective-based-questions

**1. Which method is used to redirect users in Laravel?**
<details>
	<summary><b>View Answer</b></summary>
<ul>
In Laravel, you can redirect users using the `redirect()` helper function or the `Redirect` facade. Here are the common methods:

### 1. **Basic Redirect**
```php
return redirect('/home');
```

### 2. **Redirect to a Named Route**
```php
return redirect()->route('route.name');
```

### 3. **Redirect with Parameters (for Named Routes)**
```php
return redirect()->route('profile', ['id' => 1]);
```

### 4. **Redirect Back to Previous Page**
```php
return back();
// or
return redirect()->back();
```

### 5. **Redirect with Flash Data (Session Data)**
```php
return redirect('/dashboard')->with('status', 'Profile updated!');
```

### 6. **Redirect to a Controller Action**
```php
return redirect()->action([UserController::class, 'index']);
```

### 7. **Redirect with Input (Old Form Data)**
```php
return back()->withInput();
```

### 8. **Redirect to External URL**
```php
return redirect()->away('https://google.com');
```

### 9. **Conditional Redirects**
You can also chain conditions:
```php
return redirect()->to('/home')->with('error', 'Invalid access');
```

### Example in a Controller:
```php
public function store(Request $request)
{
    // Validate and store data...

    return redirect('/dashboard')->with('success', 'User created successfully!');
}
```

</ul>
</details>

**2. what is the difference between  migrate:fresh and migarte:refresh?**


<details>
	<summary><b>View Answer</b></summary>
<ul>
In Laravel, both `migrate:fresh` and `migrate:refresh` are Artisan commands used to reset and rebuild your database, but they work differently:

### **1. `migrate:fresh`**  
- **Drops all tables** from the database and then runs all migrations again.  
- **Does not run the `down()` methods** of existing migrations.  
- **Faster** because it bypasses rolling back migrations step-by-step.  
- **Use case:** When you want a completely clean database (e.g., during development or testing).  

#### **Command:**  
```bash
php artisan migrate:fresh
```

### **2. `migrate:refresh`**  
- **Rolls back all migrations** (executes `down()` methods) **one by one** and then re-runs them (`up()`).  
- **Preserves migration order** and executes each migration's `down()` logic.  
- **Slower** because it processes each migration step-by-step.  
- **Use case:** When you need to test if your `down()` methods work correctly.  

#### **Command:**  
```bash
php artisan migrate:refresh
```

### **Key Differences Summary**  
| Feature               | `migrate:fresh` | `migrate:refresh` |
|-----------------------|----------------|------------------|
| Drops all tables directly | ✅ Yes | ❌ No |
| Runs `down()` methods | ❌ No | ✅ Yes |
| Speed | ⚡ Faster | 🐢 Slower (due to rollback) |
| Use Case | Quick DB reset | Testing rollback logic |

### **When to Use Which?**  
- Use `fresh` when you want a **quick reset** (e.g., during development).  
- Use `refresh` when you need to **test migration rollbacks** (e.g., checking if `down()` works).  


</ul>
</details>

**100. What is the default database system used in Laravel?**
```php
A) PostgreSQL
B) MySQL
C) SQLite
D) MongoDB
```

<details>
	<summary><b>View Answer</b></summary>
<ul>
Answer: C
</ul>
</details>