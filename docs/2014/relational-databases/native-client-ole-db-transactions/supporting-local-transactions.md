---
title: Поддержка локальных транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b75104940cca183005f8a465ea19d0a517247c25
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63213817"
---
# <a name="supporting-local-transactions"></a>Поддержка локальных транзакций
  Сеанс ограничивает область транзакции для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] локальных транзакций поставщика OLE DB для собственного клиента. Когда в направлении потребителя, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента отправляет запрос на подключенном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запрос представляет собой единицу работы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента. Локальные транзакции всегда содержат одну или несколько единиц работы в одном [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сеанс поставщика OLE DB для собственного клиента.  
  
 По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] режим автоматической фиксации поставщика OLE DB для собственного клиента, одной единице работы рассматривается как область действия локальной транзакции. В локальной транзакции участвует только одна единица работы. При создании сеанса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента начинает транзакцию для сеанса. При успешном завершении единицы работы выполненная работа фиксируется. При сбое выполняется откат всей начатой работы; потребителю сообщается об ошибке. В любом случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента начинает новую локальную транзакцию для сеанса, чтобы вся работа выполняется в рамках транзакции.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Потребителем поставщика OLE DB для собственного клиента может направлять более точного контроля над локальную область транзакций с помощью **ITransactionLocal** интерфейс. Если сеанс потребителя инициирует транзакцию, все рабочие единицы сеанса между точкой начала транзакции и последующими неизбежными вызовами методов **Commit** или **Abort** рассматриваются как единая операция. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента неявно начинает транзакцию, если для этого объектом-получателем. Если потребитель не запрашивает хранения, сеанс восстанавливает режим родительской транзакции. Как правило, это режим автозавершения.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поддерживает поставщик OLE DB для собственного клиента **ITransactionLocal::StartTransaction** параметры следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*isoLevel*[in]|Уровень изоляции, который должен использоваться с этой транзакцией. В локальной транзакции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента поддерживает следующее:<br /><br /> -ЗНАЧЕНИЕ ISOLATIONLEVEL_UNSPECIFIED<br />-ISOLATIONLEVEL_CHAOS<br />-ЗНАЧЕНИЯМИ ISOLATIONLEVEL_READUNCOMMITTED<br />-ISOLATIONLEVEL_READCOMMITTED<br />-ISOLATIONLEVEL_REPEATABLEREAD<br />-   ISOLATIONLEVEL_CURSORSTABILITY<br />-ISOLATIONLEVEL_REPEATABLEREAD<br />-ISOLATIONLEVEL_SERIALIZABLE<br />-ISOLATIONLEVEL_ISOLATED<br />-ISOLATIONLEVEL_SNAPSHOT **Примечание:**  Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ISOLATIONLEVEL_SNAPSHOT допустим для *isoLevel* аргумент, включено ли управление версиями для базы данных. Однако произойдет ошибка, если пользователь попытается выполнить инструкцию, когда управление версиями не включено, а база данных предназначена не только для чтения. Кроме того, ошибка XACT_E_ISOLATIONLEVEL возникнет, если для *isoLevel* задано значение ISOLATIONLEVEL_SNAPSHOT при соединении с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|*isoFlags*[in]|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает ошибку для ненулевых значений.|  
|*pOtherOptions*[in]|Если значение не NULL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента запрашивает объект параметров с помощью интерфейса. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента возвращает XACT_E_NOTIMEOUT, если объект параметров *ulTimeout* не равен нулю. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента не учитывает значение *szDescription* член.|  
|*pulTransactionLevel*[out]|Если значение не NULL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента Возвращает уровень вложенности транзакции.|  
  
 Для локальных транзакций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реализует поставщик OLE DB для собственного клиента **ITransaction::Abort** параметры следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*pboidReason*[in]|При установке не учитывается. Может иметь значение NULL.|  
|*fRetaining*[in]|Если задано значение TRUE, то для сеанса неявным образом запускается новая транзакция. Эта транзакция должна быть зафиксирована или завершена объектом-получателем. Если задано значение FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента возвращается в режим автоматической фиксации для сеанса.|  
|*fAsync*[in]|Асинхронная Отмена не поддерживается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает XACT_E_NOTSUPPORTED, если не имеет значение FALSE.|  
  
 Для локальных транзакций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реализует поставщик OLE DB для собственного клиента **ITransaction::Commit** параметры следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*fRetaining*[in]|Если задано значение TRUE, то для сеанса неявным образом запускается новая транзакция. Эта транзакция должна быть зафиксирована или завершена объектом-получателем. Если задано значение FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента возвращается в режим автоматической фиксации для сеанса.|  
|*grfTC*[in]|Асинхронные возвраты и возвраты на первом этапе не поддерживаются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента возвращает xact_e_notsupported, если значение, отличное от XACTTC_SYNC.|  
|*grfRM*[in]|Должно быть равно 0.|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Наборы строк поставщика OLE DB для собственного клиента в сеансе, сохраняются на локальной фиксации или прервать операцию, на основе значений набора строк свойств DBPROP_ABORTPRESERVE и DBPROP_COMMITPRESERVE. По умолчанию эти свойства имеют значение VARIANT_FALSE и все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наборы строк поставщика OLE DB для собственного клиента в сеансе теряются после фиксации или отмены операции.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента не реализует **ITransactionObject** интерфейс. При попытке потребителя получить ссылку на интерфейс возвращается E_NOINTERFACE.  
  
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
  
## <a name="see-also"></a>См. также  
 [Транзакции](transactions.md)   
 [Работа с изоляцией моментального снимка](../native-client/features/working-with-snapshot-isolation.md)  
  
  
