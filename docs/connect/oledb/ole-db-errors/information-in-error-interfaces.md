---
title: Сведения в интерфейсах обработки ошибок | Документы Microsoft
description: Сведения в интерфейсах обработки ошибок
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 36cfb611737570e0d2a0d2774a0306706bfe5c6a
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2018
---
# <a name="information-in-error-interfaces"></a>Сведения в интерфейсах обработки ошибок
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server сообщает некоторые сведения об ошибках и состоянии в интерфейсах OLE DB определен ошибок **IErrorInfo**, **IErrorRecords**, и **ISQLErrorInfo**.  
  
 Драйвер OLE DB для SQL Server поддерживает **IErrorInfo** для функций-членов следующим образом.  
  
|Функция-член|Description|  
|---------------------|-----------------|  
|**GetDescription**|Строка описательного сообщения об ошибке.|  
|**GetGUID**|Идентификатор GUID интерфейса, в котором была определена ошибка.|  
|**GetHelpContext**|Не поддерживается. Всегда возвращает значение 0.|  
|**GetHelpFile**|Не поддерживается. Всегда возвращает значение NULL.|  
|**GetSource**|Строка «Microsoft OLE DB Driver для SQL Server».|  
  
 Драйвер OLE DB для SQL Server поддерживает доступные потребителя **IErrorRecords** для функций-членов следующим образом.  
  
|Функция-член|Description|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Заполняет структуру ERRORINFO основными сведениями об ошибке. Структура ERRORINFO содержит элементы, которые идентифицируют возвращаемое значение HRESULT для ошибки, поставщика и интерфейс, к которому относится ошибка.|  
|**GetCustomErrorObject**|Возвращает ссылку на интерфейсы **ISQLErrorInfo** и [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).|  
|**GetErrorInfo**|Возвращает ссылку на **IErrorInfo** интерфейса.|  
|**GetErrorParameters**|Драйвер OLE DB для SQL Server не возвращает потребителю через параметры **GetErrorParameters**.|  
|**GetRecordCount**|Число доступных записей ошибок.|  
  
 Драйвер OLE DB для SQL Server поддерживает **ISQLErrorInfo::GetSQLInfo** параметры следующим образом.  
  
|Параметр|Description|  
|---------------|-----------------|  
|*pbstrSQLState*|Возвращает значение SQLSTATE для ошибки. Значения SQLSTATE определены в стандартах SQL-92, ODBC и ISO SQL, а также спецификациях API-интерфейсов. Ни [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , ни значения SQLSTATE реализации определены драйвер OLE DB для SQL Server.|  
|*plNativeError*|Возвращает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] номер ошибки в **master.dbo.sysmessages** при ее наличии. Собственные ошибки доступны после успешной попытки инициализировать драйвер OLE DB для источника данных SQL Server. До этой попытки драйвер OLE DB для SQL Server всегда возвращает ноль.|  
  
## <a name="see-also"></a>См. также  
 [ошибки](../../oledb/ole-db-errors/errors.md)  
  
  
