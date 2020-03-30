---
title: IServerVirtualDeviceSet2::GetConfiguration
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IServerVirtualDeviceSet2::GetConfiguration.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1d62a2042221bebf04e19a46a21ba81caa7c877b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "70847255"
---
# <a name="iservervirtualdeviceset2getconfiguration-vdi"></a>IServerVirtualDeviceSet2::GetConfiguration (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Функция **GetConfiguration** получает конфигурацию, запрашиваемую клиентом.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IServerVirtualDeviceSet2::GetConfiguration (
   VDConfig*   pCfg
);
```

## <a name="parameters"></a>Параметры

*pCfg* — конфигурация, указанная клиентом с помощью функции IClientVirtualDeviceSet2::Create.

## <a name="return-value"></a>Возвращаемое значение

Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение NOERROR указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.

## <a name="remarks"></a>Remarks

Предполагается, что сервер проверяет параметры, предоставленные клиентом, и реагирует на них. Дополнительные сведения см. в разделе "Конфигурация". Сервер может использовать SignalAbort, если определит, что не может правильно работать с предоставленной конфигурацией.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).