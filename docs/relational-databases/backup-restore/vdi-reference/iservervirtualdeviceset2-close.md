---
title: IServerVirtualDeviceSet2::Close
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IServerVirtualDeviceSet2::Close.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d2b0a5d12f256236a0d79c372c44e9b7d0cd2fb3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892034"
---
# <a name="iservervirtualdeviceset2close-vdi"></a>IServerVirtualDeviceSet2::Close (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Функция **Close** закрывает набор виртуальных устройств, открытый с помощью функции IServerVirtualDeviceSet2::Open. В результате высвобождаются все ресурсы, связанные с виртуальным устройством. Дескриптор IServerVirtualDeviceSet2 бесполезен после возврата управления этой функцией, и его следует вернуть модели COM.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IServerVirtualDeviceSet2::Close ();
```

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| VD_E_PROTOCOL | Устройства по-прежнему открыты. |

## <a name="remarks"></a>Remarks

Набор виртуальных устройств не следует закрывать до закрытия устройств. В такой ситуации возвращается значение VD_E_PROTOCOL. Это действие приводит к немедленному высвобождению сопоставления общей памяти функцией Close. На сервере могут возникать нарушения прав доступа, если он предполагает, что по-прежнему является владельцем ресурсов, которые возвращаются через интерфейс виртуального устройства. Интерфейс выполняет обработку SignalAbort.

Агент завершения, если он выполняется, завершает все невыполненные команды перед возвратом управления вызывающему объекту. Все незавершенные команды завершаются с ошибкой ERROR_OPERATION_ABORTED. Это значит, что для каждой такой команды вызывается функция обратного вызова.

Во всех случаях, в том числе при возвращении ошибок, функция Close освобождает все ресурсы для интерфейса виртуального устройства. Все буферы и другие указатели интерфейса, возвращенные из VDI, становятся недействительными.

Работа агента завершения должна быть завершена до выгрузки библиотеки COM. Если библиотека выгружается до того, как агент завершения возвращается вызывающему объекту, в процессе может произойти нарушение выполнения инструкций.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).