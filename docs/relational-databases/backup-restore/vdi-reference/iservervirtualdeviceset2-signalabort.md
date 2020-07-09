---
title: IServerVirtualDeviceSet2::SignalAbort
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IServerVirtualDeviceSet2::SignalAbort.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee70ef059e80d9c8a31281ce50f451e7787f637a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85895946"
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