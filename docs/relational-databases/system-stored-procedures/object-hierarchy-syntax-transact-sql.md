---
title: Объект иерархии синтаксис (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], hierarchy syntax
ms.assetid: 7ed8df86-9fd2-4e09-96bc-5381fec85f65
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 3fe5e6b71836854fc6cdcc409e61ef1936641def
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679652"
---
# <a name="object-hierarchy-syntax-transact-sql"></a>Синтаксис иерархии объектов (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  *Propertyname* параметр sp_OAGetProperty и sp_OASetProperty и *имя_метода* параметр процедуры sp_OAMethod поддерживают синтаксис иерархии объектов, аналогичны [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. При использовании этого синтаксиса приведенные выше аргументы имеют следующий общий вид:  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
'TraversedObject.PropertyOrMethod'  
```  
  
## <a name="arguments"></a>Аргументы  
 *TraversedObject*  
 Объект OLE, находящийся в иерархии под *objecttoken* указан в хранимой процедуре. Серии коллекций, свойства объектов и методы, возвращающие объекты, указываются с помощью синтаксиса [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. Описатели объектов в сериях разделяются точкой (.).  
  
 Элемент в серии может быть именем коллекции. Коллекции указываются с помощью следующего синтаксиса:  
  
 Коллекции ("*элемент*")  
  
 Следует обязательно использовать двойные кавычки ("). Синтаксис [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] с восклицательным знаком (!) не поддерживается для коллекций.  
  
 *PropertyOrMethod*  
 Имя свойства или метода *TraversedObject*.  
  
 Все аргументы индексов или методов задаются процедурами sp_OAGetProperty, sp_OASetProperty или sp_OAMethod (включая поддержку для выходных аргументов процедуры sp_OAMethod) с помощью следующего синтаксиса:  
  
 *PropertyOrMethod*  
  
 Чтобы указать все аргументы индекса или метода внутри скобок (в результате все аргументы индекса или метода процедур sp_OAGetProperty, sp_OASetProperty или sp_OAMethod игнорируются), применяется следующий синтаксис:  
  
 *PropertyOrMethod*([ *ParameterName*: =] "*параметр*» [,...])  
  
 Следует обязательно использовать двойные кавычки ("). Все именованные параметры должны указываться после указания всех позиционных параметров.  
  
## <a name="remarks"></a>Примечания  
 Если *TraversedObject* не указан, *PropertyOrMethod* является обязательным.  
  
 Если *PropertyOrMethod* не указан, *TraversedObject* возвращается в виде объекта маркера выходного параметра из хранимой процедуры OLE Automation. Если *PropertyOrMethod* указан, свойство или метод *TraversedObject* вызывается, и значение свойства или возвращаемое значение метода возвращается в виде выходного параметра из OLE-автоматизации Хранимая процедура.  
  
 Если хотя бы один элемент в *TraversedObject* списка не возвращает объект OLE, возникает ошибка.  
  
 Дополнительные сведения о синтаксисе объектов OLE в [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] см. в документации по [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].  
  
 Дополнительные сведения о кодах возврата HRESULT см. в разделе [sp_OACreate &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-oacreate-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 Ниже приведены примеры синтаксиса иерархии объекта для использования объекта SQLServer языка SQL-DMO.  
  
```  
-- Get the AdventureWorks2012 Person.Address Table object.  
EXEC @hr = sp_OAGetProperty @object,  
   'Databases("AdventureWorks2012").Tables("Person.Address")',  
   @table OUT  
  
-- Get the Rows property of the AdventureWorks2012 Person.Address table.  
EXEC @hr = sp_OAGetProperty @object,  
   'Databases("AdventureWorks2012").Tables("Person.Address").Rows',  
   @rows OUT  
  
-- Call the CheckTable method to validate the   
-- AdventureWorks2012 Person.Address table.  
EXEC @hr = sp_OAMethod @object,  
   'Databases("AdventureWorks2012").Tables("Person.Address").CheckTable',  
   @checkoutput OUT  
```  
  
## <a name="see-also"></a>См. также  
 [Пример скрипта OLE-автоматизации](../../relational-databases/stored-procedures/ole-automation-sample-script.md)   
 [Хранимые процедуры OLE-автоматизации (Transact-SQL)](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)  
  
  
