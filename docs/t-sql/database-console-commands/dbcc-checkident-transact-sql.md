---
title: "Инструкция DBCC CHECKIDENT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKIDENT
- DBCC CHECKIDENT
- CHECKIDENT_TSQL
- DBCC_CHECKIDENT_TSQL
dev_langs: TSQL
helpviewer_keywords:
- checking identity values
- reseeding identity values
- resetting identity values
- identity values [SQL Server]
- identity values [SQL Server], checking
- modifying identity values
- current identity values
- DBCC CHECKIDENT statement
- identity values [SQL Server], reseeding
- reporting current identity values
ms.assetid: 2c00ee51-2062-4e47-8b19-d90f524c6427
caps.latest.revision: "63"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Active
ms.openlocfilehash: 0a370a89e175a00f33d26992cfc5c6aaecbd7436
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-checkident-transact-sql"></a>DBCC CHECKIDENT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Проверяет текущее значение идентификатора для указанной таблицы в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и при необходимости изменяет значение идентификатора. Также инструкцию DBCC CHECKIDENT можно использовать для ручной установки нового текущего значения идентификатора для столбца идентификаторов.  
   
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DBCC CHECKIDENT   
 (   
    table_name  
        [, { NORESEED | { RESEED [, new_reseed_value ] } } ]  
)  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_таблицы*  
 Это имя таблицы, для которой выполняется проверка текущего значения идентификатора. Указанная таблица должна содержать столбец идентификаторов. Имена таблиц должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md). Имена двух или трех частей должен иметь разделители, например «Person.AddressType» или [Person.AddressType].   
  
 NORESEED  
 Определяет, что текущее значение идентификатора не должно изменяться.  
  
 RESEED  
 Определяет, что текущее значение идентификатора должно изменяться.  
  
 *new_reseed_value*  
 Новое значение, предназначенное для использования в качестве текущего значения для столбца идентификаторов.  
  
 WITH NO_INFOMSGS  
 Подавляет вывод всех информационных сообщений.  
  
## <a name="remarks"></a>Remarks  
 Конкретные изменения, вносимые в текущее значение идентификатора, зависят от определений параметров.  
  
|команда DBCC CHECKIDENT|Изменение текущего значения идентификатора или идентификаторов|  
|-----------------------------|---------------------------------------------|  
|Инструкция DBCC CHECKIDENT ( *table_name*, NORESEED)|Текущее значение идентификатора не сбрасывается. Инструкция DBCC CHECKIDENT возвращает текущее значение идентификатора и текущее максимальное значение столбца идентификаторов. Если эти два значения не равны друг другу, необходимо сбросить значение идентификатора, чтобы избежать потенциальных ошибок или пропусков в последовательности значений.|  
|Инструкция DBCC CHECKIDENT ( *table_name* )<br /><br /> либо<br /><br /> Инструкция DBCC CHECKIDENT ( *table_name*, RESEED)|Если текущее значение идентификатора таблицы меньше, чем максимальное значение из содержащихся в столбце, оно устанавливается в максимальное значение в столбце идентификаторов. См. раздел «Исключения» далее.|  
|Инструкция DBCC CHECKIDENT ( *table_name*, RESEED, *new_reseed_value* )|Текущее значение идентификатора равно *new_reseed_value*. Если строки не были вставлены в таблицу с момента создания таблицы или если все строки были удалены с помощью инструкции TRUNCATE TABLE, первая строка, вставляемая после запуска инструкции DBCC CHECKIDENT использует *new_reseed_value* с удостоверением.<br /><br /> Если строки присутствуют в таблице, следующая строка вставляется с *new_reseed_value* значение. В версии [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] и более ранних версий, используется следующая Вставляемая строка *new_reseed_value* + [текущий шаг](../../t-sql/functions/ident-incr-transact-sql.md) значение.<br /><br /> Если таблица не пустая, установка значения идентификатора меньше, чем максимальное значение столбца идентификаторов может привести к одному из следующих условий.<br /><br /> -Если существует ограничение PRIMARY KEY или UNIQUE для столбца идентификаторов, сообщение об ошибке 2627 будут создаваться на последующие операции вставки в таблицу, так как созданное значение идентификатора будет конфликтовать с существующими значениями.<br /><br /> -Если ограничение PRIMARY KEY или UNIQUE не существует, последующие операции вставки приведет к дублированию значений идентификаторов.|  
  
## <a name="exceptions"></a>Исключения  
 В следующей таблице перечислены условия, при которых инструкция DBCC CHECKIDENT не будет выполнять автоматический сброс текущего значения идентификатора, а также представлены способы сброса значения.  
  
