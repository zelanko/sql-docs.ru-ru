---
title: "DROP EXTERNAL LIBRARY (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 08/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: 
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
manager: craigg
ms.openlocfilehash: 8c45da28bf795fca50454fde21eb7d2c3c798296
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="drop-external-library-transact-sql"></a>DROP EXTERNAL LIBRARY (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Удаляет существующую библиотеку пакета.

## <a name="syntax"></a>Синтаксис  

```
DROP EXTERNAL LIBRARY library_name  
[ AUTHORIZATION owner_name ];  
```

### <a name="arguments"></a>Аргументы

**library_name**

Указывает имя существующей библиотеки пакетов.

Область действия библиотек ограничивается пользователем. То есть имена библиотек считаются уникальными в контексте определенного пользователя или владельца.

**owner_name**

Указывает имя пользователя или роли, которой принадлежит внешняя библиотека.

Владельцы базы данных могут удалять библиотеки, созданные другими пользователями.

### <a name="return-values"></a>Возвращаемые значения

Если инструкция была выполнена успешно, возвращается информационное сообщение.

## <a name="remarks"></a>Remarks

В отличие от других инструкций `DROP` в SQL Server, эта инструкция поддерживает указание необязательного предложения авторизации. Это позволяет **dbo** или пользователям роли **db_owner** удалять пакет библиотеки, отправленный обычным пользователем в базе данных.

## <a name="examples"></a>Примеры

Добавление пользовательского пакета R `customPackage` в базу данных:

```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM 'C:\Users\Username\CustomPackages\customPackage.zip';
```

Удалите библиотеку `customPackage`.

```sql
DROP EXTERNAL LIBRARY customPackage <user_name>;
```

## <a name="see-also"></a>См. также раздел  
[CREATE EXTERNAL LIBRARY (Transact-SQL)](create-external-library-transact-sql.md)  
[ALTER EXTERNAL LIBRARY (Transact-SQL)](alter-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  

