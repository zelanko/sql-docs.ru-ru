---
title: "ASSEMBLYPROPERTY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9556834a173302e19358f5333b059d7b4f902519
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="assemblyproperty-transact-sql"></a>ASSEMBLYPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Возвращает данные о свойстве сборки.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
ASSEMBLYPROPERTY('assembly_name', 'property_name')  
```  
  
## <a name="arguments"></a>Аргументы  
*assembly_name*  
Имя сборки.
  
*property_name*  
Имя свойства, о котором будут получены данные. *property_name* может принимать одно из следующих значений.
  
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
В следующем примере предполагается, что сборка `HelloWorld` зарегистрирована в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Дополнительные сведения см. в разделе [Образец Hello World](http://msdn.microsoft.com/library/fed6c358-f5ee-4d4c-9ad6-089778383ba7).
  
```sql
USE AdventureWorks2012;  
GO  
SELECT ASSEMBLYPROPERTY ('HelloWorld' , 'PublicKey');  
```  
  
## <a name="see-also"></a>См. также:
[CREATE ASSEMBLY (Transact-SQL)](../../t-sql/statements/create-assembly-transact-sql.md)  
[DROP ASSEMBLY (Transact-SQL)](../../t-sql/statements/drop-assembly-transact-sql.md)
  
  

