---
title: "Изменение действия функций служб Analysis Services в SQL Server 2016 | Microsoft Docs"
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
ms.assetid: 92ebd5cb-afb6-4b62-968f-39f5574a452b
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 17
---
# Изменение действия функций служб Analysis Services в SQL Server 2016
  *Изменения в работе* влияют на поведение функций или их взаимодействие в текущей версии по сравнению с предыдущими версиями SQL Server.  
  
 Примерами изменения в работе могут служить перемена значений по умолчанию, необходимость в ручной настройке для завершения обновления или восстановления функциональности и новая реализация существующей функции.  
  
 Здесь перечислены функции, которые изменены в этом выпуске, но в то же время не нарушают работу существующей модели или код после обновления.  
  
> [!NOTE]  
>  В отличие от *изменения в работе*, *критическое изменение* нарушает работу модели данных или приложения, интегрированного с [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , после обновления сервера, клиентского средства или модели. Дополнительные сведения см. в разделе [Критические изменения функций служб Analysis Services в SQL Server 2016](../analysis-services/breaking-changes-to-analysis-services-features-in-sql-server-2016.md).  
  
## Службы Analysis Services в режиме интеграции с SharePoint  
 Запуск мастера настройки Power Pivot в виде задачи после установки больше не требуется. Это действует для всех поддерживаемых версий SharePoint, загружающих модели из текущего выпуска [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
## Режим DirectQuery в табличных моделях  
 *DirectQuery* — это режим доступа к данным для табличных моделей, при котором выполнение запроса происходит на серверной реляционной базе данных с получением результирующего набора в режиме реального времени. Он часто используется для очень больших наборов данных, которые не помещаются в памяти, или быстро меняющихся данных, если необходимо вернуть самые последние данные с помощью запросов к табличной модели.  
  
 DirectQuery выступает в качестве режима доступа к данным в последних нескольких выпусках. В выпуске [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]реализация этого режима немного изменена, так как предполагается, что табличная модель находится на уровне совместимости 1200. Режим DirectQuery имеет меньше ограничений, чем раньше. Кроме того, изменены свойства базы данных.  
  
 При использовании DirectQuery для существующей табличной модели ее можно сохранить на текущем уровне совместимости (1100 или 1103) и работать далее в том же режиме и на том же уровне. Кроме того, можно выполнить обновление до уровня 1200, чтобы использовать улучшения, внесенные в DirectQuery в этом выпуске [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Обновление модели DirectQuery на месте не поддерживается, так как параметры предыдущих уровней совместимости не имеют точных аналогов на новом уровне совместимости 1200. Существующую табличную модель в режиме DirectQuery, при наличии, следует открыть в SQL Server Data Tools, отключить этот режим, задать для **уровня совместимости** значение 1200, а затем изменить свойства DirectQuery на определенные для табличных моделей 1200. Сведения см. в разделе [Режим DirectQuery (табличные службы SSAS)](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md).  
  
## См. также  
 [Обратная совместимость_удалено](../Topic/Backward%20Compatibility_deleted.md)   
 [Критические изменения функций служб Analysis Services в SQL Server 2016](../analysis-services/breaking-changes-to-analysis-services-features-in-sql-server-2016.md)   
 [Уровень совместимости табличных моделей в службах Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Скачивание SQL Server Data Tools](https://msdn.microsoft.com/en-us/library/mt204009.aspx)  
  
  