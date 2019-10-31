---
title: sys. DM _pdw_nodes_exec_query_statistics_xml (Transact-SQL) | Документация Майкрософт
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
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 2b12e1a1400ec2d9d4bb85466671cda446511f24
ms.sourcegitcommit: af6f66cc3603b785a7d2d73d7338961a5c76c793
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2019
ms.locfileid: "73145649"
---
# <a name="dm_pdw_nodes_exec_query_statistics_xml-transact-sql"></a>dm_pdw_nodes_exec_query_statistics_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Возвращает план выполнения запроса для запросов в реальном режиме. Используйте это динамическое административное представление для получения XML-документа Showplan с временной статистикой.

## <a name="table-returned"></a>Таблица возвращена

|Column Name|Тип данных|Description|  
|-----------------|---------------|-----------------|
|node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.|
|session_id|**smallint**|Идентификатор сеанса. Не допускает значения NULL.|
|request_id|**int**|Идентификатор запроса. Не допускает значения NULL.|
|sql_handle|**varbinary (64)**|Токен, однозначно определяющий пакет или хранимую процедуру, частью которой является запрос. Допускает значение NULL.|
|plan_handle|**varbinary (64)**|Токен, однозначно определяющий план выполнения запроса для выполняемого в данный момент пакета. Допускает значение NULL.|
|query_plan|**xml**;|Содержит представление среды выполнения Showplan плана выполнения запроса, указанного в параметре *plan_handle* , содержащем частичную статистику. Представление Showplan имеет формат XML. Для каждого пакета, содержащего, например нерегламентированные инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], вызовы хранимых процедур и вызовы определяемых пользователем функций, формируется один план. Допускает значение NULL.|

## <a name="remarks"></a>Remarks
Те же примечания в [представлении sys. DM _exec_query_statistics_xml](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql?view=sql-server-ver15) применяются.   

## <a name="permissions"></a>Permissions  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  

## <a name="see-also"></a>См. также раздел  
 [Динамические административные представления &#40;хранилища данных SQL и параллельного хранилища данных TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

 ## <a name="next-steps"></a>Следующие шаги
 Дополнительные советы по разработке см. в статье [Общие сведения о разработке хранилища данных SQL](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).

