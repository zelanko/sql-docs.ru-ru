---
title: sp_OACreate (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OACreate
- sp_OACreate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OACreate
ms.assetid: eb84c0f1-26dd-48f9-9368-13ee4a30a27c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2ad8059466ac520b6f9f793af7670cbd73b96b38
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68107934"
---
# <a name="sp_oacreate-transact-sql"></a>sp_OACreate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает экземпляр OLE-объекта.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_OACreate { progid | clsid } , objecttoken OUTPUT [ , context ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *ID*  
 Программный идентификатор (ProgID) создаваемого OLE-объекта. Эта символьная строка описывает класс объекта OLE и имеет следующий вид: **'**_олекомпонент_**.** _Объект_**"**  
  
 *Олекомпонент* — имя компонента сервера OLE-автоматизации, а *объект* — имя объекта OLE. Указанный объект OLE должен быть допустимым и должен поддерживать интерфейс **IDispatch** .  
  
 Например, SQLDMO. SQLServer — это идентификатор ProgID объекта **SQLServer** SQL-DMO. SQL-DMO имеет имя компонента SQLDMO, объект **SQLServer** является допустимым, и (как и все объекты SQL-DMO) объект **SQLServer** поддерживает **IDispatch**.  
  
 *этому*  
 Идентификатор класса (CLSID) создаваемого OLE-объекта. Эта символьная строка описывает класс объекта OLE и имеет следующий вид: **"{**_nnnnnnnn-NNNN-NNNN-NNNN-нннннннннннн_**}"**. Указанный объект OLE должен быть допустимым и должен поддерживать интерфейс **IDispatch** .  
  
 Например, {00026BA1-0000-0000-C000-000000000046} является идентификатором CLSID объекта **SQLServer** SQL-DMO.  
  
 _objecttoken_ **выходные данные** обжекттокен  
 Возвращаемый токен объекта, который должен быть локальной переменной типа данных **int**. Этот маркер объекта определяет созданный OLE-объект и используется в вызовах других хранимых процедур OLE-автоматизации.  
  
 *context*  
 Указывает контекст выполнения, в котором запускается созданный OLE-объект. Если аргумент указан, то его значение должно быть одним из следующих:  
  
 **1** = только внутрипроцессный (. dll) OLE-сервер.  
  
 **4** = только локальный OLE-сервер (exe).  
  
 **5** = разрешены как внутрипроцессный, так и локальный OLE-сервер  
  
 Если этот параметр не указан, по умолчанию используется значение **5**. Это значение передается как параметр *двклсконтекст* для вызова **CoCreateInstance**.  
  
 Если внутрипроцессный OLE-сервер разрешен (используя значение контекста **1** или **5** или не указывая значение контекста), он имеет доступ к памяти и другим ресурсам, принадлежащим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Внутрипроцессный OLE-сервер может повредить память или другие ресурсы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и привести к непредсказуемым результатам, например к нарушению прав доступа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 При указании значения контекста, равного **4**, локальный сервер OLE не имеет доступа к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ресурсам и не может повредить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] память или ресурсы.  
  
> [!NOTE]  
>  Аргументы для данной хранимой процедуры указываются по позиции, а не по имени.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое число (неуспешное завершение), которое является целочисленным значением типа HRESULT, возвращаемого объектом OLE-автоматизации.  
  
 Дополнительные сведения о кодах возврата HRESULT см. в разделе [коды возврата OLE Automation и сведения об ошибке](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="remarks"></a>Remarks  
 Если включены процедуры OLE-автоматизации, вызов **sp_OACreate** запустит общую среду выполнения OLE-автоматизации. Дополнительные сведения о включении OLE Automation см. в разделе [параметр конфигурации сервера «процедуры OLE Automation](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)».  
  
 Созданный OLE-объект автоматически уничтожается по завершении пакета инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли сервера **sysadmin** или разрешение EXECUTE непосредственно в этой хранимой процедуре. `Ole Automation Procedures`для использования любой системной процедуры, связанной с OLE Automation, необходимо **включить** конфигурацию.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-progid"></a>A. Использование идентификатора ProgID  
 В следующем примере создается объект SQL-DMO **SQLServer** с помощью его ProgID.  
  
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
  
### <a name="b-using-clsid"></a>Б) Использование идентификатора CLSID  
 В следующем примере создается объект SQL-DMO **SQLServer** с помощью его CLSID.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры OLE-автоматизации &#40;&#41;Transact — SQL](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Параметр конфигурации сервера «процедуры OLE Automation»](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)   
 [Пример скрипта OLE-автоматизации](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
