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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62657664"
---
# <a name="information-in-error-interfaces"></a>Сведения в интерфейсах обработки ошибок
  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента сообщает о некоторых ошибках и состоянии в определяемых OLE DB интерфейсах ошибок **IErrorInfo**, **IErrorRecords**и **ISQLErrorInfo**.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента поддерживает функции членов **IErrorInfo** следующим образом.  
  
|Функция-член|Description|  
|---------------------|-----------------|  
|**GetDescription**|Строка описательного сообщения об ошибке.|  
|**GetGUID**|Идентификатор GUID интерфейса, в котором была определена ошибка.|  
|**жеселпконтекст**|Не поддерживается. Всегда возвращает значение 0.|  
|**GetHelpFile**|Не поддерживается. Всегда возвращает значение NULL.|  
|**GetSource**|Строка «Собственный клиент Microsoft SQL Server».|  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента поддерживает функции-члены **IErrorRecords** , доступные для потребителей, как показано ниже.  
  
|Функция-член|Description|  
|---------------------|-----------------|  
|**жетбасицерроринфо**|Заполняет структуру ERRORINFO основными сведениями об ошибке. Структура ERRORINFO содержит элементы, которые идентифицируют возвращаемое значение HRESULT для ошибки, поставщика и интерфейс, к которому относится ошибка.|  
|**жеткустомерроробжект**|Возвращает ссылку на интерфейсы **ISQLErrorInfo** и [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md).|  
|**жетерроринфо**|Возвращает ссылку на интерфейс **IErrorInfo**.|  
|**жетеррорпараметерс**|Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента не возвращает параметры потребителю через **жетеррорпараметерс**.|  
|**жетрекордкаунт**|Число доступных записей ошибок.|  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента поддерживает параметры **ISQLErrorInfo:: GetSQLInfo** , как показано ниже.  
  
|Параметр|Description|  
|---------------|-----------------|  
|*пбстрсклстате*|Возвращает значение SQLSTATE для ошибки. Значения SQLSTATE определены в стандартах SQL-92, ODBC и ISO SQL, а также спецификациях API-интерфейсов. Ни [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] клиента OLE DB не определил значения SQLSTATE, специфичные для реализации.|  
|*плнативиррор*|Возвращает номер ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из системной таблицы **master.dbo.sysmessages**, если он доступен. Собственные ошибки доступны после успешной попытки инициализации источника данных поставщика OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента. Прежде чем пытаться, поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB всегда возвращает ноль.|  
  
## <a name="see-also"></a>См. также:  
 [ошибки](errors.md)  
  
  
