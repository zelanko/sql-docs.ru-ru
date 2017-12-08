---
title: "Установка, распространять и ссылаться на табличные модели объекта | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e51769f7-aac7-4835-a5ae-91aac04aa476
caps.latest.revision: "22"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a2ba71ce1ac7dcc0787e84edba3ea436bd33e25f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="install-distribute-and-reference-the-tabular-object-model"></a>Установка, распространять и ссылаться на табличные модели объектов

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

В этой статье объясняется, как для загрузки, ссылки и распространения Analysis Services табличной объекта модели (TOM), библиотеки C# для создания и управления табличными моделями и баз данных в управляемом коде.  
  
ТОМ является расширением библиотеки клиентских объектов AMO (Microsoft.AnalysisServices.dll), поставляемое с SQL Server 2016. Он работает с табличными моделями, предназначенных для механизма табличных метаданных в выпуске SQL Server 2016. Чтобы использовать TOM, модели и базы данных должны быть на уровне совместимости 1200 или выше.  

## <a name="amo-tom-assemblies"></a>Объекты AMO TOM сборок

SQL Server 2016 выполняет рефакторинг и разворачивает объектов AMO для включения новых сборок Core, табличные и JSON. Он также включает исходной сборки AMO, Microsoft.AnalysisServices.dll, который был частью служб Analysis Services с момента первого выпуска. Измененной структурой AMO разгружает общие классы в одну сборку, а также логическое деление между табличные и многомерные API-интерфейсы через дополнительные сборки. 

В следующей таблице описаны каждой сборки.
  
Сборка  |Функциональность  |Важные классы |
---------|---------|--------------  |
Основные сведения <br/>Microsoft.AnalysisServices.Core.dll | Общие для табличных и многомерных баз данных. <br/><br/>Предоставляет обработку исключений, универсального подключения к экземпляру служб Analysis Services и базы данных и доступ к общие свойства и методы для объектов сервера и базы данных. <br/><br/>Он должен для любого решения объектов AMO, предназначенных для SQL Server 2016. | Основные&nbsp;сервера<br/>Основные&nbsp;базы данных<br/>AmoException
ТОМ<br/> Microsoft.AnalysisServices.Tabular.dll, версия 13.0.1601.5 или более поздней версии.| Создание и управление объектов табличных метаданных. | TOM&nbsp;сервера <br/>TOM&nbsp;базы данных<br /> Модель<br /> Таблица<br /> Столбец<br /> Связь
  AMO<br /> Microsoft.AnalysisServices.dll| Создание и управление объектов многомерные метаданные, включая базы данных в табличную модель 1050 – 1103. | Объекты AMO&nbsp;сервера <br />Объекты AMO&nbsp;базы данных <br /> Cube <br /> Измерение <br /> Группа мер 
Json<br/>Microsoft.AnalysisServices.Tabular.Json.dll | Вспомогательной библиотеки DLL, которая служит оболочкой для NewtonSoftJson.dll (JSON.NET) для управления обновлениями, удаление риск возникновения функциональные изменения для сериализации JSON в рабочих нагрузках служб Analysis Services. <br /> <br />Эта библиотека DLL существует как элемент dependency в том и не предназначен для непосредственного использования в коде. | Нет.  
  
 ### <a name="understanding-assembly-dependencies"></a>Основные сведения о зависимостях сборки
  
Программировать с использованием объектов AMO, решение должно включать ссылки на зависимые библиотеки DLL. Объекты AMO и TOM зависят от основных компонентов, так как он предоставляет базовые классы.

Объекты AMO зависит TOM, поскольку некоторые классы объектов AMO ссылки классы из TOM. Например объект AMO базы данных имеет свойство модели типа модели, реализованы в TOM dll. 

![Объекты AMO TOM зависимости](../../analysis-services/tabular-model-programming-compatibility-level-1200/media/amo-tom-dependencies.png)

Нельзя распространять Microsoft.AnalysisServices.dll без Microsoft.AnalysisServices.Tabular.dll, но может ссылаться их соответствующих пространств имен, а второй.

### <a name="choosing-which-namespace-to-use-in-code"></a>Выбор какое пространство имен для использования в коде

В [иерархии объектов](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md) , любой объект ниже базы данных, является построение табличных метаданных с помощью объекта модели, либо в конструкциях многомерные метаданные через объект куба, измерения или группы мер. Для операций высокого уровня на уровне сервера, базы данных, роли или трассировки выбрать, какие пространства имен для ссылки на будет зависеть от рабочих нагрузок кода должна поддерживать.

* Используйте Tabular.Server или Tabular.Database, если решения — уровень совместимости 1200 или выше, а объект базы данных, которыми вы работаете необходимо предоставить доступ к модели, таблицы, столбцы и другие объекты, выраженное как конструкции табличных метаданных.
* Используйте AnalysisServices.Server или AnalysisServices.Database, если Нижеследующий код ссылается на многомерные объекты, такие как кубы, источники данных, DataSourceViews и измерения.

