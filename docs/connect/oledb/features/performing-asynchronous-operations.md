---
title: Выполнение асинхронных операций | Документы Microsoft
description: Выполнение асинхронных операций с драйвером OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- initialization [OLE DB Driver for SQL Server]
- database connections [OLE DB Driver for SQL Server]
- data access [OLE DB Driver for SQL Server], asynchronous operations
- connections [OLE DB Driver for SQL Server]
- asynchronous operations [OLE DB Driver for SQL Server]
- rowsets [SQL Server], initializing
- MSOLEDBSQL, asynchronous operations
- OLE DB Driver for SQL Server, asynchronous operations
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: a19dcf4d5b5655b89ac8ebc9d79ec3d58b416ca5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="performing-asynchronous-operations"></a>Выполнение асинхронных операций
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] позволяет приложениям выполнять асинхронные операции с базой данных. Асинхронная обработка позволяет выполнять возврат из методов немедленно, не блокируя вызывающий поток. Это позволяет использовать значительную часть мощности и гибкости многопотоковой обработки, и разработчику при этом не требуется явно создавать потоки или обрабатывать синхронизацию. Приложения запрашивают асинхронную обработку при инициализации подключения к базе данных или при инициализации результата выполнения команды.  
  
## <a name="opening-and-closing-a-database-connection"></a>Открытие и закрытие подключения к базе данных  
 При использовании драйвера OLE DB для SQL Server, приложения, предназначенные для асинхронно инициализировать объект источника данных можно задать DBPROPVAL_ASYNCH_INITIALIZE в свойстве DBPROP_INIT_ASYNCH до вызова метода **IDBInitialize::Initialize** . Если это свойство задано, поставщик немедленный возврат из вызова **инициализировать** с S_OK, если операция была завершена немедленно, или DB_S_ASYNCHRONOUS, если инициализация продолжена асинхронно. Приложения могут запросить **IDBAsynchStatus** или [ISSAsynchStatus](../../oledb/ole-db-interfaces/issasynchstatus-ole-db.md) интерфейс для объекта источника данных, а затем вызвать **IDBAsynchStatus::GetStatus** или [ ISSAsynchStatus::WaitForAsynchCompletion](../../oledb/ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md) для получения состояния инициализации.  
  
 Кроме того, в набор свойств DBPROPSET_SQLSERVERROWSET добавлено свойство SSPROP_ISSAsynchStatus. Поставщики, поддерживающие интерфейс **ISSAsynchStatus** , должны реализовывать это свойство со значением VARIANT_TRUE.  
  
 **IDBAsynchStatus::Abort** или [ISSAsynchStatus::Abort](../../oledb/ole-db-interfaces/issasynchstatus-abort-ole-db.md) может вызываться для отмены асинхронного **инициализировать** вызова. Потребитель должен явно запросить асинхронную инициализацию источника данных. В противном случае **IDBInitialize::Initialize** не возвращается до полной инициализации объекта источника данных.  
  
> [!NOTE]  
>  Объекты источника данных, используемые для организации пулов соединений не удается вызвать **ISSAsynchStatus** интерфейс драйвера OLE DB для SQL Server. **ISSAsynchStatus** интерфейс не реализован для объектов источников данных в составе пула.  
>   
>  Если приложение явно и принудительно использует ядро курсора **IOpenRowset::OpenRowset** и **IMultipleResults::GetResult** не будут поддерживать асинхронную обработку.  
>   
>  Кроме того, библиотеки dll прокси/заглушки удаленного взаимодействия (в компонентах MDAC 2.8) не удается вызвать **ISSAsynchStatus** интерфейса в драйвер OLE DB для SQL Server. **ISSAsynchStatus** интерфейс не предоставляется через службу удаленного взаимодействия.  
>   
>  Компоненты службы не поддерживают **ISSAsynchStatus**.  
  
