---
title: DROP EXTERNAL LIBRARY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/05/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP EXTERNAL LIBRARY
- DROP_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP EXTERNAL LIBRARY
author: HeidiSteen
ms.author: heidist
manager: cgronlund
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: b28876a3e6724e680d2d1e92ba47704afbd14d14
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38022652"
---
# <a name="drop-external-library-transact-sql"></a>DROP EXTERNAL LIBRARY (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Удаляет существующую библиотеку пакета. Библиотеки пакетов используются поддерживаемыми внешними средами выполнения, например R или Python.

## <a name="syntax"></a>Синтаксис

```sql
DROP EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ];
```

### <a name="arguments"></a>Аргументы

**library_name**

Указывает имя существующей библиотеки пакетов.

Область действия библиотек ограничивается пользователем. Имена библиотек должны быть уникальными в контексте определенного пользователя или владельца.

**owner_name**

Указывает имя пользователя или роли, которой принадлежит внешняя библиотека.

Владельцы базы данных могут удалять библиотеки, созданные другими пользователями.

## <a name="permissions"></a>Разрешения

Для удаления библиотеки необходима привилегия ALTER ANY EXTERNAL LIBRARY. По умолчанию удалить внешнюю библиотеку может также любой владелец базы данных или владелец объекта.

### <a name="return-values"></a>Возвращаемые значения

Если инструкция была выполнена успешно, возвращается информационное сообщение.

## <a name="remarks"></a>Remarks

В отличие от других инструкций `DROP` в SQL Server, эта инструкция поддерживает указание необязательного предложения авторизации. Это позволяет **dbo** или пользователям роли **db_owner** удалять пакет библиотеки, отправленный обычным пользователем в базе данных.

## <a name="examples"></a>Примеры

Добавление пользовательского пакета R `customPackage` в базу данных.

```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM (CONTENT = 'C:\temp\customPackage_v1.1.zip')
WITH (LANGUAGE = 'R');
GO
```

Удалите библиотеку `customPackage`.

```sql
DROP EXTERNAL LIBRARY customPackage;
```

## <a name="see-also"></a>См. также раздел

[CREATE EXTERNAL LIBRARY (Transact-SQL)](create-external-library-transact-sql.md)  
[ALTER EXTERNAL LIBRARY (Transact-SQL)](alter-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  

