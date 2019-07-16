---
title: sys.dm_db_xtp_merge_requests (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 02/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: c1224e88-af74-4c99-ae32-d5d2c552a1f5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f522fde05ce951575d3e02b3cdc4d3336056bd4e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68026802"
---
# <a name="sysdmdbxtpmergerequests-transact-sql"></a>sys.dm_db_xtp_merge_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

Отслеживает запросы на слияние базы данных. Запрос на слияние мог быть создан по SQL Server или запроса могут выполняться пользователем, имеющим [sys.sp_xtp_merge_checkpoint_files (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql.md).

> [!NOTE]
> Это динамическое административное представление (DMV), существует sys.dm_db_xtp_merge_requests, до выпуска Microsoft SQL Server 2014.
> Но начиная с SQL Server 2016 это динамическое административное Представление больше не применяется.

## <a name="columns-in-the-report"></a>Столбцы в отчете

| Имя столбца | Тип данных | Описание |
| :-- | :-- | :-- |
| request_state | tinyint | Состояние запроса на слияние:<br/>0 = запрошен<br/>1 = ожидание<br/>2 = установлен<br/>3 = оставлен |
| request_state_desc | nvarchar(60) | Значения для текущего состояния запроса:<br/><br/>Запрошенный - запрос на слияние существует.<br/>Ожидающие - слияние обрабатывается.<br/>Установлен - слияния завершена.<br/>Прерван - слияния не удалось завершить, возможно из-за отсутствия пространства хранения. |
| destination_file_id | GUID | Уникальный идентификатор целевого файла для слияния исходных файлов. |
| lower_bound_tsn | BIGINT | Минимальная метка времени для целевого файла объединения. Наименьшая метка времени транзакции всех исходных файлов, которые необходимо объединить. |
| upper_bound_tsn | BIGINT | Максимальная метка времени для целевого файла объединения. Наивысшая метка времени транзакции всех исходных файлов, которые необходимо объединить. |
| collection_tsn | BIGINT | Метка времени, в которое можно собрать текущую строку.<br/><br/>Строка в состоянии «Установлено» удаляется при обретении параметром checkpoint_tsn значения, численно превышающего значение collection_tsn.<br/><br/>Строка в состоянии «Оставлено» удаляется при обретении параметром checkpoint_tsn значения, которое численно меньше значения collection_tsn. |
| checkpoint_tsn | BIGINT | Время запуска контрольной точки.<br/><br/>Все операции удаления, выполняемые транзакциями, с меткой времени ниже этой учитываются в новом файле данных. Остальные операции удаления перемещаются в целевой разностный файл. |
| sourcenumber_file_id | GUID | До 16 внутренних идентификаторов файлов, которые однозначно определяют исходных файлов слияния. |

## <a name="permissions"></a>Разрешения

Необходимо разрешение VIEW DATABASE STATE на текущую базу данных.

## <a name="see-also"></a>См. также

[Таблица, оптимизированная для памяти динамические административные представления (Transact-SQL)](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)
