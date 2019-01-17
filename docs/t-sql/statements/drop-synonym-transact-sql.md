---
title: DROP SYNONYM (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f44ba9c4d2b882e97b397fdf959c41d7a9b35fbf
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53213143"
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
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](https://go.microsoft.com/fwlink/p/?LinkId=299658))
  
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
  
  
