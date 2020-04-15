---
title: Объекты источника данных (OLE DB) | Документация Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d8bb984c789f759eb764ad580f971ab71c9fc946
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297698"
---
# <a name="data-source-objects-ole-db"></a>Объекты источников данных (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Родной клиент использует термин «источник данных» для набора интерфейсов OLE DB, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]используемых для установления ссылки на хранилище данных, например. Создание экземпляра объекта источника данных поставщика является первой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задачей потребителя Native Client.  
  
 Каждый поставщик OLE DB объявляет свой идентификатор класса (CLSID). CLSID для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика Native Client OLE DB является CLSID_SQLNCLI10 ГУИД C/C's (символ, SQLNCLI_CLSID будет разрешаться с правильным progid в файле sqlncli.h, на который вы ссылаетесь). Используя CLSID, потребитель может вызвать функцию OLE **CoCreateInstance** для создания экземпляра объекта источника данных.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Родной клиент — это сервер, наданный в процессе. Instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объектов поставщика Native Client OLE DB создаются с использованием макроса CLSCTX_INPROC_SERVER для обозначения исполняемого контекста.  
  
 Объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных поставщика данных Native Client OLE DB предоставляет интерфейсы инициализации OLE DB, которые позволяют потребителю подключаться к существующим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базам данных.  
  
 Каждое соединение, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сделанное через поставщика Native Client OLE DB, устанавливает следующие параметры автоматически:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 Этот пример использует макрос идентификатора класса для создания исходного объекта исходного кода [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client OLE DB и получения ссылки на интерфейс **IDB Initialize.**  
  
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
  
 Успешно создавая экземпляр объекта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных поставщика данных Native Client OLE DB, приложение потребителя может продолжиться путем инициализации источника данных и создания сеансов. Сеансы OLE DB предоставляют интерфейсы, через которые можно получать доступ к данным и манипулировать ими.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB впервые подключен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к указанному экземпляру в рамках успешной инициализации источника данных. Соединение с источником данных поддерживается до тех пор, пока хранятся ссылки на любой интерфейс инициализации источника данных или пока не вызван метод **IDBInitialize::Uninitialize**.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Свойства источника данных &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [Свойства сведений об источнике данных](../../relational-databases/native-client-ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [Свойства инициализации и авторизации](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [Сеансы](../../relational-databases/native-client-ole-db-data-source-objects/sessions.md)  
  
-   [Свойства сеанса — поставщик OLE DB для SQL Server Native Client](../../relational-databases/native-client-ole-db-data-source-objects/session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Материализованные данные исходного объекта](../../relational-databases/native-client-ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client (OLE DB)](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
