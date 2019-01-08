---
title: sp_OAGetErrorInfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OAGetErrorInfo_TSQL
- sp_OAGetErrorInfo
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OAGetErrorInfo
ms.assetid: ceecea08-456f-4819-85d9-ecc9647d7187
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7819e14ccfea387a83e88f7aff8c81541968e89a
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53589128"
---
# <a name="spoageterrorinfo-transact-sql"></a>sp_OAGetErrorInfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Получает данные об ошибке OLE-автоматизации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_OAGetErrorInfo [ objecttoken ]  
    [ , source OUTPUT ]   
    [ , description OUTPUT ]   
    [ , helpfile OUTPUT ]   
    [ , helpid OUTPUT ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *objecttoken*  
 Токен объекта OLE-объекта, который ранее был создан с помощью **sp_OACreate** или NULL. Если *objecttoken* будет указан, возвращаются сведения об ошибке для этого объекта. Если задается NULL, то возвращаются сведения об ошибке для всего пакета.  
  
 _источник_ **выходных данных**  
 Источник сведений об ошибке. Если указан, он должен быть локальной **char**, **nchar**, **varchar**, или **nvarchar** переменной. Возвращаемое значение при необходимости усекается, чтобы оно уместилось в локальной переменной.  
  
 _Описание_ **выходных данных**  
 Описание ошибки. Если указан, он должен быть локальной **char**, **nchar**, **varchar**, или **nvarchar** переменной. Возвращаемое значение при необходимости усекается, чтобы оно уместилось в локальной переменной.  
  
 _HelpFile_ **выходных данных**  
 Файл справки для объекта OLE. Если указан, он должен быть локальной **char**, **nchar**, **varchar**, или **nvarchar** переменной. Возвращаемое значение при необходимости усекается, чтобы оно уместилось в локальной переменной.  
  
 _helpid_ **выходных данных**  
 Идентификатор контекста файла справки. Если указан, он должен быть локальной **int** переменной.  
  
> [!NOTE]  
>  Параметры для этой хранимой процедуры задаются по положению, а не по имени.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое число (неуспешное завершение), которое является целочисленным значением типа HRESULT, возвращаемого объектом OLE-автоматизации.  
  
 Дополнительные сведения о кодах возврата HRESULT см. в разделе [OLE Automation коды возврата и сведения об ошибках](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если не заданы никакие выходные параметры, в качестве результирующего набора клиенту возвращаются сведения об ошибке.  
  
|Имена столбцов|Тип данных|Описание|  
|------------------|---------------|-----------------|  
|**Ошибка**|**binary(4)**|Двоичное представление номера ошибки.|  
|**Source**|**nvarchar(nn)**|Источник ошибки.|  
|**Описание**|**nvarchar(nn)**|Описание ошибки.|  
|**HelpFile**|**nvarchar(nn)**|Файл справки для источника.|  
|**HelpID**|**int**|Идентификатор контекста справки в исходном файле справки.|  
  
## <a name="remarks"></a>Примечания  
 Каждый вызов OLE-автоматизации хранимой процедуры (за исключением **sp_OAGetErrorInfo**) сбрасывает сведения об ошибке, поэтому **sp_OAGetErrorInfo** получает данные об ошибке только для самой последней OLE Автоматизация вызова хранимой процедуры. Обратите внимание, что поскольку **sp_OAGetErrorInfo** не сбрасывает сведения об ошибке, он может вызываться несколько раз для получения тем же сведения об ошибке.  
  
 В следующей таблице перечисляются ошибки OLE-автоматизации и их наиболее частые причины.  
  
|Ошибка и HRESULT|Наиболее частая причина|  
|-----------------------|------------------|  
|**Неверный тип переменной (0x80020008)**|Тип данных [!INCLUDE[tsql](../../includes/tsql-md.md)] значение передается как параметр метода не соответствует [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] тип данных параметра метода, или значение NULL был передан в качестве параметра метода.|  
|**Неизвестное имя (0x8002006)**|Указанное имя свойства или метода для данного объекта не найдено.|  
|**Строка недействительного класса (0x800401f3)**|Заданные ProgID или CLSID не зарегистрированы в качестве объектов OLE в экземпляре сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пользовательские серверы OLE-автоматизации должны регистрироваться, прежде чем они смогут быть созданы с помощью **sp_OACreate**. Это можно сделать с помощью программы Regsvr32.exe для серверов (DLL-файл) в процессе или **/regserver** параметр командной строки для серверов локальной (.exe).|  
|**Выполнение сервера закончено неудачей (0x80080005)**|Заданный объект OLE зарегистрирован как локальный сервер OLE (файл EXE), но файл EXE не был найден или запущен.|  
|**Указанный модуль не найден (0x8007007e)**|Заданный объект OLE зарегистрирован как внутрипроцессный сервер OLE (файл DLLl), но файл DLL не мог быть найден или загружен.|  
|**Несоответствие типов (данных 0x80020005)**|Тип данных локальной переменной [!INCLUDE[tsql](../../includes/tsql-md.md)], используемой для хранения возвращаемого значения свойства или возвращаемого значения метода, не соответствует типу данных [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] возвращаемого значения свойства или метода. Либо возвращаемое значение свойства или метода было запрошено, но значение не было возвращено.|  
|**Тип данных или значение параметра «контекст» sp_OACreate недопустимы. (0x8004275B)**|Параметр контекста должен принимать одно из следующих значений: 1, 4 или 5.|  
  
 Дополнительные сведения об обработке возвращаемых кодов HRESULT см. в разделе [OLE Automation коды возврата и сведения об ошибках](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере отображаются сведения об ошибке OLE-автоматизации.  
  
```  
DECLARE @output varchar(255);  
DECLARE @hr int;  
DECLARE @source varchar(255);  
DECLARE @description varchar(255);  
PRINT 'OLE Automation Error Information';  
EXEC @hr = sp_OAGetErrorInfo @object, @source OUT, @description OUT;  
IF @hr = 0  
BEGIN  
    SELECT @output = '  Source: ' + @source  
    PRINT @output  
    SELECT @output = '  Description: ' + @description  
    PRINT @output  
END  
ELSE  
BEGIN  
    PRINT '  sp_OAGetErrorInfo failed.'  
    RETURN  
END;  
```  
  
## <a name="see-also"></a>См. также  
 [OLE Automation хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Пример скрипта OLE-автоматизации](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
