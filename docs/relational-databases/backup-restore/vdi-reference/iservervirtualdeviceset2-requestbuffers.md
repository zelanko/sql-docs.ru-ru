---
title: IServerVirtualDeviceSet2::RequestBuffers
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IServerVirtualDeviceSet2::RequestBuffers.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1b941f251c9093f10abbced8c3522f1719a1580e
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70847185"
---
# <a name="iservervirtualdeviceset2requestbuffers-vdi"></a>IServerVirtualDeviceSet2::RequestBuffers (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Функция **RequestBuffers** сообщает VDI о том, что серверу потребуется определенное количество буферов с заданными размерами и требованиями к выравниванию.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IServerVirtualDeviceSet2::RequestBuffers (
   DWORD   dwSize,
   DWORD   dwAlignment,
   DWORD   dwCount
);
```

## <a name="parameters"></a>Параметры

*dwSize* — определяет размер каждого буфера. Этот размер должен включать в себя только область, необходимую для данных. VDI отвечает за обеспечение требований к выравниванию и префиксам.

*dwAlignment* — выравнивание, требуемое для буферов. Можно использовать более строгое значение выравнивания, чем базовое значение, указанное с помощью BeginConfiguration. Если указано значение 0, по умолчанию используется базовое значение выравнивания.

*dwCount* — количество буферов, которые будут запрошены функцией AllocateBuffer с указанным размером и выравниванием.

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| NOERROR | Функция выполнена успешно. |
| VD_E_ABORT | Запрошено прерывание. |
| VD_E_PROTOCOL | Набор находится не в том состоянии, в котором можно объявлять выделения буфера (см. матрицу переходов состояния). |
| VD_E_MEMORY | Не удалось получить запрошенную память. |

## <a name="remarks"></a>Remarks

Этот метод следует использовать перед выделением буферов с помощью AllocateBuffer. Сначала с помощью RequestBuffers запрашиваются наборы буферов с заданным размером и выравниванием, а затем отдельные буферы выделяются с помощью AllocateBuffer.

На этапе настройки вызовы RequestBuffers "суммируются", чтобы при вызове EndConfiguration можно было использовать одну буферную область (она выделяется во время этого вызова). После завершения настройки все вызовы RequestBuffers приводят к немедленному выделению дополнительного места в буфере.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).