---
title: Объекты (OLE DB) источника данных | Документы Microsoft
description: Объекты источников данных (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
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
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0bb61761984d6f50450961ff02fec7db6921b1df
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="data-source-objects-ole-db"></a>Объекты источников данных (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server использует источник данных термин для набора интерфейсов OLE DB, используемый для установления связи с хранилищем данных, таких как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Создание экземпляра объекта источника данных поставщика — первая задача драйвер OLE DB для SQL Server потребителя.  
  
 Каждый поставщик OLE DB объявляет свой идентификатор класса (CLSID). Идентификатор CLSID для драйвер OLE DB для SQL Server является CLSID_MSOLEDBSQL GUID C/C++ (символ MSOLEDBSQL_CLSID будет разрешен в правильный идентификатор progid в файле msoledbsql.h, на которую ссылается). Используя CLSID, потребитель использует OLE **CoCreateInstance** функции для создания экземпляра объекта источника данных.  
  
 Драйвер OLE DB для SQL Server — это внутрипроцессный сервер. Экземпляры драйвер OLE DB для SQL Server объектов создаются с помощью макроса CLSCTX_INPROC_SERVER для указания на исполняемый контекст.  
  
 Драйвер OLE DB для объекта источника данных SQL Server предоставляет интерфейсы инициализации OLE DB, которые позволяют потребителю подключаться к существующим [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] баз данных.  
  
 Все соединения, сделанные через драйвер OLE DB для SQL Server автоматически устанавливают следующие параметры:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 В этом примере используется макрос идентификатора класса для создания драйвер OLE DB для объекта источника данных SQL Server и получить ссылку на его **IDBInitialize** интерфейса.  
  
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
  
 Успешного создания экземпляра драйвер OLE DB для объекта источника данных SQL Server приложение потребителя можно продолжить, инициализации источника данных и создавать сеансы. Сеансы OLE DB предоставляют интерфейсы, через которые можно получать доступ к данным и манипулировать ими.  
  
 Драйвер OLE DB для SQL Server проводит первое соединение для указанного экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] как часть успешной инициализации источника данных. Подключение сохраняется до тех пор, пока сохраняется, ссылка на любой интерфейс инициализации источника данных, или пока не **IDBInitialize::Uninitialize** вызывается метод.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Свойства источника данных & #40; OLE DB & #41;](../../oledb/ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [Свойства сведений об источнике данных](../../oledb/ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [Свойства инициализации и авторизации](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [Сеансы](../../oledb/ole-db-data-source-objects/sessions.md)  
  
-   [Свойства сеанса — драйвер OLE DB для SQL Server](../../oledb/ole-db-data-source-objects/session-properties-oledb-driver-for-sql-server.md)  
  
-   [Материализованные данные исходного объекта](../../oledb/ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>См. также  
 [Программирование драйвера OLE DB для SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
