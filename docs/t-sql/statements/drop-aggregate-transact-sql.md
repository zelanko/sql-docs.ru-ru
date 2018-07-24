---
title: DROP AGGREGATE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: a0abb9e26fa1c12aee35ed174ca4cfb43073fa41
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38035292"
---
# <a name="drop-aggregate-transact-sql"></a>DROP AGGREGATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет пользовательскую агрегатную функцию из текущей базы данных. Определяемые пользователем агрегатные функции создаются при помощи инструкции [CREATE AGGREGATE](../../t-sql/statements/create-aggregate-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP AGGREGATE [ IF EXISTS ] [ schema_name . ] aggregate_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *IF EXISTS*  
 **Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условное удаление агрегатной функции только в том случае, если она уже существует.  
  
 *schema_name*  
 Имя схемы, которой принадлежит определяемая пользователем агрегатная функция.  
  
 *aggregate_name*  
 Имя пользовательской агрегатной функции, которую необходимо удалить.  
  
## <a name="remarks"></a>Remarks  
 Инструкция DROP AGGREGATE не выполняется, если имеются какие-либо представления, функции или хранимые процедуры, созданные с привязкой схемы, которые ссылаются на удаляемую пользовательскую агрегатную функцию.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения инструкции DROP AGGREGATE пользователь, как минимум, должен иметь разрешение ALTER на схему, которой принадлежит пользовательская статистическая функция, либо разрешение CONTROL на эту функцию.  
  
## <a name="examples"></a>Примеры  
 В данном примере производится удаление статистической функции `Concatenate`.  
  
```  
DROP AGGREGATE dbo.Concatenate;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE AGGREGATE (Transact-SQL)](../../t-sql/statements/create-aggregate-transact-sql.md)   
 [Создание пользовательских агрегатных функций](../../relational-databases/user-defined-functions/create-user-defined-aggregates.md)  
  
  
