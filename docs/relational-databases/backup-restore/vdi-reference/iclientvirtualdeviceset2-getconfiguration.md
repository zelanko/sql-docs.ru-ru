---
title: IClientVirtualDeviceSet2::GetConfiguration
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IClientVirtualDeviceSet2::GetConfiguration.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5d7d42d081b0494feeb5c2b221575e0d5df1143a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "70847455"
---
# <a name="iclientvirtualdeviceset2getconfiguration-vdi"></a>IClientVirtualDeviceSet2::GetConfiguration (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

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