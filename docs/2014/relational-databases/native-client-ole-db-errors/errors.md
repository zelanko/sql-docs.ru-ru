---
title: Ошибки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e3979390a58235dbb8ec7c76e7b16478e7d9deb9
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705005"
---
# <a name="errors"></a>ошибки
  Объекты OLE/COM сообщают об ошибках с помощью кодов возврата HRESULT функций-членов объектов. Тип HRESULT в OLE/COM представляет собой структуру с битовой упаковкой. OLE предоставляет макросы для разыменования членов структуры.  
  
 OLE/COM задает интерфейс **IErrorInfo**. Интерфейс предоставляет доступ к методам (например, **GetDescription**). Это позволяет клиентам получать подробную информацию об ошибках у серверов OLE/COM. В OLE DB к интерфейсу **IErrorInfo** добавлена поддержка возврата сразу нескольких пакетов информации об ошибках на один вызов метода.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может возвращать несколько ошибок. Приложение может получать ошибки сервера поочередно, вызывая метод [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630) в сочетании с ISQLErrorInfo и IErrorRecords.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента предоставляет OLE DB расширенный интерфейс **IErrorInfo**, настраиваемый `ISQLErrorInfo` объект и интерфейсы объекта ошибки [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) , относящиеся к поставщику.  
  
 Сведения об ошибках трассировки см. в статье [Отслеживание доступа к данным](https://go.microsoft.com/fwlink/?LinkId=125805). См. сведения об улучшениях трассировки ошибок, добавленных в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], в руководстве по [получению доступа к диагностическим сведениям в расширенном журнале событий](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Коды возврата](return-codes.md)  
  
-   [Сведения в интерфейсах ошибок](information-in-error-interfaces.md)  
  
-   [Подробные сведения об ошибках SQL Server](sql-server-error-detail.md)  
  
-   [Получение информации об ошибке](retrieving-error-information.md)  
  
-   [Результаты сообщения SQL Server](sql-server-message-results.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client (OLE DB)](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
