---
title: "SESSION_ID (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 02/23/2018
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fbc453282e442e9adb5a378c216b2e5a83eb2bb0
ms.sourcegitcommit: f0c5e37c138be5fb2cbb93e9f2ded307665b54ea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/24/2018
---
# <a name="sessionid-transact-sql"></a>SESSION_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Возвращает идентификатор текущего сеанса [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
SESSION_ID ( )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение **nvarchar(32)**.  
  
## <a name="general-remarks"></a>Общие замечания  
 Идентификатор сеанса присваивается каждому соединению пользователя при установке соединения. Он сохраняется в течение всего соединения. По окончании соединения идентификатор сеанса освобождается.  
  
 Идентификатор сеанса начинается с буквенных символов SID. Они чувствительны к регистру и должны начинаться с прописной буквы, если идентификатор сеанса используется в командах [!INCLUDE[DWsql](../../includes/dwsql-md.md)].  
  
 Выполните запрос к представлению [sys.dm_pdw_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) для получения тех же сведений, которые выдает эта функция.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается идентификатор текущего сеанса.  
  
```  
SELECT SESSION_ID();  
```  
  
## <a name="see-also"></a>См. также:  
 [DB_NAME (Transact-SQL)](../../t-sql/functions/db-name-transact-sql.md)   
 [VERSION (Хранилище данных SQL)](../../t-sql/functions/version-transact-sql-configuration-functions.md)
  
  
