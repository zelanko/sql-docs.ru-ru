---
title: "sp_OAMethod (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_OAMethod
- sp_OAMethod_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_OAMethod
ms.assetid: 1dfaebe2-c7cf-4041-a586-5d04faf2e25e
caps.latest.revision: "25"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 95623f8fa5493679bb7e2125dd1af9dedd9fc637
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spoamethod-transact-sql"></a>sp_OAMethod (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вызывает метод OLE-объекта.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_OAMethod objecttoken , methodname  
    [ , returnvalue OUTPUT ]   
    [ , [ @parametername = ] parameter [ OUTPUT ] [ ...n ] ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *objecttoken*  
 Токен OLE-объекта, который был создан ранее с помощью **sp_OACreate**.  
  
 *имя_метода*  
 Имя вызываемого метода OLE-объекта.  
  
 *returnValue***выходных данных**   
 Возвращаемое значение метода OLE-объекта. Если значение указано, оно должно быть локальной переменной соответствующего типа данных.  
  
 Если метод возвращает одиночное значение, либо указать локальную переменную для *returnvalue*, возвращающий метод возвращаемое значение в локальной переменной или не указывайте *returnvalue*, который возвращает метод возвращаемое значение клиенту в виде одного столбца и одной строки результирующего набора.  
  
 Если возвращаемое значение метода является OLE-объекта *returnvalue* должен быть локальной переменной типа данных **int**. Токен объекта сохранен в локальной переменной. Этот токен может использоваться другими хранимыми процедурами OLE-автоматизации.  
  
 Если возвращаемое значение метода является массивом, если *returnvalue* указан, ему присваивается значение NULL.  
  
 Ошибка выдается в одном из следующих случаев.  
  
-   *returnValue* указан, но метод не возвращает значение.  
  
-   Метод возвращает массив, имеющий более двух измерений.  
  
-   Метод возвращает массив в качестве выходного параметра.  
  
 [  *@parametername*   **=**  ] *параметр*[ **ВЫВОДА** ]  
 Параметр метода. Если указано, *параметр* должен быть величиной соответствующего типа данных.  
  
 Для получения возвращаемого значения аргумент, *параметр* должен быть локальной переменной соответствующего типа данных, и **ВЫВОДА** должен быть указан. Если задан параметр-константа или **ВЫВОДА** не указан, любое возвращаемое выходным параметром значение игнорируется.  
  
 Если указано, *имя_параметра* должно быть имя [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] именованного параметра. Обратите внимание, что  **@**  *имя_параметра*не [!INCLUDE[tsql](../../includes/tsql-md.md)] локальной переменной. Знак (**@**) удаляется, и *имя_параметра*передается объекту OLE имени параметра. Все именованные параметры должны указываться после указания всех позиционных параметров.  
  
 *n*  
 Заполнитель, указывающий на возможность указания нескольких параметров.  
  
> [!NOTE]  
>  *@parametername*может быть именованным параметром, так как он является частью указанного метода и передается через объект. Другие параметры для такой хранимой процедуры задаются позицией, а не именем.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое число (неуспешное завершение), которое является целочисленным значением типа HRESULT, возвращаемого объектом OLE-автоматизации.  
  
 Дополнительные сведения о кодах возврата HRESULT [OLE Automation коды возврата и сведения об ошибках](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если возвращаемое значение метода представляет собой массив с одним или двумя измерениями, этот массив возвращается клиенту в виде результирующего набора.  
  
-   Одномерный массив возвращается клиенту как результирующий набор, состоящий из одной строки, в которой число столбцов соответствует количеству элементов массива. Иными словами, массив возвращается в виде (столбцы).  
  
-   Двумерный массив возвращается клиенту в виде результирующего набора с числом столбцов, равным числу элементов первого измерения массива, и числом строк, равным числу элементов второго измерения массива. Иными словами, массив возвращается в виде (столбцы, строки).  
  
 Если возвращаемое значение свойства или метода является массивом, **sp_OAGetProperty** или **sp_OAMethod** возвращает результирующий набор клиенту. (Выходные параметры метода не могут быть массивами.) Эти процедуры просматривают все значения в массиве для определения подходящих типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их длин для каждого столбца результирующего набора. Для каждого отдельного столбца эти процедуры используют тип и длину данных, необходимые для представления всех значений данных этого столбца.  
  
 Если все значения данных в столбце имеют один и тот же тип данных, этот тип используется для всего столбца. Если значения данных в столбце имеют различные типы данных, тип данных всего столбца определяется по следующей схеме.  
  
||int|float|money|datetime|varchar|nvarchar|  
|------|---------|-----------|-----------|--------------|-------------|--------------|  
|**int**|**int**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**float**|**float**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**money**|**money**|**money**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**datetime**|**varchar**|**varchar**|**varchar**|**datetime**|**varchar**|**nvarchar**|  
|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**nvarchar**|  
|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|  
  
## <a name="remarks"></a>Замечания  
 Можно также использовать **sp_OAMethod** для получения значения свойства.  
  
## <a name="permissions"></a>Permissions  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-calling-a-method"></a>A. Вызов метода  
 В следующем примере вызывается `Connect` метод созданного ранее **SQLServer** объекта.  
  
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
 В следующем примере извлекается `HostName` свойство (созданного ранее **SQLServer** объекта) и сохраняет его в локальной переменной.  
  
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
  
## <a name="see-also"></a>См. также:  
 [OLE-автоматизация хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Пример скрипта OLE-автоматизации](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
