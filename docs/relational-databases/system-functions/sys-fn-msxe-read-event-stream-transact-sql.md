---
title: sys.fn_MSxe_read_event_stream (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_MSxe_read_event_stream_TSQL
- sys.fn_MSxe_read_event_stream_TSQL
- sys.fn_MSxe_read_event_stream
- fn_MSxe_read_event_stream
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_MSxe_read_event_stream
- fn_MSxe_read_event_stream
ms.assetid: 5edb1162-625a-41e0-8ec9-1edc8ab9a74a
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 587180830491c10b6dc09a2af8d28718bf612e87
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752202"
---
# <a name="sysfnmsxereadeventstream-transact-sql"></a>sys.fn_MSxe_read_event_stream (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Расширенные события предоставляют функцию с табличным значением (TVF) для внутреннего использования пользовательским интерфейсом расширенных событий. Таблица не предоставляет данные, пригодные для использования клиентом.  
  
 Для просмотра данных о событиях используйте один из следующих методов:  
  
-   Пользовательский интерфейс нового сеанса расширенных событий.  
  
-   Возвращающая табличное значение функция fn_xe_file_target_read_file. Дополнительные сведения см. в разделе [sys.fn_xe_file_target_read_file (Transact-SQL)](../../relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql.md).  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_MSxe_read_event_stream ( session_name)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Session_name*  
 Имя сеанса, выполняемого на сервере.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|Тип|**Целое число (4)**|Тип события. Не допускает значение NULL.|  
|.|**Изображение (16)**|Данные образа события. Допускает значение NULL.|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления расширенных событий](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)   
 [Представления каталога расширенных событий (Transact-SQL)](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
