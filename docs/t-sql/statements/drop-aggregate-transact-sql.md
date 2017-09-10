---
title: "DROP AGGREGATE (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_AGGREGATE_TSQL
- DROP AGGREGATE
dev_langs:
- TSQL
helpviewer_keywords:
- aggregate functions [SQL Server], removing
- removing user-defined functions
- dropping user-defined functions
- user-defined functions [CLR integration]
- deleting user-defined functions
- DROP AGGREGATE statement
ms.assetid: 84ffc4e7-c451-4f1f-9a67-7fc3a120e53f
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a9fcab3dc576f15110bed8c1c82271731f326280
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-aggregate-transact-sql"></a>DROP AGGREGATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет пользовательскую агрегатную функцию из текущей базы данных. Определяемые пользователем статистические функции создаются с помощью [CREATE AGGREGATE](../../t-sql/statements/create-aggregate-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP AGGREGATE [ IF EXISTS ] [ schema_name . ] aggregate_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *ЕСЛИ СУЩЕСТВУЕТ*  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условно производится удаление статистической функции только в том случае, если он уже существует.  
  
 *schema_name*  
 Имя схемы, которой принадлежит определяемая пользователем агрегатная функция.  
  
 *aggregate_name*  
 Имя пользовательской агрегатной функции, которую необходимо удалить.  
  
## <a name="remarks"></a>Замечания  
 Инструкция DROP AGGREGATE не выполняется, если имеются какие-либо представления, функции или хранимые процедуры, созданные с привязкой схемы, которые ссылаются на удаляемую пользовательскую агрегатную функцию.  
  
## <a name="permissions"></a>Permissions  
 Для выполнения инструкции DROP AGGREGATE пользователь, как минимум, должен иметь разрешение ALTER на схему, которой принадлежит пользовательская статистическая функция, либо разрешение CONTROL на эту функцию.  
  
## <a name="examples"></a>Примеры  
 В данном примере производится удаление статистической функции `Concatenate`.  
  
```  
DROP AGGREGATE dbo.Concatenate;  
```  
  
## <a name="see-also"></a>См. также:  
 [СОЗДАТЬ агрегат &#40; Transact-SQL &#41;](../../t-sql/statements/create-aggregate-transact-sql.md)   
 [Создание пользовательских агрегатных функций](../../relational-databases/user-defined-functions/create-user-defined-aggregates.md)  
  
  

