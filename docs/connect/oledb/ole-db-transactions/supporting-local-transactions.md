---
title: Поддержка локальных транзакций | Документы Microsoft
description: Локальные транзакции в драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- OLE DB Driver for SQL Server, transactions
- local transactions [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 25d6c98c17c139a1658d0711bcff0c1c8f3f1d18
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689367"
---
# <a name="supporting-local-transactions"></a>Поддержка локальных транзакций
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Сеанс ограничивает область транзакции для драйвера OLE DB для SQL Server локальной транзакции. Когда в направлении потребителя, драйвер OLE DB для SQL Server отправляет запрос на подключенный экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], этот запрос представляет собой единицу работы драйвера OLE DB для SQL Server. Локальные транзакции всегда содержат одну или несколько единиц работы на один драйвер OLE DB для SQL Server сеанса.  
  
 По умолчанию драйвер OLE DB для SQL Server режим автоматической фиксации, одной единицы работы рассматривается как область действия локальной транзакции. В локальной транзакции участвует только одна единица работы. При создании сеанса драйвер OLE DB для SQL Server начинает транзакцию для сеанса. При успешном завершении единицы работы выполненная работа фиксируется. При сбое выполняется откат всей начатой работы; потребителю сообщается об ошибке. В любом случае драйвер OLE DB для SQL Server начинает новую локальную транзакцию для сеанса, чтобы вся работа ведется в рамках транзакции.  
  
 Драйвер OLE DB для SQL Server потребителя можно направить более точного контроля над локальную область транзакций с помощью **ITransactionLocal** интерфейса. Если сеанс потребителя инициирует транзакцию, все рабочие единицы сеанса между транзакции запуск точки и последующими неизбежными **зафиксировать** или **прервать** вызовы методов рассматриваются как единый модуль. Драйвер OLE DB для SQL Server неявно начинает транзакцию, если для этого объектом-получателем. Если потребитель не запрашивает хранения, сеанс восстанавливает режим родительской транзакции. Как правило, это режим автозавершения.  
  
 Драйвер OLE DB для SQL Server поддерживает **ITransactionLocal::StartTransaction** параметры следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*isoLevel*[in]|Уровень изоляции, который должен использоваться с этой транзакцией. В локальной транзакции драйвер OLE DB для SQL Server поддерживает следующие функции:<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> Примечание: Начиная с версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], ISOLATIONLEVEL_SNAPSHOT допустим для *isoLevel* аргумент, включено ли управление версиями для базы данных. Однако произойдет ошибка, если пользователь попытается выполнить инструкцию, когда управление версиями не включено, а база данных предназначена не только для чтения. Кроме того, ошибка XACT_E_ISOLATIONLEVEL возникнет, если задано как *isoLevel* при подключении к версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более раннюю, чем [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].|  
|*isoFlags*[in]|Драйвер OLE DB для SQL Server возвращает ошибку для ненулевых значений.|  
|*pOtherOptions*[in]|В противном случае значение NULL, драйвер OLE DB для SQL Server запрашивает объект параметров от интерфейса. Драйвер OLE DB для SQL Server возвращает XACT_E_NOTIMEOUT, если объект параметров *ulTimeout* не равен нулю. Драйвер OLE DB для SQL Server пропускает значения *szDescription* член.|  
|*pulTransactionLevel*[out]|В противном случае значение NULL, драйвер OLE DB для SQL Server возвращает уровень вложенности транзакции.|  
  
 Для локальных транзакций реализует драйвер OLE DB для SQL Server **ITransaction::Abort** параметры следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*pboidReason*[in]|При установке не учитывается. Может иметь значение NULL.|  
|*fRetaining*[in]|Если задано значение TRUE, то для сеанса неявным образом запускается новая транзакция. Эта транзакция должна быть зафиксирована или завершена объектом-получателем. Если задано значение FALSE, драйвер OLE DB для SQL Server переходит в режим автоматической фиксации для данного сеанса.|  
|*fAsync*[in]|Асинхронное прерывание не поддерживается драйвером OLE DB для SQL Server. Драйвер OLE DB для SQL Server возвращает XACT_E_NOTSUPPORTED, если значение не равно FALSE.|  
  
 Для локальных транзакций реализует драйвер OLE DB для SQL Server **ITransaction::Commit** параметры следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*fRetaining*[in]|Если задано значение TRUE, то для сеанса неявным образом запускается новая транзакция. Эта транзакция должна быть зафиксирована или завершена объектом-получателем. Если задано значение FALSE, драйвер OLE DB для SQL Server переходит в режим автоматической фиксации для данного сеанса.|  
|*grfTC*[in]|Асинхронная и возвращает одно для фазы не поддерживаются драйвером OLE DB для SQL Server. Драйвер OLE DB для SQL Server возвращает xact_e_notsupported, если значение не равно XACTTC_SYNC.|  
|*grfRM*[in]|Должно быть равно 0.|  
  
 Драйвер OLE DB для SQL Server наборы строк в сеансе, сохраняются на локальном фиксация или прерывание операции на основе значений набора строк свойств DBPROP_ABORTPRESERVE и DBPROP_COMMITPRESERVE. По умолчанию эти свойства являются VARIANT_FALSE и все драйвер OLE DB для SQL Server наборы строк в сеансе, будут потеряны после прерывания или зафиксировать операцию.  
  
 Драйвер OLE DB для SQL Server не реализует **ITransactionObject** интерфейса. При попытке потребителя получить ссылку на интерфейс возвращается E_NOINTERFACE.  
  
 В этом примере используется **ITransactionLocal**.  
  
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
  
## <a name="see-also"></a>См. также  
 [Транзакции](../../oledb/ole-db-transactions/transactions.md)   
 [Работа с изоляцией моментального снимка](../../oledb/features/working-with-snapshot-isolation.md)  
  
  
