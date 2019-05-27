---
title: -- (комментарий) (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
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
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4bfe7d296aece6b62df151bd7880ed474a56200c
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65982703"
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
  
## <a name="remarks"></a>Remarks  
 Используйте два дефиса (--) для однострочных или вложенных комментариев. Комментарии, вставленные с использованием --, заканчиваются символом новой строки. Длина комментариев не ограничена. В следующей таблице перечислены сочетания клавиш, используемые для комментирования и раскомментирования текста.  
  
|Действие|Standard|  
|------------|--------------|  
|Преобразование выделенного текста в комментарий|CTRL + K, CTRL + C|  
|Снять комментарий с выделенного текста|CTRL + K, CTRL + U|  
  
 Дополнительные сведения о сочетаниях клавиш см. в статье [Сочетания клавиш среды SQL Server Management Studio](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md).  
  
 Сведения о многострочных комментариях см. в статье [Косая черта-звездочка (блок комментариев) (Transact-SQL)](../../t-sql/language-elements/slash-star-comment-transact-sql.md).  
  
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
 [Язык управления потоком (Transact-SQL)](~/t-sql/language-elements/control-of-flow.md)  
  
  
