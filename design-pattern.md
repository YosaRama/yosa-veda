# Design Pattern

Design pattern will be separated into 3 main category:

1. Object Creational Patterns
2. Object Compositions / Structural Patterns
3. Behavior Patterns

## Creational Patterns

Definitions:

This pattern will be help us to indicate "self lock" for creation the object. This pattern will help us to answer&#x20;

> “How do I create objects **without locking myself into concrete implementations**?”

Why this needed to know? because we need to setup at the first time to make all the object "Rigid"&#x20;

When we need this?&#x20;

* When we got this question "we might change this later"
* When "we have conditional on creations"
* When "we got struggle doing testing"
* When "same object was created on many places"
* When "one object create many related objects"

> Pattern is Medicines NOT a Vitamins.

by that we need to think, don't focus on Patterns first, when you get a problem with the object then ask your self "What Pattern will suitable for this case?"

### 1️⃣ Singleton Pattern

Problem to solved:

I want **exactly one instance** of this object for the entire application.

Example:

without Singleton

```typescript
function handleRequest() {
  const db = new DatabaseConnection()
  db.query(...)
}
```

if we looking for this, every `handleRequest` will create new object called `DatabaseConnection` this very bad, because every time it will be create:

* new memory
* new connection
* new overhead

Singleton concept should be like:

> “Create it once, reuse everywhere.”

How it works:

* **Private creation**
  * You cannot freely `new` it
* **Single stored instance**
  * Created once, reused
* **Global access point**
  * Everyone gets the same instance

but there are some PROBLEM will happens when implement this patterns:

#### 🚨 Problem 1: Hidden global state

```typescript
Logger.log("something")
```

Where did `Logger` come from?

* Who owns it?
* Who initializes it?
* What config does it use?

Singletons act like **globals in disguise**.

#### 🚨 Problem 2: Hard to test

Imagine:

```ts
const db = Database.getInstance()
```

In tests:

* You can’t replace it easily
* State leaks between tests
* Tests depend on execution order

This breaks **test isolation**.

#### 🚨 Problem 3: Tight coupling

Even though you didn’t write `new`,\
you still depend on **a concrete class**.

```ts
Database.getInstance()
```

This violates **Dependency Inversion**.

#### 🚨 Problem 4: Lifecycle control is unclear

* When is it created?
* When is it destroyed?
* What happens on hot reload?

In large systems, this matters.

#### ✅ When we should use Singleton

Singleton is **acceptable** when ALL of these are true:

✅ The object:

* Is **stateless** or safely shared
* Represents a **system-level resource**
* Is expensive to create
* Truly must be unique

#### Good examples

* Logger
* Metrics registry
* Process-wide config (read-only)
* Connection pool (with care)

Even here, many teams still wrap them behind abstractions.

#### ❌ When you should NOT use Singleton&#x20;

❌ Business logic\
❌ Domain entities\
❌ Use cases\
❌ Anything with user-specific state\
❌ Anything you want to mock easily

### 2️⃣ Factory Patterns

Problem to solved:

> Class should be not decide what concrete object to create

it's make a problem because "Business Logic" will contain "concrete implementations". and it will be affect changing "Adapters" also change "Business Logic" it should NOT. we should separated the Infra and also Business Logic. like what we learn on SOLID Principels.&#x20;

> Business Logic should agnostic with Infra. Business Logic will not change if Infra change

Example

#### ❌ BAD VERSION

```typescript
class OrderService {
  pay(order) {
    if (order.paymentMethod === 'stripe') {
      const stripe = new StripePayment()
      stripe.charge(order.total)
    }

    if (order.paymentMethod === 'paypal') {
      const paypal = new PaypalPayment()
      paypal.charge(order.total)
    }
  }
}

```

what is the problem from the top "Business Logic" ?

1. Explosion of `if`
2. Business logic knows too much
3. Testing nightmare

#### ✅ GOOD VERSION

**Step 1: Extract common behavior (interface)**

```ts
interface Payment {
  charge(amount: number): void
}
```

**Step 2: Concrete implementations (unchanged)**

```ts
class StripePayment implements Payment {
  charge(amount) {
    console.log("Stripe charge", amount)
  }
}

class PaypalPayment implements Payment {
  charge(amount) {
    console.log("Paypal charge", amount)
  }
}
```

So far: **no factory yet**.

**Step 3: Create the Factory (THIS is the key)**

```ts
class PaymentFactory {
  create(method: string): Payment {
    switch (method) {
      case 'stripe':
        return new StripePayment()
      case 'paypal':
        return new PaypalPayment()
      default:
        throw new Error("Unsupported payment method")
    }
  }
}
```

Notice:

* `if/switch` still exists
* But **moved out** of business logic

**Step 4: Use factory in business logic**

```ts
class OrderService {
  constructor(private paymentFactory: PaymentFactory) {}

  pay(order) {
    const payment = this.paymentFactory.create(order.paymentMethod)
    payment.charge(order.total)
  }
}
```
