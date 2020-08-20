---
description: SESSION_ID (Transact-SQL)
title: SESSION_ID (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 02/23/2018
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
author: VanMSFT
ms.author: vanto
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b32c82b37e56b61a2395201937b13f47eb08f774
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88467896"
---
# <a name="session_id-transact-sql"></a>SESSION_ID (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Возвращает идентификатор текущего сеанса [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
  
## <a name="see-also"></a>См. также  
 [DB_NAME (Transact-SQL)](../../t-sql/functions/db-name-transact-sql.md)   
 [VERSION (Хранилище данных SQL)](../../t-sql/functions/version-transact-sql-configuration-functions.md)
  
  
