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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0a8c87eb8ed41b1669cf423aaccb8b06ee8b0e54
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47690012"
---
# <a name="spoagetproperty-transact-sql"></a>sp_OAGetProperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Получает значение свойства объекта OLE.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_OAGetProperty objecttoken , propertyname   
    [ , propertyvalue OUTPUT ]  
    [ , index...]   
```  
  
## <a name="arguments"></a>Аргументы  
 *objecttoken*  
 Токен OLE-объекта, который ранее был создан с помощью **sp_OACreate**.  
  
 *propertyname*  
 Возвращаемое имя свойства объекта OLE.  
  
 *propertyvalue* **выходных данных**  
 Значение возвращаемого свойства. Если значение указано, оно должно быть локальной переменной соответствующего типа данных.  
  
 Если свойство возвращает объект OLE, *propertyvalue* должен быть локальной переменной типа данных **int**. Токен объекта сохранен в локальной переменной. Этот токен может использоваться другими хранимыми процедурами OLE-автоматизации.  
  
 Если свойство возвращает одно значение, либо указать локальную переменную для *propertyvalue*, который возвращает свойство, значение в локальной переменной, либо не указывайте *propertyvalue*, который возвращает значение свойства клиенту в виде результирующего набора с одним столбцом и одной строки.  
  
 Если это свойство возвращает массив, если *propertyvalue* указан, ему присваивается значение NULL.  
  
 Если *propertyvalue* указан, но свойство не возвращает значение, возникает ошибка. Если свойство возвращает массив более двух измерений, то возникает ошибка.  
  
 *index*  
 Индексный параметр. Если указано, *индекс* должен быть величиной соответствующего типа данных.  
  
 Некоторые свойства имеют параметры. Эти свойства называются индексированными свойствами, а параметры — индексными параметрами. Свойство может иметь несколько индексных параметров.  
  
> [!NOTE]  
>  Параметры для этой хранимой процедуры задаются по положению, а не по имени.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое число (неуспешное завершение), которое является целочисленным значением типа HRESULT, возвращаемого объектом OLE-автоматизации.  
  
 Дополнительные сведения о кодах возврата HRESULT см. в разделе [OLE Automation коды возврата и сведения об ошибках](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если свойство возвращает массив с одним или двумя измерениями, то массив возвращается клиенту как результирующий набор.  
  
-   Одномерный массив возвращается клиенту как результирующий набор, состоящий из одной строки, в которой число столбцов соответствует количеству элементов массива. Иными словами, массив возвращается в виде набора столбцов.  
  
-   Двумерный массив возвращается клиенту в виде результирующего набора с числом столбцов, равным числу элементов первого измерения массива, и числом строк, равным числу элементов второго измерения массива. Иными словами, массив возвращается в виде (столбцы, строки).  
  
 Если возвращаемое значение свойства или метода значение является массивом, **sp_OAGetProperty** или **sp_OAMethod** возвращает результирующий набор клиенту. (Выходные параметры метода не могут быть массивами.) Эти процедуры просматривают все значения в массиве для определения подходящих типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их длин для каждого столбца результирующего набора. Для каждого отдельного столбца эти процедуры используют тип и длину данных, необходимые для представления всех значений данных этого столбца.  
  
 Если все значения данных в столбце имеют один и тот же тип данных, этот тип используется для всего столбца. Если значения данных в столбце имеют различные типы данных, тип данных всего столбца определяется по следующей схеме.  
  
||ssNoversion|FLOAT|money|DATETIME|varchar|NVARCHAR|  
|------|---------|-----------|-----------|--------------|-------------|--------------|  
|**int**|**int**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**float**|**float**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**money**|**money**|**money**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**datetime**|**varchar**|**varchar**|**varchar**|**datetime**|**varchar**|**nvarchar**|  
|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**nvarchar**|  
|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|  
  
## <a name="remarks"></a>Примечания  
 Можно также использовать **sp_OAMethod** для получения значения свойства.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-a-local-variable"></a>A. Использование локальной переменной  
 В следующем примере возвращается `HostName` свойство (созданного ранее **SQLServer** объекта) и сохраняет его в локальной переменной.  
  
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
 В следующем примере возвращается `HostName` свойство (созданного ранее **SQLServer** объекта) и возвращает его клиенту в виде результирующего набора.  
  
```  
EXEC @hr = sp_OAGetProperty @object, 'HostName';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
```  
  
## <a name="see-also"></a>См. также  
 [OLE Automation хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Пример скрипта OLE-автоматизации](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
