---
title: DROP MESSAGE TYPE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_MESSAGE_TYPE_TSQL
- DROP MESSAGE TYPE
dev_langs:
- TSQL
helpviewer_keywords:
- message types [Service Broker], removing
- deleting message types
- dropping message types
- DROP MESSAGE TYPE statement
- removing message types
ms.assetid: 805e8ad5-8a93-49f0-88e5-e6fca8814dd5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 48c1a96998adf9fddd8ffd8da0e6f6711b9277b0
ms.sourcegitcommit: a97d551b252b76a33606348082068ebd6f2c4c8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70745315"
---
# <a name="drop-message-type-transact-sql"></a>DROP MESSAGE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Удаляет существующий тип сообщений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP MESSAGE TYPE message_type_name  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *message_type_name*  
 Название удаляемого типа сообщений. Не могут быть указаны имена сервера, базы данных и схемы.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешением на удаление типа сообщений обладает владелец типа сообщений, члены предопределенной роли базы данных db_ddladmin или db_owner и члены предопределенной роли сервера sysadmin.  
  
## <a name="remarks"></a>Remarks  
 Можно удалить тип сообщений, если хотя бы один контракт ссылается на этот тип сообщений.  
  
## <a name="examples"></a>Примеры  
 В следующем примере производится удаление из базы данных сообщений типа `//Adventure-Works.com/Expenses/SubmitExpense`.  
  
```  
DROP MESSAGE TYPE [//Adventure-Works.com/Expenses/SubmitExpense] ;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER MESSAGE TYPE (Transact-SQL)](../../t-sql/statements/alter-message-type-transact-sql.md)   
 [CREATE MESSAGE TYPE (Transact-SQL)](../../t-sql/statements/create-message-type-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
