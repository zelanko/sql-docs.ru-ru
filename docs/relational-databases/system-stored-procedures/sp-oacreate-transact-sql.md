---
title: sp_OACreate (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_OACreate
- sp_OACreate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OACreate
ms.assetid: eb84c0f1-26dd-48f9-9368-13ee4a30a27c
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 02a05fb8b97c1ae74682b442c45ca54552052236
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43019453"
---
# <a name="spoacreate-transact-sql"></a>sp_OACreate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает экземпляр OLE-объекта.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_OACreate { progid | clsid } , objecttoken OUTPUT [ , context ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *Идентификатор ProgID*  
 Программный идентификатор (ProgID) создаваемого OLE-объекта. Данная строка символов описывает класс OLE-объекта и имеет следующий вид: **"***OLEComponent***. ***Объект***"**  
  
 *OLEComponent* имя компонента сервера OLE-автоматизации, и *объект* — имя OLE-объекта. Указанный OLE-объект должен быть допустимым и должен поддерживать **IDispatch** интерфейс.  
  
 Например, SQLDMO. SQLServer — это идентификатор ProgID объекта SQL-DMO **SQLServer** объекта. SQL-DMO содержит имя компонента — Sqldmo, **SQLServer** объект является допустимым и (как и все объекты SQL-DMO объектов) **SQLServer** поддерживает **IDispatch**.  
  
 *CLSID*  
 Идентификатор класса (CLSID) создаваемого OLE-объекта. Данная строка символов описывает класс OLE-объекта и имеет следующий вид: **"{***nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn***}"**. Указанный OLE-объект должен быть допустимым и должен поддерживать **IDispatch** интерфейс.  
  
 Например, {00026BA1-0000-0000-C000-000000000046} — это идентификатор CLSID объекта SQL-DMO **SQLServer** объекта.  
  
 *objecttoken* **выходных данных**  
 Токен, возвращаемый объект, и должен быть локальной переменной типа данных **int**. Токен объекта идентифицирует созданный OLE-объект и используется в вызовах других хранимых процедур OLE-автоматизации.  
  
 *Контекст*  
 Указывает контекст выполнения, в котором запускается созданный OLE-объект. Если аргумент указан, то его значение должно быть одним из следующих:  
  
 **1** = только внутрипроцессный (.dll) OLE-сервер.  
  
 **4** = local (.exe) OLE только для сервера.  
  
 **5** = и внутри процесса, так и локальный OLE-сервер разрешено  
  
 Если не указан, значение по умолчанию — **5**. Это значение передается в качестве *dwClsContext* параметра вызова **CoCreateInstance**.  
  
 Если внутрипроцессный OLE-сервер может (с помощью значения контекста **1** или **5** или, не указывая значение контекста), он имеет доступ к памяти и другие ресурсы, принадлежащие [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Внутрипроцессный OLE-сервер может повредить память или другие ресурсы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и привести к непредсказуемым результатам, например к нарушению прав доступа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 При указании значения контекста **4**, локальный OLE-сервер не имеет доступа к любому [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ресурсы и не может повредить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] памяти или ресурсов.  
  
> [!NOTE]  
>  Аргументы для данной хранимой процедуры указываются по позиции, а не по имени.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое число (неуспешное завершение), которое является целочисленным значением типа HRESULT, возвращаемого объектом OLE-автоматизации.  
  
 Дополнительные сведения о кодах возврата HRESULT см. в разделе [OLE Automation коды возврата и сведения об ошибках](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="remarks"></a>Примечания  
 Если процедуры OLE-автоматизации включены, вызов **sp_OACreate** начнется OLE-автоматизации общую среду выполнения. Дополнительные сведения о включении OLE-автоматизации, см. в разделе [Ole Automation процедуры параметр конфигурации сервера](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md).  
  
 Созданный OLE-объект автоматически уничтожается по завершении пакета инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-progid"></a>A. Использование идентификатора ProgID  
 В следующем примере создается объект SQL-DMO **SQLServer** объекта с помощью идентификатора ProgID.  
  
```  
DECLARE @object int;  
DECLARE @hr int;  
DECLARE @src varchar(255), @desc varchar(255);  
EXEC @hr = sp_OACreate 'SQLDMO.SQLServer', @object OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object, @src OUT, @desc OUT   
   raiserror('Error Creating COM Component 0x%x, %s, %s',16,1, @hr, @src, @desc)  
    RETURN  
END;  
GO  
```  
  
### <a name="b-using-clsid"></a>Б. Использование идентификатора CLSID  
 В следующем примере создается объект SQL-DMO **SQLServer** объекта с помощью идентификатора CLSID.  
  
```  
DECLARE @object int;  
DECLARE @hr int;  
DECLARE @src varchar(255), @desc varchar(255);  
EXEC @hr = sp_OACreate '{00026BA1-0000-0000-C000-000000000046}',  
    @object OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object, @src OUT, @desc OUT   
   raiserror('Error Creating COM Component 0x%x, %s, %s',16,1, @hr, @src, @desc)  
    RETURN  
END;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [OLE Automation хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Параметр конфигурации сервера OLE Automation Procedures](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)   
 [Пример скрипта OLE-автоматизации](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
