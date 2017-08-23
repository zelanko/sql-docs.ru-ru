---
title: "Промежуточная хранимая процедура (Master Data Services) | Документы Microsoft"
ms.custom: 
ms.date: 04/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
caps.latest.revision: 15
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c2c12151d25b7d563a8a37a7ccfd617bca5cb479
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="staging-stored-procedure-master-data-services"></a>Промежуточная хранимая процедура (службы Master Data Services)
  При запуске промежуточного процесса из [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]используется одна из трех хранимых процедур.  
  
-   stg.udp_\<name > _Leaf  
  
-   stg.udp_\<name > _Consolidated  
  
-   stg.udp_\<name > _Relationship  
  
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
  
  

