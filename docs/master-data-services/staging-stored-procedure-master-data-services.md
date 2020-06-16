---
title: Промежуточная хранимая процедура
description: Используйте одну из трех хранимых процедур для запуска промежуточного процесса из SQL Server Management Studio в Master Data Services.
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 82b068612f0699cdba3788e4931fb6bdfe8c7e69
ms.sourcegitcommit: 7d6eb09588ff3477cf39a8fd507d537a603bc60d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/16/2020
ms.locfileid: "84796505"
---
# <a name="staging-stored-procedure-master-data-services"></a>Промежуточная хранимая процедура (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  При запуске промежуточного процесса из [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]используется одна из трех хранимых процедур.  
  
-   STG. udp_ \<name> _Leaf  
  
-   STG. udp_ \<name> _Consolidated  
  
-   STG. udp_ \<name> _Relationship  
  
 Где имя — это имя промежуточной таблицы, определенной при создании сущности.  
  
## <a name="staging-process-stored-procedure-parameters"></a>Параметры хранимой процедуры промежуточного процесса  
 В следующей таблице приведены параметры этих хранимых процедур.  
  
|Параметр|Описание|  
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
      @UserName=N'domain\user'  
  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Master Data Services &#40;хранимой процедуры проверки&#41;](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [Просмотр ошибок, возникающих во время помещения на промежуточное хранение (службы Master Data Services)](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)  
  
  
