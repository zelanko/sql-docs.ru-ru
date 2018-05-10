---
title: WRITETEXT (Transact-SQL) | Документы Майкрософт
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
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9d5e4b322eb6c334d8e5f946ff233901230d87ba
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="writetext-transact-sql"></a>WRITETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Обеспечивает интерактивное обновление существующего столбца типа **text**, **ntext** или **image** с минимальным ведением журнала. Инструкция WRITETEXT перезаписывает любые существующие данные в столбце, для которого применяется. Инструкцию WRITETEXT нельзя использовать для столбцов типа **text**, **ntext** и **image** в представлениях.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого пользуйтесь типами данных большого объема и предложением **.** WRITE инструкции [UPDATE](../../t-sql/queries/update-transact-sql.md).  
  
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
  
 *table* **.column**  
 Имя обновляемой таблицы и столбца типа **text**, **ntext** или **image**. Имена таблиц и столбцов должны соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md). Указание имени базы данных и владельца необязательно.  
  
 *text_ptr*  
 Значение, в котором хранится указатель на данные типа **text**, **ntext** или **image**. Аргумент *text_ptr* должен иметь тип **binary(16)**. Для создания текстового указателя следует выполнить инструкцию [INSERT](../../t-sql/statements/insert-transact-sql.md) или [UPDATE](../../t-sql/queries/update-transact-sql.md) с ненулевыми данными для столбца типа **text**, **ntext** или **image**.  
  
 WITH LOG  
 Не учитывается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ведение журнала определяется моделью восстановления, действующей для базы данных.  
  
 *data*  
 Представляет собой фактические данные **text**, **ntext** или **text** для хранения. Аргумент *data* может быть литералом или параметром. Максимальная длина текста, который можно вставить интерактивно с помощью инструкции WRITETEXT — приблизительно 120 КБ для данных типа **text**, **ntext** и **image**.  
  
## <a name="remarks"></a>Примечания  
 Используйте WRITETEXT для замены данных типа **text**, **ntext** и **image** и UPDATETEXT для изменения данных типа **text**, **ntext** и **image**. Инструкция UPDATETEXT более гибкая, так как изменяет не весь столбец типа **text**, **ntext** или **image**, а только его часть.  
  
 Для достижения оптимальной производительности рекомендуется вставлять или обновлять данные типа **text**, **ntext** и **image** фрагментами, размер которых кратен 8040 байтам.  
  
 Если модель восстановления базы данных простая или с неполным протоколированием, операции над данными типа **text**, **ntext** и **image**, в которых используется инструкция WRITETEXT, выполняются с минимальным ведением журнала при вставке или добавлении новых данных.  
  
> [!NOTE]  
>  Если обновляются существующие значения, ведение журнала не сокращается до минимума.  
  
 Для правильного выполнения инструкции WRITETEXT столбец уже должен содержать действительный указатель на текст.  
  
 Если в строке таблицы не содержится текст, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экономит пространство, не выполняя инициализации столбцов **text** при добавлении явных или неявных значений NULL в столбцы **text** с помощью инструкции INSERT. Для этих значений NULL не может быть получен указатель на текст. Для инициализации столбцов **text** значением NULL следует использовать инструкцию UPDATE. Если в строке таблицы содержится текст, не нужно заполнять столбцы типа text значениями NULL и всегда можно получить указатель на текст.  
  
 Функция ODBC SQLPutData выполняется быстрее и занимает меньше динамической памяти, чем инструкция WRITETEXT. С помощью этой функции можно вставить до 2 гигабайт (ГБ) данных типа **text**, **ntext** или **image**.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутристрочные текстовые указатели на данные типа **text**, **ntext** или **image** могут существовать, но могут быть неверными. Дополнительные сведения о параметре text in row см. в разделе [sp_tableoption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Сведения о допустимости указателей текста см. в разделе [sp_invalidate_textptr (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
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
 [UPDATETEXT (Transact-SQL)](../../t-sql/queries/updatetext-transact-sql.md)  
  
  
