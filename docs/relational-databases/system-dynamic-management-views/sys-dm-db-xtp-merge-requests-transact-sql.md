---
title: sys.dm_db_xtp_merge_requests (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 02/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: relational-databases
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1224e88-af74-4c99-ae32-d5d2c552a1f5
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e511ba417e4eb58d1ff52b1896a03f8bb5f0722c
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="sysdmdbxtpmergerequests-transact-sql"></a>sys.dm_db_xtp_merge_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]


Отслеживает запросы на слияние базы данных. Запрос на слияние было создано с SQL Server или возможно, запрос создан пользователем с [sys.sp_xtp_merge_checkpoint_files (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql.md).

> [!NOTE]
> Это динамическое административное представление (DMV) sys.dm_db_xtp_merge_requests, существует до Microsoft SQL Server 2014.
> 
> Однако начиная с SQL Server 2016 Данное динамическое административное Представление больше не применяется.

## <a name="columns-in-the-report"></a>Столбцы в отчете

| Имя столбца | Тип данных | Описание |
| :-- | :-- | :-- |
| request_state | tinyint | Состояние запроса на слияние:<br/>0 = запрошен<br/>1 = ожидание<br/>2 = установлен<br/>3 = оставлен |
| request_state_desc | nvarchar(60) | Значения для текущего состояния запроса:<br/><br/>Запрошенный - запрос на слияние существует.<br/>Отложить - слияние обрабатывается.<br/>Установить - слияния будет завершена.<br/>Прервана - слияния не удалось завершить, возможно из-за отсутствия пространства хранения. |
| destination_file_id | GUID | Уникальный идентификатор целевого файла для слияния исходных файлов. |
| lower_bound_tsn | bigint | Минимальная метка времени для целевого файла объединения. Наименьшая метка времени транзакции всех исходных файлов, которые необходимо объединить. |
| upper_bound_tsn | bigint | Максимальная метка времени для целевого файла объединения. Наивысшая метка времени транзакции всех исходных файлов, которые необходимо объединить. |
| collection_tsn | bigint | Метка времени, в которое можно собрать текущую строку.<br/><br/>Строка в состоянии «Установлено» удаляется при обретении параметром checkpoint_tsn значения, численно превышающего значение collection_tsn.<br/><br/>Строка в состоянии «Оставлено» удаляется при обретении параметром checkpoint_tsn значения, которое численно меньше значения collection_tsn. |
| checkpoint_tsn | bigint | Время запуска контрольной точки.<br/><br/>Все операции удаления, выполняемые транзакциями, с меткой времени ниже этой учитываются в новом файле данных. Остальные операции удаления перемещаются в целевой разностный файл. |
| sourcenumber_file_id | GUID | До 16 внутренних идентификаторов файлов, уникальным образом определяющих исходные файлы при слиянии. |

## <a name="permissions"></a>Разрешения

Необходимо разрешение VIEW DATABASE STATE на текущую базу данных.

## <a name="see-also"></a>См. также:

[Таблицы, оптимизированные для памяти динамические административные представления (Transact-SQL)](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)


