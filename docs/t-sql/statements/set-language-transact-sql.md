---
title: "SET LANGUAGE (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 06/05/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_LANGUAGE_TSQL
- SET LANGUAGE
dev_langs:
- TSQL
helpviewer_keywords:
- LANGUAGE option
- languages [SQL Server], setting language
- SET LANGUAGE statement
- options [SQL Server], date
- default languages
ms.assetid: 0ec0e5cf-e115-4be9-a0db-e65837d6fa45
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 606c97d144bf209836ae89db199bd4d81ef137c0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="set-language-transact-sql"></a>SET LANGUAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Устанавливает языковое окружение сеанса. Язык сеанса определяет форматы **datetime** и системные сообщения.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET LANGUAGE { [ N ] 'language' | @language_var }   
```  
  
## <a name="arguments"></a>Аргументы  
 [**N**]**'***language***'** | **@***language_var*  
 Имя языка, хранящееся в [sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md). Этот аргумент может быть указан либо в кодировке Юникод, либо в двухбайтовой кодировке (DBCS), преобразуемой в Юникод. Чтобы указать язык в Юникоде, воспользуйтесь параметром **N'***language***'**. Если указана переменная, то она должна иметь тип **sysname**.  
  
## <a name="remarks"></a>Remarks  
 Установка SET LANGUAGE может производиться на этапе запуска или выполнения, но не на этапе синтаксического анализа.  
  
 SET LANGUAGE неявно задает параметр [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере производится установка языка по умолчанию `Italian`, отображение названия месяца, переключение обратно на язык `us_english` и снова отображение названия месяца.  
  
```  
DECLARE @Today DATETIME;  
SET @Today = '12/5/2007';  
  
SET LANGUAGE Italian;  
SELECT DATENAME(month, @Today) AS 'Month Name';  
  
SET LANGUAGE us_english;  
SELECT DATENAME(month, @Today) AS 'Month Name' ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)   
 [sp_helplanguage (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
