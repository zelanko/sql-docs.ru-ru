---
title: "Изменение скомпилированных в собственном коде модулей T-SQL | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 010318a0-6807-47c3-8ecc-bb7cb60513f0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4696039c56ebf5f1fd6ea440cd27da84721f35b9
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="altering-natively-compiled-t-sql-modules"></a>Изменение скомпилированных в собственном коде модулей T-SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  В [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (и более поздних версиях) и [!INCLUDE[ssSDS](../../includes/sssds-md.md)] можно выполнять операции ALTER применительно к скомпилированным в собственном коде хранимым процедурам и другим скомпилированным в собственном коде модулям T-SQL, например определяемым пользователем скалярным функциям и триггерам, с помощью инструкции ALTER.  
  
 При выполнении инструкции ALTER скомпилированный в собственном коде модуль T-SQL перекомпилируется с использованием нового определения. Во время перекомпиляции старую версию модуля все еще можно выполнить. После завершения компиляции выполнение модуля постепенно завершается, и устанавливается новая версия модуля. При изменении скомпилированного в собственном коде модуля T-SQL можно изменить перечисленные ниже параметры.  
  
-   Параметры  
  
-   EXECUTE AS  
  
-   TRANSACTION ISOLATION LEVEL  
  
-   LANGUAGE  
  
-   DATEFIRST  
  
-   DATEFORMAT  
  
-   DELAYED_DURABILITY  
  
> [!NOTE]  
>  Невозможно преобразовать скомпилированные в собственном коде модули T-SQL в модули, не скомпилированные в собственном коде. Невозможно преобразовать модули T-SQL, не скомпилированные в собственном коде, в модули, скомпилированные в собственном коде.  
  
 Дополнительные сведения о функции ALTER PROCEDURE и ее синтаксисе см. в разделе [ALTER PROCEDURE (Transact-SQL)](../../t-sql/statements/alter-procedure-transact-sql.md).  
  
 Вы можете выполнить sp_recompile для скомпилированного в собственном коде модуля T-SQL, что приведет к повторной компиляции при следующем выполнении.  
  
## <a name="example"></a>Пример  
 В следующем примере создается оптимизированная для памяти таблица (T1) и скомпилированная в собственном коде хранимая процедура (SP1), которая выбирает все столбцы таблицы T1. Затем процедура SP1 изменяется: из нее удаляется предложение EXECUTE AS, в ней меняется параметр LANGUAGE, а из таблицы T1 выбирается только один столбец (C1).  
  
```  
CREATE TABLE [dbo].[T1]  
(  
[c1] [int] NOT NULL,  
[c2] [float] NOT NULL,  
CONSTRAINT [PK_T1] PRIMARY KEY NONCLUSTERED ([c1])  
)WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
CREATE PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english'  
)  
 SELECT c1, c2 from dbo.T1  
END  
GO  
  
ALTER PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'Dutch'  
)  
 SELECT c1 from dbo.T1  
END  
GO  
  
```  
  
  

