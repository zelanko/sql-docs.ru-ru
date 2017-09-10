---
title: "DROP ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/17/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP EXTERNAL LIBRARY
- DROP_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 143e9ac0dbe042ebbb034dff847cfc01ea5a5411
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-external-library-transact-sql"></a>DROP ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

Удаляет существующую библиотеку пакета.

## <a name="syntax"></a>Синтаксис  
```
DROP EXTERNAL LIBRARY library_name  
[ AUTHORIZATION owner_name ];  
```

### <a name="arguments"></a>Аргументы

**library_name**

Указывает имя существующей библиотеки пакета.

Библиотеки областью действия пользователя. То есть имена библиотек, считаются уникальными в контексте определенного пользователя или владелец.

**owner_name**

Указывает имя пользователя или роли, которой принадлежит внешней библиотеки.

Владельцы базы данных могут удалять библиотеки, созданными другими пользователями.

### <a name="return-values"></a>Возвращаемые значения

Информационное сообщение возвращается, если инструкция была успешной.

## <a name="remarks"></a>Замечания

В отличие от других `DROP` инструкций в SQL Server, эта инструкция поддерживает указание предложения authorization необязательно. Это позволяет **dbo** или пользователей в **db_owner** роли для удаления библиотеки пакета, загруженных с обычного пользователя в базе данных.

## <a name="examples"></a>Примеры

Добавьте ggplot2 базы данных:

```sql
CREATE EXTERNAL LIBRARY ggplot2 
FROM 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\ggplot2.zip';
```

Удалите библиотеку ggplot2.

```sql
DROP EXTERNAL LIBRARY ggplot2 <user_name>;
```

## <a name="see-also"></a>См. также:  
[Создание ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL)](create-external-library-transact-sql.md)  
[ALTER ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL)](alter-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  


