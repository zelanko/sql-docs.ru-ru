---
description: sp_batch_params (Transact-SQL)
title: sp_batch_params (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_batch_params
- sp_batch_params_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_batch_params
ms.assetid: 7b92fe9e-e755-4b7a-8a15-822c58a813d3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d385c34f58e7796d7ed09fe5d5ba644f32a6eff1
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548307"
---
# <a name="sp_batch_params-transact-sql"></a>sp_batch_params (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает набор строк, содержащий сведения о параметрах, входящих в [!INCLUDE[tsql](../../includes/tsql-md.md)] пакет. **sp_batch_params** выполняет синтаксический анализ только указанного пакета и возвращает сведения о значениях внедренных параметров. Она не исполняет пакет и не меняет среду исполнения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_batch_params [ [ @tsqlbatch = ] 'tsqlbatch' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @tsqlbatch = ] 'tsqlbatch'` Строка в Юникоде, содержащая [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкцию или пакет, для которых требуются сведения о параметрах. *тсклбатч* имеет тип **nvarchar (max)** или неявно преобразуется в **nvarchar (max)**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**PARAMETER_NAME**|**sysname**|Имя параметра, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил в пакете.|  
|**COLUMN_TYPE**|**smallint**|Это поле возвращает одно из следующих значений:<br /><br /> 0 = SQL_PARAM_TYPE_UNKNOWN<br /><br /> 1 = SQL_PARAM_TYPE_INPUT<br /><br /> 2 = SQL_PARAM_TYPE_OUTPUT<br /><br /> 3 = SQL_RESULT_COL<br /><br /> 4 = SQL_PARAM_OUTPUT<br /><br /> 5 = SQL_RETURN_VALUE<br /><br /> Этот столбец всегда содержит значение 0.|  
|**DATA_TYPE**|**smallint**|Тип данных параметра (целочисленный код для типа данных ODBC). Если этот тип данных нельзя сопоставить с типом ISO, то значением будет NULL. Имя собственного типа данных возвращается в столбец **TYPE_NAME** . Это значение всегда равно NULL.|  
|**TYPE_NAME**|**sysname**|Строковое представление типа данных, как оно представляется в базовой СУБД. Значение NULL.|  
|**PRECISION**|**int**|Количество значащих цифр. Возвращаемое значение для столбца **точности** находится в базовом 10.|  
|**LENGTH**|**int**|Размер передаваемых данных. Значение NULL.|  
|**Измените**|**smallint**|Число цифр справа от десятичной запятой. Значение NULL.|  
|**RADIX**|**smallint**|Основание системы счисления для числовых типов. Значение NULL.|  
|**ОБНУЛЯЕМОГО**|**smallint**|Определяет допустимость значений NULL:<br /><br /> 1 = тип данных параметра может быть создан со значением NULL.<br /><br /> 0 = значения NULL недопустимы.<br /><br /> Значение NULL.|  
|**SQL_DATA_TYPE**|**smallint**|Значение системного типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], как оно показано в поле TYPE дескриптора. Этот столбец содержит то же значение, что и столбец **DATA_TYPE**, за исключением типов данных **datetime** и ISO **interval**. Этот столбец всегда возвращает значение. Значение NULL.|  
|**SQL_DATETIME_SUB**|**smallint**|Код **интервала** **DateTime** или ISO, если значение **SQL_DATA_TYPE** равно SQL_DATETIME или SQL_INTERVAL. Для типов данных, отличных от **datetime** и **interval** в стандарте ISO, это поле имеет значение NULL. Значение NULL.|  
|**CHAR_OCTET_LENGTH**|**int**|Максимальная длина в байтах для параметра **символьного** или **двоичного** типа данных. Для всех других типов данных этот столбец возвращает значение NULL. Это значение всегда равно NULL.|  
|**ORDINAL_POSITION**|**int**|Положение по порядку параметра в пакете. Если имя параметра повторяется несколько раз, то этот столбец содержит порядковый номер первого вхождения. Первый параметр имеет порядковый номер 1. Этот столбец всегда возвращает значение.|  
  
## <a name="permissions"></a>Разрешения  
 Разрешение на выполнение **sp_batch_params** предоставляется **общедоступному**.  
  
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
 [Разделы руководства по выполнению хранимых процедур &#40;ODBC&#41;](https://msdn.microsoft.com/library/c2220182-a23d-4475-b353-77a77ab613d6)   
 [Выполнение хранимых процедур (OLE DB)](../../relational-databases/native-client/ole-db/stored-procedures-running.md)  
  
  
