---
title: "Создание и развертывание пустой базы данных (службы Analysis AMO-TOM) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: dcb916e9-97c5-47e0-922a-404891423b2a
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f8aafa733ba61563072e304cf77945203df7585d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-and-deploy-an-empty-database-analysis-services-amo-tom"></a>Создание и развертывание пустой базы данных (службы Analysis AMO-TOM)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

Обычный сценарий для программирования для объектов AMO TOM является создание баз данных и моделей в режиме реального времени. В этой статье рассматриваются действия по созданию базы данных. 

Для табличных решений имеется однозначное соответствие между базой данных и модели с одной модели на базу данных. Обычно можно указать одно из них, и обработчик выведет отсутствующего объекта. 

Создание и развертывание новой базы данных — это задача трех частей: 

* Создать экземпляр **базы данных** и задайте его свойства, включая имя. 

* Добавить **базы данных** объект **Server.Databases** коллекции. 

* Вызовите **обновление** метод **базы данных** объекта для сохранения его в **сервера**. 

## <a name="code-example-create-empty-database"></a>Пример кода: создать пустую базу данных 

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
                    server.Databases.GetNewName("New Empty Database"); 
 
                // 
                // Instantiate a new  
                // Microsoft.AnalysisServices.Tabular.Database object. 
                // 
                var blankDatabase = new Database() 
                { 
                    Name = newDatabaseName, 
                    ID = newDatabaseName, 
                    CompatibilityLevel = 1200, 
                    StorageEngineUsed = StorageEngineUsed.TabularMetadata, 
                }; 
                // 
                // Add the new database object to the server's  
                // Databases connection and submit the changes 
                // with full expansion to the server. 
                // 
                server.Databases.Add(blankDatabase); 
                blankDatabase.Update(UpdateOptions.ExpandFull); 

                Console.Write("Database "); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                Console.Write(blankDatabase.Name); 
                Console.ResetColor(); 
                Console.WriteLine(" created successfully."); 
                Console.WriteLine(); 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```

## <a name="next-steps"></a>Следующие шаги 

После создания базы данных можно добавить объекты модели. 

- [Добавьте источник данных для табличной модели](../../analysis-services/tabular-model-programming-compatibility-level-1200/add-a-data-source-to-tabular-model-analysis-services-amo-tom.md)
- [Создание таблицы, столбцы и секции в табличной модели](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-tables-partitions-and-columns-in-a-tabular-model.md)
 

