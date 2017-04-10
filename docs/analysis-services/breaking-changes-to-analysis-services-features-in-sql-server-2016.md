---
title: "Критические изменения функций служб Analysis Services в SQL Server 2016 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "критические изменения [службы Analysis Services]"
  - "обновление служб Analysis Services"
ms.assetid: aeb02542-5a6c-458c-a110-13413dd3e9d9
caps.latest.revision: 55
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 53
---
# Критические изменения функций служб Analysis Services в SQL Server 2016
  *Критическое изменение* приводит к прекращению работы модели данных, кода приложения или сценария после обновления модели или сервера.  
  
> [!NOTE]  
>  *Изменение в работе* определяется как изменение кода, которое не нарушает работу модели или приложения, но приводит к другим действиям, характерным для предыдущего выпуска.  Примерами изменений в работе могут быть: изменение значения по умолчанию, запрет настройки свойств или параметров, которая ранее была разрешена. Дополнительные сведения об изменениях в работе для этого выпуска см. в разделе [Behavior Changes to Analysis Services Features in SQL Server 2016](../analysis-services/behavior-changes-to-analysis-services-features-in-sql-server-2016.md).  
  
## Обновление версии .NET 4.0  
 Клиентские библиотеки управляющих объектов служб Analysis Services (AMO), ADOMD.NET и табличной объектной модели (TOM) в [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] теперь ориентированы на среду выполнения .NET 4.0. Это может быть критическим изменением для приложений, ориентированных на платформу .NET 3.5. Приложения, использующие более новые версии этих сборок, теперь должны ориентироваться на платформу .NET 4.0 или более поздней версии.  
  
## Обновление версии объектов AMO  
 [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] — обновление версии для объектов [управляющих объектов служб Analysis Services (AMO)](../Topic/Analysis%20Services%20Management%20Objects%20\(AMO\).md), которое при определенных обстоятельствах является критическим изменением.  Существующий код и сценарии, которые вызывают объекты AMO, продолжают работать как прежде, если обновление произведено из предыдущей версии. Но если требуется *перекомпилировать* приложение и использовать экземпляр [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] , нужно добавить следующее пространство имен, чтобы код или сценарий работали:  
  
```  
  
using Microsoft.AnalysisServices;  
using Microsoft.AnalysisServices.Core;  
  
```  
  
 Если в коде делается ссылка на сборку Microsoft.AnalysisServices, необходимо использовать пространство имен [Microsoft.AnalysisServices.Core](../Topic/Microsoft.AnalysisServices.Core.md). Объекты, которые ранее содержались только в пространстве имен **Microsoft.AnalysisServices** и одинаково используются в табличных и многомерных сценариях, в этом выпуске перемещены в основное пространство имен.  Например, API, связанные с сервером, перемещены в основное пространство имен.  
  
 Несмотря на множество доступных пространств имен, оба вида существуют в одной сборке (Microsoft.AnalysisServices.dll).  
  
## Изменения XEvent DISCOVER  
 Чтобы улучшить поддержку потоковой передачи XEvent DISCOVER в среде SSMS для [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], `DISCOVER_XEVENT_TRACE_DEFINITION` заменяется следующими трассировками XEvent:  
  
-   DISCOVER_XEVENT_PACKAGES  
  
-   DISCOVER_XEVENT_OBJECT  
  
-   DISCOVER_XEVENT_OBJECT_COLUMNS  
  
-   DISCOVER_XEVENT_SESSION_TARGETS  
  
## См. также  
 [Analysis Services Backward Compatibility](../analysis-services/analysis-services-backward-compatibility.md)  
  
  