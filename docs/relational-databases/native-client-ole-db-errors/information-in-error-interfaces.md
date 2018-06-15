---
title: Сведения в интерфейсах обработки ошибок | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
ms.assetid: 4620f03f-1193-43e7-ba19-ad022737d300
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6687b4dbc8dd0a47c3e2116b27e814240463cc90
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32945129"
---
# <a name="information-in-error-interfaces"></a>Сведения в интерфейсах обработки ошибок
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента сообщает некоторые сведения об ошибках и состоянии в интерфейсах OLE DB определен ошибок **IErrorInfo**, **IErrorRecords**, и **ISQLErrorInfo** .  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поддерживает поставщик OLE DB для собственного клиента **IErrorInfo** для функций-членов следующим образом.  
  
|Функция-член|Description|  
|---------------------|-----------------|  
|**GetDescription**|Строка описательного сообщения об ошибке.|  
|**GetGUID**|Идентификатор GUID интерфейса, в котором была определена ошибка.|  
|**GetHelpContext**|Не поддерживается. Всегда возвращает значение 0.|  
|**GetHelpFile**|Не поддерживается. Всегда возвращает значение NULL.|  
|**GetSource**|Строка «Собственный клиент Microsoft SQL Server».|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента поддерживает доступные потребителя **IErrorRecords** для функций-членов следующим образом.  
  
|Функция-член|Description|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Заполняет структуру ERRORINFO основными сведениями об ошибке. Структура ERRORINFO содержит элементы, которые идентифицируют возвращаемое значение HRESULT для ошибки, поставщика и интерфейс, к которому относится ошибка.|  
|**GetCustomErrorObject**|Возвращает ссылку на интерфейсы **ISQLErrorInfo** и [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).|  
|**GetErrorInfo**|Возвращает ссылку на **IErrorInfo** интерфейса.|  
|**GetErrorParameters**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента не возвращает потребителю через параметры **GetErrorParameters**.|  
|**GetRecordCount**|Число доступных записей ошибок.|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поддерживает поставщик OLE DB для собственного клиента **ISQLErrorInfo::GetSQLInfo** параметры следующим образом.  
  
|Параметр|Description|  
|---------------|-----------------|  
|*pbstrSQLState*|Возвращает значение SQLSTATE для ошибки. Значения SQLSTATE определены в стандартах SQL-92, ODBC и ISO SQL, а также спецификациях API-интерфейсов. Ни [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ни [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента определены значения SQLSTATE зависит от реализации.|  
|*plNativeError*|Возвращает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] номер ошибки в **master.dbo.sysmessages** при ее наличии. Собственные ошибки доступны после успешной попытки инициализировать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных поставщика OLE DB для собственного клиента. До этой попытки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента всегда возвращает ноль.|  
  
## <a name="see-also"></a>См. также:  
 [ошибки](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
