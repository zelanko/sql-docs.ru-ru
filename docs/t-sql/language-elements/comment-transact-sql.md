---
title: "--(Комментарий) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --_TSQL
- Comment
- --
dev_langs:
- TSQL
helpviewer_keywords:
- nonexecuting text strings [SQL Server]
- remarks [SQL Server]
- -- (comment character)
- comments [SQL Server]
ms.assetid: 676ea8c2-52c1-4ef6-9354-320f1a091153
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a03aff79db25c07fc828145177e29196405a9264
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="---comment-transact-sql"></a>-- (комментарий) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Обозначает текст комментария пользователя. Комментарии могут вставляться отдельной строкой, добавляться в конец командной строки [!INCLUDE[tsql](../../includes/tsql-md.md)] или инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Сервер не обрабатывает комментарий.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
-- text_of_comment  
```  
  
## <a name="arguments"></a>Аргументы  
 *text_of_comment*  
 Строка, содержащая текст комментария.  
  
## <a name="remarks"></a>Замечания  
 Используйте два дефиса (--) для однострочных или вложенных комментариев. Комментарии, вставленные с использованием --, заканчиваются символом новой строки. Длина комментариев не ограничена. В следующей таблице перечислены сочетания клавиш, используемые для комментирования и раскомментирования текста.  
  
|Действие|Standard Edition|  
|------------|--------------|  
|Преобразование выделенного текста в комментарий|CTRL + K, CTRL + C|  
|Снять комментарий с выделенного текста|CTRL + K, CTRL + U|  
  
 Дополнительные сведения о сочетаниях клавиш см. в разделе [SQL Server Management Studio Keyboard Shortcuts](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md).  
  
 Для многострочных комментариях см. в разделе [косой черты комментарий звезда &#40; Transact-SQL &#41; ](../../t-sql/language-elements/slash-star-comment-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере используются символы комментария --.  
  
```  
-- Choose the AdventureWorks2012 database.  
USE AdventureWorks2012;  
GO  
-- Choose all columns and all rows from the Address table.  
SELECT *  
FROM Person.Address  
ORDER BY PostalCode ASC; -- We do not have to specify ASC because   
-- that is the default.  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Язык управления выполнением &#40; Transact-SQL &#41;](~/t-sql/language-elements/control-of-flow.md)  
  
  

