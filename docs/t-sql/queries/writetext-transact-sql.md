---
title: "WRITETEXT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/23/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WRITETEXT_TSQL
- WRITETEXT
dev_langs:
- TSQL
helpviewer_keywords:
- replacing data
- WRITETEXT statement
- updating data [SQL Server]
- nonlogged updating
- minimally logged updating [SQL Server]
- overwriting data
- data updates [SQL Server], WRITETEXT statement
ms.assetid: 80c252fd-a8b8-4a2e-888a-059081ed4109
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: fda340750c555d7e6e858ddac1a87401e215891e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="writetext-transact-sql"></a>WRITETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Разрешает протоколируются интерактивное обновление существующего **текст**, **ntext**, или **изображения** столбца. Инструкция WRITETEXT перезаписывает любые существующие данные в столбце, для которого применяется. Инструкция WRITETEXT не может использоваться для **текст**, **ntext**, и **изображения** столбцы в представлениях.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Использовать типы данных больших значений и **.** Предложение записи [обновление](../../t-sql/queries/update-transact-sql.md) инструкции вместо него.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WRITETEXT [BULK]  
  { table.column text_ptr }  
  [ WITH LOG ] { data }  
```  
  
## <a name="arguments"></a>Аргументы  
 BULK  
 Включает внешние средства для передачи потока двоичных данных. Поток должен быть передан средством на уровне протокола TDS. В отсутствие потока данных обработчик запросов не учитывает параметр BULK.  
  
> [!IMPORTANT]  
>  Рекомендуется не использовать параметр BULK в приложениях с поддержкой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот параметр может быть изменен или удален в следующих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *Таблица* **.column**  
 Имя таблицы и **текст**, **ntext**, или **изображения** столбец для обновления. Имена таблиц и столбцов должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md). Указание имени базы данных и владельца необязательно.  
  
 *text_ptr*  
 — Значение, которое хранится указатель на **текст**, **ntext**, или **изображения** данные. *text_ptr* должно быть **binary(16)**. Для создания текстового указателя, выполните процедуру [вставить](../../t-sql/statements/insert-transact-sql.md) или [обновление](../../t-sql/queries/update-transact-sql.md) инструкции с данными, не имеет значение null для **текст**, **ntext**, или **изображения** столбца.  
  
 WITH LOG  
 Не учитывается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ведение журнала определяется моделью восстановления, действующей для базы данных.  
  
 *data*  
 Представляет собой фактические **текст**, **ntext** или **изображения** данные для хранения. *данные* может быть литералом или параметром. Максимальная длина текста, который можно вставить интерактивно с помощью инструкции WRITETEXT — приблизительно 120 КБ для **текст**, **ntext**, и **изображения** данные.  
  
## <a name="remarks"></a>Remarks  
 Используйте WRITETEXT для замены **текст**, **ntext**, и **изображения** данных и UPDATETEXT для изменения **текст**, **ntext**, и **изображения** данные. UPDATETEXT является более гибкой, так как изменяется только часть **текст**, **ntext**, или **изображения** столбца, а не весь столбец.  
  
 Для наилучшей производительности рекомендуется **текст**, **ntext**, и **изображения** вставлять или обновлять фрагментами, кратными 8040 байт данных.  
  
 Если модель восстановления базы данных простая или с неполным протоколированием, **текст**, **ntext**, и **изображения** операций, в которых используется инструкция WRITETEXT, операции с минимальным протоколированием новых данных вставляемых или добавляемых.  
  
> [!NOTE]  
>  Если обновляются существующие значения, ведение журнала не сокращается до минимума.  
  
 Для правильного выполнения инструкции WRITETEXT столбец уже должен содержать действительный указатель на текст.  
  
 Если таблица не содержит текст строки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экономит пространство, не выполняя инициализации **текст** столбцов при добавлении явных или неявных значений null в **текст** столбцы с INSERT, а не текстовый указатель может быть получить для этих значений NULL. Для инициализации **текст** столбцам значения NULL, инструкция UPDATE. Если в строке таблицы содержится текст, не нужно заполнять столбцы типа text значениями NULL и всегда можно получить указатель на текст.  
  
 Функция ODBC SQLPutData выполняется быстрее и занимает меньше динамической памяти, чем инструкция WRITETEXT. Этой функции можно вставить до 2 гигабайт **текст**, **ntext**, или **изображения** данные.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в текстовые указатели на строки **текст**, **ntext**, или **изображения** данных могут существовать, но могут оказаться недопустимыми. Сведения о текста в строке см. в разделе [sp_tableoption &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Сведения о допустимости указателей текста см. в разделе [sp_invalidate_textptr &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение UPDATE на указанную таблицу. Разрешение может передаваться, если передано разрешение UPDATE.  
  
## <a name="examples"></a>Примеры  
 В следующем примере указатель на текст вводится в локальную переменную `@ptrval`, а затем инструкция `WRITETEXT` помещает новую строку текста в строку, на которую указывает `@ptrval`.  
  
> [!NOTE]  
>  Для выполнения данного примера необходимо установить образец базы данных pubs.  
  
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
WRITETEXT pub_info.pr_info @ptrval 'New Moon Books (NMB) has just released another top ten publication. With the latest publication this makes NMB the hottest new publisher of the year!';  
GO  
ALTER DATABASE pubs SET RECOVERY SIMPLE;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [UPDATETEXT &#40; Transact-SQL &#41;](../../t-sql/queries/updatetext-transact-sql.md)  
  
  
