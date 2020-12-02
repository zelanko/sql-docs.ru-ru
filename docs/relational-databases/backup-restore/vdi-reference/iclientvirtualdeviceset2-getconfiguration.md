---
title: IClientVirtualDeviceSet2::GetConfiguration
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IClientVirtualDeviceSet2::GetConfiguration.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: cawrites
ms.author: chadam
ms.openlocfilehash: 5d46efb493dc67c38affc25f99871f3ff4617ecb
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2020
ms.locfileid: "96125397"
---
# <a name="iclientvirtualdeviceset2getconfiguration-vdi"></a>IClientVirtualDeviceSet2::GetConfiguration (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Функция **GetConfiguration** используется для ожидания настройки набора виртуальных устройств сервером.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IClientVirtualDeviceSet2::GetConfiguration (
   DWORD         dwTimeOut,
   VDConfig*      pCfg
);
```

## <a name="parameters"></a>Параметры

*DwTimeOut* — время ожидания в миллисекундах. Чтобы избежать времени ожидания, используйте значение INFINITE.

*pCfg* — после успешного выполнения содержит конфигурацию, выбранную сервером. Дополнительные сведения см. в разделе "Конфигурация".

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| NOERROR | Конфигурация возвращена. |
| VD_E_ABORT | Вызван SignalAbort. |
| VD_E_TIMEOUT | Время ожидания функции истекло. |

## <a name="remarks"></a>Remarks

Эта функция блокируется в состоянии ожидания оповещения. После успешного вызова можно открыть устройства в наборе виртуальных устройств.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).