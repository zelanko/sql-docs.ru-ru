---
title: Сведения в интерфейсах обработки ошибок
description: Драйвер OLE DB Driver for SQL Server сообщает некоторые сведения об ошибках и состоянии в определяемых OLE DB интерфейсах обработки ошибок IErrorInfo, IErrorRecords и ISQLErrorInfo.
ms.custom: ''
ms.date: 05/06/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
author: pmasl
ms.author: pelopes
ms.openlocfilehash: f398cb4ca6cdeaa9484e01b5ca41ae28b7d9f095
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86003368"
---
# <a name="information-in-error-interfaces"></a>Сведения в интерфейсах обработки ошибок
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server сообщает некоторые сведения об ошибках и состоянии в определяемых OLE DB интерфейсах обработки ошибок **IErrorInfo**, **IErrorRecords** и **ISQLErrorInfo**.  
  
 OLE DB Driver for SQL Server поддерживает функции-члены интерфейса **IErrorInfo** следующим образом.  
  
|Функция-член|Описание|  
|---------------------|-----------------|  
|**GetDescription**|Строка описательного сообщения об ошибке.|  
|**GetGUID**|Идентификатор GUID интерфейса, в котором была определена ошибка.|  
|**GetHelpContext**|Не поддерживается. Всегда возвращает значение 0.|  
|**GetHelpFile**|Не поддерживается. Всегда возвращает значение NULL.|  
|**GetSource**|Строка "Драйвер Microsoft OLE DB для SQL Server".|  
  
 OLE DB Driver for SQL Server поддерживает доступные для потребителей функции-члены интерфейса **IErrorRecords** следующим образом.  
  
|Функция-член|Описание|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Заполняет структуру ERRORINFO основными сведениями об ошибке. Структура ERRORINFO содержит элементы, которые идентифицируют возвращаемое значение HRESULT для ошибки, поставщика и интерфейс, к которому относится ошибка.|  
|**GetCustomErrorObject**|Возвращает ссылку на интерфейсы **ISQLErrorInfo** и [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).|  
|**GetErrorInfo**|Возвращает ссылку на интерфейс **IErrorInfo**.|  
|**GetErrorParameters**|OLE DB Driver for SQL Server не возвращает потребителю параметры через функцию **GetErrorParameters**.|  
|**GetRecordCount**|Число доступных записей ошибок.|  
  
 OLE DB Driver for SQL Server поддерживает параметры **ISQLErrorInfo::GetSQLInfo** следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*pbstrSQLState*|Возвращает значение SQLSTATE для ошибки. Значения SQLSTATE определены в стандартах SQL-92, ODBC и ISO SQL, а также спецификациях API-интерфейсов. Ни [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ни OLE DB Driver for SQL Server не определяют значений SQLSTATE для конкретной реализации.|  
|*plNativeError*|Возвращает номер ошибки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из системной таблицы **master.dbo.sysmessages**, если он доступен. Собственные ошибки доступны после успешной попытки инициализировать источник данных OLE DB Driver for SQL Server. До такой попытки OLE DB Driver for SQL Server всегда возвращает нулевое значение.|  
  
## <a name="see-also"></a>См. также:  
 [ошибки](../../oledb/ole-db-errors/errors.md)  
  
  
