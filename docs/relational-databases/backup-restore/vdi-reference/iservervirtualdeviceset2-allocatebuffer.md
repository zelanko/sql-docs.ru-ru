---
title: IServerVirtualDeviceSet2::AllocateBuffer
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IServerVirtualDeviceSet2::AllocateBuffer.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: cawrites
ms.author: chadam
ms.openlocfilehash: d311b2253e9083c78207d1443782096b4c82a491
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2020
ms.locfileid: "96128939"
---
# <a name="iservervirtualdeviceset2allocatebuffer-vdi"></a>IServerVirtualDeviceSet2::AllocateBuffer (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Функция **AllocateBuffer** получает буфер общей памяти из набора виртуальных устройств.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IServerVirtualDeviceSet2::AllocateBuffer (
   LPVOID*      ppBuffer,
   UINT32      dwSize,
   UINT32      dwAlignment
);
```

## <a name="parameters"></a>Параметры

*ppBuffer* — возвращает указатель на начало буфера.

*dwSize* — размер буфера в байтах. Не включает в себя префиксную зону, запрошенную клиентом. Такие зоны скрываются от сервера, и до возвращения адреса буфера будет доступно место.

*dwAlignment* — определяет границу выравнивания для буфера. Например, при значении 4096 буфер будет выровнен по границе в 4096 байт. Это означает, что младшие 12 бит в возвращенном адресе будут установлены в нулевое значение. Значение этого параметра должно быть степенью двойки.

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| NOERROR | Буфер возвращается. |
| VD_E_MEMORY | Не хватает памяти. |
| VD_E_INVALID | Был указан недопустимый параметр. |

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).