---
title: Установление подключения к источнику данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [SQL Server Native Client]
- connections [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, data source connections
- CoCreateInstance method
- OLE DB data sources [SQL Server Native Client]
ms.assetid: 7ebd1394-cc8d-4bcf-92f3-c374a26e7ba0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 263728218fd032c0814d73197cde56fc2d661e9c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63183738"
---
# <a name="establishing-a-connection-to-a-data-source"></a>Устанавливает соединение с источником данных
  Чтобы получить доступ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к поставщику OLE DB собственного клиента, потребитель должен сначала создать экземпляр объекта источника данных, вызвав метод **CoCreateInstance** . Каждый поставщик OLE DB определяется уникальным идентификатором класса (CLSID). Для поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB идентификатор класса CLSID_SQLNCLI10. Можно также использовать символы SQLNCLI_CLSID, которые будут разрешаться в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента, используемый в ссылке sqlncli. h.  
  
 Объект источника данных предоставляет интерфейс **IDBProperties**, который потребитель использует с целью передачи сведений для обычной проверки подлинности — имени сервера, имени базы данных, идентификатора пользователя и пароля. Для задания значений этих свойств используется метод **IDBProperties::SetProperties**.  
  
 Если на компьютере выполняется несколько экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], имя сервера указывается как «Имя_Сервера\Имя_Экземпляра».  
  
 Объект источника данных также предоставляет интерфейс **IDBInitialize**. После присвоения значений свойствам устанавливается соединение с источником данных с помощью вызова метода **IDBInitialize::Initialize**. Пример:  
  
```  
CoCreateInstance(CLSID_SQLNCLI10,   
                 NULL,   
                 CLSCTX_INPROC_SERVER,  
                 IID_IDBInitialize,   
                 (void **) &pIDBInitialize)  
```  
  
 Этот вызов **CoCreateInstance** создает один объект класса, связанный с CLSID_SQLNCLI10 (кслид, связанный с данными и кодом, который будет использоваться для создания объекта). IID_IDBInitialize представляет собой ссылку на идентификатор интерфейса (**IDBInitialize**), который будет использоваться для взаимодействия с объектом.  
  
 Далее приведен образец функции, которая проводит инициализацию и устанавливает соединение с источником данных.  
  
```  
void InitializeAndEstablishConnection() {  
   // Initialize the COM library.  
   CoInitialize(NULL);  
  
   // Obtain access to the SQL Server Native Client OLE DB provider.  
   hr = CoCreateInstance(CLSID_SQLNCLI10,   
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
 [Создание приложения поставщика OLE DB для собственного клиента SQL Server](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
