# Consultas de SQL para Azure SQL Database

Recursos que vas a necesitar:
- Azure SQL Database
- Repositorio DP-900 -> https://github.com/MicrosoftLearning/DP-900T00A-Azure-Data-Fundamentals
- Azure Cloud Shell activado

1. Ejecuta los siguientes comandos en el **Azure Cloud Shell"" en el orden en el que se encuentran:


```Bash
git clone https://github.com/MicrosoftLearning/DP-900T00A-Azure-Data-Fundamentals dp-900
```

```Bash
cd dp-900/sql
```

```Bash
bash setup.sh
```

**NOTA:** Debes esperar a que se termine de ejecutar el comando anterior para correr el siguiente.

2. Ve al recurso **SQL Database** y agrega tu IP en la sección "Set Server Firewall. Si no lo haces, no podrás seguir

3. Busca en las opciones del lado izquierdo "Editor de consultas SQL" o "Query Editor"

4. Los accesos para el Servidor de bases de datos son los siguientes:

```Bash
login="sampleLogin"
password="samplePassword123!
```

5. Si no tiene datos la Base de datos ejecuta el siguiente Query:

```sql
USE DATABASE Inventory;

CREATE TABLE Inventory (
	Id int PRIMARY KEY, 
	Name VARCHAR(50), 
	Stock INTEGER
);

CREATE TABLE CustomerOrder (
	Id int PRIMARY KEY, 
	CustomerName VARCHAR(50),
    Quantity int,
    Created DATETIME,
    InventoryId int FOREIGN KEY REFERENCES Inventory(Id)
);

INSERT INTO Inventory (Id, Name, Stock) VALUES (1, 'banana', 150); 
INSERT INTO Inventory (Id, Name, Stock) VALUES (2, 'orange', 154);
INSERT INTO Inventory (Id, Name, Stock) VALUES (3, 'apple', 23); 
INSERT INTO Inventory (Id, Name, Stock) VALUES (4, 'lemon', 254);


INSERT INTO CustomerOrder(Id, CustomerName, InventoryId, Quantity, Created) VALUES (1, 'John Smith', 2, 5, getdate());
INSERT INTO CustomerOrder(Id, CustomerName, InventoryId, Quantity, Created) VALUES (2, 'Jane Brown', 2, 8, getdate());
INSERT INTO CustomerOrder(Id, CustomerName, InventoryId, Quantity, Created) VALUES (3, 'Stephen Stone', 3, 3, getdate());
INSERT INTO CustomerOrder(Id, CustomerName, InventoryId, Quantity, Created) VALUES (4, 'Claire Smith', 1, 1, getdate());
INSERT INTO CustomerOrder(Id, CustomerName, InventoryId, Quantity, Created) VALUES (5, 'Sarah Fedun', 4, 3, getdate());
INSERT INTO CustomerOrder(Id, CustomerName, InventoryId, Quantity, Created) VALUES (6, 'Graham Hinson', 3, 9, getdate());
```

6. El siguiente comando devuelve todos los valores de la tabla *Inventory*

```sql
SELECT * 
FROM Inventory
```

7. Para mostrar solo el número de plátanos que hay en las existencias:

```sql
SELECT * 
FROM Inventory 
WHERE Name = 'banana'
```

8. Para recuperar los artículos de inventario ordenados por la cantidad en las existencias:

```sql
SELECT * 
FROM Inventory 
ORDER BY Stock
```

9. Muestra los detalles de los pedidos realizados por los clientes junto con la información de inventario relativa a cada artículo solicitado:

```sql
SELECT * 
FROM Inventory 
JOIN CustomerOrder ON Inventory.Id = CustomerOrder.InventoryId
```

10. En la siguiente consulta se suman las cantidades para generar un total

```sql
SELECT SUM(CustomerOrder.Quantity) 
FROM CustomerOrder
```

