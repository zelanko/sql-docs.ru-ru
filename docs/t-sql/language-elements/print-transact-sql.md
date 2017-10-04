---
title: "PRINT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PRINT_TSQL
- PRINT
dev_langs:
- TSQL
helpviewer_keywords:
- PRINT statement
- user-defined messages [SQL Server]
- messages [SQL Server], PRINT statement
- displaying user-defined messages
- viewing user-defined messages
- conditionally returning messages [SQL Server]
ms.assetid: 32ba0729-c4b5-4cfb-a5aa-e8b9402be028
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 51377ebe291fe4c76d8761aaba74eab8f5201108
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="print-transact-sql"></a>Печать Transact-SQL
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает клиенту пользовательское сообщение.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
PRINT msg_str | @local_variable | string_expr  
```  
  
## <a name="arguments"></a>Аргументы  
 *msg_str*  
 Символьная строка или строковая константа Юникода. Дополнительные сведения см. в разделе [константы &#40; Transact-SQL &#41; ](../../t-sql/data-types/constants-transact-sql.md).  
  
 **@***local_variable*  
 Переменная любого допустимого символьного типа данных. **@***local_variable* должно быть **char**, **nchar**, **varchar**, или **nvarchar**, или он должен иметь возможность быть неявно преобразуется в этих типов данных.  
  
 *string_expr*  
 Выражение, возвращающее строку. Может содержать объединенные буквенные значения, функции и переменные. Дополнительные сведения см. в разделе [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="remarks"></a>Замечания  
 Строка сообщения может иметь длину до 8 000 символов для строки, отличной от Юникода, и 4 000 символов для строки в Юникоде. Более длинные строки усекаются. **Varchar(max)** и **nvarchar(max)** типы данных усекаются до типов данных, которые не превышают **varchar(8000)** и **nvarchar(4000)**.  
  
 Для возвращения сообщений можно также использовать функцию RAISERROR. Преимущества функции RAISERROR перед функцией PRINT:  
  
-   функция RAISERROR поддерживает вставку аргументов в строку сообщения об ошибке с помощью механизма, основанного на функции printf из стандартной библиотеки языка С;  
  
-   в дополнение к текстовому сообщению, функция RAISERROR может в сообщении указать уникальный номер ошибки, степень ее серьезности и код состояния;  
  
-   функция RAISERROR может быть использована для возвращения пользовательских сообщений, созданных с помощью системной хранимой процедуры sp_addmessage.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-conditionally-executing-print-if-exists"></a>A. Печать, выполняемая по условию (IF EXISTS)  
 В следующем примере инструкция `PRINT` применяется для возвращения сообщения по условию.  
  
```  
IF @@OPTIONS & 512 <> 0  
    PRINT N'This user has SET NOCOUNT turned ON.';  
ELSE  
    PRINT N'This user has SET NOCOUNT turned OFF.';  
GO  
```  
  
### <a name="b-building-and-displaying-a-string"></a>Б. Построение и отображение строки  
 В следующем примере результаты функции `GETDATE` преобразуются в тип данных `nvarchar` и объединяются с текстовой строкой для последующего возврата функцией `PRINT`.  
  
```  
-- Build the message text by concatenating  
-- strings and expressions.  
PRINT N'This message was printed on '  
    + RTRIM(CAST(GETDATE() AS nvarchar(30)))  
    + N'.';  
GO  
-- This example shows building the message text  
-- in a variable and then passing it to PRINT.  
-- This was required in SQL Server 7.0 or earlier.  
DECLARE @PrintMessage nvarchar(50);  
SET @PrintMessage = N'This message was printed on '  
    + RTRIM(CAST(GETDATE() AS nvarchar(30)))  
    + N'.';  
PRINT @PrintMessage;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-conditionally-executing-print"></a>В. Печать, выполняемая по условию  
 В следующем примере инструкция `PRINT` применяется для возвращения сообщения по условию.  
  
```  
IF DB_ID() = 1  
    PRINT N'The current database is master.';  
ELSE  
    PRINT N'The current database is not master.';  
GO  
```  
  
### <a name="d-building-and-displaying-a-string"></a>Г. Построение и отображение строки  
 В следующем примере результаты функции `GETDATE` преобразуются в тип данных `nvarchar` и объединяются с текстовой строкой для последующего возврата функцией `PRINT`.  
  
```  
-- Build the message text by concatenating  
-- strings and expressions.  
PRINT N'This message was printed on '  
    + RTRIM(CAST(GETDATE() AS nvarchar(30)))  
    + N'.';  
GO  
-- This example shows building the message text  
-- in a variable and then passing it to PRINT.  
DECLARE @PrintMessage nvarchar(50);  
SET @PrintMessage = N'This message was printed on '  
    + RTRIM(CAST(GETDATE() AS nvarchar(30)))  
    + N'.';  
PRINT @PrintMessage;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [Инструкция RAISERROR &#40; Transact-SQL &#41;](../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  


