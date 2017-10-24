---
title: "DROP SYNONYM (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5f781dd3557dadcda49e2089bf98195f5adde32e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-synonym-transact-sql"></a>DROP SYNONYM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Удаляет синонимы из указанной схемы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP SYNONYM [ IF EXISTS ] [ schema. ] synonym_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *ЕСЛИ СУЩЕСТВУЕТ*  
**Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 Этот синоним удаляется условно только в том случае, если он уже существует.  
  
 *схемы*  
 Указывает схему, в которой существует этот синоним. Если схема не указана, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует применяемую по умолчанию схему текущего пользователя.  
  
 *synonym_name*  
 Имя синонима, который нужно удалить.  
  
## <a name="remarks"></a>Замечания  
 Ссылки на синонимы не привязаны к схемам, поэтому удаление синонима возможно в любое время. Ссылки на удаленные синонимы можно обнаружить только во время выполнения.  
  
 Синонимы можно создавать, удалять и ссылаться на них в динамическом SQL.  
  
## <a name="permissions"></a>Permissions  
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
  
## <a name="see-also"></a>См. также:  
 [СОЗДАТЬ СИНОНИМ &#40; Transact-SQL &#41;](../../t-sql/statements/create-synonym-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

