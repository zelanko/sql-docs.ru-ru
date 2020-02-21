---
title: ISSAbort::Abort (OLE DB) | Документация Майкрософт
description: ISSAbort::Abort (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSAbort::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 72ce7fa29adfb349fab8c9e60872740c94484108
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67994384"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Отменяет текущий набор строк и любые пакетные команды, ассоциированные с текущей командой.  
  
Интерфейс **ISSAbort**, доступ к которому обеспечивает драйвер OLE DB для SQL Server, предоставляет метод **ISSAbort::Abort**, используемый для отмены текущего набора строк, а также любых команд, находящихся в одном пакете с командой, первоначально создавшей этот набор строк, и еще не завершивших выполнение.  
  
 Интерфейс**ISSAbort** является специфичным для драйвера OLE DB для SQL Server. Доступ к нему можно получить с помощью метода **QueryInterface** объекта **IMultipleResults**, возвращенного методом **ICommand::Execute** или **IOpenRowset::OpenRowset**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Remarks  
 Если команда, выполнение которой прерывается, принадлежит хранимой процедуре, выполнение этой хранимой процедуры (и любых вызвавших ее процедур, а также командного пакета, из которого производился вызов процедуры) будет прервано. Если сервер в это время передавал клиенту результирующий набор, эта передача будет прекращена. Если клиент не хочет получать результирующий набор, перед освобождением набора строк можно вызвать метод **ISSAbort::Abort** ; это ускорит высвобождение набора строк, но если в это время существует открытая транзакция и ее свойство XACT_ABORT имеет значение ON, при вызове **ISSAbort::Abort** произойдет откат транзакции.  
  
 После того как метод **ISSAbort::Abort** вернет результат S_OK, связанный с ним интерфейс **IMultipleResults** становится непригодным к использованию и вплоть до освобождения в ответ на вызовы любых методов (кроме методов, определенных в интерфейсе **IUnknown**) возвращает результат DB_E_CANCELED. Если из интерфейса **IMultipleResults** до вызова метода **Abort** был получен интерфейс **IRowset**, он также входит в непригодное к использованию состояние и в ответ на любые вызовы методов возвращает результат DB_E_CANCELED (кроме методов, определенных для интерфейсов **IUnknown** и **IRowset::ReleaseRows**), пока не будет освобожден успешным вызовом метода **ISSAbort::Abort**.  
  
> [!NOTE]  
>  Начиная с версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], если состояние сервера XACT_ABORT имеет значение ON, вызов метода **ISSAbort::Abort** при подключении к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] прекращает все транзакции, явные и неявные, и совершает их откат. Более ранние версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не прекратят текущих транзакций.  
  
## <a name="arguments"></a>Аргументы  
 Нет.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод **ISSAbort::Abort** возвращает значение S_OK, если было прервано выполнение программного пакета, и DB_E_CANTCANCEL в противном случае. Если выполнение программного пакета уже было прервано ранее, возвращается DB_E_CANCELED.  
  
 DB_E_CANCELED  
 Выполнение пакета уже было прервано.  
  
 DB_E_CANTCANCEL  
 Выполнение пакета не было прервано.  
  
 E_FAIL  
 Произошла ошибка, связанная с поставщиком. Подробные сведения можно получить при помощи интерфейса [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например, объект находится в состоянии зомби, потому что метод **ISSAbort::Abort** уже был вызван.  
  
 E_OUTOFMEMORY  
 Ошибка, связанная с нехваткой памяти.  
  
  
