---
title: Помощник по компиляции в собственный код | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
f1_keywords:
- sql12.swb.nativecompilationwizard.f1
- swb.nativecompilationwizard.f1
ms.assetid: d3898a47-2985-4a08-bc70-fd8331a01b7b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5174b5c859fa76ceeccdb99b7a46f510fd62d923
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63072775"
---
# <a name="native-compilation-advisor"></a>Помощник по собственной компиляции
  Средство создания отчетов о производительности транзакций (см. [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) информирует о том, какие интерпретируемые хранимые процедуры в базе данных смогут воспользоваться преимуществами перехода на компиляцию в собственном коде. После определения хранимой процедуры, для которой вы собираетесь использовать собственную компиляцию, можно запустить помощник по собственной компиляции, который облегчит миграцию интерпретированной хранимой процедуры для собственной компиляции. Дополнительные сведения о скомпилированных в собственном коде хранимых процедурах см. в разделе [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).  
  
 Чтобы начать, подключитесь к экземпляру, содержащему интерпретированную хранимую процедуру. Можно подключиться к экземпляру [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] . Однако если необходимо выполнить операцию миграции с помощником, необходимо подключиться к экземпляру [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] , на котором включена функциональность In-Memory OLTP. Дополнительные сведения о требованиях In-Memory OLTP см. в разделе [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md).  
  
 Дополнительные сведения о методологиях миграции см. в разделе [Выполняемая в памяти OLTP — стандартные шаблоны рабочей нагрузки и вопросы миграции](https://msdn.microsoft.com/library/dn673538.aspx).  
  
## <a name="walkthrough-using-the-native-compilation-advisor"></a>Пошаговое руководство по использованию помощника по собственной компиляции  
 В **обозревателе объектов**щелкните правой кнопкой мыши хранимую процедуру, которую необходимо преобразовать, и выберите пункт **Помощник по собственной компиляции**. Появится стартовая страница для **помощника по собственной компиляции хранимых процедур**. Для продолжения нажмите кнопку **Далее**.  
  
### <a name="stored-procedure-validation"></a>Проверка хранимых процедур  
 Эта страница сообщает, использует ли хранимая процедура какие-либо конструкции, несовместимые с собственной компиляцией. Можно нажать кнопку **Далее** , чтобы просмотреть данные. Если найдены конструкции, несовместимые с собственной компиляцией, можно нажать кнопку **Далее** , чтобы просмотреть подробности.  
  
### <a name="stored-procedure-validation-result"></a>Результат проверки хранимой процедуры  
 При наличии конструкций, несовместимых с собственной компиляцией, на странице **Результат проверки хранимой процедуры** будут выведены подробности. Можно создать отчет (нажав **Создание отчета**), выйти из **помощника по собственной компиляции**и изменить код таким образом, чтобы он был совместим с собственной компиляцией.  
  
## <a name="code-sample"></a>Пример кода  
 В следующем примере показана интерпретированная хранимая процедура и эквивалентная хранимая процедура для собственной компиляции. В примере подразумевается каталог c:\data.  
  
```sql  
CREATE DATABASE Demo  
ON  
PRIMARY(NAME = [Demo_data],  
FILENAME = 'C:\DATA\Demo_data.mdf', size=500MB)  
, FILEGROUP [Demo_fg] CONTAINS MEMORY_OPTIMIZED_DATA(  
NAME = [Demo_dir],  
FILENAME = 'C:\DATA\Demo_dir')  
LOG ON (name = [Demo_log], Filename='C:\DATA\Demo_log.ldf', size=500MB)  
COLLATE Latin1_General_100_BIN2;  
GO  
USE Demo;  
GO  
  
CREATE TABLE [dbo].[SalesOrders]  
(  
     [order_id] [int] NOT NULL,  
     [order_date] [datetime] NOT NULL,  
     [order_status] [tinyint] NOT NULL  
  
CONSTRAINT [PK_SalesOrders] PRIMARY KEY NONCLUSTERED HASH   
(  
     [order_id]  
)WITH ( BUCKET_COUNT = 2097152)  
)WITH ( MEMORY_OPTIMIZED = ON )  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrder] @id INT, @date DATETIME2, @status TINYINT  
AS   
BEGIN   
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrderXTP] @id INT, @date DATETIME2, @status TINYINT  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS   
BEGIN ATOMIC WITH   
(    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
     LANGUAGE = N'us_english')  
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
go  
  
select * from SalesOrders  
go  
exec dbo.InsertOrder @id= 10, @date = '1956-01-01 12:00:00', @status = 1 ;  
exec dbo.InsertOrderXTP @id= 11, @date = '1956-01-01 12:01:00', @status = 2 ;  
select * from SalesOrders  
```  
  
## <a name="see-also"></a>См. также:  
 [Миграция в In-Memory OLTP](migrating-to-in-memory-oltp.md)  
  
  
