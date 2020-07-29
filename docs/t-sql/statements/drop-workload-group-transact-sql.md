---
title: DROP WORKLOAD GROUP (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 01/10/2020
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_WORKLOAD_GROUP_TSQL
- DROP WORKLOAD GROUP
dev_langs:
- TSQL
helpviewer_keywords:
- DROP WORKLOAD GROUP statement
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azure-sqldw-latest||=azuresqldb-mi-current'
ms.openlocfilehash: d5aa9af5ae45e962ff130d7de18d62417a0b3987
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87111031"
---
# <a name="drop-workload-group-transact-sql"></a>DROP WORKLOAD GROUP (Transact-SQL)

[!INCLUDE[select-product](../../includes/select-product.md)]

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions"

:::row:::
    :::column:::
        **_\* SQL Server \*_** &nbsp;
    :::column-end:::
    :::column:::
        [Управляемый экземпляр Базы данных SQL<br />](drop-workload-group-transact-sql.md?view=azuresqldb-mi-current)
    :::column-end:::
    :::column:::
        [Azure Synapse<br />Analytics](drop-workload-group-transact-sql.md?view=azure-sqldw-latest)
    :::column-end:::
:::row-end:::

&nbsp;

## <a name="sql-server-and-sql-database-managed-instance"></a>SQL Server и управляемый экземпляр базы данных SQL Azure

[!INCLUDE [DROP WORKLOAD GROUP](../../includes/drop-workload-group.md)]
  
::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"

:::row:::
    :::column:::
        [SQL Server](drop-workload-group-transact-sql.md?view=sql-server-2017)
    :::column-end:::
    :::column:::
        **_\* Управляемый экземпляр<br />Базы данных SQL \*_** &nbsp;
    :::column-end:::
    :::column:::
        [Azure Synapse<br />Analytics](drop-workload-group-transact-sql.md?view=azure-sqldw-latest)
    :::column-end:::
:::row-end:::

&nbsp;

##  <a name="sql-server-and-sql-database-managed-instance"></a>SQL Server и управляемый экземпляр базы данных SQL Azure

[!INCLUDE [DROP WORKLOAD GROUP](../../includes/drop-workload-group.md)]

::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

:::row:::
    :::column:::
        [SQL Server](drop-workload-group-transact-sql.md?view=sql-server-2017)
    :::column-end:::
    :::column:::
        [Управляемый экземпляр Базы данных SQL<br />](drop-workload-group-transact-sql.md?view=azuresqldb-mi-current)
    :::column-end:::
    :::column:::
        **_\* Azure Synapse<br />Analytics \*_** &nbsp;
    :::column-end:::
:::row-end:::

&nbsp;

## <a name="azure-synapse-analytics"></a>Azure Synapse Analytics 

Удаляет группу рабочей нагрузки.  После выполнения инструкции вступают в действие параметры.

![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

## <a name="syntax"></a>Синтаксис

```syntaxsql
DROP WORKLOAD GROUP group_name  
```

## <a name="arguments"></a>Аргументы

*group_name*  
Имя существующей, определяемой пользователем группы рабочей нагрузки.

## <a name="remarks"></a>Remarks

Группа рабочей нагрузки не может быть удалена, если для нее существуют классификаторы.  Удалите классификаторы перед удалением группы рабочей нагрузки.  При наличии активных запросов, использующих ресурсы из группы рабочей нагрузки, инструкция DROP для рабочей нагрузки блокируется.

## <a name="examples"></a>Примеры

Используйте следующий пример кода, чтобы определить, какие классификаторы необходимо удалить, прежде чем можно будет удалить группу рабочей нагрузки.

```sql
SELECT c.name as classifier_name
      ,'DROP WORKLOAD CLASSIFIER '+c.name as drop_command
  FROM sys.workload_management_workload_classifiers c
  JOIN sys.workload_management_workload_groups g
    ON c.group_name = g.name
  WHERE g.name = 'wgXYZ' --change the filter to the workload being dropped
```

## <a name="permissions"></a>Разрешения

Требуется разрешение CONTROL DATABASE

## <a name="see-also"></a>См. также раздел

- [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md)
- [ALTER WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/alter-workload-group-transact-sql.md)
- [sys.workload_management_workload_groups](../../relational-databases/system-catalog-views/sys-workload-management-workload-groups-transact-sql.md)
- [sys.dm_workload_management_workload_groups_stats](../../relational-databases/system-dynamic-management-views/sys-dm-workload-management-workload-group-stats-transact-sql.md)
- [Краткое руководство. Настройка изоляции рабочих нагрузок с помощью T-SQL](/azure/sql-data-warehouse/quickstart-configure-workload-isolation-tsql)

::: moniker-end
