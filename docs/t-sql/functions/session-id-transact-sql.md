---
title: "SESSION_ID (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2a0d500a-f6c8-490f-9abd-3ae824986404
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9089c21109d6eedb1cdae0082e1530e8d77d9dde
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="sessionid-transact-sql"></a>SESSION_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Возвращает идентификатор текущего [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] сеанса.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
SESSION_ID ( )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **nvarchar(32)** значение.  
  
## <a name="general-remarks"></a>Общие замечания  
 Идентификатор сеанса назначается каждому соединению пользователя при установке соединения. Он сохраняется в течение всего соединения. По окончании соединения освобождается идентификатор сеанса.  
  
 Идентификатор сеанса начинается с буквы «SID». Они чувствительны к регистру и должно быть прописной буквой, если идентификатор сеанса используется в [!INCLUDE[DWsql](../../includes/dwsql-md.md)] команд.  
  
 Выполнить запрос к представлению [sys.dm_pdw_exec_sessions](http://msdn.microsoft.com/en-us/5b656c55-427f-4306-8bd9-9d7987c203d9) для получения те же сведения о данной функции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается идентификатор текущего сеанса.  
  
```  
SELECT SESSION_ID();  
```  
  
## <a name="see-also"></a>См. также:  
 [Db_name &#40; Transact-SQL &#41;](../../t-sql/functions/db-name-transact-sql.md)   
 [ВЕРСИИ &#40; Хранилище данных SQL &#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)
  
  

