---
title: IClientVirtualDeviceSet2::MapBufferHandle
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IClientVirtualDeviceSet2::MapBufferHandle.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5d181d1b6ddfea034716ebb048768cd7d43fbc61
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847585"
---
# <a name="iclientvirtualdeviceset2mapbufferhandle-vdi"></a>IClientVirtualDeviceSet2::MapBufferHandle (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Функция **MapBufferHandle** используется для получения допустимого адреса буфера из дескриптора буфера, полученного из другого процесса.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IClientVirtualDeviceSet2::MapBufferHandle (
   DWORD      dwBuffer,
   BYTE**      ppBuffer
);
```

## <a name="parameters"></a>Параметры

*dwBuffer* — это дескриптор, возвращаемый функцией IClientVirtualDeviceSet2::GetBufferHandle.

*ppBuffer* — это адрес буфера, допустимый в текущем процессе.

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| NOERROR | Функция выполнена успешно. |
| VD_E_PROTOCOL | Набор виртуальных устройств в настоящее время не открыт. |
| VD_E_INVALID | ppBuffer является недопустимым дескриптором. |

## <a name="remarks"></a>Remarks

Необходимо правильно передавать данные о дескрипторах. Дескрипторы являются локальными по отношению к одному набору виртуальных устройств. Партнерские процессы с общим дескриптором должны гарантировать использование дескрипторов буферов только в пределах набора виртуальных устройств, из которого буфер был получен изначально.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).