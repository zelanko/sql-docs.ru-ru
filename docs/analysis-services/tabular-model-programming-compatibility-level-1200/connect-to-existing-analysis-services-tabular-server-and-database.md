---
title: Подключиться к существующей табличной модели Analysis Services сервера и базы данных | Документация Майкрософт
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
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38033394"
---
# <a name="connect-to-existing-analysis-services-tabular-server-and-database"></a>Подключиться к существующей табличной модели Analysis Services сервера и базы данных
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
В SQL Server 2016 объекты управления Analysis Services (AMO) включает в себя несколько пространств имен, которые могут использоваться для настройки подключения к серверу. В этой статье объясняется, как установить подключение к серверу, используя пространство имен Microsoft.AnalysisServices.Tabular для моделей и баз данных, созданных в 1200 или высоким уровнем совместимости. 

Чтобы подключиться к серверу служб Analysis Services, код должен создать экземпляр объекта Server и затем вызвать метод Connect для его. После подключения, параметры текущего экземпляра служб Analysis Services отобразятся свойства объекта сервера. 

Следующие классы могут быть использованы для подключения верхнего уровня: 

* Microsoft.AnalysisServices.Server 
* Microsoft.AnalysisServices.Database 
* Microsoft.AnalysisServices.Tabular.Server 
* Microsoft.AnalysisServices.Tabular.Database 

Как вы видите, два пространства имен предоставляют возможность подключения к серверу и базе данных объектов: исходном пространстве имен Microsoft.AnalysisServices для объектов AMO и новое пространство имен Microsoft.AnalysisServices.Tabular для тома.

Зачем два пространства имен для тех же операций? Ответ заключается подчиненных, на уровне базы данных и модели, где иерархии объектов становится относящиеся к режиму и дерево модели состоит из метаданных Multidimensional или Tabular. Для звонков в дереве model, объект сервера или базы данных предоставляется для обоих типов модели.

> [!NOTE]  
>  Метаданные, используемые для определения модели и операций полностью отличается для двух режимов. Разбиение два разных пространства имен языка определения данных (DDL), по возможности разработки упрощается при помощи представления только API, который необходим для каждого типа модели. 

Несмотря на то, что отличается DDL, подключений к серверу одинаковы во всех режимах, версий и выпусков. Поддержка сервера и подключения к базе данных через либо пространство имен позволяет создавать универсальные средства или сценарий, подключиться к любому экземпляру служб Analysis Services или база данных, без необходимости знать, какой тип модели размещается на сервере.  

Такая гибкость объясняет зависимость между сборками. Чтобы осуществлять вызовы ниже уровня базы данных (например, в модели в базу данных Tabular 1200, или куба, измерения или группы мер в базе данных 1050 – 1103 многомерный или табличный), объекты AMO имеет зависимость от TOM. 

Напротив TOM имеет зависимости от объектов AMO. Несмотря на то, что том не может использоваться для изучения многомерные метаданные (кубы), объекты AMO можно использовать для исследования многомерных и табличных метаданных. 

По этой причине первым шагом в настройке проекта необходимо добавить ссылки на все сборки AMO. См. в разделе [устанавливать, ссылки и распространять клиентскую библиотеку TOM](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md) подробные сведения. 

> [!NOTE]  
>  Подключения сервера и базы данных основаны на устаревших объектов AMO классы, наследующие от MajorObject. Несмотря на то, что основные и второстепенные объекты не используются в дереве табличной модели, MajorObject и отображается как базовый класс для объектов сервера и базы данных, независимо от того, какие API, которые позволяют настроить подключение.  

## <a name="code-example-server-connection"></a>Пример кода: соединение с сервером 

Ниже приведен пример кода C#, демонстрирующий способы подключения к локальному экземпляру служб Analysis Services и его свойства в окне консоли списка. 

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
При запуске этой программы, выходные данные показаны свойства объекта сервера в окне консоли. 

## <a name="authentication-and-authorization"></a>Проверка подлинности и авторизация 

Сервер или подключения к базе данных служб Analysis Services требуются права администратора, используемый для операций чтения и записи, а также для передачи через запрос олицетворенного соединения.  

Несмотря на то, что инфраструктура безопасности служб Analysis Services была расширена в последние годы, чтобы разрешить нестандартной проверки подлинности при определенных условиях, метод только поддерживаемые внешней проверки подлинности — встроенная безопасность Windows. Предполагается, что субъекты безопасности являются допустимым Windows пользователя или группу учетных записей домена.  

В Windows 2012 и более поздних версиях делегирования может передаваться между доменами. В службах Analysis Services делегирование используется только для модели DirectQuery. в противном случае подключения являются прямые или олицетворения. 

## <a name="next-steps"></a>Следующие шаги 

После установления подключения, следующий логический шаг — либо список существующих баз данных уже существует на сервере или возможно создание новой пустой базы данных. Приведенные ниже ссылки включают примеры кода, демонстрирующие оба этих основных задач: 

- [Создание и развертывание пустой базы данных](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-and-deploy-an-empty-database-analysis-services-amo-tom.md)
- [Список существующих баз данных](../../analysis-services/tabular-model-programming-compatibility-level-1200/list-existing-databases-on-a-tabular-server-analysis-services-amo-tom.md)
