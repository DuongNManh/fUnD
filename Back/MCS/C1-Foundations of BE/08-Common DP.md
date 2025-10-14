# 🎨 Common Design Patterns in OOP

## 💡 What Are Design Patterns?

Imagine working on a complex project where you constantly face the same challenges.
Over time, you develop **smart, repeatable solutions** that make your work easier and more efficient.

In software development, these solutions are called **design patterns**:

* ✅ **Reusable templates** for solving common problems
* ✅ **Proven best practices** for code structure
* ✅ Make applications **efficient, maintainable, and scalable**

---

## 🧭 Patterns in Action

We’ll explore four widely used patterns:

1. **Singleton Pattern** → only one instance
2. **Factory Pattern** → centralizes object creation
3. **Observer Pattern** → manages communication between objects
4. **Adapter Pattern** → bridge between incompatible interfaces

---

## 🟦 1. Singleton Pattern

### 📖 Definition

Ensures a class has **only one instance** throughout an application and provides a **single point of access** to it.
Often used for managing **shared resources** like database connections or configuration managers.

---

### ⚙️ Structure (UML)

```plaintext
   ┌────────────────┐
   │   Database     │
   │────────────────│
   │ - instance     │  (static)
   │ - Database()   │  (private)
   │ + GetInstance()│
   └───────┬────────┘
           │
           ▼
    Global shared object
```

---

### 💻 Code Example (C#)

```csharp
public class Database
{
    private static Database instance;
    private Database()
    {
        Console.WriteLine("Database connection established");
    }

    public static Database GetInstance()
    {
        if (instance == null)
            instance = new Database();
        return instance;
    }
}
```

* ✅ `Database` constructor is **private** → prevents direct instantiation
* ✅ `GetInstance()` → ensures **only one instance exists**
* ✅ Access to `Database` is **centralized** through `GetInstance()`

---

## 🏭 2. Factory Pattern

### 📖 Definition

Provides a way to **create objects without exposing creation logic**.
The factory decides which object type to create based on input, making the system more **flexible and extensible**.

---

### ⚙️ Structure (UML)

```plaintext
          ┌───────────────┐
          │   Client      │
          └──────┬────────┘
                 │ uses
                 ▼
       ┌────────────────────────┐
       │ NotificationFactory    │
       │------------------------│
       │ + CreateNotification() │
       └──────────┬─────────────┘
                  │
     ┌────────────┼───────────────┐
     ▼                            ▼
┌───────────────────┐     ┌─────────────────┐
│ EmailNotification │     │ SmsNotification │
└───────────────────┘     └─────────────────┘
```

---

### 💻 Code Example (C#)

```csharp
public interface INotification
{
    void Send(string message);
}

public class EmailNotification : INotification
{
    public void Send(string message) => Console.WriteLine($"Email: {message}");
}

public class SmsNotification : INotification
{
    public void Send(string message) => Console.WriteLine($"SMS: {message}");
}

public class NotificationFactory
{
    public INotification CreateNotification(string channel)
    {
        if (channel == "EMAIL") return new EmailNotification();
        if (channel == "SMS") return new SmsNotification();
        throw new ArgumentException("Invalid channel");
    }
}
```

* ✅ `INotification` = common interface
* ✅ `EmailNotification` & `SmsNotification` = concrete products
* ✅ `NotificationFactory` = decides which product to instantiate
* ✅ Client = uses factory, doesn’t worry about **creation details**

---

## 🟩 3. Observer Pattern

### 📖 Definition

Defines a **one-to-many dependency**: when one object changes state, all its dependents are **automatically notified**.
Useful for **real-time updates** (e.g., UI refreshing when data changes).

---

### ⚙️ Structure (UML)

```plaintext
   ┌───────────────┐      registers/updates    ┌────────────────┐
   │ WeatherStation│-------------------------->│   IObserver    │
   │ (Subject)     │                           │ (Interface)    │
   └───────────────┘                           └───────┬────────┘       
                                            ┬─────────────────────────┬
                                            │                         │
                                            ▼                         ▼
                                    ┌───────────────┐       ┌───────────────────┐
                                    │ PhoneDisplay  │       │ DesktopDisplay    │
                                    │ (ConcreteObs) │       │ (ConcreteObs)     │
                                    └───────────────┘       └───────────────────┘
```

---

### 💻 Code Example (C#)

```csharp
public interface IObserver
{
    void Update(int temperature);
}

public class WeatherStation
{
    private List<IObserver> observers = new();
    private int temperature;

    public void RegisterObserver(IObserver observer) => observers.Add(observer);
    public void RemoveObserver(IObserver observer) => observers.Remove(observer);

    private void NotifyObservers()
    {
        foreach (var observer in observers)
            observer.Update(temperature);
    }

    public void SetTemperature(int newTemperature)
    {
        temperature = newTemperature;
        NotifyObservers();
    }
}

public class PhoneDisplay : IObserver
{
    public void Update(int temperature) =>
        Console.WriteLine($"Phone display: {temperature}°C");
}

public class DesktopDisplay : IObserver
{
    public void Update(int temperature) =>
        Console.WriteLine($"Desktop display: {temperature}°C");
}
```

* ✅ `WeatherStation` = **Subject** (manages observers)
* ✅ `PhoneDisplay` & `DesktopDisplay` = **Observers**
* ✅ `SetTemperature()` → notifies all registered observers automatically

---

## 🔌 4. Adapter Pattern

### 📖 Definition

The **Adapter Pattern** allows incompatible interfaces to work together.
It acts like a **translator**, converting one interface into another that clients expect.

---

### ⚙️ Structure (UML)

```plaintext
   ┌──────────┐       ┌──────────────────┐
   │  Client  │       │   Adaptee        │
   │----------│       │------------------│
   │ Request()│ ----> │ SpecificRequest()│
   └──────────┘       └──────────────────┘
         │
         ▼
   ┌──────────┐
   │ Adapter  │
   │----------│
   │ Request()│ → Calls Adaptee.SpecificRequest()
   └──────────┘
```

---

### 💻 Code Example (C#)

```csharp
public interface ITarget
{
    void Request();
}

public class Adaptee
{
    public void SpecificRequest()
    {
        Console.WriteLine("Called SpecificRequest() in Adaptee");
    }
}

public class Adapter : ITarget
{
    private readonly Adaptee _adaptee;
    public Adapter(Adaptee adaptee) => _adaptee = adaptee;

    public void Request() => _adaptee.SpecificRequest();
}

public class Program
{
    public static void Main()
    {
        Adaptee adaptee = new Adaptee();
        ITarget target = new Adapter(adaptee);
        target.Request();
    }
}
```

* ✅ `ITarget` = expected interface (used by client)
* ✅ `Adaptee` = existing class with incompatible method
* ✅ `Adapter` = wraps `Adaptee`, translates `Request()` → `SpecificRequest()`
* ✅ `Client` = works with adapter as if it were the target interface

---

## 🎯 Key Takeaways

* **Singleton** → one instance, shared globally
* **Factory** → decouples creation logic from usage
* **Observer** → automatic updates across multiple objects
* **Adapter** → makes incompatible interfaces work together

📌 Together, these patterns improve:

* **Code organization**
* **Maintainability**
* **Scalability**

---
