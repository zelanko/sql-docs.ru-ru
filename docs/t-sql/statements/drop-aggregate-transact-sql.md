---
title: DROP AGGREGATE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cc0242e401902bc661e3e60ac0db12b94710f9a1
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51702872"
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
 **Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](https://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
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
  
  
