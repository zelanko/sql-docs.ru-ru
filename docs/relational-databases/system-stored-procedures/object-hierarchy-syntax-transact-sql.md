---
title: Синтаксис иерархии объектов (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: 3405621d604e6450756520f6d93b66a51d4d66c8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67941987"
---
# <a name="object-hierarchy-syntax-transact-sql"></a>Синтаксис иерархии объектов (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Параметр *PropertyName* параметра sp_OAGetProperty и sp_OASetProperty и параметр *MethodName* sp_OAMethod поддерживают синтаксис иерархии объектов, аналогичный представленному в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. При использовании этого синтаксиса приведенные выше аргументы имеют следующий общий вид:  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
'TraversedObject.PropertyOrMethod'  
```  
  
## <a name="arguments"></a>Аргументы  
 *траверседобжект*  
 — Это объект OLE в иерархии под *обжекттокен* , указанным в хранимой процедуре. Серии коллекций, свойства объектов и методы, возвращающие объекты, указываются с помощью синтаксиса [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. Описатели объектов в сериях разделяются точкой (.).  
  
 Элемент в серии может быть именем коллекции. Коллекции указываются с помощью следующего синтаксиса:  
  
 Коллекция ("*Item*")  
  
 Следует обязательно использовать двойные кавычки ("). Синтаксис [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] с восклицательным знаком (!) не поддерживается для коллекций.  
  
 *пропертйормесод*  
 Имя свойства или метода *траверседобжект*.  
  
 Все аргументы индексов или методов задаются процедурами sp_OAGetProperty, sp_OASetProperty или sp_OAMethod (включая поддержку для выходных аргументов процедуры sp_OAMethod) с помощью следующего синтаксиса:  
  
 *пропертйормесод*  
  
 Чтобы указать все аргументы индекса или метода внутри скобок (в результате все аргументы индекса или метода процедур sp_OAGetProperty, sp_OASetProperty или sp_OAMethod игнорируются), применяется следующий синтаксис:  
  
 *Пропертйормесод*([ *ParameterName*: =] "*параметр*" [,...])  
  
 Следует обязательно использовать двойные кавычки ("). Все именованные параметры должны указываться после указания всех позиционных параметров.  
  
## <a name="remarks"></a>Remarks  
 Если *траверседобжект* не указан, требуется *пропертйормесод* .  
  
 Если *пропертйормесод* не указан, *траверседобжект* возвращается в качестве выходного параметра токена объекта из хранимой процедуры OLE-автоматизации. Если указан параметр *пропертйормесод* , вызывается свойство или метод *траверседобжект* , а значение свойства или возвращаемое значение метода возвращается в виде выходного параметра из хранимой процедуры OLE-автоматизации.  
  
 Если какой-либо элемент в списке *траверседобжект* не ВОЗВРАЩАЕТ объект OLE, возникает ошибка.  
  
 Дополнительные сведения о синтаксисе объектов OLE в [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] см. в документации по [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].  
  
 Дополнительные сведения о кодах возврата HRESULT см. в разделе [sp_OACreate &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-oacreate-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 Ниже приведены примеры синтаксиса иерархии объекта, в которых используется объект SQLServer SQL-DMO.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Пример скрипта OLE Automation](../../relational-databases/stored-procedures/ole-automation-sample-script.md)   
 [Хранимые процедуры OLE-автоматизации (Transact-SQL)](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)  
  
  
