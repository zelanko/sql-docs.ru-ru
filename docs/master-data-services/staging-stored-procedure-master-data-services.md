---
title: "Промежуточная хранимая процедура (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 04/01/2016
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
caps.latest.revision: 15
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 19ce25e1182e362761b1919f36d72623dd7289e7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="staging-stored-procedure-master-data-services"></a>Промежуточная хранимая процедура (службы Master Data Services)
  При запуске промежуточного процесса из [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]используется одна из трех хранимых процедур.  
  
-   stg.udp_\<имя>_Leaf  
  
-   stg.udp_\<имя>_Consolidated  
  
-   stg.udp_\<имя>_Relationship  
  
 Где имя — это имя промежуточной таблицы, определенной при создании сущности.  
  
## <a name="staging-process-stored-procedure-parameters"></a>Параметры хранимой процедуры промежуточного процесса  
 В следующей таблице приведены параметры этих хранимых процедур.  
  
|Параметр|Description|  
|---------------|-----------------|  
|**VersionName**<br /><br /> Обязательно|Имя версии. С учетом или без учета регистра, в зависимости от параметров сортировки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
|**LogFlag**<br /><br /> Обязательно|Определяет, будут ли регистрироваться транзакции в ходе промежуточного процесса. Возможны следующие значения:<br /><br /> **0**: не регистрировать транзакции.<br /><br /> **1**: регистрировать транзакции.<br /><br /> <br /><br /> Дополнительные сведения о транзакциях см. в разделе [Транзакции (службы Master Data Services)](../master-data-services/transactions-master-data-services.md).|  
|**BatchTag**<br /><br /> Требуется, за исключением веб-службы|Значение **BatchTag** , как указано в промежуточной таблице.|  
|**Batch_ID**<br /><br /> Требуется только для веб-службы|Значение **Batch_ID** , как указано в промежуточной таблице.|  
|**Имя пользователя**|Необязательный параметр|  
|**Идентификатор пользователя**|Необязательный параметр|  
  
### <a name="staging-process-stored-procedure-example"></a>Пример хранимой процедуры промежуточного процесса  
 В следующем примере показан запуск промежуточного процесса с помощью хранимой процедуры.  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
      @UserName=N’domain\user’  
  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Проверка хранимых процедур (службы Master Data Services)](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [Просмотр ошибок, возникающих во время помещения на промежуточное хранение (службы Master Data Services)](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)  
  
  

