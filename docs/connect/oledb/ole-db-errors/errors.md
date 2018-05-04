---
title: Ошибки | Документы Microsoft
description: ошибки
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: b95b26c453df083a6fc1e7463eb512bf30f7f271
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="errors"></a>ошибки
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Объекты OLE/COM сообщают об ошибках с помощью кодов возврата HRESULT функций-членов объектов. Тип HRESULT в OLE/COM представляет собой структуру с битовой упаковкой. OLE предоставляет макросы для разыменования членов структуры.  
  
 OLE/COM задает **IErrorInfo** интерфейса. Интерфейс предоставляет методы, такие как **GetDescription**. Это позволяет клиентам получать подробную информацию об ошибках у серверов OLE/COM. Расширяет OLE DB **IErrorInfo** поддержка возврата из нескольких пакетов информации об ошибках при выполнении функции единственный элемент.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может возвращать несколько ошибок. Приложение может получать ошибки сервера одновременно, вызвав [IMultipleResults::GetResult](http://go.microsoft.com/fwlink/?LinkId=129630) в сочетании с ISQLErrorInfo и IErrorRecords.  
  
 Драйвер OLE DB для SQL Server предоставляет OLE DB улучшенному **IErrorInfo**, настраиваемый **ISQLErrorInfo**и от поставщика [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) ошибки интерфейсы объекта.  
  
 Сведения об ошибках трассировки см. в разделе [трассировка доступа к данным](http://go.microsoft.com/fwlink/?LinkId=125805). Сведения об улучшениях для отслеживания ошибок, появившихся в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], в разделе [доступ к диагностической информации в журнале расширенных событий](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Коды возврата](../../oledb/ole-db-errors/return-codes.md)  
  
-   [Сведения в интерфейсах обработки ошибок](../../oledb/ole-db-errors/information-in-error-interfaces.md)  
  
-   [Подробные сведения об ошибках SQL Server](../../oledb/ole-db-errors/sql-server-error-detail.md)  
  
-   [Получение сведений об ошибках](../../oledb/ole-db-errors/retrieving-error-information.md)  
  
-   [Результаты сообщения SQL Server](../../oledb/ole-db-errors/sql-server-message-results.md)  
  
## <a name="see-also"></a>См. также  
 [Программирование драйвера OLE DB для SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
