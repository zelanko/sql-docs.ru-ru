---
title: IClientVirtualDeviceSet2::CreateEx
titlesuffix: SQL Server VDI reference
description: В этой статье приводятся справочные сведения о команде IClientVirtualDeviceSet2::CreateEx.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: cawrites
ms.author: chadam
ms.openlocfilehash: 180ad0ca42904a6a9c4820db1cb5fab36157e972
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2020
ms.locfileid: "96125426"
---
# <a name="iclientvirtualdeviceset2createex-vdi"></a>IClientVirtualDeviceSet2::CreateEx (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Функция **CreateEx** создает набор виртуальных устройств.

## <a name="syntax"></a>Синтаксис

```c
HRESULT IClientVirtualDeviceSet2::CreateEx (
   LPCWSTR         lpInstanceName,
   LPCWSTR         lpName,
   VDConfig*      pCfg
);
```

## <a name="parameters"></a>Параметры

*lpInstanceName* — эта строка определяет экземпляр SQL Server, в который будет отправлена команда SQL.

*lpName* — определяет набор виртуальных устройств. Необходимо следовать правилам для имен, используемых в CreateFileMapping(). Можно использовать любой символ, кроме обратной косой черты (\)). Это строка расширенных символов Юникода. К строке рекомендуется добавить префикс в виде названия продукта или компании пользователя и имени базы данных.

*pCfg* — это конфигурация для набора виртуальных устройств. Дополнительные сведения см. в разделе "Конфигурация".

## <a name="return-value"></a>Возвращаемое значение

|Возвращаемое значение | Объяснение |
|---|---|
| NOERROR | Функция выполнена успешно. |
| VD_E_NOTSUPPORTED | Одно или несколько полей в конфигурации недопустимы или не поддерживаются. |
| VD_E_PROTOCOL | Набор виртуальных устройств создан. |

## <a name="remarks"></a>Remarks

Метод CreateEx следует вызывать только один раз для каждой операции резервного копирования или восстановления. После вызова метода Close клиент может повторно использовать интерфейс для создания другого набора виртуальных устройств.

Имя экземпляра должно указывать на экземпляр, к которому выполняется запрос Transact-SQL. Значение NULL означает экземпляр по умолчанию. Префикс "machineName\" не допускается.

Вызовы метода CreateEx (и Create) изменяют список DACL для дескриптора клиентского процесса. По этой причине любые другие изменения дескриптора процесса должны быть сериализованы с вызовом CreateEx. Метод CreateEx сериализуется с другими вызовами CreateEx, но не может сериализоваться с внешней обработкой. Доступ предоставляется учетной записи, с которой запущена служба SQL Server.

Метод CreateEx заменяет метод Create, определенный в исходном интерфейсе IClientVirtualDeviceSet. Исходный метод Create является устаревшим, и его не следует использовать в будущем. Исходный метод Create реализует поддержку имен экземпляров с помощью переменной среды _VIRTUAL_SERVER_NAME_. Если эта переменная задана в среде, то метод Create автоматически вызывает метод CreateEx, передавая значение переменной _VIRTUAL_SERVER_NAME_ в качестве имени экземпляра.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения см. в [справке по интерфейсу виртуальных устройств SQL Server](reference-virtual-device-interface.md).