## <a name="execution-and-rowset-initialization"></a>Выполнение и инициализация наборов строк  
 Приложения, способные асинхронно открывать результаты выполнения команд, могут установить бит DBPROPVAL_ASYNCH_INITIALIZE в свойстве DBPROP_ROWSET_ASYNCH. Если задать этот бит перед вызовом метода **IDBInitialize::Initialize**, **ICommand::Execute**, **IOpenRowset::OpenRowset** или **IMultipleResults:: GetResult**, *riid* аргумент должен иметь значение IID_IDBAsynchStatus, IID_ISSAsynchStatus или IID_IUnknown.  
  
 Метод возвращается немедленно с результатом S_OK, если инициализация набора строк завершается немедленно, или с результатом DB_S_ASYNCHRONOUS, если набора строк продолжается асинхронно, инициализация с *ppRowset* включен на запрошенный интерфейс набор строк. Для OLE DB Driver for SQL Server, этот интерфейс может быть только **IDBAsynchStatus** или **ISSAsynchStatus**. Пока набор строк полностью инициализирован, этот интерфейс действует, как если бы он был в приостановленном состоянии, а вызов метода **QueryInterface** для интерфейсов, отличных от **IID_IDBAsynchStatus** или **IID_ ISSAsynchStatus** могут возвращать E_NOINTERFACE. Если потребитель явно не запросил асинхронную обработку, набор строк инициализируется синхронно. Все запрашиваемые интерфейсы доступны, когда **IDBAsynchStaus::GetStatus** или **ISSAsynchStatus::WaitForAsynchCompletion** возвращается с указанием о завершении асинхронной операции. Это не обязательно означает, что набор строк заполнен, но он завершен и полностью функционален.  
  
 Если выполняемая команда возвращает набор строк, он все равно возвращается немедленно с объектом, который поддерживает **IDBAsynchStatus**.  
  
 Если требуется получить несколько результатов асинхронного выполнения команды, выполните следующие действия.  
  
-   Установите бит DBPROPVAL_ASYNCH_INITIALIZE свойства DBPROP_ROWSET_ASYNCH перед выполнением команды.  
  
-   Вызовите **ICommand::Execute**и запрос **IMultipleResults**.  
  
 **IDBAsynchStatus** и **ISSAsynchStatus** затем интерфейсы можно получить с помощью запроса к нескольким интерфейса результатов с помощью **QueryInterface**.  
  
 После завершения выполнения команды **IMultipleResults** можно использовать обычным образом с единственным отличием от синхронной: DB_S_ASYNCHRONOUS могут быть возвращены, в этом случае **IDBAsynchStatus** или **ISSAsynchStatus** можно использовать для определения, когда операция будет завершена.  
  
## <a name="examples"></a>Примеры  
 В следующем примере приложение вызывает неблокирующий метод, выполняет некоторую другую обработку, а затем возвращает результаты процессу. **ISSAsynchStatus::WaitForAsynchCompletion** ожидает объект внутреннего события до завершения операции асинхронного выполнения или объем времени, заданного параметром *dwMilisecTimeOut* передается.  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
  
DBPROPSET CmdPropset[1];  
DBPROP CmdProperties[1];  
  
CmdPropset[0].rgProperties = CmdProperties;  
CmdPropset[0].cProperties = 1;  
CmdPropset[0].guidPropertySet = DBPROPSET_ROWSET;  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
CmdProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
  
hr = pICommandProps->SetProperties(1, CmdPropset);  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if ( hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 **ISSAsynchStatus::WaitForAsynchCompletion** ожидает объект внутреннего события до завершения операции асинхронного выполнения или *dwMilisecTimeOut* передается значение.  
  
 В следующем примере показана асинхронная обработка с несколькими результирующими наборами.  
  
```  
DBPROP CmdProperties[1];  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_IMultipleResults,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pIMultipleResults);  
  
// Use GetResults for ISSAsynchStatus.  
hr = pIMultipleResults->GetResult(IID_ISSAsynchStatus, (void **) &pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if (hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 Чтобы предотвратить блокировку, клиент может проверить состояние выполняющейся асинхронной операции, как показано в следующем примере.  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);   
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   do{  
      // Do some work...  
      hr = pISSAsynchStatus->GetStatus(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN, NULL, NULL, &ulAsynchPhase, NULL);  
   }while (DBASYNCHPHASE_COMPLETE != ulAsynchPhase)  
   if SUCCEEDED(hr)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
   }  
   pIDBAsynchStatus->Release();  
}  
```  
  
 В следующем примере показано, как можно отменить выполняющуюся в настоящее время асинхронную операцию.  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work...  
   hr = pISSAsynchStatus->Abort(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN);  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для компонентов SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 [Свойства и поведение наборов строк](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md)   
 [ISSAsynchStatus & #40; OLE DB & #41;](../../oledb/ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
