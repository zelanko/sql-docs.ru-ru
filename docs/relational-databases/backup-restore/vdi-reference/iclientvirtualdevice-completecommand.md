---
title: IClientVirtualDevice::CompleteCommand
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IClientVirtualDevice::CompleteCommand.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0fb96d94ae330fdf55d82625ed71217ba71e50ff
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "70847405"
---
# <a name="iclientvirtualdevicecompletecommand-vdi"></a>IClientVirtualDevice::CompleteCommand (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Функция **CompleteCommand** используется для уведомления SQL Server о завершении команды. Должны возвращаться сведения о завершении, соответствующие команде.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IClientVirtualDevice::CompleteCommand (
   VDC_Command*         const pCmd,
   UINT32               dwCompletionCode,
   UINT32               dwBytesTransferred,
   UINT64               dwlPosition
);
```

## <a name="parameters"></a>Параметры

*pCmd* — адрес команды, ранее возвращенной функцией IClientVirtualDevice::GetCommand.

*dwCompletionCode* — код состояния WIN32, указывающий состояние завершения. Этот параметр должен возвращаться для всех команд. Возвращаемый код должен соответствовать выполняемой команде. ERROR_SUCCESS используется во всех случаях для обозначения успешно выполненной команды. Полный список возможных кодов см. в файле Winerror.h. Список стандартных кодов состояния для каждой команды см. в разделе "Команды".

*dwBytesTransferred* — количество успешно переданных байт. Возвращается только для команд чтения и записи при передаче данных.

*dwlPosition* — это ответ только на команду GetPosition.

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| NOERROR | Завершение отмечено правильно. |
| VD_E_INVALID | pCmd не была активной командой. |
| VD_E_ABORT | Получена команда о прерывании. |
| VD_E_PROTOCOL | Устройство не открыто. |

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).
