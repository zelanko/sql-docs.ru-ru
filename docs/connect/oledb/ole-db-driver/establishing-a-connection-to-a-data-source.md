---
title: Установление подключения к источнику данных | Документы Microsoft
description: Подключения к источнику данных с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [OLE DB Driver for SQL Server]
- connections [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, data source connections
- CoCreateInstance method
- OLE DB data sources [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: a3b7aa0723200fe59d948b5f45913d0ad3deaaac
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="establishing-a-connection-to-a-data-source"></a>Устанавливает соединение с источником данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Чтобы открыть драйвер OLE DB для SQL Server, потребитель должен сначала создать экземпляр объекта источника данных, вызвав **CoCreateInstance** метод. Каждый поставщик OLE DB определяется уникальным идентификатором класса (CLSID). Драйвер OLE DB для SQL Server идентификатор класса касается CLSID_MSOLEDBSQL. Также можно использовать символ MSOLEDBSQL_CLSID, который разрешает драйвер OLE DB для SQL Server, который используется в msoledbsql.h, на которое имеется ссылка.  
  
 Объект источника данных предоставляет **IDBProperties** интерфейс, который потребитель использует обычную проверку подлинности данные, такие как имя сервера, имя базы данных, идентификатор пользователя и пароль. **IDBProperties::SetProperties** метод вызывается для установки этих свойств.  
  
 Если на компьютере выполняется несколько экземпляров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], имя сервера указывается как «Имя_Сервера\Имя_Экземпляра».  
  
 Объект источника данных также предоставляет **IDBInitialize** интерфейса. После задания свойства подключения к источнику данных устанавливается посредством вызова **IDBInitialize::Initialize** метод. Например:  
  
```  
CoCreateInstance(CLSID_MSOLEDBSQL,   
                 NULL,   
                 CLSCTX_INPROC_SERVER,  
                 IID_IDBInitialize,   
                 (void **) &pIDBInitialize)  
```  
  
 Этот вызов **CoCreateInstance** создает единственный объект класса, связанного с CLSID_MSOLEDBSQL (идентификатор CLSID, связанный с данными и код, который будет использоваться для создания объекта). IID_IDBInitialize представляет собой ссылку на идентификатор интерфейса (**IDBInitialize**) для связи с объектом.  
  
 Далее приведен образец функции, которая проводит инициализацию и устанавливает соединение с источником данных.  
  
```  
void InitializeAndEstablishConnection() {  
   // Initialize the COM library.  
   CoInitialize(NULL);  
  
   // Obtain access to the OLE DB Driver for SQL Server.  
   hr = CoCreateInstance(CLSID_MSOLEDBSQL,   
                         NULL,   
                         CLSCTX_INPROC_SERVER,  
                         IID_IDBInitialize,   
                         (void **) &pIDBInitialize);  
   // Initialize property values needed to establish connection.  
   for (i = 0 ; i < 4 ; i++)   
      VariantInit(&InitProperties[i].vValue);  
  
   // Server name.  
   // See DBPROP structure for more information on InitProperties  
   InitProperties[0].dwPropertyID  = DBPROP_INIT_DATASOURCE;  
   InitProperties[0].vValue.vt    = VT_BSTR;  
   InitProperties[0].vValue.bstrVal=   
                     SysAllocString(L"Server");  
   InitProperties[0].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[0].colid       = DB_NULLID;  
  
   // Database.  
   InitProperties[1].dwPropertyID  = DBPROP_INIT_CATALOG;  
   InitProperties[1].vValue.vt    = VT_BSTR;  
   InitProperties[1].vValue.bstrVal= SysAllocString(L"database");  
   InitProperties[1].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[1].colid       = DB_NULLID;  
  
   // Username (login).  
   InitProperties[2].dwPropertyID  = DBPROP_AUTH_INTEGRATED;  
   InitProperties[2].vValue.vt    = VT_BSTR;  
   InitProperties[2].vValue.bstrVal= SysAllocString(L"SSPI");  
   InitProperties[2].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[2].colid       = DB_NULLID;  
   InitProperties[3].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[3].colid       = DB_NULLID;  
  
   // Construct the DBPROPSET structure(rgInitPropSet). The   
   // DBPROPSET structure is used to pass an array of DBPROP   
   // structures (InitProperties) to the SetProperties method.  
   rgInitPropSet[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgInitPropSet[0].cProperties   = 4;  
   rgInitPropSet[0].rgProperties   = InitProperties;  
  
   // Set initialization properties.  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties,   
                           (void **)&pIDBProperties);  
   hr = pIDBProperties->SetProperties(1, rgInitPropSet);   
   pIDBProperties->Release();  
  
   // Now establish the connection to the data source.  
   pIDBInitialize->Initialize();  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Создание приложения с драйвером OLE DB для SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
