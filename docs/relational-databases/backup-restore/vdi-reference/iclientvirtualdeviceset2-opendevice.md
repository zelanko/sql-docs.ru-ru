---
title: IClientVirtualDeviceSet2::OpenDevice
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IClientVirtualDeviceSet2::OpenDevice.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f28a7547d16a03e5be963b3cfeb837e7ab78c007
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896869"
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