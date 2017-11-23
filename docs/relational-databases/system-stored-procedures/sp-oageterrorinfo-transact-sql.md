---
title: "sp_OAGetErrorInfo (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
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
- sp_OAGetErrorInfo_TSQL
- sp_OAGetErrorInfo
dev_langs: TSQL
helpviewer_keywords: sp_OAGetErrorInfo
ms.assetid: ceecea08-456f-4819-85d9-ecc9647d7187
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b107c2599e11a81a401a08bfba2a20df3b5962e8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spoageterrorinfo-transact-sql"></a>sp_OAGetErrorInfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Получает данные об ошибке OLE-автоматизации.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
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
 Токен объекта OLE-объекта, который был создан ранее с помощью **sp_OACreate** или NULL. Если *objecttoken* будет указано, возвращаются сведения об ошибке для этого объекта. Если задается NULL, то возвращаются сведения об ошибке для всего пакета.  
  
 *источник* **выходных данных**  
 Источник сведений об ошибке. Если указан, он должен быть локальной **char**, **nchar**, **varchar**, или **nvarchar** переменной. Возвращаемое значение при необходимости усекается, чтобы оно уместилось в локальной переменной.  
  
 *Описание* **выходных данных**  
 Описание ошибки. Если указан, он должен быть локальной **char**, **nchar**, **varchar**, или **nvarchar** переменной. Возвращаемое значение при необходимости усекается, чтобы оно уместилось в локальной переменной.  
  
 *HelpFile* **выходных данных**  
 Файл справки для объекта OLE. Если указан, он должен быть локальной **char**, **nchar**, **varchar**, или **nvarchar** переменной. Возвращаемое значение при необходимости усекается, чтобы оно уместилось в локальной переменной.  
  
 *Идентификатор справки* **выходных данных**  
 Идентификатор контекста файла справки. Если указан, он должен быть локальной **int** переменной.  
  
> [!NOTE]  
>  Параметры для этой хранимой процедуры задаются по положению, а не по имени.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое число (неуспешное завершение), которое является целочисленным значением типа HRESULT, возвращаемого объектом OLE-автоматизации.  
  
 Дополнительные сведения о кодах возврата HRESULT см. в разделе [OLE Automation коды возврата и сведения об ошибках](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если не заданы никакие выходные параметры, в качестве результирующего набора клиенту возвращаются сведения об ошибке.  
  
|Имена столбцов|Тип данных|Description|  
|------------------|---------------|-----------------|  
|**Ошибка**|**binary(4)**|Двоичное представление номера ошибки.|  
|**Source**|**nvarchar(nn)**|Источник ошибки.|  
|**Description**|**nvarchar(nn)**|Описание ошибки.|  
|**Файл справки**|**nvarchar(nn)**|Файл справки для источника.|  
|**Идентификатор справки**|**int**|Идентификатор контекста справки в исходном файле справки.|  
  
## <a name="remarks"></a>Замечания  
 Каждый вызов OLE-автоматизации хранимой процедуры (за исключением **sp_OAGetErrorInfo**) сбрасывает сведения об ошибке, поэтому **sp_OAGetErrorInfo** получает данные об ошибке только для последнего OLE Автоматизация вызова хранимой процедуры. Обратите внимание, что поскольку **sp_OAGetErrorInfo** не сбрасывает сведения об ошибке может вызываться несколько раз для получения того же сведения об ошибке.  
  
 В следующей таблице перечисляются ошибки OLE-автоматизации и их наиболее частые причины.  
  
|Ошибка и HRESULT|Наиболее частая причина|  
|-----------------------|------------------|  
|**Неверный тип переменной (0x80020008)**|Тип данных [!INCLUDE[tsql](../../includes/tsql-md.md)] значение передается как параметр метода не соответствует [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] тип данных параметра метода, или значение NULL был передан в качестве параметра метода.|  
|**Неизвестное имя (0x8002006)**|Указанное имя свойства или метода для данного объекта не найдено.|  
|**Строка недействительного класса (0x800401f3)**|Заданные ProgID или CLSID не зарегистрированы в качестве объектов OLE в экземпляре сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пользовательские серверы OLE-автоматизации должны регистрироваться, прежде чем они смогут быть созданы с помощью **sp_OACreate**. Это можно сделать с помощью программы Regsvr32.exe для серверов в процессе (.dll) или **/regserver** параметр командной строки для серверов локальной (.exe).|  
|**Выполнение сервера закончено неудачей (0x80080005)**|Заданный объект OLE зарегистрирован как локальный сервер OLE (файл EXE), но файл EXE не был найден или запущен.|  
|**Указанный модуль не найден (0x8007007e)**|Заданный объект OLE зарегистрирован как внутрипроцессный сервер OLE (файл DLLl), но файл DLL не мог быть найден или загружен.|  
|**Несоответствие типов (данных 0x80020005)**|Тип данных локальной переменной [!INCLUDE[tsql](../../includes/tsql-md.md)], используемой для хранения возвращаемого значения свойства или возвращаемого значения метода, не соответствует типу данных [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] возвращаемого значения свойства или метода. Либо возвращаемое значение свойства или метода было запрошено, но значение не было возвращено.|  
|**Тип данных или значение параметра «контекст» sp_OACreate недопустимы. (0x8004275B)**|Значение параметра контекста должно быть одним из: 1, 4 или 5.|  
  
 Дополнительные сведения об обработке возвращаемых кодов HRESULT см. в разделе [OLE Automation коды возврата и сведения об ошибках](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="permissions"></a>Permissions  
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
  
## <a name="see-also"></a>См. также:  
 [OLE-автоматизация хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Пример скрипта OLE-автоматизации](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
