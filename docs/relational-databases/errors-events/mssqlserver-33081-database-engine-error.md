---
title: MSSQLSERVER_33081 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 33081 (Database Engine error)
ms.assetid: 839705e7-fa37-4c0d-9f3f-95a9eab98bcf
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 364182de23d57db1665b3fc28b8ecb027e1485ba
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver33081"></a>MSSQLSERVER_33081
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|33081|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SEC_DLL_TRUST_VERIFICATION_FAILED|  
|Текст сообщения|Не удалось загрузить поставщик служб шифрования "%.*ls" из-за недействительной подписи Authenticode или недействительного пути к файлу.  Проверьте наличие других ошибок в предыдущих сообщениях.|  
  
## <a name="explanation"></a>Объяснение  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не смог загрузить поставщик служб шифрования, указанный в сообщении об ошибке. Существует несколько ошибок Win API, которые могут вызвать эту ошибку. Кольцевой буфер содержит имя ошибочного API и код ошибки Windows, возвращенный API. Чтобы получить дополнительные сведения, выполните следующий запрос к представлению sys.dm_os_ring_buffers.  
  
```  
SELECT * FROM sys.dm_os_ring_buffers   
WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
```  
  
## <a name="user-action"></a>Действие пользователя  
Чтобы исследовать эту проблему, выполните поиск кода ошибки Windows в MSDN (http://msdn.microsoft.com/). Устраните ошибку или обратитесь к службу поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] за дополнительными сведениями. Перед обращением в службу поддержки пользователей соберите следующие данные.  
  
-   Журнал ошибок, отображающий ошибку загрузки поставщика служб шифрования.  
  
-   Выход из следующей инструкции:  
  
    ```  
    SELECT * FROM sys.dm_os_ring_buffers   
    WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
    ```  
  
> [!NOTE]  
> Попробуйте сразу собрать данные кольцевого буфера, поскольку они могут быть потеряны при перезагрузке.  
  
