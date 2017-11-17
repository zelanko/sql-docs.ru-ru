---
title: "SET CONCAT_NULL_YIELDS_NULL (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONCAT_NULL_YIELDS_NULL_TSQL
- SET CONCAT_NULL_YIELDS_NULL
- CONCAT_NULL_YIELDS_NULL
- SET_CONCAT_NULL_YIELDS_NULL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT_NULL_YIELDS_NULL option
- null values [SQL Server], concatenation results
- concatenation [SQL Server]
- SET CONCAT_NULL_YIELDS_NULL statement
ms.assetid: 3091b71c-6518-4eb4-88ab-acae49102bc5
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 60281ff903bf7eb04165a65e8f2b75a80f589780
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-concatnullyieldsnull-transact-sql"></a>SET CONCAT_NULL_YIELDS_NULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Управляет представлением результатов объединения в виде значений NULL или пустых строковых значений.  
  
> [!IMPORTANT]  
>  В будущей версии параметр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CONCAT_NULL_YIELDS_NULL всегда будет иметь значение ON, а приложения, явно присваивающие ему значение OFF, будут вызывать ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  
    
SET CONCAT_NULL_YIELDS_NULL { ON | OFF }   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET CONCAT_NULL_YIELDS_NULL ON    
```  
  
## <a name="remarks"></a>Замечания  
 Когда параметр SET CONCAT_NULL_YIELDS_NULL установлен в ON, объединение значения NULL со строкой дает в результате NULL. Например, `SELECT 'abc' + NULL` дает в результате `NULL`. Когда параметр SET CONCAT_NULL_YIELDS_NULL установлен в значение OFF, объединение значения NULL со строкой дает в результате исходную строку (значение NULL рассматривается как пустая строка). Например, `SELECT 'abc' + NULL` дает в результате `abc`.  
  
 Если параметр SET CONCAT_NULL_YIELDS_NULL не задан, параметр **CONCAT_NULL_YIELDS_NULL** применяется параметр базы данных.  
  
> [!NOTE]  
>  SET CONCAT_NULL_YIELDS_NULL — это такая же установка, что и установка CONCAT_NULL_YIELDS_NULL для ALTER DATABASE.  
  
 Настройка SET CONCAT_NULL_YIELDS_NULL устанавливается во время выполнения или запуска, но не во время синтаксического анализа.  
  
 Параметр SET CONCAT_NULL_YIELDS_NULL должен быть в состоянии ON при создании или изменении индексов в вычисляемых столбцах или индексированных представлениях. Если параметр SET CONCAT_NULL_YIELDS_NULL установлен в OFF, любое применение инструкций CREATE, UPDATE, INSERT и DELETE к таблицам с индексами на вычисляемых столбцах или к индексированным представлениям завершится ошибкой. Дополнительные сведения о необходимых УСТАНОВКАХ параметров SET для индексированных представлений и индексов на вычисляемых столбцах см. в разделе «Вопросы при вы использования операторов SET» в [инструкции SET &#40; Transact-SQL &#41; ](../../t-sql/statements/set-statements-transact-sql.md).  
  
 Когда параметр CONCAT_NULL_YIELDS_NULL установлен в OFF, объединение строк через границы сервера становится невозможным.  
  
 Чтобы просмотреть текущее значение параметра для этого параметра, выполните следующий запрос.  
  
```  
DECLARE @CONCAT_NULL_YIELDS_NULL VARCHAR(3) = 'OFF';  
IF ( (4096 & @@OPTIONS) = 4096 ) SET @CONCAT_NULL_YIELDS_NULL = 'ON';  
SELECT @CONCAT_NULL_YIELDS_NULL AS CONCAT_NULL_YIELDS_NULL;  
  
```  
  
## <a name="examples"></a>Примеры  
 Следующий пример демонстрирует использование обеих настроек `SET CONCAT_NULL_YIELDS_NULL`.  
  
```  
PRINT 'Setting CONCAT_NULL_YIELDS_NULL ON';  
GO  
-- SET CONCAT_NULL_YIELDS_NULL ON and testing.  
SET CONCAT_NULL_YIELDS_NULL ON;  
GO  
SELECT 'abc' + NULL ;  
GO  
  
-- SET CONCAT_NULL_YIELDS_NULL OFF and testing.  
SET CONCAT_NULL_YIELDS_NULL OFF;  
GO  
SELECT 'abc' + NULL;   
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/sessionproperty-transact-sql.md)  
  
  

