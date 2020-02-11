---
title: sys. database_event_session_targets (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 38d775ee-1fe1-4820-88c6-02b2f875a66b
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7e736adef1648785ec0d037688c340f31a0e1bda
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915102"
---
# <a name="sysdatabase_event_session_targets-azure-sql-database"></a>sys.database_event_session_targets (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает строку для каждой цели события для сеанса событий.  
  
||  
|-|  
|**Применимо к**версии [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 12 и всем более поздним версиям.|  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|Идентификатор сеанса событий. Не допускает значение NULL.|  
|target_id|**int**|Идентификатор цели. Идентификатор уникален внутри объекта сеанса событий. Не допускает значение NULL.|  
|name|**имеет sysname**|Имя цели события. Не допускает значение NULL.|  
|Пакет|**имеет sysname**|Имя пакета событий, который содержит цель события. Не допускает значение NULL.|  
|module|**имеет sysname**|Имя модуля, который содержит цель события. Не допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE на сервере.  
  
## <a name="remarks"></a>Remarks  
 Это представление имеет следующее количество элементов связей.  
  
||||  
|-|-|-|  
|С|Кому|Связь|  
|sys. database_event_session_targets. event_session_id|sys. database_event_sessions. event_session_id|Многие к одному|  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
