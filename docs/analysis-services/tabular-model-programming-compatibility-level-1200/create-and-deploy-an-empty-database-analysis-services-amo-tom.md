---
title: Создание и развертывание пустой базы данных (службы Analysis AMO-TOM) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: afacae6ab8fc6f5a4f592e87758cca3142579c0a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="create-and-deploy-an-empty-database-analysis-services-amo-tom"></a>Создание и развертывание пустой базы данных (службы Analysis AMO-TOM)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
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
 
