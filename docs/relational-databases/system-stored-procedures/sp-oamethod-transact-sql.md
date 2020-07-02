---
title: sp_OAMethod (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OAMethod
- sp_OAMethod_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OAMethod
ms.assetid: 1dfaebe2-c7cf-4041-a586-5d04faf2e25e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3a9c125b718d3d48888499828ea84e9c5ab28d1e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758783"
---
# <a name="sp_oamethod-transact-sql"></a>sp_OAMethod (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Вызывает метод OLE-объекта.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_OAMethod objecttoken , methodname  
    [ , returnvalue OUTPUT ]   
    [ , [ @parametername = ] parameter [ OUTPUT ] [ ...n ] ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *обжекттокен*  
 Токен объекта OLE, который был создан ранее с помощью **sp_OACreate**.  
  
 *имя_метода*  
 Имя вызываемого метода OLE-объекта.  
  
 _returnvalue_**выходные данные** ReturnValue    
 Возвращаемое значение метода OLE-объекта. Если значение указано, оно должно быть локальной переменной соответствующего типа данных.  
  
 Если метод возвращает одно значение, укажите локальную переменную для *ReturnValue*, возвращающую возвращаемое значение метода в локальной переменной, или не указывайте *ReturnValue*, которая возвращает возвращаемое значение метода клиенту в виде однострочного результирующего набора с одним столбцом.  
  
 Если возвращаемое значение метода является объектом OLE, то параметр *ReturnValue* должен быть локальной переменной типа данных **int**. Токен объекта хранится в локальной переменной, и этот маркер объекта можно использовать с другими хранимыми процедурами OLE-автоматизации.  
  
 Если возвращаемое значение метода является массивом, если *ReturnValue* задано, то для него задается значение null.  
  
 Ошибка выдается в одном из следующих случаев.  
  
-   указана *ReturnValue* , но метод не возвращает значение.  
  
-   Метод возвращает массив, имеющий более двух измерений.  
  
-   Метод возвращает массив в качестве выходного параметра.  
  
`[ _@parametername = ] parameter[ OUTPUT ]`— Это параметр метода. Если он указан, *параметр* должен иметь значение соответствующего типа данных.  
  
 Чтобы получить возвращаемое значение выходного параметра, параметр должен быть локальной переменной соответствующего типа данных, а *аргумент* **Output** должен быть указан. Если указан постоянный параметр или если **Output** не указан, то любые возвращаемые значения из выходного параметра игнорируются.  
  
 Если аргумент имеет значение, параметр *ParameterName* должен быть именем [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] именованного параметра. Обратите внимание, что **@** _parametername_is не [!INCLUDE[tsql](../../includes/tsql-md.md)] Локальная переменная. Удаляется знак at ( **@** ), а параметр *ParameterName*передается в объект OLE в качестве имени параметра. Все именованные параметры должны указываться после указания всех позиционных параметров.  
  
 *n*  
 Заполнитель, указывающий на возможность указания нескольких параметров.  
  
> [!NOTE]
>  * \@ ParameterName* может быть именованным параметром, так как он является частью указанного метода и передается в объект. Другие параметры для такой хранимой процедуры задаются позицией, а не именем.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое число (неуспешное завершение), которое является целочисленным значением типа HRESULT, возвращаемого объектом OLE-автоматизации.  
  
 Дополнительные сведения о кодах возврата HRESULT, [кодах возврата OLE Automation и сведения об ошибках](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если возвращаемое значение метода представляет собой массив с одним или двумя измерениями, этот массив возвращается клиенту в виде результирующего набора.  
  
-   Одномерный массив возвращается клиенту как результирующий набор, состоящий из одной строки, в которой число столбцов соответствует количеству элементов массива. Иными словами, массив возвращается в виде (столбцы).  
  
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
  
### <a name="a-calling-a-method"></a>A. Вызов метода  
 В следующем примере вызывается `Connect` метод ранее созданного объекта **SQLServer** .  
  
```  
EXEC @hr = sp_OAMethod @object, 'Connect', NULL, 'my_server',  
    'my_login', 'my_password';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
```  
  
### <a name="b-getting-a-property"></a>Б. Получение свойства  
 В следующем примере показано получение `HostName` Свойства (ранее созданного объекта **SQLServer** ) и его сохранение в локальной переменной.  
  
```  
DECLARE @property varchar(255);  
EXEC @hr = sp_OAMethod @object, 'HostName', @property OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
PRINT @property;  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры OLE-автоматизации &#40;&#41;Transact — SQL](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Пример скрипта OLE-автоматизации](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
