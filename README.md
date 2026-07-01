# ShopSphere - E-Commerce System (C++ OOP Mini Project)

This is a console-based online shopping platform I built in C++ to practice Object Oriented Programming concepts like inheritance, polymorphism, abstraction and encapsulation. It's basically a simplified version of a site like Amazon/Flipkart, with three types of users - Customer, Seller and Admin, each having their own panel and permissions.

## What it does

ShopSphere lets customers browse products, add them to a cart or wishlist, place orders and pay using different payment methods, track their orders, and leave reviews. Sellers can register, list their own products (which need admin approval before going live), and check their sales report. The Super Admin manages the whole platform - approving/rejecting products, blocking customers or sellers, and updating order tracking status.

## Features

**Customer**
- Register / Login
- Browse products by category or search by name
- Add to cart / remove from cart
- Add to wishlist / remove from wishlist
- Place order with COD, Card or UPI payment
- View order history, track order status, cancel order
- Write product reviews (rating auto-updates based on reviews)

**Seller**
- Register (needs admin approval before login works)
- Add new product (goes into "pending" status until admin approves)
- Edit / delete own products
- View sales report (total, approved, pending products)

**Super Admin**
- View platform statistics (total customers, sellers, products, orders, revenue)
- Approve / reject pending seller products
- Block / unblock customers and sellers
- Approve seller accounts
- View all orders and update tracking status (Placed -> Shipped -> Out for Delivery -> Delivered)

## Files

| File | What's in it |
|---|---|
| `main.cpp` | Entry point, main menu, customer menu, browse function |
| `User.h` | User base class + Customer, Seller, SuperAdmin (inheritance) + AuthManager for login/register |
| `Product.h` | Product class with reviews |
| `Cart.h` | Cart class |
| `Wishlist.h` | Wishlist class |
| `Order.h` | Order class + OrderManager |
| `Payment.h` | Abstract Payment class + CashPayment, CardPayment, UPIPayment (polymorphism) |
| `AdminPanel.h` | Older/basic admin panel (not currently used in main.cpp) |
| `SellerPanel.h` | Seller dashboard menu |
| `SuperAdminPanel.h` | Super admin dashboard menu |
| `InputUtils.h` | Helper functions for safe input (readInt, readDouble, readPhone) |

Note: `Product.cpp` and `Cart.cpp` are earlier/simpler versions of those classes I wrote before adding features like reviews, seller info and stock availability check. The project actually runs using `Product.h` and `Cart.h`, not the `.cpp` ones.

## OOP Concepts Used

- **Inheritance** - `Customer`, `Seller`, `SuperAdmin` all inherit from `User`. `CashPayment`, `CardPayment`, `UPIPayment` inherit from `Payment`.
- **Polymorphism** - `showRole()` and `getRole()` behave differently for each user type. `pay()` behaves differently for each payment type, called through a `Payment*` pointer.
- **Abstraction** - `User` and `Payment` are abstract classes (pure virtual functions), can't create objects of them directly.
- **Encapsulation** - All class data members are private, accessed only through getters/setters.

## How to compile and run

```
g++ main.cpp -o shopsphere
./shopsphere
```

(Windows: `g++ main.cpp -o shopsphere.exe` then `shopsphere.exe`)

## Sample login

Super Admin login is hardcoded:
- Email: `superadmin@shopsphere.com`
- Password: `super@123`

Customers and sellers need to register first before they can log in.

## Known limitations / things I'd improve later

- Data is not saved to a file, so everything resets when the program closes (no file handling/database yet)
- No real payment gateway, it's just simulated on console
- Product search is a simple substring match, not case-insensitive
- `AdminPanel.h` is leftover from an earlier version and isn't linked into `main.cpp` anymore (SuperAdminPanel replaced it)
