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
ms.openlocfilehash: f0f50ecd1b6cb74367512822b0257094aa3e3d5b
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81636401"
---
# <a name="drop-workload-group-transact-sql"></a>DROP WORKLOAD GROUP (Transact-SQL)

## <a name="click-a-product"></a>Выберите продукт!

В следующей строке щелкните имя продукта, который вас интересует. На этой веб-странице отобразится другой контент, относящийся к выбранному продукту.

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current||=sqlallproducts-allversions"

> |||||
> |---|---|---|---|
> |**_\* SQL Server \*_** &nbsp;|[Управляемый экземпляр Базы данных SQL<br />](drop-workload-group-transact-sql.md?view=azuresqldb-mi-current)|[Azure Synapse<br />Analytics](drop-workload-group-transact-sql.md?view=azure-sqldw-latest)|

&nbsp;

## <a name="sql-server-and-sql-database-managed-instance"></a>SQL Server и управляемый экземпляр базы данных SQL Azure

Удаляет существующую, определяемую пользователем группу рабочей нагрузки регулятора ресурсов.

![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

## <a name="syntax"></a>Синтаксис

```syntaxsql
DROP WORKLOAD GROUP group_name
[;]
```

## <a name="arguments"></a>Аргументы

*group_name* — имя существующей определяемой пользователем группы рабочей нагрузки.

## <a name="remarks"></a>Remarks

Использование инструкции DROP WORKLOAD GROUP не допускается для внутренней группы или группы по умолчанию регулятора ресурсов.

При выполнении инструкций DDL рекомендуется иметь представление о состояниях регулятора ресурсов. Дополнительные сведения см. в разделе [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) (Регулятор ресурсов).

Если группа рабочей нагрузки содержит активные сеансы, удаление или перемещение этой группы в другой пул ресурсов завершится неудачно при вызове инструкции ALTER RESOURCE GOVERNOR RECONFIGURE для применения изменения. Во избежание этой проблемы можно предпринять одно из следующих действий.

- Подождать, пока все сеансы затронутых групп завершатся, и заново выполнить инструкцию ALTER RESOURCE GOVERNOR RECONFIGURE.

- Явно остановить сеанс в затронутой группе, используя команду KILL, и затем заново выполнить инструкцию ALTER RESOURCE GOVERNOR RECONFIGURE.

- Перезапустите сервер. После завершения процесса перезапуска удаленная группа не будет создана, а перемещенная группа будет использовать новое назначение пула ресурсов.

- Если при выполнении сценария с инструкцией DROP WORKLOAD GROUP решено не останавливать сеанс явно для применения изменений, то можно создать заново группу, используя то же имя для нее, которое она имела до объявления оператора DROP, и потом переместить группу в исходный пул ресурсов. Чтобы применить изменения, выполните инструкцию ALTER RESOURCE GOVERNOR RECONFIGURE.

## <a name="permissions"></a>Разрешения

Необходимо разрешение CONTROL SERVER.

## <a name="examples"></a>Примеры

В следующем примере удаляется группа рабочей нагрузки с именем `adhoc`.

```
DROP WORKLOAD GROUP adhoc;
GO
ALTER RESOURCE GOVERNOR RECONFIGURE;
GO
```

## <a name="see-also"></a>См. также:

- [Регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)
- [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md)  
- [ALTER WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/alter-workload-group-transact-sql.md)
- [CREATE RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-resource-pool-transact-sql.md)
- [ALTER RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-resource-pool-transact-sql.md)
- [DROP RESOURCE POOL (Transact-SQL)](../../t-sql/statements/drop-resource-pool-transact-sql.md)
- [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

> ||||
> |---|---|---|
> |[SQL Server](drop-workload-group-transact-sql.md?view=sql-server-2017)||[Управляемый экземпляр Базы данных SQL<br />](drop-workload-group-transact-sql.md?view=azuresqldb-mi-current)||**_\* Azure Synapse<br />Analytics \*_** &nbsp;||||

&nbsp;

## <a name="azure-synapse-analytics-preview"></a>Azure Synapse Analytics (предварительная версия)

Удаляет группу рабочей нагрузки.  После выполнения инструкции вступают в действие параметры.

![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

## <a name="syntax"></a>Синтаксис

```
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

[CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md)

::: moniker-end
