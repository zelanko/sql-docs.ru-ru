---
title: sys.dm_pdw_nodes_exec_query_statistics_xml (Transact-SQL) | Документация Майкрософт
description: Динамическое административное представление, возвращающее план выполнения запросов на поступающие запросы. Используйте это динамическое административное представление для получения XML-документа Showplan с временной статистикой.
ms.custom: ''
ms.date: 10/14/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest
ms.openlocfilehash: 540a5632997c025a98e259e23f87780134649b75
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97482553"
---
# <a name="dm_pdw_nodes_exec_query_statistics_xml-transact-sql"></a>dm_pdw_nodes_exec_query_statistics_xml (Transact-SQL)
[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Возвращает план выполнения запроса для запросов в реальном режиме. Используйте это динамическое административное представление для получения XML-документа Showplan с временной статистикой.

## <a name="table-returned"></a>Таблица возвращена

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|
|node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.|
|session_id|**smallint**|Идентификатор сеанса. Не допускает значения NULL.|
|request_id|**int**|Идентификатор запроса. Не допускает значения NULL.|
|sql_handle|**varbinary (64)**|Токен, однозначно определяющий пакет или хранимую процедуру, частью которой является запрос. Допускает значение NULL.|
|plan_handle|**varbinary (64)**|Токен, однозначно определяющий план выполнения запроса для выполняемого в данный момент пакета. Допускает значение NULL.|
|query_plan|**xml**|Содержит представление среды выполнения Showplan плана выполнения запроса, указанного в *plan_handle* содержащего частичную статистику. Представление Showplan имеет формат XML. Для каждого пакета, содержащего, например нерегламентированные инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], вызовы хранимых процедур и вызовы определяемых пользователем функций, формируется один план. Допускает значение NULL.|

## <a name="remarks"></a>Комментарии
Те же примечания в [sys.dm_exec_query_statistics_xml](./sys-dm-exec-query-statistics-xml-transact-sql.md?view=sql-server-ver15) применяются.   

## <a name="permissions"></a>Разрешения  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  

## <a name="see-also"></a>См. также раздел  
 [Динамические административные представления Azure синапсе Analytics и Параллельное хранилище данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

 ## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные советы по разработке см. в статье [Общие сведения о разработке для Azure синапсе Analytics](/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).