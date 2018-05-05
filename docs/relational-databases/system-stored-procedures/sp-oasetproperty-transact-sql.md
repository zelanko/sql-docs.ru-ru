---
title: sp_OASetProperty (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_OASetProperty
- sp_OASetProperty_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OASetProperty
ms.assetid: 0fe7d554-6b67-4d55-9d3e-4096802c47f8
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f20dc37550f2105c72d67268fb0b2cb7924973ae
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spoasetproperty-transact-sql"></a>sp_OASetProperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Устанавливает новое значение свойства OLE-объекта.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_OASetProperty objecttoken , propertyname , newvalue [ , index... ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *objecttoken*  
 Токен OLE-объекта, который был создан ранее с **sp_OACreate**.  
  
 *propertyname*  
 Имя свойства OLE-объекта, которому присваивается новое значение.  
  
 *новое значение*  
 Новое значение свойства должно быть величиной соответствующего типа данных.  
  
 *index*  
 Индексный параметр. Если указано, *индекс* должен быть величиной соответствующего типа данных.  
  
 Некоторые свойства имеют параметры. Эти свойства называются индексированными свойствами, а параметры — индексными параметрами. Свойство может иметь несколько индексных параметров.  
  
> [!NOTE]  
>  Параметры для этой хранимой процедуры задаются по положению, а не по имени.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое число (неуспешное завершение), которое является целочисленным значением типа HRESULT, возвращаемого объектом OLE-автоматизации.  
  
 Дополнительные сведения о кодах возврата HRESULT см. в разделе [OLE Automation коды возврата и сведения об ошибках](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере задается `HostName` свойство (созданного ранее **SQLServer** объекта) с новым значением.  
  
```  
EXEC @hr = sp_OASetProperty @object, 'HostName', 'Gizmo';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END'  
```  
  
## <a name="see-also"></a>См. также  
 [OLE Automation хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Пример скрипта OLE-автоматизации](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