|Условие|Способы сброса|  
|---------------|-------------------|  
|Текущее значение идентификатора больше максимального значения в таблице.|Выполните инструкцию DBCC CHECKIDENT (*table_name*, NORESEED) чтобы определить текущее максимальное значение в столбце, а затем указать это значение как *new_reseed_value* в инструкцию DBCC CHECKIDENT (*table_ имя*, RESEED,*new_reseed_value*) команды.<br /><br /> -ИЛИ-<br /><br /> Выполните инструкцию DBCC CHECKIDENT (*table_name*, RESEED,*new_reseed_value*) с *new_reseed_value* слишком маленькое значение, а затем запустите инструкцию DBCC CHECKIDENT ( *имя_таблицы*, RESEED) чтобы исправить это значение.|  
|Из таблицы удалены все строки.|Выполните инструкцию DBCC CHECKIDENT (*table_name*, RESEED,*new_reseed_value*) с *new_reseed_value* присвоено нужным начальным значением.|  
  
## <a name="changing-the-seed-value"></a>Изменение начального значения  
 Начальное значение представляет собой значение, вставляемое в столбец идентификаторов для самой первой строки, загружаемой в таблицу. Все последующие строки содержат текущее значение идентификатора, увеличенное на значение приращения, где текущее значение идентификатора представляет собой последнее значение идентификатора, сформированное для таблицы или представления.  
  
 Инструкцию DBCC CHECKIDENT нельзя использовать для выполнения следующих задач.  
  
-   Изменение исходного начального значения, которое было указано для столбца идентификаторов при создании таблицы или представления.  
  
-   Повторное указание начального значения для существующих строк в таблице или представлении.  
  
 Чтобы изменить исходное начальное значение и повторно задать начальное значение для каких-либо существующих строк, необходимо удалить столбец идентификаторов и создать его повторно, указав новое начальное значение. Если таблица содержит данные, то номера идентификаторов добавляются к существующим строкам с учетом указанного начального значения и приращения. Порядок, в котором выполняется обновление строк, не гарантирован.  
  
## <a name="result-sets"></a>Результирующие наборы  
 В зависимости от того, указаны ли какие-либо параметры для таблицы, содержащей столбец идентификаторов, инструкция DBCC CHECKIDENT возвращает следующее сообщение для всех операций за исключением случаев, когда задается новое начальное значение.  
  
`Checking identity information: current identity value '\<current identity value>', current column value '\<current column value>'. DBCC execution completed. If DBCC printed error messages, contact your system administrator.`
  
 При использовании инструкции DBCC CHECKIDENT для указания нового начального значения с помощью RESEED *new_reseed_value*, возвращается следующее сообщение.  
  
`Checking identity information: current identity value '\<current identity value>'. DBCC execution completed. If DBCC printed error messages, contact your system administrator.`
  
## <a name="permissions"></a>Разрешения  
 Вызывающий объект должен быть владельцем схемы, содержащей таблицу или быть членом **sysadmin** предопределенной роли сервера **db_owner** предопределенной роли базы данных или **db_ddladmin** исправлена роль базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-resetting-the-current-identity-value-if-it-is-needed"></a>A. Сброс текущего значения идентификатора при необходимости  
 В следующем примере при необходимости сбрасывается текущее значение идентификатора для указанной таблицы в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
DBCC CHECKIDENT ('Person.AddressType');  
GO  
```  
  
### <a name="b-reporting-the-current-identity-value"></a>Б. Выдача текущего значения идентификатора  
 В следующем примере возвращается текущее значение идентификатора из указанной таблицы базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], при этом не исправляя значение идентификатора, если оно окажется неверным.  
  
```  
USE AdventureWorks2012;   
GO  
DBCC CHECKIDENT ('Person.AddressType', NORESEED);   
GO  
  
```  
  
### <a name="c-forcing-the-current-identity-value-to-a-new-value"></a>В. Принудительная установка нового значения текущему значению идентификатора  
 Следующий пример принудительно устанавливает для идентификатора значение 10 в столбце `AddressTypeID` для таблицы `AddressType`. Поскольку таблица уже содержит строки, то следующая вставляемая строка будет использовать в качестве значения 11, то есть новое текущее значение, определенное для значения столбца, плюс 1.  
  
```  
USE AdventureWorks2012;  
GO  
DBCC CHECKIDENT ('Person.AddressType', RESEED, 10);  
GO  
  
```  
  
## <a name="see-also"></a>См. также  
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Свойство IDENTITY (Transact-SQL)](../../t-sql/statements/create-table-transact-sql-identity-property.md)  
[Репликация столбцов идентификаторов](../../relational-databases/replication/publish/replicate-identity-columns.md)  
[USE (Transact-SQL)](../../t-sql/language-elements/use-transact-sql.md)  
[IDENT_SEED &#40; Transact-SQL &#41;](../../t-sql/functions/ident-seed-transact-sql.md)  
[IDENT_INCR &#40; Transact-SQL &#41;](../../t-sql/functions/ident-incr-transact-sql.md)  
  
  
