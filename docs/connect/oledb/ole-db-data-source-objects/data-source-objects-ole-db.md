---
title: Объекты источника данных (OLE DB) | Документация Майкрософт
description: Объекты источников данных (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], data source objects
- OLE DB Driver for SQL Server, data source objects
- MSOLEDBSQL, data source objects
- OLE DB Driver for SQL Server, data source objects
- OLE DB data source objects [OLE DB Driver for SQL Server]
- data source objects [OLE DB]
- CLSID
author: pmasl
ms.author: pelopes
ms.openlocfilehash: e0394c5fd3b72c538904c9b8cf946316e76e6650
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015922"
---
# <a name="data-source-objects-ole-db"></a>Объекты источников данных (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server использует термин "источник данных" для обозначения набора интерфейсов OLE DB, дающих возможность устанавливать соединения с хранилищем данных, например с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Первая задача потребителя OLE DB Driver for SQL Server — создание экземпляра объекта для источника данных поставщика.  
  
 Каждый поставщик OLE DB объявляет свой идентификатор класса (CLSID). OLE DB Driver for SQL Server в C/C++ имеет уникальный идентификатор (CLSID) CLSID_MSOLEDBSQL (это означает, что символ CLSID_MSOLEDBSQL будет разрешен в правильный идентификатор progid из файла msoledbsql.h, на который вы ссылаетесь). Используя CLSID, потребитель может вызвать функцию OLE **CoCreateInstance** для создания экземпляра объекта источника данных.  
  
 OLE DB Driver for SQL Server является внутрипроцессным сервером. Экземпляры объектов драйвера OLE DB для SQL Server создаются с помощью макроса CLSCTX_INPROC_SERVER для указания на исполняемый контекст.  
  
 Объект источника данных драйвера OLE DB для SQL Server предоставляет интерфейсы инициализации OLE DB, которые позволяют потребителю подключаться к существующим базам данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Все подключения, созданные через OLE DB Driver for SQL Server, автоматически устанавливают следующие параметры:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 В этом примере используется макрос идентификатора класса для создания объекта источника данных драйвера OLE DB для SQL Server и получения ссылки на его интерфейс **IDBInitialize**.  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_MSOLEDBSQL, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 После успешного создания экземпляра объекта источника данных драйвера OLE DB для SQL Server приложение-потребитель может инициализировать источник данных и создавать сеансы. Сеансы OLE DB предоставляют интерфейсы, через которые можно получать доступ к данным и манипулировать ими.  
  
 Драйвер OLE DB для SQL Server выполняет первое соединение с указанным экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в ходе успешной инициализации источника данных. Соединение с источником данных поддерживается до тех пор, пока хранятся ссылки на любой интерфейс инициализации источника данных или пока не вызван метод **IDBInitialize::Uninitialize**.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Свойства источника данных &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [Свойства сведений об источнике данных](../../oledb/ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [Свойства инициализации и авторизации](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [Сеансы](../../oledb/ole-db-data-source-objects/sessions.md)  
  
-   [Свойства сеанса — драйвер OLE DB для SQL Server](../../oledb/ole-db-data-source-objects/session-properties-oledb-driver-for-sql-server.md)  
  
-   [Материализованные объекты источника данных](../../oledb/ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>См. также:  
 [Программирование драйвера OLE DB для SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