Вам потребуется обоих пространствах имен для средства и приложения, поддерживающие сочетание баз данных и типы моделей. 

Создание ссылок на основное пространство имен в коде не требуется; Классы ядра, базовые классы, созданные с целью предоставления общих свойств, такие как имя и описание для основных объектов.  
  
## <a name="determine-whether-amo-and-tom-installation-is-required"></a>Определить, требуется ли установка объектов AMO и TOM  
   
 Объекты AMO и тома могут быть объединены в одну клиентскую библиотеку. Если вы уже установлен экземпляр SQL Server 2016 Analysis Services, клиентские библиотеки или версия SQL Server Data Tools, нацеленный на экземпляре служб SQL Server 2016, Microsoft.AnalysisServices.dll уже установлена.  
  
 Чтобы определить, установлены ли сборки, проверьте следующие расположения:
* C:\Windows\Microsoft.NET\assembly\GAC_MSIL
* C:\Program Files\Microsoft SQL Server\130\SDK\Assemblies
* C:\Program Files\Microsoft SQL Server\130\DTS\Tasks
* C:\Program Files\Microsoft SQL Server\MSAS13. MSSQLSERVER\OLAP\bin
 
 Убедитесь, что существуют следующие сборки:
*  Microsoft.AnalysisServices.Core.dll
*  Microsoft.AnalysisServices.dll
*  Microsoft.AnalysisServices.Tabular.dll
*  Microsoft.AnalysisServices.Tabular.Json.dll   
   
## <a name="download-sqlasamo"></a>Загрузить SQL_AS_AMO  
 
 Обратите внимание, что Microsoft.AnalysisServices.dll недоступен через диспетчер NuGet.
  
1. Последовательно выберите пункты [странице загрузки пакета дополнительных компонентов SQL Server 2016](https://www.microsoft.com/download/details.aspx?id=52676).  
  
2. Нажмите кнопку **Загрузить**.  
  
3. Выберите либо **\X64\SQL_AS_AMO.msi** или **\X86\SQL_AS_AMO.msi**. Можно выбрать любой из них: объекты AMO и TOM сборки, независимый от платформы.
  
4. Нажмите кнопку **Далее** продолжить загрузку. Вы найдете MSI-файлы в вашей **загружает** папки.  
  
## <a name="install-sqlasamo"></a>Установить SQL_AS_AMO  
  
1. Дважды щелкните **SQL_AS_AMO.msi** и пошаговое выполнение установки.  
  
2. Последовательно выберите пункты **C:\Program Files\Microsoft SQL Server\130\SDK\Assemblies** для подтверждения размещение Microsoft.AnalysisServices.Core.dll, Microsoft.AnalysisServices.dll, Microsoft.AnalysisServices.Tabular.dll, и Microsoft.AnalysisServices.Tabular.Json.dll.   
  
## <a name="add-references"></a>Добавление ссылок  
  
1. В **обозревателе решений** > **добавить ссылку** > **Обзор**.  
2. Последовательно выберите пункты **C:\Program Files\Microsoft SQL Server\130\SDK\Assemblies** и выберите:  
   * Microsoft.AnalysisServices.Core  
   * Microsoft.AnalysisServices.Tabular  
   * Microsoft.AnalysisSerivces.Tabular.Json  
  
3. Нажмите кнопку **ОК**.  В **обозревателе решений**, подтвердите находятся эти сборки в папке "ссылки".
  
4. На странице кода добавьте пространство имен Microsoft.AnalysisServces.Tabular, если баз данных и моделей Tabular 1200 или высоким уровнем совместимости. 
  
   ```   
   using Microsoft.AnalysisServices; 
   using Microsoft.AnalysisServices.Tabular;
   ```  
    При необходимости добавьте Microsoft.AnalysisServces для поддержки более широкого круга соединения с экземплярами служб Analysis Services, которые не являются специально SQL Server 2016 в табличном режиме сервера. 
 
    При включении пространства имен, которые содержат классы, общие для объектов сервера, базы данных, роли и трассировки, избежать неоднозначных ссылок, указав, какие пространства имен, необходимо использовать (например, Microsoft.AnalysisServices.Tabular.Server создается экземпляр сервера Объект, с помощью табличное пространство имен).

## <a name="redistribute-amo-and-tom-with-your-application"></a>Распространять вместе с приложением AMO и TOM  
  
Распространение AMO и TOM — с помощью **sql_as_amo.msi** пакет установки. При создании программы установки для клиентского приложения, которое вызывает в AMO или TOM добавить **sql_as_amo.msi** для исполняемого файла. Это только поддерживаемые механизм для распространения объектов AMO и TOM клиентских библиотек.  
  
Пакет является самодостаточным и предоставляет все сборки, необходимые для вызова объектов AMO и TOM в коде. Другие пакеты, например SQL_AS_OLEDB.msi или SQL_AS_ADOMD.msi, специально не требуются для сценариев программирования TOM.
