---
title: Поддержка распределенных транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- distributed transactions [OLE DB]
- MS DTC
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
- ITransactionJoin interface
- MS DTC, about distributed transaction support
ms.assetid: d250b43b-9260-4ea4-90cc-57d9a2f67ea7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0f6248636338d810127d7006ca87fd91ab359069
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704491"
---
# <a name="supporting-distributed-transactions"></a>Поддержка распределенных транзакций
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Потребители поставщика OLE DB собственного клиента могут использовать метод **ITransactionJoin:: жоинтрансактион** для участия в распределенной транзакции, которая координируется Microsoft координатор распределенных транзакций (MS DTC).  
  
 Службы MS DTC предоставляют доступ к COM-объектам, которые позволяют клиентам запускать и участвовать в координированных транзакциях через несколько соединений с различными хранилищами данных. Чтобы инициировать транзакцию, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребитель поставщика OLE DB собственного клиента использует интерфейс MS DTC **ITransactionDispenser** . Элемент **BeginTransaction** интерфейса **ITransactionDispenser** возвращает ссылку на объект распределенной транзакции. Эта ссылка передается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный поставщик OLE DB клиента с помощью **жоинтрансактион**.  
  
 Службы MS DTC поддерживают асинхронную фиксацию и прерывание распределенных транзакций. Для уведомления о состоянии асинхронных транзакций потребитель реализует интерфейс **ITransactionOutcomeEvents** и подключает интерфейс к объекту транзакции MS DTC.  
  
 Для распределенных транзакций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB реализует параметры **ITransactionJoin:: жоинтрансактион** следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*punkTransactionCoord*|Указатель на объект транзакции MS DTC.|  
|*IsoLevel*|Игнорируется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщиком собственного клиента OLE DB. Уровень изоляции для транзакций, координируемых с использованием служб MS DTC, определяется, когда пользователь получает объект транзакции от координатора MS DTC.|  
|*IsoFlags*|Должно быть равно 0. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента возвращает XACT_E_NOISORETAIN, если потребитель указал любое другое значение.|  
|*POtherOptions*|Если значение не равно NULL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента запрашивает объект параметров из интерфейса. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента возвращает XACT_E_NOTIMEOUT, если элемент *ултимеаут* объекта параметров не равен нулю. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента игнорирует значение элемента *сздескриптион* .|  
  
 В этом примере осуществляется координирование транзакции с использованием координатора MS DTC.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*       pIDBCreateSession   = NULL;  
ITransactionJoin*       pITransactionJoin   = NULL;  
IDBCreateCommand*       pIDBCreateCommand   = NULL;  
IRowset*                pIRowset            = NULL;  
  
// Transaction dispenser and transaction from MS DTC.  
ITransactionDispenser*  pITransactionDispenser = NULL;  
ITransaction*           pITransaction       = NULL;  
  
    HRESULT             hr;  
  
// Get the command creation interface for the session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
// Get a transaction dispenser object from MS DTC and  
// start a transaction.  
if (FAILED(hr = DtcGetTransactionManager(NULL, NULL,  
    IID_ITransactionDispenser, 0, 0, NULL,  
    (void**) &pITransactionDispenser)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
if (FAILED(hr = pITransactionDispenser->BeginTransaction(  
    NULL, ISOLATIONLEVEL_READCOMMITTED, ISOFLAG_RETAIN_DONTCARE,  
    NULL, &pITransaction)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
  
// Join the transaction.  
if (FAILED(pIDBCreateCommand->QueryInterface(IID_ITransactionJoin,  
    (void**) &pITransactionJoin)))  
    {  
    // Process failure to get an interface, release any references, and  
    // then return.  
    }  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) pITransaction, 0, 0, NULL)))  
    {  
    // Process join failure, release any references, and then return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then abort.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, 0, 0)))  
        {  
        // Get error from failed commit.  
        //  
        // If a distributed commit fails, application logic could  
        // analyze failure and retry. In this example, terminate. The   
        // consumer must resolve this somehow.  
        pITransaction->Abort(NULL, FALSE, FALSE);  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Un-enlist from the distributed transaction by setting   
// the transaction object pointer to NULL.  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) NULL, 0, 0, NULL)))  
    {  
    // Process failure, and then return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>См. также  
 [Транзакции](transactions.md)  
  
  
