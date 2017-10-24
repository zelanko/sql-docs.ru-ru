---
title: "Запрос метод (RDS) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Query method [ADO]
ms.assetid: 20f2480f-3758-405d-a379-05a0dce74796
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 53647d80b2e6110e5af084e6a3f983381ced1690
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="query-method-rds"></a>Метод запроса (RDS)
Использует строку допустимый SQL-запроса для возврата [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set Recordset = DataFactory.Query(Connection, Query)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Набор записей*  
 Объектную переменную, которая представляет **записей** объекта.  
  
 *DataFactory*  
 Объектную переменную, которая представляет [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта.  
  
 *Соединение*  
 Объект **строка** значение, содержащее сведения о соединении сервера. Это похоже на [Connect](../../../ado/reference/rds-api/connect-property-rds.md) свойство.  
  
 *Запрос*  
 Объект **строка** , содержащий SQL-запроса.  
  
## <a name="remarks"></a>Замечания  
 Запрос должен использовать разновидность языка SQL на сервере базы данных. Состояние результата возвращается в том случае, если возникает ошибка с запросом, который был выполнен. **Запроса** метод не выполняет проверку на любой синтаксиса **запроса** строки.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>См. также:  
 [Объект DataFactory, метод запроса и пример метода CreateObject (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)



