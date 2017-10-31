---
title: "Функция FORMATMESSAGE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FORMATMESSAGE
- FORMATMESSAGE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmessages system table
- sys.messages catalog view
- FORMATMESSAGE function
- messages [SQL Server], formats
- errors [SQL Server], formats
ms.assetid: 83f18102-2035-4a87-acd0-8d96d03efad5
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 071f6def07baf0b74919fd5ce93e65494877dda0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="formatmessage-transact-sql"></a>FORMATMESSAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает сообщение из существующего сообщения в представлении каталога sys.messages или введенная строка. Функция FORMATMESSAGE работает аналогично инструкции RAISERROR, но в отличие от нее не выводит сообщение немедленно, а возвращает сформированный текст для дальнейшей обработки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
FORMATMESSAGE ( { msg_number  | ' msg_string ' } , [ param_value [ ,...n ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *msg_number*  
 — Идентификатор сообщения, сохраненного в представлении каталога sys.messages. Если *msg_number* будет < = 13000 или если сообщение не существует в представлении каталога sys.messages, возвращается значение NULL.  
  
 *msg_string*  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 — Строка заключена в одинарные кавычки и содержащий значение параметра заполнители. Это сообщение об ошибке не должно содержать более 2 047 символов. Если сообщение содержит 2 048 и более символов, то отображаются только первые 2 044, а за ними появляется знак многоточия, показывающий, что сообщение было усечено. Обратите внимание, что параметры подстановки содержат больше символов, чем видно на выходе из-за внутренней структуры хранения.  Сведения о структуре строку сообщения и использование параметров в строке, см. в описании *msg_str* аргумент в [RAISERROR &#40; Transact-SQL &#41; ](../../t-sql/language-elements/raiserror-transact-sql.md).  
  
 *param_value*  
 Значение параметра для включения в текст сообщения. Может быть указано несколько значений, при этом они должны быть перечислены в том же порядке, в котором заполнители присутствуют в сообщении. Допускается не более 20 значений.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nvarchar**  
  
## <a name="remarks"></a>Замечания  
 Как и инструкция RAISERROR, функция FORMATMESSAGE производит формирование сообщения, подставляя указанные значения параметров вместо заполнителей. Дополнительные сведения о заполнителях, которые допускаются в сообщения об ошибках и о процессе его формирования см. в разделе [RAISERROR &#40; Transact-SQL &#41; ](../../t-sql/language-elements/raiserror-transact-sql.md).  
  
 Она находит сообщение для текущего языка, установленного для пользователя. Если локализованная версия сообщения отсутствует, то берется версия сообщения для языка «Английский (США)».  
  
 Для локализованных сообщений указанные параметры должны соответствовать заполнителям в версиях для языка «Английский (США)». Таким образом, параметр 1 в локализованной версии должен соответствовать параметру 1 в версии для языка «Английский (США)», параметр 2 — параметру 2 и т. д.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-example-with-a-message-number"></a>A. Пример с номер сообщения  
 В следующем примере используется сообщение репликации `20009` хранятся в представлении каталога sys.messages, как «статьи «%s» не быть добавить публикацию «%s».» Функция FORMATMESSAGE подставляет вместо заполнителей параметров значения `First Variable` и `Second Variable`. Результирующая строка «статьи «Первая переменная» удалось не добавить в публикацию «Вторая переменная».», сохраняется в локальной переменной `@var1`.  
  
```  
SELECT text FROM sys.messages WHERE message_id = 20009 AND language_id = 1033;  
DECLARE @var1 VARCHAR(200);   
SELECT @var1 = FORMATMESSAGE(20009, 'First Variable', 'Second Variable');   
SELECT @var1;  
```  
  
### <a name="b-example-with-a-message-string"></a>Б. Пример вместе со строкой сообщения  
  
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Следующий пример принимает строку в качестве входных данных.  
  
```  
SELECT FORMATMESSAGE('This is the %s and this is the %s.', 'first variable', 'second variable') AS Result;  
```  
  
 Возвращает:`This is the first variable and this is the second variable.`  
  
### <a name="c-additional-message-string-formatting-examples"></a>В. Форматирование примеры строки дополнительное сообщение  
 В следующих примерах показано разнообразные параметры форматирования.  
  
```  
SELECT FORMATMESSAGE('Signed int %i, %d %i, %d, %+i, %+d, %+i, %+d', 5, -5, 50, -50, -11, -11, 11, 11);  
SELECT FORMATMESSAGE('Signed int with leading zero %020i', 5);  
SELECT FORMATMESSAGE('Signed int with leading zero 0 %020i', -55);  
SELECT FORMATMESSAGE('Unsigned int %u, %u', 50, -50);  
SELECT FORMATMESSAGE('Unsigned octal %o, %o', 50, -50);  
SELECT FORMATMESSAGE('Unsigned hexadecimal %x, %X, %X, %X, %x', 11, 11, -11, 50, -50);  
SELECT FORMATMESSAGE('Unsigned octal with prefix: %#o, %#o', 50, -50);  
SELECT FORMATMESSAGE('Unsigned hexadecimal with prefix: %#x, %#X, %#X, %X, %x', 11, 11, -11, 50, -50);  
SELECT FORMATMESSAGE('Hello %s!', 'TEST');  
SELECT FORMATMESSAGE('Hello %20s!', 'TEST');  
SELECT FORMATMESSAGE('Hello %-20s!', 'TEST');  
SELECT FORMATMESSAGE('Hello %20s!', 'TEST');  
```  
  
## <a name="see-also"></a>См. также:  
 [THROW &#40; Transact-SQL &#41;](../../t-sql/language-elements/throw-transact-sql.md)   
 [sp_addmessage &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sys.messages (Transact-SQL)](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [Инструкция RAISERROR &#40; Transact-SQL &#41;](../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  

