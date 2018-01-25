---
title: "UPDATETEXT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/23/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATETEXT
- UPDATETEXT_TSQL
dev_langs: TSQL
helpviewer_keywords:
- text updates [SQL Server]
- updating data [SQL Server]
- data updates [SQL Server], UPDATETEXT statement
- UPDATETEXT statement
ms.assetid: d73c28ee-3972-4afd-af8d-ebbbd9e50793
caps.latest.revision: "34"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c4d7c7a51daeba116e695ba9cae797f0d69c70cf
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="updatetext-transact-sql"></a>UPDATETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Обновляет существующий **текст**, **ntext**, или **изображения** поля. Используйте UPDATETEXT для изменения только часть **текст**, **ntext**, или **изображения** столбца на месте. Используйте WRITETEXT для обновления и замены всего **текст**, **ntext**, или **изображения** поля.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Использовать типы данных больших значений и **.** Предложение записи [обновление](../../t-sql/queries/update-transact-sql.md) инструкции вместо него.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
UPDATETEXT [BULK] { table_name.dest_column_name dest_text_ptr }  
  { NULL | insert_offset }  
     { NULL | delete_length }  
     [ WITH LOG ]  
     [ inserted_data  
    | { table_name.src_column_name src_text_ptr } ]  
```  
  
## <a name="arguments"></a>Аргументы  
 BULK  
 Включает внешние средства для передачи потока двоичных данных. Поток должен быть передан средством на уровне протокола TDS. В отсутствие потока данных обработчик запросов не учитывает параметр BULK.  
  
> [!IMPORTANT]  
>  Рекомендуется не использовать параметр BULK в приложениях с поддержкой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот параметр может быть изменен или удален в следующих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *table_name* **.** *dest_column_name*  
 Имя таблицы и **текст**, **ntext**, или **изображения** обновляемого столбца. Имена таблиц и имена столбцов должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md). Указание имени базы данных и владельца необязательно.  
  
 *dest_text_ptr*  
 Текстового указателя (возвращается функцией TEXTPTR) значение, которое указывает на **текст**, **ntext**, или **изображения** обновление данных. *dest_text_ptr* должно быть **двоичный (**16**)**.  
  
 *insert_offset*  
 Начальная позиция для обновления. Отсчет начинает с нуля. Для **текст** или **изображения** столбцы, *insert_offset* число байтов, которые необходимо пропустить с начала существующего столбца перед вставкой новых данных. Для **ntext** столбцы, *insert_offset*число символов (каждый **ntext** символ занимает 2 байта). Существующий **текст**, **ntext**, или **изображения** данные, начиная с этого Начальная позиция сдвигается вправо, чтобы освободить место для новых данных. При значении 0 новые данные вставляются в начало существующих данных. Если значение равно NULL, новые данные добавляются в конец существующих.  
  
 *delete_length*  
 Длина удаляемых данных из существующей **текст**, **ntext**, или **изображения** столбца, начиная с *insert_offset* позиции. *Delete_length*значение указывается в байтах для **текст** и **изображения** столбцы и в символах для **ntext** столбцов. Каждый **ntext** символ занимает 2 байта. При значении 0 данные не удаляются. При значении NULL удаляются все данные из *insert_offset* положения до конца существующего **текст** или **изображения** столбца.  
  
 WITH LOG  
 Ведение журнала определяется моделью восстановления, действующей для базы данных.  
  
 *inserted_data*  
 Данные должны быть вставлены в существующих **текст**, **ntext**, или **изображения** столбец на *insert_offset* расположение. Это один **char**, **nchar**, **varchar**, **nvarchar**, **двоичных**,  **varbinary**, **текст**, **ntext**, или **изображения** значение. *inserted_data* может быть литералом или переменной.  
  
 *table_name.src_column_name*  
 Имя таблицы и **текст**, **ntext**, или **изображения** столбец, используемый в качестве источника вставляемых данных. Имена таблиц и имена столбцов должны соответствовать правилам для идентификаторов.  
  
 *src_text_ptr*  
 Текстового указателя (возвращается функцией TEXTPTR) значение, которое указывает на **текст**, **ntext**, или **изображения** столбец, используемый в качестве источника вставляемых данных.  
  
> [!NOTE]  
>  *scr_text_ptr* значение не должно быть таким же, как *dest_text_ptr*значение.  
  
## <a name="remarks"></a>Remarks  
 Вставленные данные могут представлять собой одно *inserted_data* константа, имя таблицы, имя столбца или текстовый указатель.  
  
|Операция обновления|Параметры UPDATETEXT|  
|-------------------|---------------------------|  
|Для замены существующих данных|Укажите аргумента *insert_offset* значение ненулевое *delete_length* значение и новые данные для вставки.|  
|Для удаления существующих данных|Укажите аргумента *insert_offset* значение и ненулевое *delete_length*. Не указывайте вставляемые данные.|  
|Для вставки новых данных|Укажите *insert_offset* значение *delete_length* 0, и для вставки новых данных.|  
  
 Для наилучшей производительности рекомендуется **текст**, **ntext** и **изображения** вставлять или обновлять фрагментами с размером, кратным 8 040 байт данных.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], внутристрочные текстовые указатели на **текст**, **ntext**, или **изображения** данных могут существовать, но могут оказаться недопустимыми. Сведения о текста в строке см. в разделе [sp_tableoption &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Сведения о допустимости указателей текста см. в разделе [sp_invalidate_textptr &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
 Для инициализации **текст** столбцам значения NULL, используйте функцию WRITETEXT. UPDATETEXT присваивает **текст** столбцов на пустую строку.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение UPDATE на указанную таблицу.  
  
## <a name="examples"></a>Примеры  
 Следующий пример присваивает локальной переменной `@ptrval` значение текстового указателя и использует `UPDATETEXT` для исправления грамматической ошибки.  
  
> [!NOTE]  
>  Чтобы запустить данный пример, требуется установить базу данных pubs.  
  
```  
USE pubs;  
GO  
ALTER DATABASE pubs SET RECOVERY SIMPLE;  
GO  
DECLARE @ptrval binary(16);  
SELECT @ptrval = TEXTPTR(pr_info)   
   FROM pub_info pr, publishers p  
      WHERE p.pub_id = pr.pub_id   
      AND p.pub_name = 'New Moon Books'  
UPDATETEXT pub_info.pr_info @ptrval 88 1 'b';  
GO  
ALTER DATABASE pubs SET RECOVERY FULL;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [READTEXT &#40; Transact-SQL &#41;](../../t-sql/queries/readtext-transact-sql.md)   
 [TEXTPTR &#40; Transact-SQL &#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)   
 [WRITETEXT (Transact-SQL)](../../t-sql/queries/writetext-transact-sql.md)  
  
  
