---
title: ISSAsynchStatus::WaitForAsynchCompletion (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
apitype: COM
helpviewer_keywords:
- WaitForAsynchCompletion method
ms.assetid: 9f65e9e7-eb93-47a1-bc42-acd4649fbd0e
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2188d0b591e6e383076e2668cab0b1bb7ad0a505
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785317"
---
# <a name="issasynchstatuswaitforasynchcompletion-ole-db"></a>ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Ожидает завершения асинхронно выполняющейся операции или истечения времени ожидания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT WaitForAsynchCompletion(   
        DWORD dwMillisecTimeOut);  
```  
  
## <a name="arguments"></a>Аргументы  
 *dwMillisecTimeOut*[in]  
 Время ожидания в миллисекундах.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_UNEXPECTED  
 Набор строк находится в неиспользуемом состоянии, поскольку либо был вызван метод **ITransaction::Commit** или **ITransaction::Abort** , либо получение набора строк было отменено при его инициализации.  
  
 DB_E_CANCELED  
 Асинхронная обработка была отменена во время заполнения набора строк или инициализации объекта источника данных.  
  
 DB_S_ASYNCHRONOUS  
 Операция еще не завершена, хотя истекло заданное время ожидания.  
  
> [!NOTE]  
>  Помимо приведенных выше значений кода возврата, метод **ISSAsynchStatus::WaitForAsynchCompletion** поддерживает также значения, возвращаемые основными методами OLEDB **ICommand::Execute** и **IDBInitialize::Initialize** .  
  
## <a name="remarks"></a>Примечания  
 Метод **ISSAsynchStatus::WaitForAsynchCompletion** не возвращает управление до тех пор, пока ему не будет передано значение истечения времени ожидания (в миллисекундах) или пока не завершится отложенная операция. Объект **Command** имеет свойство **CommandTimeout** , которое управляет количеством секунд, в течение которых запрос будет выполняться до истечения времени ожидания. Свойство **CommandTimeout** будет пропущено, если используется в сочетании с методом **метод ISSAsynchStatus:: WaitForAsynchCompletion** .  
  
 Свойство времени ожидания для асинхронных операций не учитывается. Параметр истечения времени ожидания **ISSAsynchStatus::WaitForAsynchCompletion** задает максимальное время, которое должно пройти, прежде чем управление будет передано вызывающему объекту. По истечении этого времени ожидания возвращается значение DB_S_ASYNCHRONOUS. Время ожидания никогда не отменяет асинхронные операции. Если приложению необходимо отменить асинхронную операцию, которая не завершена в течение времени ожидания, то оно должно дождаться истечения этого времени, а затем явно отменить операцию, если возвращено значение DB_S_ASYNCHRONOUS.  
  
> [!NOTE]  
>  При использовании компонентов службы OLE DB может быть возвращено значение S_OK вместо DB_S_ASYNCHRONOUS, поэтому при возврате одного из этих значений приложение должно вызывать метод [ISSAsynchStatus::GetStatus](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-getstatus-ole-db.md), чтобы проверить состояние завершения операции.  
  
 Если параметр *dwMillisecTimeOut* имеет значение INFINITE, то метод **ISSAsynchStatus::WaitForAsynchCompletion** блокируется до завершения операции. Если параметр *dwMillisecTimeOut* имеет значение 0, то метод немедленно вернет состояние отложенной операции. Если время ожидания истекло до завершения операции, возвращается значение DB_S_ASYNCHRONOUS.  
  
 Если операция завершится прежде, чем истечет время ожидания, то возвращенное значение будет представлять собой HRESULT операции (то есть HRESULT, который был бы возвращен, если бы операция выполнялась синхронно).  
  
 Кроме того, в набор свойств DBPROPSET_SQLSERVERROWSET добавлено свойство SSPROP_ISSAsynchStatus. Поставщики, поддерживающие интерфейс [ISSAsynchStatus](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-ole-db.md), должны реализовывать это свойство со значением VARIANT_TRUE.  
  
## <a name="see-also"></a>См. также  
 [Выполнение асинхронных операций](../../relational-databases/native-client/features/performing-asynchronous-operations.md)   
 [ISSAsynchStatus (OLE DB)](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
