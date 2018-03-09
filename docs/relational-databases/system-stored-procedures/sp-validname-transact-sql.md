---
title: "sp_validname (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_validname
- sp_validname_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_validname
ms.assetid: d51c53c2-1332-407f-b725-4983f2e710eb
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 00dc003905fb90ae819bc49eba68aeee2f1cdbb1
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spvalidname-transact-sql"></a>sp_validname (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Проверяет на правильность имена идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Все недвоичные и ненулевые данные, включая данные в Юникоде, могут храниться с помощью **nchar**, **nvarchar**, или **ntext** типов данных, принимаются как допустимые символы для имена идентификаторов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_validname [@name =] 'name'   
     [, [@raise_error =] raise_error]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@name=** ] **"***имя***"**  
 Имя [идентификаторы](../../relational-databases/databases/database-identifiers.md) для которых необходимо проверить правильность. *имя* — **sysname**, не имеет значения по умолчанию. *имя* не может иметь значение NULL, не может быть пустой строкой и не может содержать двоичные или нулевые символы.  
  
 [  **@raise_error=** ] *raise_error*  
 Указывает, формировать ли ошибку. *raise_error* — **бит**, значение по умолчанию 1. Это означает, что ошибки будут отображаться. 0 приводит к тому, что сообщения об ошибках появляться не будут.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="see-also"></a>См. также:  
 [Компонент Database Engine хранимой процедуры &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [NCHAR &#40; Transact-SQL &#41;](../../t-sql/functions/nchar-transact-sql.md)   
 [nchar и nvarchar &#40; Transact-SQL &#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)   
 [ntext, text и изображение &#40; Transact-SQL &#41;](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
