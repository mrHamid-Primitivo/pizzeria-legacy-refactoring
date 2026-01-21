#  Pizza System: Legacy to Clean Architecture Refactoring

This project demonstrates the **modernization and refactoring** of a legacy monolithic application into a scalable, pattern-based architecture. 

It serves as a technical case study on **Software Architecture**, **Design Patterns**, and **Technical Debt reduction**.

## Project Structure

The repository is divided into two versions to showcase the evolution of the software:

### 1.  `v1-legacy-monolith` (Before)
* **State:** The original legacy system.
* **Characteristics:**
    * **Monolithic Class Design:** Logic, UI, and Data Access mixed in single classes.
    * **Tight Coupling:** UI components directly dependent on file system operations.
    * **No Separation of Concerns:** Hard to maintain and test.
    * **Tech Stack:** JavaFX (FXML) with direct `.txt` file manipulation.

### 2.  `v2-clean-architecture` (After - Current)
* **State:** Refactored version applying **SOLID principles**.
* **Architecture:** Layered Architecture (Presentation → Service Layer → Domain Model → Persistence).
* **Key Improvements:**
    * **Decoupling:** UI only interacts with Controllers; Controllers only interact with the Service Façade.
    * **Persistence Abstraction:** The system uses Repositories, making it easy to switch from `.txt` to Oracle DB/SQL without changing business logic.

## 🛠 Design Patterns Implemented (v2)

We transitioned from procedural code to Object-Oriented Design Patterns:

| Pattern | Usage in Project |
| :--- | :--- |
| ** Builder** | `PizzaPersonalizadaBuilder` creates complex Pizza objects step-by-step (dough, sauce, toppings). |
| ** Observer** | `PanelControlEmpleado` and `PantallaEstadoCliente` automatically update when the Order state changes. |
| ** State** | `EstadoPedido` interface manages the order lifecycle (Received → Prep → Baking → Delivered), eliminating complex `if/else` chains. |
| ** Strategy** | `EstrategiaPrecio` allows switching between `PrecioEstandar` and `PrecioPromocion` dynamically. |
| ** Facade** | `ServicioPedidos` provides a simple interface for the UI, hiding the complexity of the domain model. |
| ** Singleton** | `GestorPedidos` ensures a single global instance manages the in-memory order queue. |

##  How to Run

1.  Clone the repository.
2.  Open **v2-clean-architecture** in NetBeans or IntelliJ.
3.  Ensure Java/JavaFX SDK is configured.
4.  Run `Main.java` inside the `com.pizzasystem` package.

---
*> **Note on Persistence:** The persistence layer was intentionally kept file-based (`.txt` and `.ticket` files) to simulate the constraints of the original legacy environment while proving that architecture can be improved independently of the storage mechanism.*
