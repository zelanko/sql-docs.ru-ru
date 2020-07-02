---
title: sp_OAGetProperty (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OAGetProperty_TSQL
- sp_OAGetProperty
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OAGetProperty
ms.assetid: 240eeeb9-6d8b-4930-b912-1d273ca0ab38
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 753ee7cc87546c180a911ffef9c54efe143f1faf
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85734318"
---
# <a name="sp_oagetproperty-transact-sql"></a>sp_OAGetProperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Получает значение свойства объекта OLE.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_OAGetProperty objecttoken , propertyname   
    [ , propertyvalue OUTPUT ]  
    [ , index...]   
```  
  
## <a name="arguments"></a>Аргументы  
 *обжекттокен*  
 Токен объекта OLE, который был создан ранее с помощью **sp_OACreate**.  
  
 *propertyname*  
 Возвращаемое имя свойства объекта OLE.  
  
 *propertyvalue* **выходные данные** PropertyValue  
 Значение возвращаемого свойства. Если значение указано, оно должно быть локальной переменной соответствующего типа данных.  
  
 Если свойство возвращает объект OLE, *propertyvalue* должен быть локальной переменной типа данных **int**. Токен объекта хранится в локальной переменной, и этот маркер объекта можно использовать с другими хранимыми процедурами OLE-автоматизации.  
  
 Если свойство возвращает одно значение, либо укажите локальную переменную для *propertyvalue*, которая возвращает значение свойства в локальной переменной. или не указывайте *propertyvalue*, который возвращает значение свойства клиенту в виде однострочного результирующего набора с одним столбцом.  
  
 Если свойство возвращает массив, если параметр *propertyvalue* задан, ему ПРИСВАИВАЕТСЯ значение null.  
  
 Если указан *propertyvalue* , но свойство не возвращает значение, возникает ошибка. Если свойство возвращает массив более двух измерений, то возникает ошибка.  
  
 *номер*  
 Индексный параметр. Если этот параметр указан, *индекс* должен иметь значение соответствующего типа данных.  
  
 Некоторые свойства имеют параметры. Эти свойства называются индексированными свойствами, а параметры — индексными параметрами. Свойство может иметь несколько индексных параметров.  
  
> [!NOTE]  
>  Параметры для этой хранимой процедуры задаются по положению, а не по имени.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое число (неуспешное завершение), которое является целочисленным значением типа HRESULT, возвращаемого объектом OLE-автоматизации.  
  
 Дополнительные сведения о кодах возврата HRESULT см. в разделе [коды возврата OLE Automation и сведения об ошибке](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если свойство возвращает массив с одним или двумя измерениями, то массив возвращается клиенту как результирующий набор.  
  
-   Одномерный массив возвращается клиенту как результирующий набор, состоящий из одной строки, в которой число столбцов соответствует количеству элементов массива. Иными словами, массив возвращается в виде набора столбцов.  
  
-   Двумерный массив возвращается клиенту в виде результирующего набора с числом столбцов, равным числу элементов первого измерения массива, и числом строк, равным числу элементов второго измерения массива. Иными словами, массив возвращается в виде (столбцы, строки).  
  
 Если возвращаемое значение свойства или возвращаемое значение метода является массивом, **sp_OAGetProperty** или **sp_OAMethod** возвращает клиенту результирующий набор. (Выходные параметры метода не могут быть массивами.) Эти процедуры просматривают все значения в массиве для определения подходящих типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их длин для каждого столбца результирующего набора. Для каждого отдельного столбца эти процедуры используют тип и длину данных, необходимые для представления всех значений данных этого столбца.  
  
 Если все значения данных в столбце имеют один и тот же тип данных, этот тип используется для всего столбца. Если значения данных в столбце имеют различные типы данных, тип данных всего столбца определяется по следующей схеме.  
  
||INT|FLOAT|money|DATETIME|varchar|nvarchar|  
|------|---------|-----------|-----------|--------------|-------------|--------------|  
|**int**|**int**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**float**|**float**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**money**|**money**|**money**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**datetime**|**varchar**|**varchar**|**varchar**|**datetime**|**varchar**|**nvarchar**|  
|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**nvarchar**|  
|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|  
  
## <a name="remarks"></a>Примечания  
 Для получения значения свойства также можно использовать **sp_OAMethod** .  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли сервера **sysadmin** или разрешение EXECUTE непосредственно в этой хранимой процедуре. `Ole Automation Procedures`для использования любой системной процедуры, связанной с OLE Automation, необходимо **включить** конфигурацию.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-a-local-variable"></a>A. Использование локальной переменной  
 В следующем примере показано получение `HostName` Свойства (ранее созданного объекта **SQLServer** ) и его сохранение в локальной переменной.  
  
```  
DECLARE @property varchar(255);  
EXEC @hr = sp_OAGetProperty @object, 'HostName', @property OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END  
PRINT @property;  
```  
  
### <a name="b-using-a-result-set"></a>Б. Использование результирующего набора  
 В следующем примере показано получение `HostName` Свойства (ранее созданного объекта **SQLServer** ) и его возврат клиенту в качестве результирующего набора.  
  
```  
EXEC @hr = sp_OAGetProperty @object, 'HostName';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры OLE-автоматизации &#40;&#41;Transact — SQL](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Пример скрипта OLE-автоматизации](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
