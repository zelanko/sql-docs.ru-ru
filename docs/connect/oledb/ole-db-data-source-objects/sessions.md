---
title: Сеансы | Документация Майкрософт
description: Сеансы в драйвере OLE DB для SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- OLE DB Driver for SQL Server, sessions
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 0753e0d4347a86db3401806c2b46cba7224342eb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731422"
---
# <a name="sessions"></a>Сеансы
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server сеанса представляет одно соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Драйвер OLE DB для SQL Server требует, чтобы сеансы разделили область транзакции для источника данных. Все объекты команд, созданные из определенного объекта сеанса, участвуют в локальной или распределенной транзакции объекта сеанса.  
  
 Первый объект сеанса, созданный на инициализированном источнике данных, получает соединение [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], установленное при инициализации. Когда все ссылки на интерфейсах объекта сеанса освобождены, соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] становится доступным другому объекту сеанса, созданному на источнике данных.  
  
 Дополнительный объект сеанса, созданный на источнике данных, устанавливает собственное соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], указанным источником данных. Соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] удаляется, когда приложение освобождает все ссылки на объекты, созданные в этом сеансе.  
  
 В следующем примере показано, как использовать драйвер OLE DB для SQL Server для подключения к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных:  
  
```  
int main()  
{  
    // Interfaces used in the example.  
    IDBInitialize*      pIDBInitialize      = NULL;  
    IDBCreateSession*   pIDBCreateSession   = NULL;  
    IDBCreateCommand*   pICreateCmd1        = NULL;  
    IDBCreateCommand*   pICreateCmd2        = NULL;  
    IDBCreateCommand*   pICreateCmd3        = NULL;  
  
    // Initialize COM.  
    if (FAILED(CoInitialize(NULL)))  
    {  
        // Display error from CoInitialize.  
        return (-1);  
    }  
  
    // Get the memory allocator for this task.  
    if (FAILED(CoGetMalloc(MEMCTX_TASK, &g_pIMalloc)))  
    {  
        // Display error from CoGetMalloc.  
        goto EXIT;  
    }  
  
    // Create an instance of the data source object.  
    if (FAILED(CoCreateInstance(CLSID_MSOLEDBSQL, NULL,  
        CLSCTX_INPROC_SERVER, IID_IDBInitialize, (void**)  
        &pIDBInitialize)))  
    {  
        // Display error from CoCreateInstance.  
        goto EXIT;  
    }  
  
    // The InitFromPersistedDS function   
    // performs IDBInitialize->Initialize() establishing  
    // the first application connection to the instance of SQL Server.  
    if (FAILED(InitFromPersistedDS(pIDBInitialize, L"MyDataSource",  
        NULL, NULL)))  
    {  
        goto EXIT;  
    }  
  
    // The IDBCreateSession interface is implemented on the data source  
    // object. Maintaining the reference received maintains the   
    // connection of the data source to the instance of SQL Server.  
    if (FAILED(pIDBInitialize->QueryInterface(IID_IDBCreateSession,  
        (void**) &pIDBCreateSession)))  
    {  
        // Display error from pIDBInitialize.  
        goto EXIT;  
    }  
  
    // Releasing this has no effect on the SQL Server connection  
    // of the data source object because of the reference maintained by  
    // pIDBCreateSession.  
    pIDBInitialize->Release();  
    pIDBInitialize = NULL;  
  
    // The session created next receives the SQL Server connection of  
    // the data source object. No new connection is established.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd1)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
    // A new connection to the instance of SQL Server is established to support the  
    // next session object created. On successful completion, the  
    // application has two active connections on the SQL Server.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd2)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
    // pICreateCmd1 has the data source connection. Because the  
    // reference on the IDBCreateSession interface of the data source  
    // has not been released, releasing the reference on the session  
    // object does not terminate a connection to the instance of SQL Server.  
    // However, the connection of the data source object is now   
    // available to another session object. After a successful call to   
    // Release, the application still has two active connections to the   
    // instance of SQL Server.  
    pICreateCmd1->Release();  
    pICreateCmd1 = NULL;  
  
    // The next session created gets the SQL Server connection  
    // of the data source object. The application has two active  
    // connections to the instance of SQL Server.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd3)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
EXIT:  
    // Even on error, this does not terminate a SQL Server connection   
    // because pICreateCmd1 has the connection of the data source   
    // object.  
    if (pICreateCmd1 != NULL)  
        pICreateCmd1->Release();  
  
    // Releasing the reference on pICreateCmd2 terminates the SQL  
    // Server connection supporting the session object. The application  
    // now has only a single active connection on the instance of SQL Server.  
    if (pICreateCmd2 != NULL)  
        pICreateCmd2->Release();  
  
    // Even on error, this does not terminate a SQL Server connection   
    // because pICreateCmd3 has the connection of the   
    // data source object.  
    if (pICreateCmd3 != NULL)  
        pICreateCmd3->Release();  
  
    // On release of the last reference on a data source interface, the  
    // connection of the data source object to the instance of SQL Server is broken.  
    // The example application now has no SQL Server connections active.  
    if (pIDBCreateSession != NULL)  
        pIDBCreateSession->Release();  
  
    // Called only if an error occurred while attempting to get a   
    // reference on the IDBCreateSession interface of the data source.  
    // If so, the call to IDBInitialize::Uninitialize terminates the   
    // connection of the data source object to the instance of SQL Server.  
    if (pIDBInitialize != NULL)  
    {  
        if (FAILED(pIDBInitialize->Uninitialize()))  
        {  
            // Uninitialize is not required, but it fails if an  
            // interface has not been released. Use it for  
            // debugging.  
        }  
        pIDBInitialize->Release();  
    }  
  
    if (g_pIMalloc != NULL)  
        g_pIMalloc->Release();  
  
    CoUninitialize();  
  
    return (0);  
}  
```  
  
 При соединении объектов сеанса драйвера OLE DB для SQL Server с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] могут возникнуть существенные издержки для приложений, которые постоянно создают и освобождают объекты сеанса. Издержки можно уменьшить, эффективно управляя драйвера OLE DB для объектов сеанса SQL Server. Приложения драйвера OLE DB для SQL Server могут сохранять соединение [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] объекта сеанса активным, поддерживая ссылку по крайней мере на один интерфейс объекта.  
  
 Например, поддержание пула ссылок на объект создания команды сохраняет активными соединения для этих объектов сеанса в пуле. Когда требуются объекты сеанса, код обслуживания пула передает действительный указатель интерфейса **IDBCreateCommand** методу приложения, которому требуется сеанс. Когда сеанс более не требуется методу приложения, метод возвращает указатель интерфейса коду обслуживания пула, а не освобождает ссылку приложения на объект создания команды.  
  
> [!NOTE]  
>  В предыдущем примере используется интерфейс **IDBCreateCommand**, так как интерфейс **ICommand** реализует метод **GetDBSession**, единственный метод в команде или области набора строк, который позволяет объекту определить сеанс, в котором он был создан. Поэтому объект команды, и только объект команды, позволяет приложению получить указатель объекта источника данных, из которого могут быть созданы дополнительные сеансы.  
  
## <a name="see-also"></a>См. также:  
 [Объекты источника данных &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
