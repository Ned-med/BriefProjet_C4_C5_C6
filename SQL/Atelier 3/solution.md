# SOLUTION DE L'ATELIER 3

##  vous devez créer une base données, et imiter les requêtes dans le fichier sql shema.

### Warehouses Table
| Code  | Location      | Capacity |
| :---: | :------------ | :------: |
|   1   | Chicago       |    3     |
|   2   | Chicago       |    4     |
|   3   | New York      |    7     |
|   4   | Los Angeles   |    2     |
|   5   | San Francisco |    8     |

### Boxes Table

| Code  | Contents | Value | Warehouse |
| :---: | :------- | :---: | :-------: |
| 0MN7  | Rocks    |  180  |     3     |
| 4H8P  | Rocks    |  250  |     1     |
| 4RT3  | Scissors |  190  |     4     |
| 7G3H  | Rocks    |  200  |     1     |
| 8JN6  | Papers   |  75   |     1     |
| 8Y6U  | Papers   |  50   |     3     |
| 9J6F  | Papers   |  175  |     2     |
| LL08  | Rocks    |  140  |     4     |
| P0H6  | Scissors |  125  |     1     |
| P2T6  | Scissors |  150  |     2     |
| TU55  | Papers   |  90   |     5     |

> Exprimer les requêtes suivantes en SQL : 

## 3.1 Sélectionner tous les entrepôts.
```sql
 SELECT * FROM warehouses;
```
## 3.2 Sélectionnez toutes les cases dont la valeur est supérieure à 150 $.
```sql
 SELECT * FROM boxes WHERE value > 150;
```
## 3.3 Sélectionner tous les contenus distincts dans toutes les cases.
```sql
SELECT DISTINCT contents FROM boxes;
```
## 3.4 Sélectionner la valeur moyenne de toutes les boîtes.
```sql
 SELECT avg(value) FROM boxes;
```
## 3.5 Sélectionner le code de l'entrepôt et la valeur moyenne des boîtes dans chaque entrepôt.
```sql
 SELECT Warehouse , avg(value) FROM boxes group by Warehouse;
```
## 3.6 Identique à l'exercice précédent, mais ne sélectionnez que les entrepôts où la valeur moyenne des boîtes est supérieure à 150.
```sql
 SELECT Warehouse , avg(value) FROM boxes group by Warehouse having avg(value) > 150;
```
## 3.7 Sélectionnez le code de chaque boîte, ainsi que le nom de la ville dans laquelle la boîte est située.
```sql
 SELECT b.Code , w.Location FROM boxes b join warehouses w on b.Warehouse = w.Code;
```
## 3.8 Sélectionnez les codes des entrepôts, ainsi que le nombre de boîtes dans chaque entrepôt. 
```sql
 SELECT Warehouse, count(Warehouse) FROM boxes group by Warehouse;
```
    >  Facultativement, tenez compte du fait que certains entrepôts sont vides (c'est-à-dire que le nombre de boîtes devrait apparaître comme zéro, au lieu d'omettre l'entrepôt du résultat).
## 3.9 Sélectionnez les codes de tous les entrepôts qui sont saturés (un entrepôt est saturé si le nombre de boîtes qu'il contient est supérieur à la capacité de l'entrepôt).
```sql
 SELECT code FROM warehouses WHERE Capacity < (SELECT count(*) FROM boxes WHERE Warehouse = warehouses.code);
```
## 3.10 Sélectionnez les codes de toutes les boîtes situées à Chicago.
```sql
```
## 3.11 Créer un nouvel entrepôt à New York avec une capacité de 3 boîtes.
```sql
```
## 3.12 Créer une nouvelle boîte, avec le code "H5RT", contenant des "Papers" d'une valeur de 200 $, et située dans l'entrepôt 2.
```sql
```
## 3.13 Réduire la valeur de toutes les boîtes de 15 %.
```sql
```
## 3.14 Retirer toutes les boîtes d'une valeur inférieure à 100 $.
```sql
```
##  3.15 Retirer toutes les boîtes des entrepôts saturés.
```sql
```
##  3.16 Ajouter un indice pour la colonne "Entrepôt" dans le tableau "boîtes".
```sql
```
    > !!!NOTE!! : l'index ne doit PAS être utilisé sur des petites tables dans la pratique
##  3.17 Imprimer tous les index existants
```sql
```
    > !!!NOTE!! : l'index ne doit PAS être utilisé sur des petites tables dans la pratique