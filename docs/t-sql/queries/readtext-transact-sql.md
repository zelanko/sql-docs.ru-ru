---
title: "READTEXT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- READTEXT_TSQL
- READTEXT
dev_langs:
- TSQL
helpviewer_keywords:
- column reading [SQL Server]
- READTEXT statement
- reading columns
ms.assetid: 91b69853-1381-4306-8343-afdb73105738
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2c501fe8ea8146b4b2ec6e138f72fc2604b4b374
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="readtext-transact-sql"></a>READTEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Считывает **текст**, **ntext**, или **изображения** значения из **текст**, **ntext**, или **изображения**  столбца, начиная с указанной позиции и чтение заданного числа байтов.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Используйте [ПОДСТРОКИ](../../t-sql/functions/substring-transact-sql.md) вместо этого функцию.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
READTEXT { table.column text_ptr offset size } [ HOLDLOCK ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Таблица* **.** *столбец*  
 Имя таблицы и столбца, откуда должны быть считаны данные. Имена таблиц и столбцов должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md). Указание имен таблицы и столбца обязательно; однако указание имени базы данных и имен владельца является необязательным.  
  
 *text_ptr*  
 Действительный текстовый указатель. *text_ptr* должно быть **binary(16)**.  
  
 *Смещение*  
 Число байтов (при **текст** или **изображения** используются типы данных) или знаков (при **ntext** используется тип данных) следует пропустить прежде чем приступить к чтению **текст**, **изображения**, или **ntext** данных.  
  
 *размер*  
 Число байтов (при **текст** или **изображения** используются типы данных) или знаков (при **ntext** используется тип данных) данных для чтения. Если *размер* равно 0, считывается 4 КБ данных.  
  
 HOLDLOCK  
 Вызывает блокировку считывания для текстового значения до окончания транзакции. Другие пользователи могут считывать значение, но не могут изменять его.  
  
## <a name="remarks"></a>Замечания  
 Используйте [TEXTPTR](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md) функции для получения допустимого *text_ptr* значение. TEXTPTR возвращает указатель на **текст**, **ntext**, или **изображения** столбца в указанной строке или в **текст**, **ntext** , или **изображения** столбца в последней строке, возвращенные запросом, если возвращается более одной строки. Поскольку TEXTPTR возвращает 16-байтовую двоичную строку, рекомендуется объявить локальную переменную для хранения текстового указателя, а затем использовать эту переменную с READTEXT. Дополнительные сведения об объявлении локальной переменной см. в разделе [DECLARE @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/declare-local-variable-transact-sql.md).  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутристрочные текстовые указатели могут существовать, но при этом быть недействительными. Дополнительные сведения о **текст в строке** см. в разделе [sp_tableoption &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Дополнительные сведения о допустимости указателей текста см. в разделе [sp_invalidate_textptr &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
 Значение @@TEXTSIZE функция заменяет размер, указанный для READTEXT, если оно меньше размера, указанного для READTEXT. @@TEXTSIZE Функция указывает предельное число байтов данных, возвращаемых инструкцией SET TEXTSIZE набора. Дополнительные сведения о том, как определить настройку сеанса для TEXTSIZE см. в разделе [SET TEXTSIZE &#40; Transact-SQL &#41; ](../../t-sql/statements/set-textsize-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Разрешения READTEXT по умолчанию принадлежат пользователям, имеющим разрешения SELECT для указанной таблицы. Разрешения могут быть переданы при передаче разрешений SELECT.  
  
## <a name="examples"></a>Примеры  
 В нижеследующем примере считываются знаки со второго по двадцать шестой в столбце `pr_info` таблицы `pub_info`.  
  
> [!NOTE]  
>  Чтобы выполнить этот пример, необходимо установить **pubs** образца базы данных.  
  
```  
USE pubs;  
GO  
DECLARE @ptrval varbinary(16);  
SELECT @ptrval = TEXTPTR(pr_info)   
   FROM pub_info pr INNER JOIN publishers p  
      ON pr.pub_id = p.pub_id   
      AND p.pub_name = 'New Moon Books'  
READTEXT pub_info.pr_info @ptrval 1 25;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [@@TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/functions/textsize-transact-sql.md)   
 [UPDATETEXT (Transact-SQL)](../../t-sql/queries/updatetext-transact-sql.md)   
 [WRITETEXT (Transact-SQL)](../../t-sql/queries/writetext-transact-sql.md)  
  
  

