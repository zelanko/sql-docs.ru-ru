---
title: IServerVirtualDevice::SendCommand
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IServerVirtualDevice::SendCommand.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c75cd206557547f55d47eec0a7aec52cc0069b71
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847515"
---
# <a name="iservervirtualdevicesendcommand-vdi"></a>IServerVirtualDevice::SendCommand (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Функция **SendCommand** отправляет клиенту команду с помощью объекта виртуального устройства, возвращенного функцией IServerVirtualDeviceSet2::OpenDevice.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IServerVirtualDevice::SendCommand (
   VDS_Command*   pCmd
);
```

## <a name="parameters"></a>Параметры

*pCmd* — указатель на блок запроса команды. Дополнительные сведения см. в разделе "Команды". Поле completionFunction должно указывать на адрес функции со следующей сигнатурой:

```c
void callbackFunction ( VDS_Command *pCmd);
```

Этот обратный вызов выполняется агентом завершения, когда клиент сообщает о завершении команды. SQL Server задает поле completionContext параметра pCmd. Оно служит для предоставления контекста функции обратного вызова.

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| NOERROR | Команда успешно добавлена в очередь клиента. |
| VD_E_QUEUE_FULL | Очередь устройства заполнена. |
| VD_E_IO_ERROR | Устройство находится в состоянии IO-ERROR. |
| VD_E_PROTOCOL | Устройство не активно. |

## <a name="remarks"></a>Remarks

Если при попытке отправить команду происходит ошибка, вызывается функция обратного вызова и поле completionCode в буфере команд задается следующим образом:

| completionCode | Ошибка |
|---|---|
| VD_E_QUEUE_FULL | ERROR_NO_SYSTEM_RESOURCES |
| VD_E_IO_ERROR   | ERROR_IO_DEVICE |
| VD_E_PROTOCOL   | ERROR_INVALID_HANDLE |
| VD_E_ABORT      | ERROR_OPERATION_ABORTED |

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).