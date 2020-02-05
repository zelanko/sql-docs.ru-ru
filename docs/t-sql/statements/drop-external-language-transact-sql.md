---
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
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3767bec1807b68df3eb3f82287a5c871d653a286
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68892983"
---
# <a name="drop-external-library-transact-sql"></a>DROP EXTERNAL LIBRARY (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

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
