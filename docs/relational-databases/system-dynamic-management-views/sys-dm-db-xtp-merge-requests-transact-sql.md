---
title: sys. dm_db_xtp_merge_requests (Transact-SQL) | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68026802"
---
# <a name="sysdm_db_xtp_merge_requests-transact-sql"></a>sys.dm_db_xtp_merge_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

Отслеживает запросы на слияние базы данных. Запрос на слияние мог быть создан SQL Server или запрос был выполнен пользователем с помощью [sys. sp_xtp_merge_checkpoint_files (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql.md).

> [!NOTE]
> Это динамическое административное представление sys. dm_db_xtp_merge_requests существует до Microsoft SQL Server 2014.
> Но начиная с SQL Server 2016 это динамическое административное представление больше не применяется.

## <a name="columns-in-the-report"></a>Столбцы в отчете

| Имя столбца | Тип данных | Description |
| :-- | :-- | :-- |
| request_state | tinyint; | Состояние запроса на слияние:<br/>0 = запрошен<br/>1 = ожидание<br/>2 = установлено<br/>3 = оставлен |
| request_state_desc | nvarchar(60) | Значения для текущего состояния запроса:<br/><br/>Запрошено — существует запрос на слияние.<br/>Ожидание — выполняется обработка слияния.<br/>Установлено — слияние завершено.<br/>Брошено — слияние не удалось завершить, возможно, из-за отсутствия хранилища. |
| destination_file_id | GUID | Уникальный идентификатор целевого файла для слияния исходных файлов. |
| lower_bound_tsn | bigint | Минимальная метка времени для целевого файла объединения. Наименьшая метка времени транзакции всех исходных файлов, которые необходимо объединить. |
| upper_bound_tsn | bigint | Максимальная метка времени для целевого файла объединения. Наивысшая метка времени транзакции всех исходных файлов, которые необходимо объединить. |
| collection_tsn | bigint | Метка времени, в которое можно собрать текущую строку.<br/><br/>Строка в состоянии «Установлено» удаляется при обретении параметром checkpoint_tsn значения, численно превышающего значение collection_tsn.<br/><br/>Строка в состоянии «Оставлено» удаляется при обретении параметром checkpoint_tsn значения, которое численно меньше значения collection_tsn. |
| checkpoint_tsn | bigint | Время запуска контрольной точки.<br/><br/>Все операции удаления, выполняемые транзакциями, с меткой времени ниже этой учитываются в новом файле данных. Остальные операции удаления перемещаются в целевой разностный файл. |
| sourcenumber_file_id | GUID | До 16 внутренних идентификаторов файлов, которые уникально идентифицируют исходные файлы в слиянии. |

## <a name="permissions"></a>Разрешения

Необходимо разрешение VIEW DATABASE STATE на текущую базу данных.

## <a name="see-also"></a>См. также раздел

[Оптимизированные для памяти динамические административные представления таблиц (Transact-SQL)](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)
