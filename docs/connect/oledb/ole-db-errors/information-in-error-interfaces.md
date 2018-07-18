---
title: Сведения в интерфейсах обработки ошибок | Документы Microsoft
description: Сведения в интерфейсах обработки ошибок
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
manager: craigg
ms.openlocfilehash: 514b2328fce0f400315be4d21539f766f8715890
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2018
ms.locfileid: "35666144"
---
# <a name="information-in-error-interfaces"></a>Сведения в интерфейсах обработки ошибок
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server сообщает некоторые сведения об ошибках и состоянии в интерфейсах OLE DB определен ошибок **IErrorInfo**, **IErrorRecords**, и **ISQLErrorInfo**.  
  
 Драйвер OLE DB для SQL Server поддерживает **IErrorInfo** для функций-членов следующим образом.  
  
|Функция-член|Описание|  
|---------------------|-----------------|  
|**GetDescription**|Строка описательного сообщения об ошибке.|  
|**GetGUID**|Идентификатор GUID интерфейса, в котором была определена ошибка.|  
|**GetHelpContext**|Не поддерживается. Всегда возвращает значение 0.|  
|**GetHelpFile**|Не поддерживается. Всегда возвращает значение NULL.|  
|**GetSource**|Строка «Microsoft OLE DB Driver для SQL Server».|  
  
 Драйвер OLE DB для SQL Server поддерживает доступные потребителя **IErrorRecords** для функций-членов следующим образом.  
  
|Функция-член|Описание|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Заполняет структуру ERRORINFO основными сведениями об ошибке. Структура ERRORINFO содержит элементы, которые идентифицируют возвращаемое значение HRESULT для ошибки, поставщика и интерфейс, к которому относится ошибка.|  
|**GetCustomErrorObject**|Возвращает ссылку на интерфейсы **ISQLErrorInfo** и [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).|  
|**GetErrorInfo**|Возвращает ссылку на **IErrorInfo** интерфейса.|  
|**GetErrorParameters**|Драйвер OLE DB для SQL Server не возвращает потребителю через параметры **GetErrorParameters**.|  
|**GetRecordCount**|Число доступных записей ошибок.|  
  
 Драйвер OLE DB для SQL Server поддерживает **ISQLErrorInfo::GetSQLInfo** параметры следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*pbstrSQLState*|Возвращает значение SQLSTATE для ошибки. Значения SQLSTATE определены в стандартах SQL-92, ODBC и ISO SQL, а также спецификациях API-интерфейсов. Ни [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , ни значения SQLSTATE реализации определены драйвер OLE DB для SQL Server.|  
|*plNativeError*|Возвращает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] номер ошибки в **master.dbo.sysmessages** при ее наличии. Собственные ошибки доступны после успешной попытки инициализировать драйвер OLE DB для источника данных SQL Server. До этой попытки драйвер OLE DB для SQL Server всегда возвращает ноль.|  
  
## <a name="see-also"></a>См. также  
 [ошибки](../../oledb/ole-db-errors/errors.md)  
  
  
