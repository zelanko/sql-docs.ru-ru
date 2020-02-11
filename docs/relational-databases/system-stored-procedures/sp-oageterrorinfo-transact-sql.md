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
ms.openlocfilehash: e263308713a80ffaad4bfd9c484d061f5c19b94e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107911"
---
# <a name="sp_oageterrorinfo-transact-sql"></a>sp_OAGetErrorInfo (Transact-SQL)
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
 *обжекттокен*  
 — Это либо маркер объекта OLE, который был создан ранее с помощью **sp_OACreate** , либо значение null. Если указан параметр *обжекттокен* , возвращается информация об ошибке для этого объекта. Если задается NULL, то возвращаются сведения об ошибке для всего пакета.  
  
 __ **выходные данные** источника  
 Источник сведений об ошибке. Если указано, это должна быть локальная переменная **типа char**, **nchar**, **varchar**или **nvarchar** . Возвращаемое значение при необходимости усекается, чтобы оно уместилось в локальной переменной.  
  
 __ **выходные данные** описания  
 Описание ошибки. Если указано, это должна быть локальная переменная **типа char**, **nchar**, **varchar**или **nvarchar** . Возвращаемое значение при необходимости усекается, чтобы оно уместилось в локальной переменной.  
  
 __ **выходные данные** HelpFile  
 Файл справки для объекта OLE. Если указано, это должна быть локальная переменная **типа char**, **nchar**, **varchar**или **nvarchar** . Возвращаемое значение при необходимости усекается, чтобы оно уместилось в локальной переменной.  
  
 __ **выходные данные** идентификатор справки  
 Идентификатор контекста файла справки. Если указано, это должна быть локальная переменная **int** .  
  
> [!NOTE]  
>  Параметры для этой хранимой процедуры задаются по положению, а не по имени.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое число (неуспешное завершение), которое является целочисленным значением типа HRESULT, возвращаемого объектом OLE-автоматизации.  
  
 Дополнительные сведения о кодах возврата HRESULT см. в разделе [коды возврата OLE Automation и сведения об ошибке](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если не заданы никакие выходные параметры, в качестве результирующего набора клиенту возвращаются сведения об ошибке.  
  
|Имена столбцов|Тип данных|Description|  
|------------------|---------------|-----------------|  
|**Ошибка**|**двоичный (4)**|Двоичное представление номера ошибки.|  
|**Source**|**nvarchar (NN)**|Источник ошибки.|  
|**Описание**|**nvarchar (NN)**|Описание ошибки.|  
|**HelpFile**|**nvarchar (NN)**|Файл справки для источника.|  
|**Идентификатор справки**|**int**|Идентификатор контекста справки в исходном файле справки.|  
  
## <a name="remarks"></a>Remarks  
 Каждый вызов хранимой процедуры OLE-автоматизации (кроме **sp_OAGetErrorInfo**) сбрасывает сведения об ошибке; Таким образом, **sp_OAGetErrorInfo** получает сведения об ошибке только для последнего вызова хранимой процедуры OLE Automation. Обратите внимание, что поскольку **sp_OAGetErrorInfo** не сбрасывает сведения об ошибке, ее можно вызывать несколько раз, чтобы получить те же сведения об ошибке.  
  
 В следующей таблице перечисляются ошибки OLE-автоматизации и их наиболее частые причины.  
  
|Ошибка и HRESULT|Наиболее частая причина|  
|-----------------------|------------------|  
|**Неверный тип переменной (0x80020008)**|Тип данных [!INCLUDE[tsql](../../includes/tsql-md.md)] значения, переданного в качестве параметра метода, не соответствует [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] типу данных параметра метода, или в качестве параметра метода передано значение null.|  
|**Неизвестное имя (0x8002006)**|Указанное имя свойства или метода для данного объекта не найдено.|  
|**Строка недействительного класса (0x800401f3)**|Заданные ProgID или CLSID не зарегистрированы в качестве объектов OLE в экземпляре сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пользовательские серверы OLE Automation должны быть зарегистрированы, прежде чем их можно будет создать с помощью **sp_OACreate**. Это можно сделать с помощью служебной программы regsvr32. exe для внутрипроцессного (DLL) серверов или параметра командной строки **/regserver** для локальных серверов (exe).|  
|**Работа сервера завершилась ошибкой (0x80080005)**|Заданный объект OLE зарегистрирован как локальный сервер OLE (файл EXE), но файл EXE не был найден или запущен.|  
|**Заданный модуль не найден (0x8007007e)**|Заданный объект OLE зарегистрирован как внутрипроцессный сервер OLE (файл DLLl), но файл DLL не мог быть найден или загружен.|  
|**Несоответствие типов данных (0x80020005)**|Тип данных локальной переменной [!INCLUDE[tsql](../../includes/tsql-md.md)], используемой для хранения возвращаемого значения свойства или возвращаемого значения метода, не соответствует типу данных [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] возвращаемого значения свойства или метода. Либо возвращаемое значение свойства или метода было запрошено, но значение не было возвращено.|  
|**Недопустимый тип данных или значение параметра "Context" sp_OACreate. (0x8004275B)**|Значение параметра context должно быть одним из следующих: 1, 4 или 5.|  
  
 Дополнительные сведения об обработке кодов возврата HRESULT см. в разделе [коды возврата OLE Automation и сведения об ошибке](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли сервера **sysadmin** или разрешение EXECUTE непосредственно в этой хранимой процедуре. `Ole Automation Procedures`для использования любой системной процедуры, связанной с OLE Automation, необходимо **включить** конфигурацию.  
  
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
 [Хранимые процедуры OLE-автоматизации &#40;&#41;Transact — SQL](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Пример скрипта OLE-автоматизации](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
