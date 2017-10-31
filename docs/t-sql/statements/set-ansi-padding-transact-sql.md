---
title: "SET ANSI_PADDING (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ANSI_PADDING_TSQL
- ANSI_PADDING
- SET_ANSI_PADDING_TSQL
- SET ANSI_PADDING
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], short values
- ANSI_PADDING option
- short values [SQL Server]
- SET ANSI_PADDING statement
- trailing blanks
ms.assetid: 92bd29a3-9beb-410e-b7e0-7bc1dc1ae6d0
caps.latest.revision: 47
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 426cbfe673bafe6e1770745ca16ba23fd068fb67
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-ansipadding-transact-sql"></a>SET ANSI_PADDING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Управляет тем, как столбец хранит значения короче, чем определенный размер столбца, и тем, как столбец хранит значения с завершающими пробелами в данных типов **char**, **varchar**, **binary**и **varbinary** .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  
  
SET ANSI_PADDING { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_PADDING ON;  
```  
  
## <a name="remarks"></a>Замечания  
 Столбцы, определенные с **char**, **varchar**, **двоичных**, и **varbinary** типы данных имеют определенный размер.  
  
 Этот параметр влияет только на определение новых столбцов. После создания столбца [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет значения, исходя из значения параметра на время создания столбца. Более поздние изменения этого параметра не влияют на существующие столбцы.  
  
> [!NOTE]  
>  Мы рекомендуем всегда устанавливать для параметра ANSI_PADDING значение ON.  
  
 В следующей таблице показаны эффекты параметр SET ANSI_PADDING при вставке значений в столбцы с **char**, **varchar**, **двоичных**, и  **varbinary** типов данных.  
  
|Настройка|char (*n*) не NULL или binary (*n*) NOT NULL|char (*n*) значение NULL или binary (*n*) значение NULL|varchar (*n*) или varbinary (*n*)|  
|-------------|----------------------------------------------------|--------------------------------------------|----------------------------------------|  
|ON|Заполнение исходного значения (с замыкающими пробелами для **char** столбцы и с замыкающими нулями для **двоичных** столбцы) до длины столбца.|Следует тем же правилам, что и для **char (***n***)** или **двоичный (**  *n*  **)** Не NULL, когда SET ANSI_PADDING установлен на ON.|Замыкающие пробелы в символьных значениях, вставляемых в **varchar** столбцы, не усекаются. Замыкающие нули в двоичных значениях, вставляемых в **varbinary** столбцы, не усекаются. Значения не подгоняются под длину столбца.|  
|OFF|Заполнение исходного значения (с замыкающими пробелами для **char** столбцы и с замыкающими нулями для **двоичных** столбцы) до длины столбца.|Следует тем же правилам, что и для **varchar** или **varbinary** когда SET ANSI_PADDING имеет значение OFF.|Замыкающие пробелы в символьных значениях, вставляемых в **varchar** столбца, усекаются. Замыкающие нули в двоичных значениях, вставляемых в **varbinary** столбца, усекаются.|  
  
> [!NOTE]  
>  При заполнении **char** столбцы заполняются пробелами, и **двоичных** столбцы заполняются нулями. При усечении **char** столбцы имеют замыкающие пробелы, а **двоичных** столбцы имеют усекаются замыкающие нули.  
  
 Инструкция SET ANSI_PADDING должна быть выполнена со значением параметра ON при создании или изменении индексов по вычисляемым столбцам или индексированным представлениям. Дополнительные сведения о необходимых УСТАНОВКАХ параметров SET для индексированных представлений и индексов на вычисляемых столбцах см. в разделе «Вопросы при вы использования операторов SET» в [инструкции SET &#40; Transact-SQL &#41; ](../../t-sql/statements/set-statements-transact-sql.md).  
  
 По умолчанию значение параметра SET ANSI_PADDING равно ON. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при соединении автоматически устанавливают ANSI_PADDING ON. Это может быть настроено в источниках данных ODBC, в атрибутах соединения ODBC или свойствах соединения OLE DB, определенных в приложении перед установкой соединения. Значением по умолчанию для параметра инструкции SET ANSI_PADDING является OFF при соединениях из приложений DB-Library.  
  
 Параметр SET ANSI_PADDING не влияет на **nchar**, **nvarchar**, **ntext**, **текст**, **изображение**, **varbinary(max)**, **varchar(max)**, и **nvarchar(max)** типов данных. Они всегда демонстрируют поведение, соответствующее установленному для параметра инструкции SET ANSI_PADDING значению ON. Это означает, что конечные пробелы и нули не вырезаются.  
  
 Когда для SET ANSI_DEFAULTS установлено значение ON, параметр SET ANSI_PADDING включен.  
  
 Значение параметра SET ANSI_PADDING устанавливается во время выполнения или запуска, а не во время синтаксического анализа.  
  
 Чтобы просмотреть текущее значение параметра для этого параметра, выполните следующий запрос.  
  
```  
DECLARE @ANSI_PADDING VARCHAR(3) = 'OFF';  
IF ( (16 & @@OPTIONS) = 16 ) SET @ANSI_PADDING = 'ON';  
SELECT @ANSI_PADDING AS ANSI_PADDING;  
  
```  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как значение этого параметра влияет на каждый из типов данных.  
  
```  
PRINT 'Testing with ANSI_PADDING ON'  
SET ANSI_PADDING ON;  
GO  
  
CREATE TABLE t1 (  
   charcol CHAR(16) NULL,   
   varcharcol VARCHAR(16) NULL,   
   varbinarycol VARBINARY(8)  
);  
GO  
INSERT INTO t1 VALUES ('No blanks', 'No blanks', 0x00ee);  
INSERT INTO t1 VALUES ('Trailing blank ', 'Trailing blank ', 0x00ee00);  
  
SELECT 'CHAR' = '>' + charcol + '\<', 'VARCHAR'='>' + varcharcol + '\<',  
   varbinarycol  
FROM t1;  
GO  
  
PRINT 'Testing with ANSI_PADDING OFF';  
SET ANSI_PADDING OFF;  
GO  
  
CREATE TABLE t2 (  
   charcol CHAR(16) NULL,   
   varcharcol VARCHAR(16) NULL,   
   varbinarycol VARBINARY(8)  
);  
GO  
INSERT INTO t2 VALUES ('No blanks', 'No blanks', 0x00ee);  
INSERT INTO t2 VALUES ('Trailing blank ', 'Trailing blank ', 0x00ee00);  
  
SELECT 'CHAR' = '>' + charcol + '\<', 'VARCHAR'='>' + varcharcol + '<',  
   varbinarycol  
FROM t2;  
GO  
  
DROP TABLE t1;  
DROP TABLE t2;  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/sessionproperty-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)  
  
  

