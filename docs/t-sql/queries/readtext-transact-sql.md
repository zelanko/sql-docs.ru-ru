---
title: READTEXT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3e98fba7617c3b1a46b64d07f2b7efa0e51b9ad2
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37980562"
---
# <a name="readtext-transact-sql"></a>READTEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Считывает значения **text**, **ntext** или **image** из столбцов типа **text**, **ntext** или **image**, начиная с указанной позиции; считывается указанное число байтов.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте вместо этого функцию [SUBSTRING](../../t-sql/functions/substring-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
READTEXT { table.column text_ptr offset size } [ HOLDLOCK ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *table* **.** *column*  
 Имя таблицы и столбца, откуда должны быть считаны данные. Имена таблиц и столбцов должны соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md). Указание имен таблицы и столбца обязательно; однако указание имени базы данных и имен владельца является необязательным.  
  
 *text_ptr*  
 Действительный текстовый указатель. Значение *text_ptr* должно иметь тип **binary(16)**.  
  
 *offset*  
 Число байтов (если используется тип данных **text** или **image**) или символов (если используется тип данных **ntext**), которые следует пропустить прежде, чем приступить к чтению данных **text**, **image** или **ntext**.  
  
 *size*  
 Число байтов (если используется тип данных **text** или **image**) или символов (если используется тип данных **ntext**), которое следует считать. Если для аргумента *size* указано значение 0, считывается 4 КБ данных.  
  
 HOLDLOCK  
 Вызывает блокировку считывания для текстового значения до окончания транзакции. Другие пользователи могут считывать значение, но не могут изменять его.  
  
## <a name="remarks"></a>Remarks  
 Используйте функцию [TEXTPTR](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md), чтобы получить действительное значение аргумента *text_ptr*. TEXTPTR возвращает указатель на столбец **text**, **ntext** или **image** в указанной строке или на столбец **text**, **ntext** или **image** в последней строке, возвращаемой запросом, если возвращается более одной строки. Поскольку TEXTPTR возвращает 16-байтовую двоичную строку, рекомендуется объявить локальную переменную для хранения текстового указателя, а затем использовать эту переменную с READTEXT. Дополнительные сведения об объявлении локальной переменной см. в статье [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md).  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутристрочные текстовые указатели могут существовать, но при этом быть недействительными. Дополнительные сведения о параметре **text in row** см. в статье [sp_tableoption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Дополнительные сведения о допустимости текстовых указателей см. в статье [sp_invalidate_textptr (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
 Значение функции @@TEXTSIZE переопределяет размер, указанный для READTEXT, если оно меньше размера, указанного для READTEXT. Функция @@TEXTSIZE указывает предельное число байтов данных, которые должны быть возвращены, как установлено инструкцией SET TEXTSIZE. Дополнительные сведения о том, как задать значение TEXTSIZE для сеанса, см. в статье [SET TEXTSIZE (Transact-SQL)](../../t-sql/statements/set-textsize-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Разрешения READTEXT по умолчанию принадлежат пользователям, имеющим разрешения SELECT для указанной таблицы. Разрешения могут быть переданы при передаче разрешений SELECT.  
  
## <a name="examples"></a>Примеры  
 В нижеследующем примере считываются знаки со второго по двадцать шестой в столбце `pr_info` таблицы `pub_info`.  
  
> [!NOTE]  
>  Для выполнения этого примера необходимо установить образец базы данных **pubs**.  
  
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
 [@@TEXTSIZE (Transact-SQL)](../../t-sql/functions/textsize-transact-sql.md)   
 [UPDATETEXT (Transact-SQL)](../../t-sql/queries/updatetext-transact-sql.md)   
 [WRITETEXT (Transact-SQL)](../../t-sql/queries/writetext-transact-sql.md)  
  
  
