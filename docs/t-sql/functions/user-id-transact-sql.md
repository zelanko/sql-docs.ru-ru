---
title: "Функция USER_ID (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- USER_ID
- USER_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- USER_ID function
- identification numbers [SQL Server]
- IDs [SQL Server], databases
- users [SQL Server], database ID numbers
- database IDs [SQL Server]
- identification numbers [SQL Server], databases
ms.assetid: 67fd29bc-eda9-4d4d-b148-5d3659181a43
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c8c8e07d6d58b6615ff5e4528556bf08e0b72c13
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="userid-transact-sql"></a>USER_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает идентификационный номер для пользователя базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Используйте [DATABASE_PRINCIPAL_ID](../../t-sql/functions/database-principal-id-transact-sql.md) вместо него.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
USER_ID ( [ 'user' ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *пользователь*  
 Используемое имя пользователя. *пользователь* — **nchar**. Если **char** значение указано, оно неявно преобразуется в **nchar**. Необходимо поставить скобки.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="remarks"></a>Замечания  
 Когда *пользователя* — этот параметр опущен, подразумевается текущий пользователь. Если параметр содержит слово NULL, то возвращается NULL. При вызове USER_ID после EXECUTE AS, USER_ID возвращает идентификатор олицетворенного контекста.  
  
 Если участник Windows, не сопоставленный с указанным пользователем базы данных, получает доступ к базе данных через участие в группе, функция USER_ID возвращает значение 0 (идентификатор пользователя public). Если такой участник создает объект без указания схемы, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создаст неявного пользователя и схему, сопоставленные с участником Windows. Пользователь, созданный таким образом, не может быть использован для подключения к базе данных. Вызовы функции USER_ID участником Windows, сопоставленным с неявным пользователем, возвратят идентификатор неявного пользователя.  
  
 Функцию USER_ID можно использовать в списке выбора, в предложении WHERE и в любом месте, где разрешается выражение. Дополнительные сведения см. в разделе [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается идентификатор пользователя `AdventureWorks2012` базы данных `Harold`.  
  
```  
USE AdventureWorks2012;  
SELECT USER_ID('Harold');  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Имя_пользователя &#40; Transact-SQL &#41;](../../t-sql/functions/user-name-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [DATABASE_PRINCIPAL_ID &#40; Transact-SQL &#41;](../../t-sql/functions/database-principal-id-transact-sql.md)   
 [Функции безопасности &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
