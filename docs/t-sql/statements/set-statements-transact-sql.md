---
title: "Инструкции SET (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET
- SET_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ISO SET statements
- queries [SQL Server], executing
- dates [SQL Server], SET statements
- time [SQL Server], SET statements
- SET statement, about SET statement
- SET statement
- statistical information [SQL Server], SET statements
- locking [SQL Server], SET statements
ms.assetid: f7e107f8-0fcf-408b-b30f-da2323eeb714
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f0426730b33f0b70fda11a8cb07242a365d10fae
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-statements-transact-sql"></a>Инструкции SET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Язык [!INCLUDE[tsql](../../includes/tsql-md.md)] предоставляет несколько инструкций SET, которые изменяют текущий сеанс, управляя специфическими данными. Инструкции SET группируются в категории, показанные в следующей таблице.  
  
 Сведения об установке локальных переменных с помощью инструкции SET см. в разделе [ЗАДАТЬ @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/set-local-variable-transact-sql.md).  
  
|Категория|Инструкции|  
|--------------|----------------|  
|Инструкции даты и времени|[SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md)<br /><br /> [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md)|  
|Инструкции блокировки|[SET DEADLOCK_PRIORITY](../../t-sql/statements/set-deadlock-priority-transact-sql.md)<br /><br /> [SET LOCK_TIMEOUT](../../t-sql/statements/set-lock-timeout-transact-sql.md)|  
|Прочие инструкции|[SET CONCAT_NULL_YIELDS_NULL](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md)<br /><br /> [SET CURSOR_CLOSE_ON_COMMIT](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md)<br /><br /> [SET FIPS_FLAGGER](../../t-sql/statements/set-fips-flagger-transact-sql.md)<br /><br /> [SET IDENTITY_INSERT](../../t-sql/statements/set-identity-insert-transact-sql.md)<br /><br /> [УСТАНОВИТЬ ЯЗЫК](../../t-sql/statements/set-language-transact-sql.md)<br /><br /> [НАБОР СМЕЩЕНИЯ](../../t-sql/statements/set-offsets-transact-sql.md)<br /><br /> [SET QUOTED_IDENTIFIER](../../t-sql/statements/set-quoted-identifier-transact-sql.md)|  
|Инструкции выполнения запросов|[SET ARITHABORT](../../t-sql/statements/set-arithabort-transact-sql.md)<br /><br /> [SET ARITHIGNORE](../../t-sql/statements/set-arithignore-transact-sql.md)<br /><br /> [SET FMTONLY](../../t-sql/statements/set-fmtonly-transact-sql.md)<br /><br /> Примечание.[!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<br /><br /> [SET NOCOUNT](../../t-sql/statements/set-nocount-transact-sql.md)<br /><br /> [SET NOEXEC](../../t-sql/statements/set-noexec-transact-sql.md)<br /><br /> [SET NUMERIC_ROUNDABORT](../../t-sql/statements/set-numeric-roundabort-transact-sql.md)<br /><br /> [SET PARSEONLY](../../t-sql/statements/set-parseonly-transact-sql.md)<br /><br /> [SET QUERY_GOVERNOR_COST_LIMIT](../../t-sql/statements/set-query-governor-cost-limit-transact-sql.md)<br /><br /> [SET ROWCOUNT](../../t-sql/statements/set-rowcount-transact-sql.md)<br /><br /> [SET TEXTSIZE](../../t-sql/statements/set-textsize-transact-sql.md)|  
|Инструкции настроек ISO|[SET ANSI_DEFAULTS](../../t-sql/statements/set-ansi-defaults-transact-sql.md)<br /><br /> [SET ANSI_NULL_DFLT_OFF](../../t-sql/statements/set-ansi-null-dflt-off-transact-sql.md)<br /><br /> [SET ANSI_NULL_DFLT_ON](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)<br /><br /> [SET ANSI_NULLS](../../t-sql/statements/set-ansi-nulls-transact-sql.md)<br /><br /> [SET ANSI_PADDING](../../t-sql/statements/set-ansi-padding-transact-sql.md)<br /><br /> [ПАРАМЕТР SET ANSI_WARNINGS](../../t-sql/statements/set-ansi-warnings-transact-sql.md)|  
|Статистические инструкции|[ИНСТРУКЦИЯ SET FORCEPLAN](../../t-sql/statements/set-forceplan-transact-sql.md)<br /><br /> [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md)<br /><br /> [ИНСТРУКЦИЯ SET SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md)<br /><br /> [SET SHOWPLAN_XML](../../t-sql/statements/set-showplan-xml-transact-sql.md)<br /><br /> [SET STATISTICS IO](../../t-sql/statements/set-statistics-io-transact-sql.md)<br /><br /> [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md)<br /><br /> [SET STATISTICS PROFILE](../../t-sql/statements/set-statistics-profile-transact-sql.md)<br /><br /> [ЗАДАТЬ STATISTICS TIME](../../t-sql/statements/set-statistics-time-transact-sql.md)|  
|Инструкции управления транзакциями|[SET IMPLICIT_TRANSACTIONS](../../t-sql/statements/set-implicit-transactions-transact-sql.md)<br /><br /> [SET REMOTE_PROC_TRANSACTIONS](../../t-sql/statements/set-remote-proc-transactions-transact-sql.md)<br /><br /> [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)<br /><br /> [ИНСТРУКЦИЯ SET XACT_ABORT](../../t-sql/statements/set-xact-abort-transact-sql.md)|  
  
## <a name="considerations-when-you-use-the-set-statements"></a>Рекомендации по использованию инструкций SET  
  
-   Все инструкции SET выполняются во время запуска или выполнения, за исключением FIPS_FLAGGER, SET OFFSETS, SET PARSEONLY и SET QUOTED_IDENTIFIER. Эти инструкции выполняются во время синтаксического анализа.  
  
-   Если инструкция SET запускается в хранимой процедуре или триггере, значение параметра инструкции SET восстанавливается после того, как управление вернется из хранимой процедуры или триггера. Кроме того Если инструкция SET указана в динамической строке SQL, которая выполняется с помощью **sp_executesql** или инструкции EXECUTE, значение параметра SET восстанавливается после возврата управления из пакета, указанного в динамической строке SQL.  
  
-   Хранимые процедуры выполняются с настройками SET, указанными во время выполнения, кроме инструкций SET ANSI_NULLS и SET QUOTED_IDENTIFIER. Хранимые процедуры, использующие инструкцию SET ANSI_NULLS или SET QUOTED_IDENTIFIER, используют настройку, указанную в хранимой процедуре во время создания. При использовании внутри хранимой процедуры любые установки SET игнорируются.  
  
-   **Пользовательских параметров** параметра **sp_configure** обеспечивает параметры на уровне сервера и работает в нескольких базах данных. Эта настройка ведет себя так же, как и явная инструкция SET, за исключением того, что возникает во время входа в систему.  
  
-   Настройки базы данных, устанавливаемые с помощью инструкции ALTER DATABASE, действительны только на уровне базы данных и применяются только при явном задании. Параметры базы данных перекрывают настройки параметров экземпляра, которые задаются с помощью **sp_configure**.  
  
-   Для любой из инструкций SET со значениями ON и OFF можно указать значения ON или OFF для множества параметров SET.  
  
    > [!NOTE]  
    >  Это неприменимо к статистическим параметрам SET.  
  
     Например `SET QUOTED_IDENTIFIER, ANSI_NULLS ON` устанавливает параметры QUOTED_IDENTIFIER и ANSI_NULLS в значение ON.  
  
-   Настройки инструкции SET перекрывают эквивалентные настройки параметров базы данных, которые были установлены с помощью инструкции ALTER DATABASE. Например, значение, указанное в инструкции SET ANSI_NULLS, перекроет настройку базы данных для параметра ANSI_NULL. Кроме того, некоторые настройки соединений автоматически устанавливаются на при подключении пользователя к базе данных на основе значений, вступили в силу, заданных предыдущим использованием **параметры пользователя хранимой процедуры sp_configure** параметр или значений, которые применяются для всех ODBC и Соединения OLE/DB.  
  
-   Настройка SET LOCK_TIMEOUT не влияет на выполнение инструкций ALTER, CREATE и DROP DATABASE.  
  
-   Каждая следующая инструкция SET, такая как SET ANSI_DEFAULTS, отменяет предыдущую настройку. Если индивидуальный параметр инструкции SET, связанной с сочетанием клавиш, явно устанавливается после вызова такого сочетания, то индивидуальная инструкция SET перекрывает подобную настройку.  
  
-   При использовании пакетов контекст базы данных определяется пакетом, установленным с помощью инструкции USE. Нерегламентированные запросы и все другие инструкции, которые выполняются за пределами хранимых процедур и которые содержатся в пакетах, наследуют настройки параметров базы данных и соединения, установленные с помощью инструкции USE.  
  
-   Запросы режима MARS совместно используют глобальное состояние, которое содержит большую часть настроек параметров SET последней сессии. Настройки SET могут измениться при выполнении любого запроса. Значения специфичны для контекста запроса, в котором они устанавливаются, и не влияют на другие параллельные запросы режима MARS. Однако после завершения выполнения запроса новые параметры SET копируются в глобальное состояние сеанса. Новые запросы, которые выполняются в том же самом сеансе, после этого изменения будут использовать новые значения параметров SET.  
  
-   При выполнении хранимой процедуры из пакета либо из другой хранимой процедуры она выполняется под значениями параметров, которые установлены в данный момент в базе данных, содержащей хранимую процедуру. Например, когда хранимые процедуры **db1.dbo.sp1** вызывает хранимую процедуру **db2.dbo.sp2**, хранимой процедуры **sp1** выполняется в текущий уровень совместимости параметр базы данных **db1**и хранимой процедуры **sp2** выполняется в соответствии с текущей настройкой уровня совместимости базы данных **db2**.  
  
-   Когда инструкция языка [!INCLUDE[tsql](../../includes/tsql-md.md)] ссылается на объект, который размещен на многих базах данных, к ней применяется текущий контекст базы данных и текущий контекст соединения. В этом случае, если инструкция языка [!INCLUDE[tsql](../../includes/tsql-md.md)] находится в пакете, текущим контекстом соединения является база данных, определенная инструкцией USE. Если инструкция языка [!INCLUDE[tsql](../../includes/tsql-md.md)] находится в хранимой процедуре, то контекстом соединения является база данных, которая содержит хранимую процедуру.  
  
-   При создании индексов на вычисляемых столбцах и индексированных представлениях, а также при управлении ими параметры SET ARITHABORT, CONCAT_NULL_YIELDS_NULL, QUOTED_IDENTIFIER, ANSI_NULLS, ANSI_PADDING и ANSI_WARNINGS должны иметь значение ON. Параметр NUMERIC_ROUNDABORT должен быть установлен в значение OFF.  
  
     Если необходимое значение любого из этих параметров не задано, инструкции INSERT, UPDATE, DELETE, DBCC CHECKDB и DBCC CHECKTABLE для индексированных представлений или таблиц с индексами на основе вычисляемых столбцов не смогут быть выполнены. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сформирует ошибку с указанием всех неправильно заданных параметров. Также [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет выполнять инструкции SELECT на этих таблицах или индексных представлениях, как будто индексы на вычисляемых столбцах или на представлениях не существуют.  
  
  

