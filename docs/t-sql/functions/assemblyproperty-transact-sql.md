---
title: ASSEMBLYPROPERTY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ASSEMBLYPROPERTY_TSQL
- ASSEMBLYPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- ASSEMBLYPROPERTY statement
- assemblies [CLR integration], properties
ms.assetid: cf03d1b1-724c-48bf-a8df-3fe2586b150a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 50fd500a3ce7248b60e423df662b5d9eeda2cef5
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87113136"
---
# <a name="assemblyproperty-transact-sql"></a>ASSEMBLYPROPERTY (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Эта функция возвращает данные о свойстве сборки.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
ASSEMBLYPROPERTY('assembly_name', 'property_name')  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
*assembly_name*  
Имя сборки.
  
*property_name*  
Имя свойства, о котором будут получены данные. *property_name* может иметь одно из следующих значений:
  
|Значение|Description|  
|---|---|
|**CultureInfo**|Локаль сборки.|  
|**PublicKey**|Открытый ключ или токен открытого ключа сборки.|  
|**MvID**|Полный идентификационный номер версии сборки, формируемый компилятором.|  
|**VersionMajor**|Первая из четырех частей идентификационного номера версии, содержащая номер основной версии.|  
|**VersionMinor**|Вторая из четырех частей идентификационного номера версии, содержащая номер дополнительной версии.|  
|**VersionBuild**|Третья из четырех частей идентификационного номера версии, содержащая номер сборки.|  
|**VersionRevision**|Последняя из четырех частей идентификационного номера версии, содержащая номер редакции.|  
|**SimpleName**|Простое имя сборки.|  
|**Архитектура**|Архитектура процессора, для которого предназначена сборка.|  
|**CLRName**|Каноническая строка, кодирующая простое имя, номер версии, культуру, открытый ключ и архитектуру сборки. Данное значение однозначно идентифицирует сборку на стороне среды CLR.|  
  
## <a name="return-type"></a>Возвращаемый тип
**sql_variant**
  
## <a name="examples"></a>Примеры  
В этом примере предполагается, что сборка `HelloWorld` зарегистрирована в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Дополнительные сведения см. в разделе [Образец "Hello World"](https://msdn.microsoft.com/library/fed6c358-f5ee-4d4c-9ad6-089778383ba7).
  
```sql
USE AdventureWorks2012;  
GO  
SELECT ASSEMBLYPROPERTY ('HelloWorld' , 'PublicKey');  
```  
  
## <a name="see-also"></a>См. также раздел
[CREATE ASSEMBLY (Transact-SQL)](../../t-sql/statements/create-assembly-transact-sql.md)  
[DROP ASSEMBLY (Transact-SQL)](../../t-sql/statements/drop-assembly-transact-sql.md)
  
  
