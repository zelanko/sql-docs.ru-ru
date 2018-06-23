---
title: Ошибки | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a3210cb1cd48a375e428cc6cf8a40e6f76f48b21
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098885"
---
# <a name="errors"></a>ошибки
  Объекты OLE/COM сообщают об ошибках с помощью кодов возврата HRESULT функций-членов объектов. Тип HRESULT в OLE/COM представляет собой структуру с битовой упаковкой. OLE предоставляет макросы для разыменования членов структуры.  
  
 OLE/COM задает **IErrorInfo** интерфейса. Интерфейс предоставляет методы, такие как **GetDescription**. Это позволяет клиентам получать подробную информацию об ошибках у серверов OLE/COM. Расширяет OLE DB **IErrorInfo** поддержка возврата из нескольких пакетов информации об ошибках при выполнении функции единственный элемент.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может возвращать несколько ошибок. Приложение может получать ошибки сервера одновременно, вызвав [IMultipleResults::GetResult](http://go.microsoft.com/fwlink/?LinkId=129630) в сочетании с ISQLErrorInfo и IErrorRecords.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет OLE DB улучшенному **IErrorInfo**, пользовательский `ISQLErrorInfo`и от поставщика [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) объекта error интерфейсы.  
  
 Сведения об ошибках трассировки см. в разделе [трассировка доступа к данным](http://go.microsoft.com/fwlink/?LinkId=125805). Сведения об улучшениях для отслеживания ошибок, появившихся в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], в разделе [доступ к диагностической информации в журнале расширенных событий](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Коды возврата](return-codes.md)  
  
-   [Сведения в интерфейсах ошибок](information-in-error-interfaces.md)  
  
-   [Подробные сведения об ошибках SQL Server](sql-server-error-detail.md)  
  
-   [Получение информации об ошибке](retrieving-error-information.md)  
  
-   [Результаты сообщения SQL Server](sql-server-message-results.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  