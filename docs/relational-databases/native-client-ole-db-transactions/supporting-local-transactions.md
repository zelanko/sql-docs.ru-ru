---
title: Поддержка локальных транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 76e14df87e8dca104fc0b9da44836288dc56ea69
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73761550"
---
# <a name="supporting-local-transactions"></a>Поддержка локальных транзакций
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Сеанс разделяет область транзакций для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB локальной транзакции поставщика. Когда, в направлении потребителя, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB поставщик отправляет запрос к подключенному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запрос создает единицу работы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB поставщика. Локальные транзакции всегда заключают одну или несколько единиц работы на один [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DBного сеанса поставщика.  
  
 При использовании режима автоматической фиксации OLE DB поставщика собственного клиента по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] умолчанию одна единица работы рассматривается как область локальной транзакции. В локальной транзакции участвует только одна единица работы. При создании сеанса поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client начинает транзакцию для сеанса. При успешном завершении единицы работы выполненная работа фиксируется. При сбое выполняется откат всей начатой работы; потребителю сообщается об ошибке. В любом случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент OLE DB поставщика начинает новую локальную транзакцию для сеанса, чтобы вся работа выполнялась в рамках транзакции.  
  
 Потребитель поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB может направить более точный контроль над областью локальной транзакции с помощью интерфейса **ITransactionLocal** . Если сеанс потребителя инициирует транзакцию, все рабочие единицы сеанса между точкой начала транзакции и последующими неизбежными вызовами методов **Commit** или **Abort** рассматриваются как единая операция. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB неявно начинает транзакцию, когда она направляется потребителю. Если потребитель не запрашивает хранения, сеанс восстанавливает режим родительской транзакции. Как правило, это режим автозавершения.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB поддерживает параметры **ITransactionLocal:: StartTransaction** , как показано ниже.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*isoLevel*[in]|Уровень изоляции, который должен использоваться с этой транзакцией. В локальных транзакциях поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB поддерживает следующие действия:<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] уровень изоляции ISOLATIONLEVEL_SNAPSHOT допустим для аргумента *isoLevel* независимо от того, включено ли в базе данных управление версиями. Однако произойдет ошибка, если пользователь попытается выполнить инструкцию, когда управление версиями не включено, а база данных предназначена не только для чтения. Кроме того, ошибка XACT_E_ISOLATIONLEVEL возникнет, если для *isoLevel* задано значение ISOLATIONLEVEL_SNAPSHOT при соединении с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|*isoFlags*[in]|Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает ошибку для любого значения, отличного от нуля.|  
|*pOtherOptions*[in]|Если значение не равно NULL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB запрашивает объект Options из интерфейса. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB возвращает XACT_E_NOTIMEOUT, если элемент *ултимеаут* объекта параметров не равен нулю. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB не учитывает значение элемента *сздескриптион* .|  
|*pulTransactionLevel*[out]|Если значение не равно NULL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB возвращает вложенный уровень транзакции.|  
  
 Для локальных транзакций поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client реализует параметры **ITransaction:: Abort** , как показано ниже.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*pboidReason*[in]|При установке не учитывается. Может иметь значение NULL.|  
|*fRetaining*[in]|Если задано значение TRUE, то для сеанса неявным образом запускается новая транзакция. Эта транзакция должна быть зафиксирована или завершена объектом-получателем. Если значение равно "FALSE", [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент OLE DB поставщик возвращается в режим автоматической фиксации для сеанса.|  
|*fAsync*[in]|Асинхронное прерывание не поддерживается поставщиком [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает XACT_E_NOTSUPPORTED, если значение не равно FALSE.|  
  
 Для локальных транзакций поставщик OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client реализует параметры **ITransaction:: Commit** следующим образом.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*fRetaining*[in]|Если задано значение TRUE, то для сеанса неявным образом запускается новая транзакция. Эта транзакция должна быть зафиксирована или завершена объектом-получателем. Если значение равно "FALSE", [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент OLE DB поставщик возвращается в режим автоматической фиксации для сеанса.|  
|*grfTC*[in]|Асинхронные и одноэтапные возвраты не поддерживаются поставщиком OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает XACT_E_NOTSUPPORTED для любого значения, кроме XACTTC_SYNC.|  
|*grfRM*[in]|Должно быть равно 0.|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственные наборы строк поставщика OLE DBного клиента в сеансе сохраняются в локальной операции фиксации или прерывания, основанной на значениях свойств набора строк DBPROP_ABORTPRESERVE и DBPROP_COMMITPRESERVE. По умолчанию эти свойства VARIANT_FALSE и все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственные наборы строк поставщика OLE DB клиента в сеансе теряются после операции прерывания или фиксации.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB не реализует интерфейс **итрансактионобжект** . При попытке потребителя получить ссылку на интерфейс возвращается E_NOINTERFACE.  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [Транзакции](../../relational-databases/native-client-ole-db-transactions/transactions.md)   
 [Работа с изоляцией моментального снимка](../../relational-databases/native-client/features/working-with-snapshot-isolation.md)  
  
  
