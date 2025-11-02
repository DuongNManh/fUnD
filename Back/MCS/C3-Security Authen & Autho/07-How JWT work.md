# 🔍 Understanding How JWT Actually Works (Visualized with JWT.io)

JWTs are one of the **gold standards** for sending stateless, tokenized information across the internet — especially for authentication and authorization.

Let’s take a step-by-step look at **what a JWT actually is**, **how it’s created**, and **why it’s secure** — using the online tool **[jwt.io](https://jwt.io)** for demonstration.

---

## 🧩 JWT Structure

A JWT always has **three parts**, separated by dots `.`:

```plaintext
<header>.<payload>.<signature>
```

Or visually:

| Section       | Description                                                 | Security Role                     |
| ------------- | ----------------------------------------------------------- | --------------------------------- |
| **Header**    | Contains metadata about the token (e.g., algorithm & type). | Defines how it’s signed/encrypted |
| **Payload**   | Contains the claims (data about the user or context).       | Not encrypted, just encoded       |
| **Signature** | Ensures data hasn’t been tampered with.                     | Verifies authenticity             |

---

## 🎨 Example

<img src="image-5.png" alt="JWT color-coded example" height="500" width="1000"/>

---

## 🧠 Decoding the First Two Parts

Many assume JWTs are encrypted — but actually, **the header and payload are just Base64URL-encoded**, *not encrypted*.

### 🔍 Why Base64URL?

Normal JSON can include characters that don’t travel safely across HTTP or URLs (e.g., `+`, `/`, `=`).
So JWT uses **Base64URL encoding** — a modified Base64 that replaces unsafe characters and removes padding.

👉 It’s purely for **transport safety**, not for **secrecy**.

Example:

```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

Becomes:

```plaintext
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9
```

If you paste that into jwt.io, you’ll see the exact header decoded again.

> 💡 You can freely decode any JWT header/payload without a key — but you **can’t forge** the token because of the **signature**.

---

## 🔏 The Signature — Where Security Happens

This is the **core** of JWT’s security.

The **signature** is created using:

```
HMACSHA256(
  base64urlEncode(header) + "." + base64urlEncode(payload),
  secret_key
)
```

So, the server signs the token using its **private secret key**, producing the third part — the **signature**.

### ✅ What it means:

* The **server** that issued the token is the only one that can generate a valid signature.
* When the token is received later, the server re-generates the same signature with the same secret.
* If the computed signature doesn’t match → token is **rejected**.

---

## 🔁 Example of Tampering

If you modify even a single character in the payload (like changing `"role": "user"` to `"role": "admin"`),
the signature no longer matches the new header/payload combination.

| Action                  | Result              |
| ----------------------- | ------------------- |
| Change payload manually | ❌ Signature invalid |
| Change secret key       | ❌ Signature invalid |
| Change header algorithm | ❌ Signature invalid |
| Keep all intact         | ✅ Signature valid   |

That’s why JWTs are **tamper-proof** without needing to store anything server-side — all validation comes from verifying the **signature**.

---

## ⚙️ Verification in ASP.NET Core

ASP.NET automatically performs this verification when you use `[Authorize]` with `AddJwtBearer`:

```csharp
builder.Services.AddAuthentication("Bearer")
    .AddJwtBearer(options =>
    {
        options.TokenValidationParameters = new TokenValidationParameters
        {
            ValidateIssuer = true,
            ValidateAudience = true,
            ValidateLifetime = true,
            ValidateIssuerSigningKey = true,
            IssuerSigningKey = new SymmetricSecurityKey(
                Encoding.UTF8.GetBytes("your_secret_key_here"))
        };
    });
```

When a request arrives with a JWT in the header:

```http
Authorization: Bearer eyJhbGciOi...
```

ASP.NET will:

1. Decode header & payload (Base64URL).
2. Recompute the signature using your secret.
3. Compare it with the token’s signature.
4. If all checks pass → `[Authorize]` grants access.

---

## 🧾 Summary Diagram

```plaintext
                    JWT CREATION & VALIDATION FLOW
+--------------------+      +-----------------------+
|  Auth Server       |      |  API Server / Client  |
+--------------------+      +-----------------------+
| 1. Create header   |      |                       |
| 2. Create payload  |      |                       |
| 3. Sign with key   |----->| 4. Verify signature   |
|                    |      | 5. Decode payload     |
|                    |      | 6. Authorize request  |
+--------------------+      +-----------------------+
```
