---
title: CONTEXT_INFO (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 014dee25c2e2237f7c9b72b79f78aa2a0abb4e47
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65948148"
---
# <a name="contextinfo--transact-sql"></a>CONTEXT_INFO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эта функция возвращает значение **context_info**, установленное для текущего сеанса или пакета либо полученное с помощью инструкции [SET CONTEXT_INFO](../../t-sql/statements/set-context-info-transact-sql.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CONTEXT_INFO()  
```  
  
## <a name="return-value"></a>Возвращаемое значение
Значение **context_info**.
  
Если значение **context_info** не было задано:
-   в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращается значение NULL;  
-   в [!INCLUDE[ssSDS](../../includes/sssds-md.md)] возвращается уникальный идентификатор GUID, связанный с сеансом.  
  
## <a name="remarks"></a>Remarks  
Множественный активный результирующий набор (функция MARS) позволяет приложениям запускать несколько пакетов или запросов одновременно, используя одно и то же подключение. Если один из пакетов подключения MARS запустит SET CONTEXT_INFO, функция `CONTEXT_INFO` вернет новое контекстное значение, когда функция `CONTEXT_INFO` запускается в том же пакете, что и инструкция SET. Если функция `CONTEXT_INFO` выполняется в одном или нескольких других пакетах подключения, `CONTEXT_FUNCTION` не возвращает новое значение, если эти пакеты не запускаются после пакета, выполнившего инструкцию SET.
  
## <a name="permissions"></a>Разрешения  
Не требует специальных разрешений. Следующие системные представления хранят сведения о контексте, и для выполнения прямых запросов к ним требуются разрешения SELECT и VIEW SERVER STATE:
- **sys.dm_exec_requests**
- **sys.dm_exec_sessions**
- **sys.sysprocesses**
  
## <a name="examples"></a>Примеры  
В этом примере значение **context_info** устанавливается в `0x1256698456`, а затем для получения значения используется функция `CONTEXT_INFO`.
  
```sql
SET CONTEXT_INFO 0x1256698456;  
GO  
SELECT CONTEXT_INFO();  
GO  
```  
  
## <a name="see-also"></a>См. также раздел
[SET CONTEXT_INFO (Transact-SQL)](../../t-sql/statements/set-context-info-transact-sql.md)
  
  
