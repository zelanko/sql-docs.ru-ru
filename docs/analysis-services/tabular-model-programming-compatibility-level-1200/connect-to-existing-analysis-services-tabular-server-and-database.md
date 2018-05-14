---
title: Подключиться к существующему серверу служб Analysis Services табличной и базы данных | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 13900e4aaad52d39a2691fb40d0e419f55f660fc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="connect-to-existing-analysis-services-tabular-server-and-database"></a>Подключиться к существующему серверу служб Analysis Services табличной и базы данных
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
В SQL Server 2016 объекты управления Analysis Services (AMO) содержит несколько пространств имен, которые могут использоваться для настройки соединения с сервером. В этой статье объясняется, как установить подключение к серверу, через пространство имен Microsoft.AnalysisServices.Tabular для моделей и баз данных, созданных на 1200 или высоким уровнем совместимости. 

Чтобы подключиться к серверу служб Analysis Services, коде создается экземпляр объекта сервера и затем вызовите метод Connect для его. После подключения объекта сервера отражают параметры текущего экземпляра служб Analysis Services. 

Для подключений верхнего уровня можно использовать следующие классы: 

* Microsoft.AnalysisServices.Server 
* Microsoft.AnalysisServices.Database 
* Microsoft.AnalysisServices.Tabular.Server 
* Microsoft.AnalysisServices.Tabular.Database 

Как видите, два пространства имен предоставляют возможность подключения к серверу и базе данных объектов: исходный файл Microsoft.AnalysisServices пространство имен для объектов AMO и новое пространство имен Microsoft.AnalysisServices.Tabular для тома.

Почему два пространства имен для операций? Ответ следует искать подчиненных, на уровне базы данных и модели, где иерархии объектов становится определенный режим и дерево модели состоит из многомерной или табличной метаданных. Для вызовов в дереве модели, объект сервера или базы данных предоставляется для обоих типов модели.

> [!NOTE]  
>  Метаданные, используемые для определения модели и операций полностью отличается в двух режимах. При разделении языка описания данных (DDL) на два разных пространства имен, через представление только API, необходимые для определенного типа модели упрощен процесс разработки. 

Несмотря на то, что зависит от инструкций DDL, подключения к серверу одинаковы для всех режимов, версий и выпусков. Поддержка сервера и подключения к базе данных через либо имен позволяет создавать универсальные средств или скрипта, подключиться к любому экземпляру служб Analysis Services или база данных, без необходимости знать, какой тип модели размещается на сервере.  

Такая гибкость Описание зависимостей между сборками. Чтобы выполнять вызовы ниже уровня базы данных (например, в модели в базе данных Tabular 1200 или для куба, измерения или группы мер в многомерной или табличной базы данных 1050 – 1103), объекты AMO имеет зависимость от TOM. 

Напротив TOM нет зависимостей для объектов AMO. Несмотря на то, что том не может использоваться для изучения многомерные метаданные (кубы), объекты AMO можно использовать для исследования многомерных и табличных метаданных. 

По этой причине первым шагом в настройке проекта необходимо добавить ссылки на все сборки объектов AMO. В разделе [установке, ссылок и распространять клиентской библиотеке TOM](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md) подробные сведения. 

> [!NOTE]  
>  Подключения к серверу и базе данных основаны на устаревших объектов AMO классы, наследующие от MajorObject. Несмотря на то, что основные и второстепенные объекты не используются в дереве табличной модели, MajorObject и отображается как базовый класс для объектов сервера и базы данных, независимо от того, какие API, который позволяет установить соединение.  

## <a name="code-example-server-connection"></a>Пример кода: подключение к серверу 

Ниже приведен пример кода C#, демонстрирующий способы подключения к локальному экземпляру служб Analysis Services и просмотр его свойств в окне консоли. 

В этом примере показано только некоторые свойства объекта сервера, но существует несколько свойств, включая ServerMode и DefaultCompatibilityLevel.  

```
using System; 
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

 
                Console.WriteLine("Connection established successfully."); 
                Console.WriteLine(); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                Console.WriteLine("Server name:\t\t{0}", server.Name); 
                Console.WriteLine("Server product name:\t{0}", server.ProductName); 
                Console.WriteLine("Server product level:\t{0}", server.ProductLevel); 
                Console.WriteLine("Server version:\t\t{0}", server.Version); 
                Console.ResetColor(); 
                Console.WriteLine(); 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```
При запуске этой программы, выходные данные приведены свойства в объекте сервера в окне консоли. 

## <a name="authentication-and-authorization"></a>Проверка подлинности и авторизация 

Сервера или подключения базы данных служб Analysis Services требуются административные разрешения, используемые для операций чтения и записи и для передачи через запрос олицетворенного соединения.  

Несмотря на то, что инфраструктура безопасности служб Analysis Services была расширена в последние годы, чтобы разрешить нестандартной проверки подлинности, определенных условиях, метод только поддерживаемые внешней проверки подлинности является встроенной безопасности Windows. Субъекты безопасности принимается равным допустимый пользователь или группа учетных записей домена Windows.  

В Windows 2012 и более поздних версиях делегирования может передаваться между доменами. В службах Analysis Services делегирование используется только для модели DirectQuery. в противном случае подключения являются прямые или олицетворенного. 

## <a name="next-steps"></a>Следующие шаги 

После установки соединения, логической следующий шаг заключается в либо список существующих баз данных на сервере, или возможно создать новую пустую базу данных. Следующие ссылки включают примеры кода, демонстрирующие обе эти основные задачи: 

- [Создание и развертывание пустой базы данных](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-and-deploy-an-empty-database-analysis-services-amo-tom.md)
- [Список существующих баз данных](../../analysis-services/tabular-model-programming-compatibility-level-1200/list-existing-databases-on-a-tabular-server-analysis-services-amo-tom.md)
