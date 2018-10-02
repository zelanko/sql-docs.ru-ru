---
title: Поддержка локальных транзакций | Документация Майкрософт
description: Локальные транзакции в драйвере OLE DB для SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- OLE DB Driver for SQL Server, transactions
- local transactions [OLE DB]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 82621a5c289a3ae7a31affa848bc5b2a77800736
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788687"
---
# <a name="supporting-local-transactions"></a>Поддержка локальных транзакций
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Сеанс ограничивает область транзакции для драйвера OLE DB для SQL Server локальной транзакции. Когда, в направлении потребителя, драйвер OLE DB для SQL Server отправляет запрос к подключенному экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], запрос представляет собой единицу работы для драйвера OLE DB для SQL Server. Локальные транзакции всегда содержат одну или несколько единиц работы на один драйвер OLE DB для SQL Server сеанса.  
  
 При использовании режима автоматической фиксации, установленного для драйвера OLE DB для SQL Server по умолчанию, одна единица работы рассматривается как область действия локальной транзакции. В локальной транзакции участвует только одна единица работы. При создании сеанса, драйвер OLE DB для SQL Server начинает транзакцию для сеанса. При успешном завершении единицы работы выполненная работа фиксируется. При сбое выполняется откат всей начатой работы; потребителю сообщается об ошибке. В любом случае драйвер OLE DB для SQL Server начинает новую локальную транзакцию для сеанса, чтобы выполнить всю работу в транзакции.  
  
 Потребитель драйвера OLE DB для SQL Server может более детально управлять областью действия локальной транзакции с помощью интерфейса **ITransactionLocal**. Если сеанс потребителя инициирует транзакцию, все рабочие единицы сеанса между точкой начала транзакции и последующими неизбежными вызовами методов **Commit** или **Abort** рассматриваются как единая операция. Драйвер OLE DB для SQL Server неявно начинает транзакцию, если для этого объектом-получателем. Если потребитель не запрашивает хранения, сеанс восстанавливает режим родительской транзакции. Как правило, это режим автозавершения.  
  
 Драйвер OLE DB для SQL Server поддерживает **ITransactionLocal::StartTransaction** параметры следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*isoLevel*[in]|Уровень изоляции, который должен использоваться с этой транзакцией. В локальной транзакции драйвер OLE DB для SQL Server поддерживает следующие функции:<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> Начиная с [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] уровень изоляции ISOLATIONLEVEL_SNAPSHOT допустим для аргумента *isoLevel* независимо от того, включено ли в базе данных управление версиями. Однако произойдет ошибка, если пользователь попытается выполнить инструкцию, когда управление версиями не включено, а база данных предназначена не только для чтения. Кроме того, ошибка XACT_E_ISOLATIONLEVEL возникнет, если для *isoLevel* задано значение ISOLATIONLEVEL_SNAPSHOT при соединении с версией [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].|  
|*isoFlags*[in]|Драйвер OLE DB для SQL Server возвращает ошибку для ненулевых значений.|  
|*pOtherOptions*[in]|В противном случае значение NULL, драйвер OLE DB для SQL Server требует, чтобы объект параметров с помощью интерфейса. Драйвер OLE DB для SQL Server возвращает XACT_E_NOTIMEOUT, если объект параметров *ulTimeout* не равен нулю. Драйвер OLE DB для SQL Server пропускает значение *szDescription* член.|  
|*pulTransactionLevel*[out]|В противном случае значение NULL, драйвер OLE DB для SQL Server возвращает уровень вложенности транзакции.|  
  
 Для локальных транзакций драйвера OLE DB для SQL Server реализует **ITransaction::Abort** параметры следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*pboidReason*[in]|При установке не учитывается. Может иметь значение NULL.|  
|*fRetaining*[in]|Если задано значение TRUE, то для сеанса неявным образом запускается новая транзакция. Эта транзакция должна быть зафиксирована или завершена объектом-получателем. Если задано значение FALSE, драйвер OLE DB для SQL Server переходит в режим автоматической фиксации для сеанса.|  
|*fAsync*[in]|Асинхронная Отмена не поддерживается драйвером OLE DB для SQL Server. Драйвер OLE DB для SQL Server возвращает XACT_E_NOTSUPPORTED, если не имеет значение FALSE.|  
  
 Для локальных транзакций драйвера OLE DB для SQL Server реализует **ITransaction::Commit** параметры следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*fRetaining*[in]|Если задано значение TRUE, то для сеанса неявным образом запускается новая транзакция. Эта транзакция должна быть зафиксирована или завершена объектом-получателем. Если задано значение FALSE, драйвер OLE DB для SQL Server переходит в режим автоматической фиксации для сеанса.|  
|*grfTC*[in]|Асинхронные возвраты и возвраты для фазы не поддерживаются с помощью драйвера OLE DB для SQL Server. Драйвер OLE DB для SQL Server возвращает xact_e_notsupported, если значение, отличное от XACTTC_SYNC.|  
|*grfRM*[in]|Должно быть равно 0.|  
  
 Наборы строк в сеансе драйвера OLE DB для SQL Server сохраняются в локальной операции фиксации или отмены на основе значений набора строк свойств DBPROP_ABORTPRESERVE и DBPROP_COMMITPRESERVE. По умолчанию эти свойства имеют значение VARIANT_FALSE, и все наборы строк в сеансе драйвера OLE DB для SQL Server теряются после операции фиксации или отмены.  
  
 Драйвер OLE DB для SQL Server не реализует **ITransactionObject** интерфейс. При попытке потребителя получить ссылку на интерфейс возвращается E_NOINTERFACE.  
  
 В этом примере используется интерфейс **ITransactionLocal**.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
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
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>См. также:  
 [Транзакции](../../oledb/ole-db-transactions/transactions.md)   
 [Работа с изоляцией моментального снимка](../../oledb/features/working-with-snapshot-isolation.md)  
  
  
