---
title: Источник данных объектов (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 6b602695720e0d6567e44e4fbe8fd06b6d496a6e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084301"
---
# <a name="data-source-objects-ole-db"></a>Объекты источников данных (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Собственный клиент использует источник данных, термин для набора интерфейсов OLE DB, используемый для установления связи с хранилищем данных, таких как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Создание экземпляра объекта источника данных поставщика — первая задача [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителя собственного клиента.  
  
 Каждый поставщик OLE DB объявляет свой идентификатор класса (CLSID). Идентификатор CLSID для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента является идентификатором GUID C/C++ CLSID_SQLNCLI10 (символ SQLNCLI_CLSID будет разрешен в правильный идентификатор progid в файле sqlncli.h, на которую ссылается). Используя CLSID, потребитель может вызвать функцию OLE **CoCreateInstance** для создания экземпляра объекта источника данных.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Собственный клиент — это внутрипроцессный сервер. Экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объекты поставщика OLE DB для собственного клиента создаются с помощью макроса CLSCTX_INPROC_SERVER для указания на исполняемый контекст.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Объект источника данных поставщика OLE DB для собственного клиента предоставляет интерфейсы инициализации OLE DB, которые позволяют потребителю подключаться к существующим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных.  
  
 Все соединения, сделанные через [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента автоматически устанавливают следующие параметры:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 В этом примере используется макрос идентификатора класса для создания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объекта источника данных поставщика OLE DB для собственного клиента и получить ссылку на его **IDBInitialize** интерфейс.  
  
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
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента проводит первое соединение с указанным экземпляром объекта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как часть успешной инициализации источника данных. Соединение с источником данных поддерживается до тех пор, пока хранятся ссылки на любой интерфейс инициализации источника данных или пока не вызван метод **IDBInitialize::Uninitialize**.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Свойства источника данных &#40;OLE DB&#41;](data-source-properties-ole-db.md)  
  
-   [Свойства сведений об источнике данных](data-source-information-properties.md)  
  
-   [Свойства инициализации и авторизации](initialization-and-authorization-properties.md)  
  
-   [Сеансы](sessions.md)  
  
-   [Свойства сеанса](session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Материализованные объекты источника данных](persisted-data-source-objects.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
