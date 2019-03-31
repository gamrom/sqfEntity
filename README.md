# sqfEntity
SqfEntity is based on SQFlite plugin and lets you build and execute SQL commands easily and quickly with the help of fluent methods similar to .Net Entity Framework

Leave the job to SqfEntitiy for CRUD operations. Do easily and faster adding tables, adding columns, defining multiple tables, etc. with the help of DbModel object

Open downloaded folder named sqfentity-master in VSCode and Click "Get Packages" button in the alert window that "Some packages are missing or out of date, would you like to get them now?"

## Getting Started

This project is a starting point for a Flutter application.
There are 5 files in the project
1. main.dart                  : Startup file contains sample methods for using sqfEntity
2. db/ SqfEntityBase.dart     : includes Database Provider, helper classes, enums.. etc 
3. db/ SqfEntityDbModel.dart  : to declare your database model and get created model class from clipboard in runtime
4. models/Product.dart        : Sample model for examples
5. app.dart                   : Sample App for display created model. (will be updated later.)
6. LICENSE.txt                : see this file for License Terms


### main.dart includes a lot of samples that you need

  // To get the your class or model from the clipboard, run it separately for each model
  // create Model String and set the Clipboard (After debugging, press Ctrl+V to paste the model from the Clipboard)
  String sqfEntityModelString = SqfEntityDbModel.createSqfEntityModel(SqfEntityDbModel.tableProduct);
  // just press Ctrl+V to paste your model in your .dart file and reference it where to use



## Running the main.dart should show the following result:
flutter: SQFENTITIY: Product Model was successfully created. Create Product.dart file in your project and press Ctrl+V to paste the model from the Clipboard
flutter: SQFENTITIY: Table named 'product' was initialized successfuly (created new table)
flutter: SQFENTITIY: The database is ready for use

flutter: EXAMPLE 1.1: SELECT ALL ROWS WITHOUT FILTER ex: SELECT * FROM PRODUCTS 
 -> Product().select().toList()
flutter: 15 matches found:
flutter: {id: 1, name: Notebook 12", description: 128 GB SSD i7, price: 6899.0, isActive: true, isDeleted: false}
flutter: {id: 2, name: Notebook 12", description: 256 GB SSD i7, price: 8244.0, isActive: true, isDeleted: false}
flutter: {id: 3, name: Notebook 12", description: 512 GB SSD i7, price: 9214.0, isActive: true, isDeleted: false}
flutter: {id: 4, name: Notebook 13", description: 128 GB SSD, price: 8500.0, isActive: true, isDeleted: false}
.........
flutter: ---------------------------------------------------------------

flutter: SAMPLE PAGING ex: PRODUCTS in 3. page (5 items per page) 
 -> Product().select().page(3,5).toList()
flutter: 5 matches found:
flutter: {id: 11, name: Ultrabook 13", description: 256 GB SSD i5, price: 11154.0, isActive: false, isDeleted: false}
flutter: {id: 12, name: Ultrabook 13", description: 512 GB SSD i5, price: 13000.0, isActive: false, isDeleted: false}
flutter: {id: 13, name: Ultrabook 15", description: 128 GB SSD i7, price: 11000.0, isActive: false, isDeleted: false}
flutter: {id: 14, name: Ultrabook 15", description: 256 GB SSD i7, price: 12000.0, isActive: false, isDeleted: false}
flutter: {id: 15, name: Ultrabook 15", description: 512 GB SSD i7 (updated) (updated) (updated) (updated) (updated), price: 14000.0, isActive: true, isDeleted: false}
flutter: ---------------------------------------------------------------
flutter:
flutter:
flutter: DISTINCT ex: SELECT DISTINCT name FROM PRODUCTS WHERE price > 3000 
 -> Product().distinct(columnsToSelect:["name").price.greaterThan(3000).toList();
flutter: 5 matches found:
flutter: {name: Notebook 12"}
flutter: {name: Notebook 13"}
flutter: {name: Notebook 15"}
flutter: {name: Ultrabook 13"}
flutter: {name: Ultrabook 15"}
flutter:
flutter:
flutter: GROUP BY WITH SCALAR OR AGGREGATE FUNCTIONS ex: SELECT name, (MIN(),MAX()).. FROM PRODUCTS GROUP BY name 
-> Product().select(....).groupBy(ProductFields.name.toString()).toListObject()
flutter: 5 matches found:
flutter: {name: Notebook 12", Count: 3, minPrice: 6899.0, maxPrice: 9214.0, avgPrice: 8119.0, sumPrice: 24357.0}
flutter: {name: Notebook 13", Count: 3, minPrice: 8500.0, maxPrice: 11000.0, avgPrice: 9800.0, sumPrice: 29400.0}
flutter: {name: Notebook 15", Count: 3, minPrice: 8999.0, maxPrice: 11999.0, avgPrice: 10499.0, sumPrice: 31497.0}
flutter: {name: Ultrabook 13", Count: 3, minPrice: 9954.0, maxPrice: 13000.0, avgPrice: 11369.333333333334, sumPrice: 34108.0}
flutter: {name: Ultrabook 15", Count: 3, minPrice: 11000.0, maxPrice: 14000.0, avgPrice: 12333.333333333334, sumPrice: 37000.0}
flutter: ---------------------------------------------------------------
flutter: 5 items updated
flutter: 10 items updated
flutter: id=15 Product item updated: {id: 15, name: Ultrabook 15", description: 512 GB SSD i7 (updated) (updated) (updated) (updated) (updated) (updated), price: 14000.0, isActive: true, isDeleted: false}
flutter: 0 items updated
flutter: SQFENTITIY: delete Product called (id=17)
flutter: 1 items updated















