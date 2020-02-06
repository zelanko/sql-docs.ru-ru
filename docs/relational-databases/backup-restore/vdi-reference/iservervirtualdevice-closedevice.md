---
title: IServerVirtualDevice::CloseDevice
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IServerVirtualDevice::CloseDevice.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c73649e2a4301e94f8e68504222cc0122061f25f
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "70847435"
---
# <a name="iservervirtualdeviceclosedevice-vdi"></a>IServerVirtualDevice::CloseDevice (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Функция **CloseDevice** закрывает виртуальное устройство, которое было открыто с помощью функции IServerVirtualDeviceSet2::OpenDevice.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IServerVirtualDevice::CloseDevice ();
```

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| VD_E_CLOSE | Устройство уже закрыто. |
| VD_E_ABORT | Интерфейс находится в состоянии прерывания. |

## <a name="remarks"></a>Remarks

Функция CloseDevice не требуется после использования SignalAbort для принудительного аварийного завершения. Если функция CloseDevice вызывается после использования SignalAbort, не выполняется никаких действий.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).