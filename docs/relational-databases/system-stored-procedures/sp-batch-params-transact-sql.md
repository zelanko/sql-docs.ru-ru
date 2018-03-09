---
title: "sp_batch_params (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_batch_params
- sp_batch_params_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_batch_params
ms.assetid: 7b92fe9e-e755-4b7a-8a15-822c58a813d3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 227cd0de3f89c7cbde4c5cb401edb60294a19940
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spbatchparams-transact-sql"></a>sp_batch_params (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает набор строк, содержащий сведения о параметрах, включенных в [!INCLUDE[tsql](../../includes/tsql-md.md)] пакета. **sp_batch_params** только синтаксический анализ указанного пакета и возвращает сведения о значениях внедренных параметров. Она не исполняет пакет и не меняет среду исполнения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_batch_params [ [ @tsqlbatch = ] 'tsqlbatch' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@tsqlbatch =**] **"***tsqlbatch***"**  
 Строка в Юникоде, содержащий [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкцию или пакет, для какой параметр сведения — это, нужно. *tsqlbatch* — **nvarchar(max)** или могут быть неявно преобразованы **nvarchar(max)**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**ИМЯ_ПАРАМЕТРА**|**sysname**|Имя параметра, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил в пакете.|  
|**COLUMN_TYPE**|**smallint**|Это поле возвращает одно из следующих значений:<br /><br /> 0 = SQL_PARAM_TYPE_UNKNOWN<br /><br /> 1 = SQL_PARAM_TYPE_INPUT<br /><br /> 2 = SQL_PARAM_TYPE_OUTPUT<br /><br /> 3 = SQL_RESULT_COL<br /><br /> 4 = SQL_PARAM_OUTPUT<br /><br /> 5 = SQL_RETURN_VALUE<br /><br /> Этот столбец всегда содержит значение 0.|  
|**ТИП ДАННЫХ**|**smallint**|Тип данных параметра (целочисленный код для типа данных ODBC). Если этот тип данных нельзя сопоставить с типом ISO, то значением будет NULL. Собственное имя типа данных возвращается в **TYPE_NAME** столбца. Это значение всегда равно NULL.|  
|**TYPE_NAME**|**sysname**|Строковое представление типа данных, как оно представляется в базовой СУБД. Значение NULL.|  
|**ТОЧНОСТЬ**|**int**|Количество значащих цифр. Возвращаемое значение для **точности** столбец имеет десятичную форму.|  
|**LENGTH**|**int**|Размер передаваемых данных. Значение NULL.|  
|**МАСШТАБ**|**smallint**|Число цифр справа от десятичной запятой. Значение NULL.|  
|**ОСНОВАНИЕ СИСТЕМЫ СЧИСЛЕНИЯ**|**smallint**|Основание системы счисления для числовых типов. Значение NULL.|  
|**ДОПУСКАЮЩИЕ ЗНАЧЕНИЯ NULL**|**smallint**|Определяет допустимость значений NULL:<br /><br /> 1 = тип данных параметра может быть создан со значением NULL.<br /><br /> 0 = значения NULL недопустимы.<br /><br /> Значение NULL.|  
|**SQL_DATA_TYPE**|**smallint**|Значение системного типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], как оно показано в поле TYPE дескриптора. Этот столбец содержит то же, как **DATA_TYPE** столбца, за исключением **datetime** и ISO **интервал** типов данных. Этот столбец всегда возвращает значение. Значение NULL.|  
|**SQL_DATETIME_SUB**|**smallint**|**Datetime** или ISO **интервал** Доп. Если значение **SQL_DATA_TYPE** равно SQL_DATETIME или SQL_INTERVAL. Для типов данных, отличный от **datetime** и ISO **интервал**, этот столбец равен NULL. Значение NULL.|  
|**CHAR_OCTET_LENGTH**|**int**|Максимальная длина в байтах **символ** или **двоичных** параметр типа данных. Для всех других типов данных этот столбец возвращает значение NULL. Это значение всегда равно NULL.|  
|**ORDINAL_POSITION**|**int**|Положение по порядку параметра в пакете. Если имя параметра повторяется несколько раз, то этот столбец содержит порядковый номер первого вхождения. Первый параметр имеет порядковый номер 1. Этот столбец всегда возвращает значение.|  
  
## <a name="permissions"></a>Permissions  
 Разрешение на выполнение **sp_batch_params** предоставляется **открытый**.  
  
## <a name="examples"></a>Примеры  
 Следующий пример показывает запрос, передаваемый в процедуру `sp_batch_params`. Результирующий набор перечисляет список значений внедренных параметров.  
  
```  
DECLARE @SQLString nvarchar(500);  
/* Build the SQL string */  
SET @SQLString =  
     N'SELECT * FROM AdventureWorks2012.HumanResources.Employee   
     WHERE BusinessEntityID = @BusinessEntityID';  
EXECUTE sp_batch_params @SQLString;  
```  
  
## <a name="see-also"></a>См. также:  
 [Выполнение хранимых процедур](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Выполнение хранимой процедуры инструкции &#40; ODBC &#41;](http://msdn.microsoft.com/library/c2220182-a23d-4475-b353-77a77ab613d6)   
 [Выполнение хранимой процедуры &#40; OLE DB &#41;](../../relational-databases/native-client/ole-db/stored-procedures-running.md)  
  
  
