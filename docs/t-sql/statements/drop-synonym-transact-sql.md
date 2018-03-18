---
title: "DROP SYNONYM (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SYNONYM
- DROP_SYNONYM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting synonyms
- synonyms [SQL Server], removing
- removing synonyms
- DROP SYNONYM statement
- dropping synonyms
ms.assetid: 23578932-e4de-4c39-a5a0-ce45139c4269
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 25af262ddc5655bc42e4893daecefe0cd8fb85d9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="drop-synonym-transact-sql"></a>DROP SYNONYM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Удаляет синонимы из указанной схемы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP SYNONYM [ IF EXISTS ] [ schema. ] synonym_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *IF EXISTS*  
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 Условное удаление синонима только в том случае, если он уже существует.  
  
 *schema*  
 Указывает схему, в которой существует этот синоним. Если схема не указана, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует применяемую по умолчанию схему текущего пользователя.  
  
 *synonym_name*  
 Имя синонима, который нужно удалить.  
  
## <a name="remarks"></a>Примечания  
 Ссылки на синонимы не привязаны к схемам, поэтому удаление синонима возможно в любое время. Ссылки на удаленные синонимы можно обнаружить только во время выполнения.  
  
 Синонимы можно создавать, удалять и ссылаться на них в динамическом SQL.  
  
## <a name="permissions"></a>Разрешения  
 Чтобы удалить синоним, пользователь должен выполнить, по крайней мере, одно из следующих условий. Пользователь должен являться:  
  
-   текущим владельцем синонима;  
  
-   участником, которому предоставлено разрешение CONTROL на синоним;  
  
-   участником, которому предоставлено разрешение ALTER SCHEMA на содержащую синоним схему.  
  
## <a name="examples"></a>Примеры  
 В следующем примере сначала создается синоним `MyProduct`, а затем этот синоним удаляется.  
  
```  
USE tempdb;  
GO  
-- Create a synonym for the Product table in AdventureWorks2012.  
CREATE SYNONYM MyProduct  
FOR AdventureWorks2012.Production.Product;  
GO  
-- Drop synonym MyProduct.  
USE tempdb;  
GO  
DROP SYNONYM MyProduct;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE SYNONYM (Transact-SQL)](../../t-sql/statements/create-synonym-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
