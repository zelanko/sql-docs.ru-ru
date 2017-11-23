---
title: "Объекты (OLE DB) источника данных | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-data-source-objects
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], data source objects
- SQL Server Native Client, data source objects
- SQLNCLI, data source objects
- SQL Server Native Client OLE DB provider, data source objects
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- CLSID
ms.assetid: c1d4ed20-ad3b-4e33-a26b-38d7517237b7
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b4f221f043fd976e5c0f6679e6f1dda29f5c199e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="data-source-objects-ole-db"></a>Объекты источников данных (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Собственный клиент использует источник данных термин для набора интерфейсов OLE DB, используемый для установления связи с хранилищем данных, таких как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Создание экземпляра объекта источника данных поставщика — первая задача [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителя собственного клиента.  
  
 Каждый поставщик OLE DB объявляет свой идентификатор класса (CLSID). Идентификатор CLSID для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента является идентификатором GUID C/C++ CLSID_SQLNCLI10 (символ SQLNCLI_CLSID будет разрешен в правильный идентификатор progid в файле sqlncli.h, на которую ссылается). Используя CLSID, потребитель использует OLE **CoCreateInstance** функции для создания экземпляра объекта источника данных.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Собственный клиент — это внутрипроцессный сервер. Экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объектов поставщика OLE DB для собственного клиента создаются с помощью макроса CLSCTX_INPROC_SERVER для указания на исполняемый контекст.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Объект источника данных поставщика OLE DB для собственного клиента предоставляет интерфейсы инициализации OLE DB, которые позволяют потребителю подключаться к существующим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных.  
  
 Каждый раз при подключении через [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента автоматически задает следующие параметры:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 В этом примере используется макрос идентификатора класса для создания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объект источника данных поставщика OLE DB для собственного клиента и получить ссылку на его **IDBInitialize** интерфейса.  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL, CLSCTX_INPROC_SERVER,  
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
  
 Успешного создания экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объекта источника данных поставщика OLE DB для собственного клиента, можно продолжить приложение-потребитель, инициализации источника данных и создавать сеансы. Сеансы OLE DB предоставляют интерфейсы, через которые можно получать доступ к данным и манипулировать ими.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента делает первое соединение с указанным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как часть успешной инициализации источника данных. Подключение сохраняется до тех пор, пока сохраняется, ссылка на любой интерфейс инициализации источника данных, или пока не **IDBInitialize::Uninitialize** вызывается метод.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Свойства источника данных &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [Свойства сведений об источнике данных](../../relational-databases/native-client-ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [Свойства инициализации и авторизации](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [Сеансы](../../relational-databases/native-client-ole-db-data-source-objects/sessions.md)  
  
-   [Свойства сеанса — поставщик OLE DB для SQL Server Native Client](../../relational-databases/native-client-ole-db-data-source-objects/session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Материализованные объекты источника данных](../../relational-databases/native-client-ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client (OLE DB)](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
