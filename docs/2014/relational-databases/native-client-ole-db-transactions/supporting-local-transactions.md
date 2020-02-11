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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63213817"
---
# <a name="supporting-local-transactions"></a>Поддержка локальных транзакций
  Сеанс разделяет область действия транзакции для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB локальной транзакции поставщика. Если, в направлении потребителя, поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента отправляет запрос к подключенному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запрос создает единицу работы для поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB. Локальные транзакции всегда заключают одну или несколько единиц работы на один [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент OLE DBного сеанса поставщика.  
  
 При использовании режима [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматической фиксации поставщика OLE DB собственного клиента по умолчанию одна единица работы рассматривается как область локальной транзакции. В локальной транзакции участвует только одна единица работы. При создании сеанса поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента начинает транзакцию для сеанса. При успешном завершении единицы работы выполненная работа фиксируется. При сбое выполняется откат всей начатой работы; потребителю сообщается об ошибке. В любом случае поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента начинает новую локальную транзакцию для сеанса, чтобы вся работа выполнялась в рамках транзакции.  
  
 Потребитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB собственного клиента может направить более точный контроль над областью локальной транзакции с помощью интерфейса **ITransactionLocal** . Если сеанс потребителя инициирует транзакцию, все рабочие единицы сеанса между точкой начала транзакции и последующими неизбежными вызовами методов **Commit** или **Abort** рассматриваются как единая операция. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента неявным образом начинает транзакцию, когда она направляется потребителю. Если потребитель не запрашивает хранения, сеанс восстанавливает режим родительской транзакции. Как правило, это режим автозавершения.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента поддерживает параметры **ITransactionLocal:: StartTransaction** , как показано ниже.  
  
|Параметр|Description|  
|---------------|-----------------|  
|*isoLevel*[in]|Уровень изоляции, который должен использоваться с этой транзакцией. В локальных транзакциях поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB поддерживает следующие действия:<br /><br /> — ISOLATIONLEVEL_UNSPECIFIED<br />— ISOLATIONLEVEL_CHAOS<br />— ISOLATIONLEVEL_READUNCOMMITTED<br />— ISOLATIONLEVEL_READCOMMITTED<br />— ISOLATIONLEVEL_REPEATABLEREAD<br />— ISOLATIONLEVEL_CURSORSTABILITY<br />— ISOLATIONLEVEL_REPEATABLEREAD<br />— ISOLATIONLEVEL_SERIALIZABLE<br />— ISOLATIONLEVEL_ISOLATED<br />-ISOLATIONLEVEL_SNAPSHOT **Примечание.** начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]версии, ISOLATIONLEVEL_SNAPSHOT является допустимым для аргумента *isoLevel* , независимо от того, включено ли управление версиями для базы данных. Однако произойдет ошибка, если пользователь попытается выполнить инструкцию, когда управление версиями не включено, а база данных предназначена не только для чтения. Кроме того, ошибка XACT_E_ISOLATIONLEVEL возникнет, если для *isoLevel* задано значение ISOLATIONLEVEL_SNAPSHOT при соединении с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|*исофлагс*[in]|Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента возвращает ошибку для любого значения, отличного от нуля.|  
|*посероптионс*[in]|Если значение не равно NULL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , поставщик OLE DB собственного клиента запрашивает объект параметров из интерфейса. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента возвращает XACT_E_NOTIMEOUT, если элемент *ултимеаут* объекта параметров не равен нулю. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента игнорирует значение элемента *сздескриптион* .|  
|*пултрансактионлевел*[out]|Если значение не равно NULL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , поставщик OLE DB собственного клиента возвращает вложенный уровень транзакции.|  
  
 Для локальных транзакций поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента реализует параметры **ITransaction:: Abort** , как показано ниже.  
  
|Параметр|Description|  
|---------------|-----------------|  
|*пбоидреасон*[in]|При установке не учитывается. Может иметь значение NULL.|  
|*фретаининг*[in]|Если задано значение TRUE, то для сеанса неявным образом запускается новая транзакция. Эта транзакция должна быть зафиксирована или завершена объектом-получателем. Если значение равно " [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] false", поставщик OLE DB собственного клиента возвращается в режим автоматической фиксации для сеанса.|  
|*фасинк*[in]|Асинхронное прерывание не поддерживается поставщиком [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента возвращает XACT_E_NOTSUPPORTED, если значение не равно false.|  
  
 Для локальных транзакций поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB реализует параметры **ITransaction:: Commit** , как показано ниже.  
  
|Параметр|Description|  
|---------------|-----------------|  
|*фретаининг*[in]|Если задано значение TRUE, то для сеанса неявным образом запускается новая транзакция. Эта транзакция должна быть зафиксирована или завершена объектом-получателем. Если значение равно " [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] false", поставщик OLE DB собственного клиента возвращается в режим автоматической фиксации для сеанса.|  
|*грфтк*[in]|Асинхронные и одноэтапные возвраты не поддерживаются поставщиком [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента возвращает XACT_E_NOTSUPPORTED для любого значения, кроме XACTTC_SYNC.|  
|*грфрм*[in]|Должно быть равно 0.|  
  
 Наборы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] строк поставщика собственного клиента OLE DB в сеансе сохраняются в локальной операции фиксации или прерывания на основе значений свойств набора строк DBPROP_ABORTPRESERVE и DBPROP_COMMITPRESERVE. По умолчанию эти свойства VARIANT_FALSE и все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наборы строк поставщика собственного клиента OLE DB в сеансе теряются после операции прерывания или фиксации.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента не реализует интерфейс **итрансактионобжект** . При попытке потребителя получить ссылку на интерфейс возвращается E_NOINTERFACE.  
  
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
 [Провод](transactions.md)   
 [Работа с изоляцией моментального снимка](../native-client/features/working-with-snapshot-isolation.md)  
  
  
