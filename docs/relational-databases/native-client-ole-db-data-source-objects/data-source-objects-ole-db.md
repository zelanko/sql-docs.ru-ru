---
title: Объекты источника данных (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2683cdc7762f1f500918edce436153e0130d04bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73758264"
---
# <a name="data-source-objects-ole-db"></a>Объекты источников данных (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Собственный клиент использует термин источник данных для набора OLE DB интерфейсов, используемых для установления связи с хранилищем данных, например [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Создание экземпляра объекта источника данных поставщика является первой задачей потребителя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента.  
  
 Каждый поставщик OLE DB объявляет свой идентификатор класса (CLSID). Идентификатором CLSID для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика собственного клиента OLE DB является GUID C/C++, CLSID_SQLNCLI10 (символ SQLNCLI_CLSID будет разрешаться в правильный идентификатор ProgID в файле sqlncli. h, на который вы ссылаетесь). Используя CLSID, потребитель может вызвать функцию OLE **CoCreateInstance** для создания экземпляра объекта источника данных.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Собственный клиент — это внутрипроцессный сервер. Экземпляры объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика собственного клиента OLE DB создаются с помощью макроса CLSCTX_INPROC_SERVER для указания контекста исполняемого файла.  
  
 Объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных поставщика собственного клиента OLE DB предоставляет интерфейсы инициализации OLE DB, позволяющие потребителю подключаться к существующим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базам данных.  
  
 Каждое подключение, устанавливаемое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщиком OLE DB собственного клиента, задает эти параметры автоматически:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 В этом примере используется макрос идентификатора класса для создания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB объекта источника данных поставщика и получения ссылки на его интерфейс **IDBInitialize** .  
  
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
  
 При успешном создании экземпляра объекта источника данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика собственного клиента OLE DB приложение-потребитель может продолжать работу, инициализируя источник данных и создавая сеансы. Сеансы OLE DB предоставляют интерфейсы, через которые можно получать доступ к данным и манипулировать ими.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента выполняет свое первое подключение к указанному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в ходе успешной инициализации источника данных. Соединение с источником данных поддерживается до тех пор, пока хранятся ссылки на любой интерфейс инициализации источника данных или пока не вызван метод **IDBInitialize::Uninitialize**.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Свойства источника данных &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [Свойства сведений об источнике данных](../../relational-databases/native-client-ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [Свойства инициализации и авторизации](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [Сеансы](../../relational-databases/native-client-ole-db-data-source-objects/sessions.md)  
  
-   [Свойства сеанса — поставщик OLE DB для SQL Server Native Client](../../relational-databases/native-client-ole-db-data-source-objects/session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Материализованные данные исходного объекта](../../relational-databases/native-client-ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
