---
title: ISSAsynchStatus::WaitForAsynchCompletion (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- WaitForAsynchCompletion method
ms.assetid: 9f65e9e7-eb93-47a1-bc42-acd4649fbd0e
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10fa772517ac96f59510245ab25ef0e5a05438d8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425854"
---
# <a name="issasynchstatuswaitforasynchcompletion-ole-db"></a>ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
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
 Метод **ISSAsynchStatus::WaitForAsynchCompletion** не возвращает управление до тех пор, пока ему не будет передано значение истечения времени ожидания (в миллисекундах) или пока не завершится отложенная операция. У объекта **Command** есть свойство **CommandTimeout** , управляющее временем (в секундах), в течение которого будет выполняться запрос, прежде чем истечет время ожидания. **CommandTimeout** свойство учитывается, если используется в сочетании с **ISSAsynchStatus::WaitForAsynchCompletion** метод.  
  
 Свойство времени ожидания для асинхронных операций не учитывается. Параметр истечения времени ожидания **ISSAsynchStatus::WaitForAsynchCompletion** задает максимальное время, которое должно пройти, прежде чем управление будет передано вызывающему объекту. По истечении этого времени ожидания возвращается значение DB_S_ASYNCHRONOUS. Время ожидания никогда не отменяет асинхронные операции. Если приложению необходимо отменить асинхронную операцию, которая не завершена в течение времени ожидания, то оно должно дождаться истечения этого времени, а затем явно отменить операцию, если возвращено значение DB_S_ASYNCHRONOUS.  
  
> [!NOTE]  
>  При применении компонентов службы OLE DB, может быть возвращено значение S_OK при ожидается DB_S_ASYNCHRONOUS, поэтому приложение должно вызывать [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) Чтобы проверить состояние завершения операции возвращается.  
  
 Если параметр *dwMillisecTimeOut* имеет значение INFINITE, то метод **ISSAsynchStatus::WaitForAsynchCompletion** блокируется до завершения операции. Если параметр *dwMillisecTimeOut* имеет значение 0, то метод немедленно вернет состояние отложенной операции. Если время ожидания истекло до завершения операции, возвращается значение DB_S_ASYNCHRONOUS.  
  
 Если операция завершится прежде, чем истечет время ожидания, то возвращенное значение будет представлять собой HRESULT операции (то есть HRESULT, который был бы возвращен, если бы операция выполнялась синхронно).  
  
 Кроме того, в набор свойств DBPROPSET_SQLSERVERROWSET добавлено свойство SSPROP_ISSAsynchStatus. Поставщики, поддерживающие [ISSAsynchStatus](issasynchstatus-ole-db.md) интерфейс должны реализовывать это свойство со значением VARIANT_TRUE.  
  
## <a name="see-also"></a>См. также  
 [Выполнение асинхронных операций](../native-client/features/performing-asynchronous-operations.md)   
 [ISSAsynchStatus &#40;OLE DB&#41;](issasynchstatus-ole-db.md)  
  
  
