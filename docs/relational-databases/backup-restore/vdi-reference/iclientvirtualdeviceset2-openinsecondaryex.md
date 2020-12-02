---
title: IClientVirtualDeviceSet2::OpenInSecondaryEx
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IClientVirtualDeviceSet2::OpenInSecondaryEx.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: cawrites
ms.author: chadam
ms.openlocfilehash: a5b2a680e34d6aa6c174cc356a2cb99bee75131f
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2020
ms.locfileid: "96128957"
---
# <a name="iclientvirtualdeviceset2openinsecondaryex-vdi"></a>IClientVirtualDeviceSet2::OpenInSecondaryEx (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Функция **OpenInSecondaryEx** открывает набор виртуальных устройств в дополнительном клиенте. Основной клиент уже должен был использовать функции CreateEx и GetConfiguration для настройки набора виртуальных устройств.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IClientVirtualDeviceSet2::OpenInSecondaryEx (
   LPCWSTR      lpInstanceName,
   LPCWSTR      lpSetName
);
```

## <a name="parameters"></a>Параметры

*lpInstanceName* — эта строка определяет экземпляр SQL Server, в который будет отправлена команда SQL.

*lpSetName* — определяет набор. В этом имени учитывается регистр, и оно должно совпадать с именем, используемым основным клиентом при вызове функции IClientVirtualDeviceSet2::Create.

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| NOERROR | Функция выполнена успешно. |
| VD_E_PROTOCOL | Набор виртуальных устройств уже открыт или не готов принимать открытые запросы от дополнительных клиентов. |
| VD_E_ABORT | Операция прерывается. |

## <a name="remarks"></a>Remarks

При использовании модели с несколькими процессами основной клиент несет ответственность за обнаружение нормального и аномального завершения работы дополнительных клиентов.

Имя экземпляра должно указывать на экземпляр, к которому выполняется запрос T-SQL. Значение NULL означает экземпляр по умолчанию. Префикс "machineName\" не допускается.

OpenInSecondaryEx заменяет функцию IClientVirtualDeviceSet::OpenInSecondary, которая была определена в исходном интерфейсе SQL Server версии 7.0. При разработке новых приложений следует использовать функцию OpenInSecondaryEx.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).