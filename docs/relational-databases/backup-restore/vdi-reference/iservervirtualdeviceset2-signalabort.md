---
title: IServerVirtualDeviceSet2::SignalAbort
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IServerVirtualDeviceSet2::SignalAbort.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: cawrites
ms.author: chadam
ms.openlocfilehash: 8275d2bbe11b550a804ab9bd9bcf475e1d2fbd34
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2020
ms.locfileid: "96125303"
---
# <a name="iservervirtualdeviceset2signalabort-vdi"></a>IServerVirtualDeviceSet2::SignalAbort (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Функция **SignalAbort** предупреждает об аварийном завершении.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IServerVirtualDeviceSet2::SignalAbort ();
```

## <a name="return-value"></a>Возвращаемое значение

Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение NOERROR указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.

## <a name="remarks"></a>Remarks

Сервер может прервать операцию резервного копирования или восстановления в любое время.

Эта подпрограмма оповещает о необходимости прекращения всех операций. Весь интерфейс переходит в состоянии прерывания. Устройства не принимают никакие дополнительные команды. Агент завершения возвращает вызывающему объекту значение ERROR_OPERATION_ABORTED для каждого необработанного запроса. Любые завершения, записанные в клиенте, игнорируются.

Сервер гарантирует, что буферы или устройства, возвращенные через интерфейс виртуального устройства, больше не потребуются. Затем сервер выполняет очистку после аварийного завершения, включая вызов функции IServerVirtualDeviceSet2::Close.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).