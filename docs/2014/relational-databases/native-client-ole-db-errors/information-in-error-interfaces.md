---
title: Сведения в интерфейсах ошибок | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
ms.assetid: 4620f03f-1193-43e7-ba19-ad022737d300
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60b6b0387aea5475d74c314a10e4fa437fadc005
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62657664"
---
# <a name="information-in-error-interfaces"></a>Сведения в интерфейсах обработки ошибок
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента сообщает некоторые сведения об ошибках и состоянии в интерфейсах OLE DB ошибки **IErrorInfo**, **IErrorRecords**, и **ISQLErrorInfo** .  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поддерживает поставщик OLE DB для собственного клиента **IErrorInfo** для функций-членов следующим образом.  
  
|Функция-член|Описание|  
|---------------------|-----------------|  
|**GetDescription**|Строка описательного сообщения об ошибке.|  
|**GetGUID**|Идентификатор GUID интерфейса, в котором была определена ошибка.|  
|**GetHelpContext**|Не поддерживается. Всегда возвращает значение 0.|  
|**GetHelpFile**|Не поддерживается. Всегда возвращает значение NULL.|  
|**GetSource**|Строка «Собственный клиент Microsoft SQL Server».|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента поддерживает доступные для потребителей **IErrorRecords** для функций-членов следующим образом.  
  
|Функция-член|Описание|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Заполняет структуру ERRORINFO основными сведениями об ошибке. Структура ERRORINFO содержит элементы, которые идентифицируют возвращаемое значение HRESULT для ошибки, поставщика и интерфейс, к которому относится ошибка.|  
|**GetCustomErrorObject**|Возвращает ссылку на интерфейсы **ISQLErrorInfo** и [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md).|  
|**GetErrorInfo**|Возвращает ссылку на интерфейс **IErrorInfo**.|  
|**GetErrorParameters**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента не возвращает параметры объекту-получателю через **GetErrorParameters**.|  
|**GetRecordCount**|Число доступных записей ошибок.|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поддерживает поставщик OLE DB для собственного клиента **ISQLErrorInfo::GetSQLInfo** параметры следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*pbstrSQLState*|Возвращает значение SQLSTATE для ошибки. Значения SQLSTATE определены в стандартах SQL-92, ODBC и ISO SQL, а также спецификациях API-интерфейсов. Ни [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ни [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента определены значения SQLSTATE зависящие от реализации.|  
|*plNativeError*|Возвращает номер ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из системной таблицы **master.dbo.sysmessages**, если он доступен. Собственные ошибки доступны после успешной попытки инициализировать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источник данных поставщика OLE DB для собственного клиента. До попытки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента всегда возвращает значение 0.|  
  
## <a name="see-also"></a>См. также  
 [ошибки](errors.md)  
  
  
