# Cinema Booking System

A cinema seat-reservation system. Pick a film and showtime, choose seats from a live auditorium map, add snacks, and check out.

---

## About this project

A team project for the Object-Oriented Programming course at the College of Computer Science and Information Technology, Imam Abdulrahman Bin Faisal University.

The brief was a desktop application demonstrating the four pillars of OOP, with a real database behind it. The Java build in [`/desktop`](desktop/) — 30 classes, NetBeans Swing interfaces, MySQL — is what was submitted.


---

## The OOP design

The type hierarchy is the point of the project, and the web version keeps it intact:

| Base | Subclasses | What changes |
|---|---|---|
| `Seat` | `NormalSeat`, `VIPSeat` | `getPrice()` is overridden — 55 vs 65 SAR |
| `MovieBase` | `Movie` | The base holds title, genre, duration and rating; the subclass adds the interface |
| `UserBase` | `EmployeeUser` | Shared identity, different permissions |
| `Cart` | `CartItem` | Composition — a cart holds items, it doesn't extend one |

| Principle | Where it shows |
|---|---|
| **Encapsulation** | Seat state is private; a seat can't be marked booked without going through the booking logic |
| **Inheritance** | `VIPSeat` and `NormalSeat` share everything except price |
| **Polymorphism** | The cart totals a list of `Seat` without knowing which kind each one is |
| **Abstraction** | The interface layer works against base types, never concrete ones |

That last row is why VIP pricing needed no change to the checkout code: the cart calls `getPrice()` and each seat answers for itself.

---

## Running the Java version

**Requirements:** JDK 8 or newer, MySQL, and the MySQL Connector/J driver.

1. Open `/desktop` in NetBeans (`File → Open Project`)
2. Create a MySQL database named `cschema` and import your schema
3. Copy `src/CinamaBooking/DatabaseConnection.java` to `DatabaseConnection.java` and fill in your credentials
4. Run the project — `Main.java` is the entry point

`DatabaseConnection.java` is git-ignored, so database credentials never reach the repository.

---

## Tech

**Web** — HTML5, CSS3, vanilla JavaScript. No frameworks, no build step.

**Desktop** — Java, Swing, NetBeans, MySQL via JDBC.

---

Team course project · CCSIT, Imam Abdulrahman Bin Faisal University
