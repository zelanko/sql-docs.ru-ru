---
title: "Создание таблицы, столбцы и секции в табличной модели | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cf0e4791-ad3b-41a8-81ce-509d4cf223f8
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2017fa20a68222bf577cc68284882ac15a22f95f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="create-tables-partitions-and-columns-in-a-tabular-model"></a>Создание таблицы, столбцы и секции в табличной модели
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]В табличной модели таблицы состоит из строк и столбцов. Строки сортируются в секции для поддержки обновления добавочных данных. Табличное решение может поддерживать несколько типов таблиц, в зависимости от того, где данные поступают из:  

* Обычных таблиц источника данных из источника реляционных данных через поставщик данных. 

* Таблицы занесенный в стек, где «передаче данных» в таблицу программными средствами. 

* Вычисляемые таблицы, где данные поступают из выражения DAX, которое ссылается на другой объект в модели данных.  

В следующем примере кода мы определим обычной таблицы. 

## <a name="required-elements"></a>Обязательные элементы 

Таблица должна иметь хотя бы одну секцию. Обычной таблице должен быть определен хотя бы один столбец. 

Каждый раздел должно содержать источник Указание источника данных, но источник можно задать значение null. Как правило источник — выражения запроса, которое определяет срез данных на языке запросов соответствующей базы данных. 

## <a name="code-example-create-a-table-column-parition"></a>Пример кода: создавать таблицы, столбца, секции

Таблицы представлены классом таблицы (в пространстве имен Microsoft.AnalysisServices.Tabular). 

В приведенном ниже примере мы определим обычной таблице с одной секции, связаны с реляционного источника данных, а также несколько обычных столбцов. Мы также отправить изменения на сервер и триггера обновления данных, который возвращает данные в модель. Это значение представляет наиболее типичный сценарий для загрузки данных из реляционной базы данных SQL Server в табличного решения. 


```
using System; 
using Microsoft.AnalysisServices; 
using Microsoft.AnalysisServices.Tabular; 
 
namespace TOMSamples 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            // 
            // Connect to the local default instance of Analysis Services 
            // 
            string ConnectionString = "DataSource=localhost"; 
 
            // 
            // The using syntax ensures the correct use of the 
            // Microsoft.AnalysisServices.Tabular.Server object. 
            // 
            using (Server server = new Server()) 
            { 
                server.Connect(ConnectionString); 
 
                // 
                // Generate a new database name and use GetNewName 
                // to ensure the database name is unique. 
                // 
                string newDatabaseName = 
                    server.Databases.GetNewName("Database with a Table Definition"); 
 
                // 
                // Instantiate a new  
                // Microsoft.AnalysisServices.Tabular.Database object. 
                // 
                var dbWithTable = new Database() 
                { 
                    Name = newDatabaseName, 
                    ID = newDatabaseName, 
                    CompatibilityLevel = 1200, 
                    StorageEngineUsed = StorageEngineUsed.TabularMetadata, 
                }; 
 
                // 
                // Add a Microsoft.AnalysisServices.Tabular.Model object to the 
                // database, which acts as a root for all other Tabular metadata objects. 
                // 
                dbWithTable.Model = new Model() 
                { 
                    Name = "Tabular Data Model", 
                    Description = "A Tabular data model at the 1200 compatibility level." 
                }; 
 
                // 
                // Add a Microsoft.AnalysisServices.Tabular.ProviderDataSource object 
                // to the data Model object created in the previous step. The connection 
                // string of the data source object in this example  
                // points to an instance of the AdventureWorks2014 SQL Server database. 
                // 
                string dataSourceName = "SQL Server Data Source Example"; 
                dbWithTable.Model.DataSources.Add(new ProviderDataSource() 
                { 
                    Name = dataSourceName, 
                    Description = "A data source definition that uses explicit Windows credentials for authentication against SQL Server.", 
                    ConnectionString = "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureWorks2014;Integrated Security=SSPI;Persist Security Info=false", 
                    ImpersonationMode = Microsoft.AnalysisServices.Tabular.ImpersonationMode.ImpersonateAccount, 
                    Account = @".\Administrator", 
                    Password = "P@ssw0rd", 
                }); 
 
                //  
                // Add a table called Individual Customers to the data model 
                // with a partition that points to a [Sales].[vIndividualCustomer] view 
                // in the underlying data source. 
                // 
                dbWithTable.Model.Tables.Add(new Table() 
                { 
                    Name = dbWithTable.Model.Tables.GetNewName("Individual Customers"), 
                    Description = "Individual customers (names and email addresses) that purchase Adventure Works Cycles products online.", 
                    Partitions = { 
                        // 
                        // Create a single partition with a QueryPartitionSource for a query 
                        // that imports all customer rows from the underlying data source. 
                        // 
                        new Partition() { 
                            Name = "All Customers", 
                            Source = new QueryPartitionSource() { 
                                DataSource = dbWithTable.Model.DataSources[dataSourceName], 
                                Query = @"SELECT   [FirstName] 
                                                    ,[MiddleName] 
                                                    ,[LastName] 
                                                    ,[PhoneNumber]  
                                                    ,[EmailAddress] 
                                                    ,[City] 
                                        FROM [Sales].[vIndividualCustomer]", 
                            } 
                        } 
                    }, 
                    Columns = 
                    { 
                        // 
                       // DataColumn objects refer to regular table columns.  
                        // Each DataColumn object corresponds to a column in the underlying data source query. 
                        // 
                        new DataColumn() { 
                            Name = "FirstName", 
                            DataType = DataType.String, 
                            SourceColumn = "FirstName", 
                        }, 
                        new DataColumn() { 
                            Name = "MiddleName", 
                            DataType = DataType.String, 
                            SourceColumn = "MiddleName", 
                        }, 
                        new DataColumn() { 
                            Name = "LastName", 
                            DataType = DataType.String, 
                            SourceColumn = "LastName", 
                        }, 
                        new DataColumn() { 
                            Name = "PhoneNumber", 
                            DataType = DataType.String, 
                            SourceColumn = "PhoneNumber", 
                        }, 
                        new DataColumn() { 
                            Name = "EmailAddress", 
                            DataType = DataType.String, 
                            SourceColumn = "EmailAddress", 
                        }, 
                        new DataColumn() { 
                            Name = "City", 
                            DataType = DataType.String, 
                            SourceColumn = "City", 
                        }, 
                    } 
                }); 
 
                // 
                // Add the new database object to the server's  
                // Databases connection and submit the changes 
                // with full expansion to the server. 
                // 
                server.Databases.Add(dbWithTable); 
 
                //  
                // Request a full refresh to import the data from the data source and 
                // and perform any necessary recalculations. 
                // The refresh operation will be performed with the next 
                // invocation of Model.SaveChanges() or Database.Update(UpdateOptions.ExpandFull). 
                dbWithTable.Model.RequestRefresh(Microsoft.AnalysisServices.Tabular.RefreshType.Full); 
                dbWithTable.Update(UpdateOptions.ExpandFull); 
 
 
                Console.Write("Database "); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                Console.Write(dbWithTable.Name); 
                Console.ResetColor(); 
                Console.WriteLine(" created successfully."); 
 
                Console.WriteLine("The data model includes the following table definitions:"); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                foreach (Table tbl in dbWithTable.Model.Tables) 
                { 
                    Console.WriteLine("\tTable name:\t\t{0}", tbl.Name); 
                    Console.WriteLine("\ttbl description:\t{0}", tbl.Description); 
                } 
                Console.ResetColor(); 
                Console.WriteLine(); 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```

