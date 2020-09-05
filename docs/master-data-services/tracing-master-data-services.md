---
title: Трассировка
description: Файл Web.config содержит раздел трассировки, новый в SQL Server 2016 Master Data Services. Сведения о поведении трассировки по умолчанию.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 45823fc8-723a-49f2-9a11-94d241245cfd
author: lrtoyou1223
ms.author: lle
manager: erikre
ms.openlocfilehash: da6742e7c2801db245002688c04fcb22ada1723a
ms.sourcegitcommit: 827ad02375793090fa8fee63cc372d130f11393f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2020
ms.locfileid: "89480456"
---
# <a name="tracing-master-data-services"></a>Трассировка (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Файл Web.config содержит раздел трассировки, как показано ниже. Это новый раздел в [!INCLUDE[ssSQL15](../includes/sssql15-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]  
  
```  
<sources>  
      <!-- Adjust the switch value to control the types of messages that should be logged.   
           https://msdn.microsoft.com/library/system.diagnostics.sourcelevels  
           Use the a switchValue of Verbose to generate a full log. Please be aware that   
           the trace file can get quite large very quickly -->  
      <source name="MDS" switchType="System.Diagnostics.SourceSwitch" switchValue="Warning, ActivityTracing">  
        <listeners>  
          <!-- Set a directory path where the service account you chose while setting up Master Data Services has read and write privileges.  
               Default path is Logs in WebApplication folder, for example C:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication  
               New log file will be created every day or every 10 mb.  
               When directory size hits the 200mb limitation, the oldest file will be deleted.-->  
          <add name="FileTraceListener"  
               type="Microsoft.MasterDataServices.Core.Logging.FileTraceListener, Microsoft.MasterDataServices.Core"   
               initializeData="DirectoryPath = Logs; FileSizeInMb = 10; MaxDirectorySizeInMb = 200"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
  
```  
  
 Ниже приведено поведение трассировки по умолчанию.  
  
-   Трассировка включена для сообщений уровня Warning и ActivityTracing.  
  
     Дополнительные сведения см. в разделе [SourceLevels — перечисление](https://msdn.microsoft.com/library/system.diagnostics.sourcelevels).  
  
-   Журналы сохраняются в папке Logs, находящейся в папке WebApplication. Расположение по умолчанию: C:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication\Logs.  
  
-   Файл создается для каждого дня или каждых 10 МБ данных.  
  
-   Если размер непосредственно достигает 200 МБ, удаляется самый старый журнал.  
  
-   В журнале используется формат CSV. В следующей таблице описывается формат журнала.  
  
    |Элемент|Описание|  
    |-------------|-----------------|  
    |Time|Когда происходит запись трассировки.|  
    |CorrelationID|Каждому запросу присваивается один идентификатор корреляции. Все трассировки, активированные данным запросом, будут иметь одинаковый идентификатор корреляции.<br /><br /> При возникновении ошибки в пользовательском интерфейсе сообщение об ошибке содержит идентификатор корреляции.|  
    |Операция|Имя запрошенной операции. Если это запрос к пользовательскому веб-интерфейсу, то именем операции является URL-адрес. Если это запрос к API, то именем операции является имя службы.|  
    |Level|Уровень данной записи трассировки.|  
    |Сообщение|Текст трассировки.|  
  
## <a name="external-resources"></a>Внешние ресурсы  
 Запись блога [Troubleshooting Logging Improvement](https://techcommunity.microsoft.com/t5/sql-server-integration-services/troubleshooting-logging-improvement/ba-p/388214)(Улучшенное ведение журнала устранения неполадок) на портале msdn.com.  
  
  
