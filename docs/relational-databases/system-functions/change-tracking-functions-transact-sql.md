---
title: Функции Отслеживание изменений (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], change tracking
- change tracking [SQL Server], functions
ms.assetid: 04eb53c4-8b69-414e-9696-185d227fea35
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 08a9d5907c93b020f45ec8405361626266ec1300
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85734418"
---
# <a name="change-tracking-functions-transact-sql"></a>Функции отслеживания изменений (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Система отслеживания изменений в данных регистрирует действия по вставке, обновлению и удалению, применяемые к отслеживаемым таблицам, сохраняя подробности операций изменения в легкообрабатываемом реляционном формате. Следующими функциями возвращаются сведения об изменениях.  
  
|Функция|Описание|  
|--------------|-----------------|  
|[CHANGETABLE (ИЗМЕНЕНИЯ)](../../relational-databases/system-functions/changetable-transact-sql.md)|Возвращает данные отслеживания изменений для всех изменений в таблице, произведенных после указанной версии.|  
|[CHANGETABLE (ВЕРСИЯ)](../../relational-databases/system-functions/changetable-transact-sql.md)|Возвращает информацию о последнем изменении указанной строки.|  
|[CHANGE_TRACKING_MIN_VALID_VERSION ()](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)|Возвращает минимальную версию, которая является допустимой для использования при получении сведений об отслеживании изменений из указанной таблицы при использовании функции [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md) .|  
|[CHANGE_TRACKING_CURRENT_VERSION](../../relational-databases/system-functions/change-tracking-current-version-transact-sql.md)|Получает версию, связанную с последней выполненной транзакцией. Эту версию можно использовать в следующий раз при перечислении изменений с помощью функции CHANGETABLE.|  
|[CHANGE_TRACKING_IS_COLUMN_IN_MASK](../../relational-databases/system-functions/change-tracking-is-column-in-mask-transact-sql.md)|Интерпретирует значение SYS_CHANGE_COLUMNS, возвращаемое функцией CHANGETABLE (CHANGEs...).|  
|[WITH CHANGE_TRACKING_CONTEXT](../../relational-databases/system-functions/with-change-tracking-context-transact-sql.md)|Активирует спецификацию изменения контекста, например идентификатор инициатора, когда приложение изменяет данные.|  
  
## <a name="see-also"></a>См. также  
 [Отслеживание измененных данных (SQL Server)](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
