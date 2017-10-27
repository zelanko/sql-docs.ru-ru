---
title: "Общие сведения о модулях обработки данных | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- data processing extensions [Reporting Services], about extensions
ms.assetid: 1d652605-9313-4c75-98b4-ba4dcbbb222d
caps.latest.revision: 39
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 075724639c912f40c3ef7c49227ba653bd086fcd
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="data-processing-extensions-overview"></a>Общие сведения о модулях обработки данных
  Модули обработки данных в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] позволяют соединяться с источником данных и получать данные. Они также служат мостом между источником данных и набором данных. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]модули обработки данных моделируются подмножество [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] интерфейсов поставщиков данных.  
  
 В следующей таблице перечисляются модули обработки данных, включенные в службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
|Модуль обработки данных|Description|  
|-------------------------------|-----------------|  
|Модуль обработки данных для служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Использует поставщик данных .NET Framework для SQL Server для подключения и извлечения данных из [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].|  
|Модуль обработки данных OLE DB|Использует поставщик данных .NET Framework для OLE DB. С помощью данного модуля сервер отчетов может осуществлять запрос к любым источникам данных с поставщиком OLE DB.|  
|Модуль обработки данных для Oracle|Использует поставщик данных .NET Framework для Oracle. С этим модулем сервер отчетов может обращаться к источникам данных Oracle через клиентское ПО Oracle.|  
|Модуль обработки данных для ODBC|Использует поставщик данных .NET Framework для ODBC. С этим модулем сервер отчетов может обращаться к данным в базе данных, для которой имеется драйвер ODBC.|  
  
 Можно использовать API-интерфейс обработки данных служб [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] для добавления на сервер отчетов пользовательской обработки данных.  
  
> [!NOTE]  
>  Службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] имеют встроенную поддержку для поставщиков данных на платформе [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Если уже реализован полный поставщик данных, нет необходимости реализовывать модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Однако следует подумать о расширении поставщика данных, включив в него функции служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 2005, в том числе учетные данные безопасного соединения и агрегаты на сервере.  
  
 Каждый из модулей обработки данных, включаемых в службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], использует общий набор интерфейсов. Это обеспечивает реализацию каждым модулем совместимых функций.  
  
 Можно разработать модули обработки данных для собственных источников данных, или можно использовать интерфейсы для добавления дополнительного уровня обработки данных в общие инфраструктуры баз данных. Можно выполнить развертывание пользовательских модулей обработки данных для гладкой интеграции данных в существующие серверы отчетов в организации. Их также можно использовать как часть пользовательского пакета составления отчетов, предоставляемого клиентам.  
  
 ![Архитектура модуля обработки данных](../../../reporting-services/extensions/data-processing/media/bk-dataprocess-extensions.gif "архитектура модуля обработки данных")  
Архитектура модуля обработки данных служб Reporting Service  
  
 Преимущества реализации пользовательского модуля обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] заключаются в следующем.  
  
-   Более простая архитектура доступа к данным, часто с более удобным обслуживанием и с более высокой производительностью.  
  
-   Возможность непосредственного предоставления клиентам функциональных возможностей, зависящих от модуля.  
  
-   Специальный интерфейс для клиентов, обеспечивающий доступ к источнику данных в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
## <a name="data-extension-process-flow"></a>Поток процесса модуля обработки данных  
 Перед разработкой пользовательского модуля обработки данных необходимо понять, как сервер отчетов использует модули данных для обработки данных. Необходимо также понимать конструкторы и методы, которые вызываются сервером отчетов.  
  
 ![Поток для модуля обработки данных](../../../reporting-services/extensions/data-processing/media/bk-ext-01.gif "поток для модуля обработки данных")  
Пошаговый поток процесса модуля обработки данных, вызываемого сервером отчетов  
  
 На рисунке показана следующая последовательность событий.  
  
1.  Сервер отчетов создает объект соединения и передает ему строку соединения и учетные данные, связанные с отчетом.  
  
2.  Текст команды отчета используется для создания объекта команды. В этом процессе модуль обработки данных может включать код, который выполняет синтаксический анализ текста команды и создает параметры для команды.  
  
3.  После обработки объекта команды и параметров создается модуль чтения данных, который возвращает результирующий набор и включает сервер отчетов для связи данных отчета с макетом отчета.  
  
## <a name="developer-requirements"></a>Требования для разработки  
 Для разработки модуля обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] необходимо следующее:  
  
-   Компьютер развертывания с установленным конструктором отчетов или сервером отчетов.  
  
-   С компьютера разработчика [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] или более поздней версии, или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Software Development Kit (SDK) установлен.  
  
-   Глубокое понимание функций и возможностей служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
-   Углубленное понимание [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] архитектуры, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] поставщики данных, объектов ADO.NET DataSet и общих [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] интерфейсов.  
  
-   Процесс разработки в [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] язык, такой как [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET.  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

