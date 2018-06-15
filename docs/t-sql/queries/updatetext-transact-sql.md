---
title: UPDATETEXT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 10/23/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|queries
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- UPDATETEXT
- UPDATETEXT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- text updates [SQL Server]
- updating data [SQL Server]
- data updates [SQL Server], UPDATETEXT statement
- UPDATETEXT statement
ms.assetid: d73c28ee-3972-4afd-af8d-ebbbd9e50793
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bf01a97b6337f154de8d6d8e2c0fb71f7c4a1dd6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33065501"
---
# <a name="updatetext-transact-sql"></a>UPDATETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Обновляет существующее поле типа **text**, **ntext** или **image**. Используйте UPDATETEXT только для изменения части столбца типа **text**, **ntext** или **image**. Используйте WRITETEXT для обновления и замены всего поля типа **text**, **ntext** или **image**.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого пользуйтесь типами данных большого объема и предложением **.** WRITE инструкции [UPDATE](../../t-sql/queries/update-transact-sql.md).  
  
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
 Имя обновляемой таблицы и столбца типа **text**, **ntext** или **image**. Имена таблиц и имена столбцов должны соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md). Указание имени базы данных и владельца необязательно.  
  
 *dest_text_ptr*  
 Значение текстового указателя (возвращается функцией TEXTPTR), который указывает на обновляемые данные типа **text**, **ntext** или **image**. Значение *dest_text_ptr* должно иметь тип **binary(** 16 **)**.  
  
 *insert_offset*  
 Начальная позиция для обновления. Отсчет начинает с нуля. Для столбцов типа **text** или **image** *insert_offset* является числом байтов, которые необходимо пропустить с начала существующего столбца перед вставкой новых данных. Для столбцов типа **ntext** *insert_offset* является числом символов (каждый символ **ntext** занимает 2 байта). Существующие данные типа **text**, **ntext** или **image**, начиная с этой начальной позиции (отсчет начинается с нуля), сдвигаются вправо, чтобы освободить место для новых данных. При значении 0 новые данные вставляются в начало существующих данных. Если значение равно NULL, новые данные добавляются в конец существующих.  
  
 *delete_length*  
 Длина удаляемых данных из существующего столбца типа **text**, **ntext** или **image** начиная с позиции, указанной в аргументе *insert_offset*. Значение *delete_length* указывается в байтах для столбцов типа **text** и **image** и в символах для столбцов типа **ntext**. Каждый символ **ntext** занимает 2 байта. При значении 0 данные не удаляются. При значении NULL удаляются все данные с позиции, указанной аргументом *insert_offset*, до конца существующего столбца типа **text** или **image**.  
  
 WITH LOG  
 Ведение журнала определяется моделью восстановления, действующей для базы данных.  
  
 *inserted_data*  
 Данные, которые необходимо вставить в существующий столбец типа **text**, **ntext** или **image** в расположении *insert_offset*. Это одно значение типа **char**, **nchar**, **varchar**, **nvarchar**, **binary**, **varbinary**, **text**, **ntext** или **image**. Аргумент *inserted_data* может быть литералом или переменной.  
  
 *table_name.src_column_name*  
 Имя таблицы и столбца типа **text**, **ntext** или **image**, используемого в качестве источника вставляемых данных. Имена таблиц и имена столбцов должны соответствовать правилам для идентификаторов.  
  
 *src_text_ptr*  
 Значение текстового указателя (возвращается функцией TEXTPTR), который указывает на столбец **text**, **ntext** или **image**, используемый в качестве источника вставляемых данных.  
  
> [!NOTE]  
>  Значение *scr_text_ptr* не должно совпадать со значением *dest_text_ptr*.  
  
## <a name="remarks"></a>Remarks  
 Вставленные данные могут быть константой *inserted_data*, именем таблицы, именем столбца или указателем на текст.  
  
|Операция обновления|Параметры UPDATETEXT|  
|-------------------|---------------------------|  
|Для замены существующих данных|Укажите значение аргумента *insert_offset*, отличное от NULL, ненулевое значение аргумента *delete_length* и новые вставляемые данные.|  
|Для удаления существующих данных|Укажите значение аргумента *insert_offset*, отличное от NULL, и ненулевое значение *delete_length*. Не указывайте вставляемые данные.|  
|Для вставки новых данных|Укажите значение аргумента *insert_offset*, значение аргумента *delete_length*, равное 0, и новые вставляемые данные.|  
  
 Для достижения оптимальной производительности рекомендуется вставлять или обновлять данные типа **text**, **ntext** и **image** фрагментами, размер которых кратен 8040 байт.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутристрочные текстовые указатели на данные типа **text**, **ntext** или **image** могут существовать, но быть неверными. Дополнительные сведения о параметре text in row см. в разделе [sp_tableoption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Сведения о допустимости указателей текста см. в разделе [sp_invalidate_textptr (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
 Для присвоения столбцам типа **text** значения NULL используйте функцию WRITETEXT. Функция UPDATETEXT записывает в столбцы типа **text** пустую строку.  
  
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
  
## <a name="see-also"></a>См. также:  
 [READTEXT (Transact-SQL)](../../t-sql/queries/readtext-transact-sql.md)   
 [TEXTPTR (Transact-SQL)](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)   
 [WRITETEXT (Transact-SQL)](../../t-sql/queries/writetext-transact-sql.md)  
  
  
