---
title: Трассировка (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 45823fc8-723a-49f2-9a11-94d241245cfd
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: erikre
ms.openlocfilehash: fd7ff134e77d9260ff402c48087945af5fc1a86d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="tracing-master-data-services"></a>Трассировка (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Файл Web.config содержит раздел трассировки, как показано ниже. Это новый раздел в [!INCLUDE[ssSQL15](../includes/sssql15-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]  
  
```  
<sources>  
      <!-- Adjust the switch value to control the types of messages that should be logged.   
           http://msdn.microsoft.com/en-us/library/system.diagnostics.sourcelevels  
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
  
     Дополнительные сведения см. в разделе [SourceLevels — перечисление](https://msdn.microsoft.com/en-us/library/system.diagnostics.sourcelevels).  
  
-   Журналы сохраняются в папке Logs, находящейся в папке WebApplication. Расположение по умолчанию: C:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication\Logs.  
  
-   Файл создается для каждого дня или каждых 10 МБ данных.  
  
-   Если размер непосредственно достигает 200 МБ, удаляется самый старый журнал.  
  
-   В журнале используется формат CSV. В следующей таблице описывается формат журнала.  
  
    |Элемент|Description|  
    |-------------|-----------------|  
    |Time|Когда происходит запись трассировки.|  
    |CorrelationID|Каждому запросу присваивается один идентификатор корреляции. Все трассировки, активированные данным запросом, будут иметь одинаковый идентификатор корреляции.<br /><br /> При возникновении ошибки в пользовательском интерфейсе сообщение об ошибке содержит идентификатор корреляции.|  
    |Операция|Имя запрошенной операции. Если это запрос к пользовательскому веб-интерфейсу, то именем операции является URL-адрес. Если это запрос к API, то именем операции является имя службы.|  
    |Level|Уровень данной записи трассировки.|  
    |Сообщение|Текст трассировки.|  
  
## <a name="external-resources"></a>Внешние ресурсы  
 Запись блога [Troubleshooting Logging Improvement](http://go.microsoft.com/fwlink/p/?LinkId=615377)(Улучшенное ведение журнала устранения неполадок) на портале msdn.com.  
  
  
