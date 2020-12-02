---
title: IClientVirtualDeviceSet2::OpenDevice
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IClientVirtualDeviceSet2::OpenDevice.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: cawrites
ms.author: chadam
ms.openlocfilehash: 040dd8842e6c718c52a70dfd9bb7646a59cb9d47
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2020
ms.locfileid: "96125406"
---
# <a name="iclientvirtualdeviceset2opendevice-vdi"></a>IClientVirtualDeviceSet2::OpenDevice (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Функция **OpenDevice** открывает одно из устройств в наборе виртуальных устройств.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IClientVirtualDeviceSet2::OpenDevice (
   LPCWSTR                  lpName,
   IClientVirtualDevice**   ppVirtualDevice

);
```

## <a name="parameters"></a>Параметры

*lpName* — определяет виртуальное устройство.

*ppVirtualDevice* — после успешного выполнения функции возвращается указатель интерфейса на виртуальное устройство. Этот интерфейс используется для команд GetCommand и CompleteCommand.

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| NOERROR | Функция выполнена успешно. |
| VD_E_ABORT | Запрошено прерывание. |
| VD_E_OPEN |Все устройства открыты. |
| VD_E_PROTOCOL | Набор не находится в состоянии инициализации, либо это конкретное устройство уже открыто. |
| VD_E_INVALID | Недопустимое имя устройства. Это имя не используется в наборе. |

## <a name="remarks"></a>Remarks

VD_E_OPEN может возвращаться без проблем. Клиент может многократно вызывать OpenDevice, пока не будет возвращен этот код.
Если настроено несколько устройств (например, n), набор виртуальных устройств вернет n уникальных интерфейсов устройств. Имя первого устройства совпадает с именем набора виртуальных устройств. Имена других устройств задаются в соответствии с предложениями VIRTUAL_DEVICE инструкции BACKUP или RESTORE.

Функцию GetConfiguration можно использовать для ожидания открытия устройств.

Если эта функция завершается ошибкой, аргумент ppVirtualDevice возвращает значение NULL.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).