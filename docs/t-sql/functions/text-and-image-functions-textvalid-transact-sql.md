---
title: "TEXTVALID (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTVALID_TSQL
- TEXTVALID
dev_langs:
- TSQL
helpviewer_keywords:
- invalid text pointers [SQL Server]
- valid text pointers [SQL Server]
- TEXTVALID function
- checking text pointers
- text-pointer values
- verifying text pointers
ms.assetid: 9411c349-b59b-4740-a270-92f91d81ad23
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 279022316af7e3a396c7089f48933281264f900f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="text-and-image-functions---textvalid-transact-sql"></a>Текст и изображения функции - TEXTVALID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Объект **текст**, **ntext**, или **изображения** функцию, которая проверяет, является ли указанный текстовый указатель допустимым.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Дополнительные возможности недоступны.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TEXTVALID ( 'table.column' ,text_ ptr )  
```  
  
## <a name="arguments"></a>Аргументы  
 *table*  
 Имя таблицы, которая будет использоваться.  
  
 *столбец*  
 Имя столбца, который будет использоваться.  
  
 *text_ptr*  
 Текстовый указатель, который подлежит проверке.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="remarks"></a>Замечания  
 Возвращает 1, если указатель является действительным, и 0, если указатель недействителен. Обратите внимание, что идентификатор для **текст** столбец должен содержать имя таблицы. Нельзя использовать инструкции UPDATETEXT, WRITETEXT или READTEXT без действительных текстовых указателей.  
  
 Следующие функции и инструкции также полезны при работе с **текст**, **ntext**, и **изображения** данные.  
  
|Функция или инструкция|Description|  
|---------------------------|-----------------|  
|Функция PATINDEX**(**"*шаблон %**"***,** *выражение***)**|Возвращает позицию знака указанной символьной строки в **текст** и **ntext** столбцов.|  
|DATALENGTH**(***выражение***)**|Возвращает длину данных в **текст**, **ntext**, и **изображения** столбцов.|  
|SET TEXTSIZE|Возвращает предельный размер в байтах, **текст**, **ntext**, или **изображения** данные, возвращаемые инструкцией SELECT.|  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается информация о том, существует ли действительный текстовый указатель для каждого значения в столбце `logo` таблицы `pub_info`.  
  
> [!NOTE]  
>  Чтобы выполнить этот пример, необходимо установить **pubs** базы данных.  
  
```  
USE pubs;  
GO  
SELECT pub_id, 'Valid (if 1) Text data'   
   = TEXTVALID ('pub_info.logo', TEXTPTR(logo))   
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id Valid (if 1) Text data   
------ ----------------------   
0736   1                        
0877   1                        
1389   1                        
1622   1                        
1756   1                        
9901   1                        
9952   1                        
9999   1                        
  
(8 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [DATALENGTH &#40; Transact-SQL &#41;](../../t-sql/functions/datalength-transact-sql.md)   
 [Функция PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
 [Значение TEXTSIZE &#40; Transact-SQL &#41;](../../t-sql/statements/set-textsize-transact-sql.md)   
 [Текст и изображения функции &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)   
 [TEXTPTR &#40; Transact-SQL &#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)  
  
  

