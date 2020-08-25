---
description: DROP EXTERNAL LANGUAGE (Transact-SQL) — SQL Server
title: DROP EXTERNAL LANGUAGE (Transact-SQL) — SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 08/08/2019
ms.prod: sql
ms.technology: language-extensions
ms.topic: language-reference
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d159d4b61e9fa8a171873d7c1a8f6466452e8fe9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88358460"
---
# <a name="drop-external-language-transact-sql"></a>DROP EXTERNAL LANGUAGE (Transact-SQL)  
[!INCLUDE [SQL Server 2019 and later](../../includes/applies-to-version/sqlserver2019.md)]

Удаляет существующий внешний язык.

## <a name="syntax"></a>Синтаксис

```text
DROP EXTERNAL LANGUAGE <language_name>
```

### <a name="arguments"></a>Аргументы

**language_name**

Языки являются объектами в области базы данных. Имена языков должны быть уникальными в пределах базы данных.

## <a name="permissions"></a>Разрешения

Для удаления языка нужна привилегия ALTER ANY EXTERNAL LANGUAGE. По умолчанию удалить внешний язык может также любой владелец базы данных или владелец объекта.

> [!NOTE]
> Обратите внимание, что перед удалением внешнего языка нужно удалить ссылающиеся на него внешние библиотеки.

### <a name="return-values"></a>Возвращаемые значения

Если инструкция была выполнена успешно, возвращается информационное сообщение.

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="remarks"></a>Remarks

Перед удалением внешнего языка нужно удалить все его внешние библиотеки.

## <a name="examples"></a>Примеры

Создание внешнего языка **Java**:

```sql
CREATE EXTERNAL LANGUAGE Java 
FROM (CONTENT = N'<path-to-zip>', FILE_NAME = 'javaextension.dll');
GO
```

Удаление внешнего языка:

```sql
DROP EXTERNAL LANGUAGE Java;
```

## <a name="see-also"></a>См. также раздел

[CREATE EXTERNAL LANGUAGE (Transact-SQL)](create-external-language-transact-sql.md)  
[ALTER EXTERNAL LANGUAGE (Transact-SQL)](alter-external-language-transact-sql.md)  
[sys.external_languages](../../relational-databases/system-catalog-views/sys-external-languages-transact-sql.md)  
[sys.external_language_files](../../relational-databases/system-catalog-views/sys-external-language-files-transact-sql.md)  
