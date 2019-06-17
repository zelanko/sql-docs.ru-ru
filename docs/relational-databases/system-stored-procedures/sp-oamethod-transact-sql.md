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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 25eccb27b75028fdebafaa7a855137946465676b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65450110"
---
# <a name="spoamethod-transact-sql"></a>sp_OAMethod (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вызывает метод OLE-объекта.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_OAMethod objecttoken , methodname  
    [ , returnvalue OUTPUT ]   
    [ , [ @parametername = ] parameter [ OUTPUT ] [ ...n ] ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *objecttoken*  
 Токен OLE-объекта, который ранее был создан с помощью **sp_OACreate**.  
  
 *имя_метода*  
 Имя вызываемого метода OLE-объекта.  
  
 _returnValue_**выходных данных**  
 Возвращаемое значение метода OLE-объекта. Если значение указано, оно должно быть локальной переменной соответствующего типа данных.  
  
 Если метод возвращает одиночное значение, либо указать локальную переменную для *returnvalue*, который возвращает метод, возвращаемое значение в локальной переменной, либо не указывайте *returnvalue*, который возвращает метод возвращать значение клиенту в виде одного столбца и одной строки результирующего набора.  
  
 Если возвращаемое значение метода является OLE-объект *returnvalue* должен быть локальной переменной типа данных **int**. Токен объекта хранится в локальной переменной, и этот токен можно использовать с другими процедурами OLE-автоматизации хранятся.  
  
 Если возвращаемое значение метода является массивом, если *returnvalue* указан, ему присваивается значение NULL.  
  
 Ошибка выдается в одном из следующих случаев.  
  
-   *returnValue* указан, но метод не возвращает значение.  
  
-   Метод возвращает массив, имеющий более двух измерений.  
  
-   Метод возвращает массив в качестве выходного параметра.  
  
`[ _@parametername = ] parameter[ OUTPUT ]` Является параметром метода. Если указано, *параметр* должен быть величиной соответствующего типа данных.  
  
 Чтобы получить возвращаемое значение выходного параметра, *параметр* должен быть локальной переменной соответствующего типа данных, и **ВЫВОДА** должен быть указан. Если задан параметр-константа или **ВЫВОДА** не указан, любое возвращаемое выходным параметром значение игнорируется.  
  
 Если указано, *parametername* должно быть имя [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] именованного параметра. Обратите внимание, что **@** _parametername_is не [!INCLUDE[tsql](../../includes/tsql-md.md)] локальной переменной. Знак ( **@** ) удаляется, и *parametername*передается на объект OLE, что имя параметра. Все именованные параметры должны указываться после указания всех позиционных параметров.  
  
 *n*  
 Заполнитель, указывающий на возможность указания нескольких параметров.  
  
> [!NOTE]
>  *@parametername* может быть именованный параметр, так как он является частью указанного метода и передается через объект. Другие параметры для такой хранимой процедуры задаются позицией, а не именем.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое число (неуспешное завершение), которое является целочисленным значением типа HRESULT, возвращаемого объектом OLE-автоматизации.  
  
 Дополнительные сведения о кодах возврата HRESULT [OLE Automation коды возврата и сведения об ошибках](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если возвращаемое значение метода представляет собой массив с одним или двумя измерениями, этот массив возвращается клиенту в виде результирующего набора.  
  
-   Одномерный массив возвращается клиенту как результирующий набор, состоящий из одной строки, в которой число столбцов соответствует количеству элементов массива. Иными словами, массив возвращается в виде (столбцы).  
  
-   Двумерный массив возвращается клиенту в виде результирующего набора с числом столбцов, равным числу элементов первого измерения массива, и числом строк, равным числу элементов второго измерения массива. Иными словами, массив возвращается в виде (столбцы, строки).  
  
 Если возвращаемое значение свойства или метода значение является массивом, **sp_OAGetProperty** или **sp_OAMethod** возвращает результирующий набор клиенту. (Выходные параметры метода не могут быть массивами.) Эти процедуры просматривают все значения в массиве для определения подходящих типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их длин для каждого столбца результирующего набора. Для каждого отдельного столбца эти процедуры используют тип и длину данных, необходимые для представления всех значений данных этого столбца.  
  
 Если все значения данных в столбце имеют один и тот же тип данных, этот тип используется для всего столбца. Если значения данных в столбце имеют различные типы данных, тип данных всего столбца определяется по следующей схеме.  
  
||ssNoversion|float|money|datetime|varchar|nvarchar|  
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
 Требуется членство в **sysadmin** предопределенной роли сервера или разрешение на выполнение непосредственно в этой хранимой процедуры. `Ole Automation Procedures` Конфигурация должна быть **включена** для использования любой системной процедуры, связанные с OLE-автоматизации.  
  
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
 В следующем примере возвращается `HostName` свойство (созданного ранее **SQLServer** объекта) и сохраняет его в локальной переменной.  
  
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
 [OLE Automation хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Пример скрипта OLE-автоматизации](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
