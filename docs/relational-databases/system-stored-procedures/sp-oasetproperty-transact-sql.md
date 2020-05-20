---
title: sp_OASetProperty (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OASetProperty
- sp_OASetProperty_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OASetProperty
ms.assetid: 0fe7d554-6b67-4d55-9d3e-4096802c47f8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 680a21141e459656e0bec19ca8417483a9024088
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82834368"
---
# <a name="sp_oasetproperty-transact-sql"></a>sp_OASetProperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Устанавливает новое значение свойства OLE-объекта.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_OASetProperty objecttoken , propertyname , newvalue [ , index... ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *обжекттокен*  
 Токен объекта OLE, который был ранее создан с помощью **sp_OACreate**.  
  
 *propertyname*  
 Имя свойства OLE-объекта, которому присваивается новое значение.  
  
 *NewValue*  
 Новое значение свойства должно быть величиной соответствующего типа данных.  
  
 *номер*  
 Индексный параметр. Если этот параметр указан, *индекс* должен иметь значение соответствующего типа данных.  
  
 Некоторые свойства имеют параметры. Эти свойства называются индексированными свойствами, а параметры — индексными параметрами. Свойство может иметь несколько индексных параметров.  
  
> [!NOTE]  
>  Параметры для этой хранимой процедуры задаются по положению, а не по имени.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое число (неуспешное завершение), которое является целочисленным значением типа HRESULT, возвращаемого объектом OLE-автоматизации.  
  
 Дополнительные сведения о кодах возврата HRESULT см. в разделе [коды возврата OLE Automation и сведения об ошибке](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли сервера **sysadmin** или разрешение EXECUTE непосредственно в этой хранимой процедуре. `Ole Automation Procedures`для использования любой системной процедуры, связанной с OLE Automation, необходимо **включить** конфигурацию.  
  
## <a name="examples"></a>Примеры  
 В следующем примере задается `HostName` новое значение свойства (ранее созданного объекта **SQLServer** ).  
  
```  
EXEC @hr = sp_OASetProperty @object, 'HostName', 'Gizmo';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END'  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры OLE-автоматизации &#40;&#41;Transact — SQL](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Пример скрипта OLE-автоматизации](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
