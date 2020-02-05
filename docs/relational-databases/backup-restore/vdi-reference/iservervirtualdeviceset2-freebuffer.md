---
title: IServerVirtualDeviceSet2::FreeBuffer
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IServerVirtualDeviceSet2::FreeBuffer.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2829f849ce8cd220fdabc75a0d2059c5da0c80fd
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "70847265"
---
# <a name="iservervirtualdeviceset2freebuffer-vdi"></a>IServerVirtualDeviceSet2::FreeBuffer (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Функция **FreeBuffer** получает буфер общей памяти из набора виртуальных устройств.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IServerVirtualDeviceSet2::FreeBuffer (
   LPVOID   pBuffer,
   UINT32   dwSize
);
```

## <a name="parameters"></a>Параметры

*pBuffer* — возвращает буфер, полученный с помощью IServerVirtualDeviceSet2::AllocateBuffer.

*dwSize* — размер буфера в байтах. Не включает в себя префиксную зону, запрошенную клиентом. Такие зоны скрываются от сервера, и до возвращения адреса буфера будет доступно место.

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| NOERROR | Буфер возвращается. |
| VD_E_INVALID | Был указан недопустимый параметр. |

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).