## <a name="partitions-in-a-table"></a>Секций в таблице 

Секции, представляются **секции** класса (в пространстве имен Microsoft.AnalysisServices.Tabular). **Секции** предоставляемых классами **источника** свойство P**artitionSource** тип, который предоставляет абстракцию через различные подходы для обработки данных в секции. Объект **секции** экземпляр может иметь **источника** свойства как null, указывающее, что данных будут отправлены в секцию путем отправки фрагментов данных на сервер как часть принудительной отправки данных API, предоставляемые службами Analysis Services . В SQL Server 2016 **PartitionSource** класс имеет два производных классов, представляющих способов привязки данных для секции: **QueryPartitionSource** и **CalculatedPartitionSource**. 

## <a name="columns-in-a-table"></a>Столбцы в таблице 

Столбцы представлены в нескольких классах, производных от базового **столбца** класса (в пространстве имен Microsoft.AnalysisServices.Tabular): 

* **DataColumn** (для обычных столбцов в обычных таблицах)
* **CalculatedColumn** (для столбцов, поддерживаемый выражение DAX)
* **CalculatedTableColumn** (для обычных столбцов в вычисляемых таблиц)
* **RowNumberColumn** (специальный тип столбца, созданного SSAS для каждой таблицы). 

## <a name="row-numbers-in-a-table"></a>Номера строк в таблице 

Каждый **таблицы** объект на сервере имеет **RowNumberColumn** используется в целях индексирования. Невозможно создать или добавить явным образом. Столбец создается автоматически при сохранении или обновить объект: 

* **базы данных. SaveChanges** 

* **базы данных. Update(ExpandFull)** 

При вызове любого метода, сервер будет создать столбец с номерами строк автоматически, видимое как **RowNumberColumn** коллекции столбцов таблицы. 

## <a name="calculated-tables"></a>Вычисляемые таблицы 

Вычисляемые таблицы получают данные из выражения DAX, которое repurposes данные из существующих структур данных в модели или ожидания привязок. Чтобы создать вычисляемую таблицу программными средствами, выполните следующие действия: 

* Создайте универсальный **таблицы**. 

* Добавить секцию с исходным типом **CalculatedPartitionSource**, где источником является выражением DAX. Источник секции имеет отличия обычной таблицы из вычисляемой таблицы. 

При сохранении изменений на сервер, сервер возвращает выводимый список **CalculatedTableColumns** (вычисляемые таблицы состоят из столбцов таблицы, вычисляемые), отображается через коллекции столбцов таблицы. 

## <a name="next-steps"></a>Следующие шаги

Просмотрите классы, используемые для обработки исключений в TOM: [обработка ошибок в том](../../analysis-services/tabular-model-programming-compatibility-level-1200/handling-errors-in-the-tom-api-analysis-services-amo-tom.md)
  
