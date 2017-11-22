---
title: "MSSQLSERVER_1793 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 808db1d0-acc1-41d0-9287-8a5455001a02
caps.latest.revision: "6"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e55735177ed8f7afe1177aa9d32255d8f19be3fe
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver1793"></a>MSSQLSERVER_1793
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1793|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|FILESTREAM_BASEDATA_NEED_SAME_PARTITION|  
|Текст сообщения|Не удается удалить «%.*ls», поскольку для данных FILESTREAM не указана схема секционирования.|  
  
## <a name="explanation"></a>Объяснение  
Это сообщение возникает при попытке удалить кластеризованный индекс для таблицы, которая содержит данные FILESTREAM, указав предложение **MOVE TO** для базовых данных, но не указав предложение **FILESTREAM_ON** для данных FILESTREAM.  
  
## <a name="user-action"></a>Действие пользователя  
При удалении кластеризованного индекса для таблицы, которая содержит данные FILESTREAM, используйте один из следующих вариантов.  
  
-   Укажите оба предложения: **MOVE TO** для базовых данных и **FILESTREAM_ON** для данных FILESTREAM.  
  
-   Не указывайте ни одно из предложений **MOVE TO** для базовых данных или **FILESTREAM_ON** для данных FILESTREAM.  
  
Следующий пример заканчивается ошибкой, потому что схема секционирования указана для базовых данных, но не указана для данных FILESTREAM.  
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY] )  
GO  
```  
  
Следующий пример завершается успешно, так как для базовых данных указано предложение **MOVE TO**, а для данных FILESTREAM — предложение **FILESTREAM_ON**.  
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY], filestream_on 'default' )  
GO  
```  
  
Следующий пример также завершается успешно, так как не указано ни одно из предложений: **MOVE TO** для базовых данных или **FILESTREAM_ON** для данных FILESTREAM.  
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF )  
GO  
```  
  
