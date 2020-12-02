---
title: IClientVirtualDeviceSet2::SignalAbort
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IClientVirtualDeviceSet2::SignalAbort.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: cawrites
ms.author: chadam
ms.openlocfilehash: d36a08586a6903a6e85bb4bad4d6344a54938cd2
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2020
ms.locfileid: "96125384"
---
# <a name="iclientvirtualdeviceset2signalabort-vdi"></a>IClientVirtualDeviceSet2::SignalAbort (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Функция **SignalAbort** используется для предупреждения об аварийном завершении.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IClientVirtualDeviceSet2::SignalAbort ();
```

## <a name="return-value"></a>Возвращаемое значение

Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение NOERROR указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.

## <a name="remarks"></a>Remarks

Клиент может прервать операцию резервного копирования или восстановления в любое время. Эта подпрограмма оповещает о необходимости прекращения всех операций. Весь набор виртуальных устройств переходит в состояние прерывания. На устройства не возвращаются никакие дополнительные команды. Все незавершенные команды завершаются автоматически, возвращая ERROR_OPERATION_ABORTED в качестве кода завершения. После безопасного завершения всех необработанных операций использования буферов клиент должен вызвать IClientVirtualDeviceSet2::Close. Дополнительные сведения см. в разделе "Аварийное завершение".

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).