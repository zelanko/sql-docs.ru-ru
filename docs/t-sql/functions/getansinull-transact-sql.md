---
title: GETANSINULL (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GETANSINULL
- GETANSINULL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- null values [SQL Server], default
- GETANSINULL function
- default nullability
- database nullability [SQL Server]
ms.assetid: 189399e4-428d-4902-b3a8-94f07fdefc6a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 081425bf857be0a637159304facdcfb1aa625642
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56287832"
---
# <a name="getansinull-transact-sql"></a>GETANSINULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает порядок использования значения NULL для базы данных по умолчанию, действующий в текущем сеансе.  
  
 ![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GETANSINULL ( [ 'database' ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 '*database*'  
 Имя базы данных, для которой возвращается информация о допустимости значений NULL. Аргумент database имеет тип **char** или **nchar**. Если аргумент *database* имеет тип **char**, он неявно преобразуется в **nchar**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
## <a name="remarks"></a>Remarks  
GETANSINULL возвращает 1, если допустимость значений NULL базы данных допускает значения NULL. Это возвращаемое значение также требует, чтобы допустимость значений NULL для столбца или типа данных не была явно определена. По умолчанию ANSI NULL задано значение 1. 
  
 Чтобы включить поведение по умолчанию для ANSI NULL, необходимо задать одно следующих условий.  
  
-   ALTER DATABASE *имя_базы_данных* SET ANSI_NULL_DEFAULT ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET ANSI_NULL_DFLT_OFF OFF  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает допустимость значений NULL, используемую по умолчанию для базы данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT GETANSINULL('AdventureWorks2012')  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ------  
1  

(1 row(s) affected)
 ```  
  
## <a name="see-also"></a>См. также:  
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  
