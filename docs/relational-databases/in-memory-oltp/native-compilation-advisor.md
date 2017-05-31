---
title: "Помощник по компиляции в собственный код | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.nativecompilationwizard.f1
- swb.nativecompilationwizard.f1
ms.assetid: d3898a47-2985-4a08-bc70-fd8331a01b7b
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6a6107fe8c3b05c31320f90c77df04731e226ba8
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="native-compilation-advisor"></a>Помощник по собственной компиляции
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Отчеты о производительности транзакций содержат информацию о том, какие интерпретируемые хранимые процедуры в базе данных будут выполняться эффективнее после компиляции в собственный код. Дополнительные сведения см. в статье [Определение, должна ли таблица или хранимая процедура быть перенесена в In-Memory OLTP](../../relational-databases/in-memory-oltp/determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md).  
  
 Когда вы определите, для какой хранимой процедуры будете выполнять компиляцию в собственный код, можно запустить помощник по компиляции в собственный код (NCA), который облегчит миграцию интерпретируемой хранимой процедуры в собственный код. Дополнительные сведения о скомпилированных в собственном коде хранимых процедурах см. в разделе [Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md).  
  
 NCA позволяет определить для конкретной интерпретируемой хранимой процедуры все функции, которые не поддерживаются в собственных модулях. NCA предложит вам ссылки на документы, в которых описаны решения или обходные варианты.  
  
 Дополнительные сведения о методологиях миграции см. в разделе [In-Memory OLTP — стандартные шаблоны рабочей нагрузки и вопросы миграции](http://msdn.microsoft.com/library/dn673538.aspx).  
  
## <a name="walkthrough-using-the-native-compilation-advisor"></a>Пошаговое руководство по использованию помощника по собственной компиляции  
 В **обозревателе объектов**щелкните правой кнопкой мыши хранимую процедуру, которую необходимо преобразовать, и выберите пункт **Помощник по собственной компиляции**. Появится стартовая страница для **помощника по собственной компиляции хранимых процедур**. Чтобы продолжить, нажмите кнопку **Далее** .  
  
### <a name="stored-procedure-validation"></a>Проверка хранимых процедур  
 Эта страница сообщает, использует ли хранимая процедура какие-либо конструкции, несовместимые с собственной компиляцией. Можно нажать кнопку **Далее** , чтобы просмотреть данные. Если найдены конструкции, несовместимые с собственной компиляцией, можно нажать кнопку **Далее** , чтобы просмотреть подробности.  
  
### <a name="stored-procedure-validation-result"></a>Результат проверки хранимой процедуры  
 При наличии конструкций, несовместимых с собственной компиляцией, на странице **Результат проверки хранимой процедуры** будут выведены подробности. Можно создать отчет (нажав **Создание отчета**), выйти из **помощника по собственной компиляции**и изменить код таким образом, чтобы он был совместим с собственной компиляцией.  
  
## <a name="code-sample"></a>Образец кода  
 В следующем примере показана интерпретируемая хранимая процедура и *эквивалентная* хранимая процедура для компиляции в собственный код. В примере подразумевается каталог c:\data.  
  
> [!NOTE]  
>  Как обычно, элемент **FILEGROUP** и инструкция **USE** mydatabase применяются к Microsoft SQL Server, но не применяются к базе данных SQL Azure.  
  
```tsql  
CREATE DATABASE Demo  
ON  
PRIMARY(NAME = [Demo_data],  
FILENAME = 'C:\DATA\Demo_data.mdf', size=500MB)  
, FILEGROUP [Demo_fg] CONTAINS MEMORY_OPTIMIZED_DATA(  
NAME = [Demo_dir],  
FILENAME = 'C:\DATA\Demo_dir')  
LOG ON (name = [Demo_log], Filename='C:\DATA\Demo_log.ldf', size=500MB)  
COLLATE Latin1_General_100_BIN2;  
go  
  
USE Demo;  
go  
  
CREATE TABLE [dbo].[SalesOrders]  
(  
     [order_id] [int] NOT NULL,  
     [order_date] [datetime] NOT NULL,  
     [order_status] [tinyint] NOT NULL  
     CONSTRAINT [PK_SalesOrders] PRIMARY KEY NONCLUSTERED HASH   
(  
     [order_id]  
) WITH ( BUCKET_COUNT = 2097152)  
) WITH ( MEMORY_OPTIMIZED = ON )  
go  
  
-- Interpreted.  
CREATE PROCEDURE [dbo].[InsertOrder] @id INT, @date DATETIME2, @status TINYINT  
AS   
BEGIN   
  INSERT dbo.SalesOrders VALUES (@id, @date, @status);  
END  
go  
  
-- Natively Compiled.  
CREATE PROCEDURE [dbo].[InsertOrderXTP]  
      @id INT, @date DATETIME2, @status TINYINT  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS   
BEGIN ATOMIC WITH   
     (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english'  
     )  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status);  
END  
go  
  
SELECT * from SalesOrders;  
go  
  
EXECUTE dbo.InsertOrder @id= 10, @date = '1956-01-01 12:00:00', @status = 1;  
EXECUTE dbo.InsertOrderXTP @id= 11, @date = '1956-01-01 12:01:00', @status = 2;  
  
SELECT * from SalesOrders;  
```  
  
## <a name="see-also"></a>См. также:  
 [Миграция в In-Memory OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)   
 [Требования для использования таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/requirements-for-using-memory-optimized-tables.md)  
  
  
