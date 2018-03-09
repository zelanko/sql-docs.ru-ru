---
title: "CONTEXT_INFO (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
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
- CONTEXT_INFO_TSQL
- CONTEXT_INFO
dev_langs:
- TSQL
helpviewer_keywords:
- CONTEXT_INFO function
- Multiple Active Result Sets
- context information [SQL Server]
- MARS [SQL Server]
- session context information [SQL Server]
ms.assetid: 571320f5-7228-4b0e-9d01-ab732d2d1eab
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a647bc7ced2188a45183200f08400f5507f7b328
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="contextinfo--transact-sql"></a>CONTEXT_INFO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает **context_info** значение, которое было задано для текущего сеанса или пакета с помощью [SET CONTEXT_INFO](../../t-sql/statements/set-context-info-transact-sql.md) инструкции.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CONTEXT_INFO()  
```  
  
## <a name="return-value"></a>Возвращаемое значение
Значение **context_info**.
  
Если **context_info** не было задано:
-   В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение NULL.  
-   В [!INCLUDE[ssSDS](../../includes/sssds-md.md)] возвращает уникальный идентификатор GUID конкретного сеанса.  
  
## <a name="remarks"></a>Замечания  
Режим MARS позволяет приложениям запускать несколько пакетов или запросов одновременно, используя одно и то же соединение. Если один из пакетов соединения с режимом MARS запустит SET CONTEXT_INFO, следующее контекстное значение возвращается функцией CONTEXT_INFO, когда она запускается в том же пакете, что и инструкция SET. Новое значение не возвращается функцией CONTEXT_INFO, запущенной в одном или нескольких других пакетах соединения, если они не запущены после пакета, выполнившего инструкцию SET.
  
## <a name="permissions"></a>Permissions  
Не требует специальных разрешений. Сведения о контексте хранятся также в **sys.dm_exec_requests**, **sys.dm_exec_sessions**, и **sys.sysprocesses** системных представлений, однако непосредственный запрос представления требует разрешения SELECT и VIEW SERVER STATE.
  
## <a name="examples"></a>Примеры  
Следующий простой пример наборов **context_info** значение `0x1256698456`, а затем использует `CONTEXT_INFO` функция для извлечения значения.
  
```sql
SET CONTEXT_INFO 0x1256698456;  
GO  
SELECT CONTEXT_INFO();  
GO  
```  
  
## <a name="see-also"></a>См. также:
[SET CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/statements/set-context-info-transact-sql.md)
  
  
