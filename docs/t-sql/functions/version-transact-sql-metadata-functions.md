---
title: "ВЕРСИЯ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 95a79b33-98f2-4929-a1a5-93b522a9e152
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8ba4237f9a43a525571a2d25f95acb0a31d4a5cb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="version---transact-sql-metadata-functions"></a>Версия - Transact SQL метаданных функции
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

 Возвращает версию [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] запущена на устройстве.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
VERSION ( )  
```  
  
## <a name="arguments"></a>Аргументы  
  
## <a name="general-remarks"></a>Общие замечания  
Необходимо указать имя таблицы в [FROM](../../t-sql/queries/from-transact-sql.md) предложение для этой функции для возврата результатов. Строки результата будет возвращаться для каждой строки в результирующем наборе запроса; Используйте [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md) позволяет ограничить число возвращаемых строк.  
  
## <a name="examples"></a>Примеры  
Следующий пример возвращает номер версии.  
  
```  
SELECT VERSION();  
```  
  
## <a name="see-also"></a>См. также 
[SESSION_ID (Transact-SQL)](../../t-sql/functions/session-id-transact-sql.md)  
[DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)  
  
  
