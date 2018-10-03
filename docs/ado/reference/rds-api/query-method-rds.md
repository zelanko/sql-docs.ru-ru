---
title: Метод (RDS) запроса | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Query method [ADO]
ms.assetid: 20f2480f-3758-405d-a379-05a0dce74796
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59dff6a0af01fe55b6b542cfe494cd93ad73b943
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616875"
---
# <a name="query-method-rds"></a>Метод Query (служба удаленных рабочих столов)
Использует строку допустимым SQL-запроса для возврата [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set Recordset = DataFactory.Query(Connection, Query)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Набор записей*  
 Объектную переменную, которая представляет **записей** объекта.  
  
 *Фабрики данных*  
 Объектную переменную, которая представляет [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта.  
  
 *Соединение*  
 Объект **строка** значение, содержащее сведения о подключении сервера. Это похоже на [Connect](../../../ado/reference/rds-api/connect-property-rds.md) свойство.  
  
 *Запрос*  
 Объект **строка** , содержащий SQL-запроса.  
  
## <a name="remarks"></a>Примечания  
 Запрос следует использовать на разновидности языка SQL, сервера базы данных. Состояние результата возвращается в том случае, если возникает ошибка при выполнении запроса, был выполнен. **Запроса** метод не выполняет проверку на любой синтаксиса **запроса** строка.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры объекта DataFactory, а также методов Query и CreateObject (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)


