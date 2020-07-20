---
title: Параметр конфигурации "allow polybase export" | Документация Майкрософт
description: Установка параметра конфигурации `allow polybase export` в параметрах сервера SQL Server
ms.custom: ''
ms.date: 07/10/2020
ms.prod: sql
ms.prod_service: ''
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c25a7e42b55561ed6337281497e847999d722292
ms.sourcegitcommit: dacd9b6f90e6772a778a3235fb69412662572d02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2020
ms.locfileid: "86279657"
---
# <a name="set-allow-polybase-export-configuration-option"></a>Установка параметра конфигурации `allow polybase export`

[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

Параметр конфигурации сервера `allow polybase export` позволяет выполнить операцию `INSERT` во внешней таблице Hadoop. 

Эта функция не поддерживает вставку в другие внешние источники данных.

 Возможные значения описаны в следующей таблице: 

| Значение | Значение                                |
|-------|----------------------------------------|
| 0     | Отключено. Это параметр по умолчанию. |
| 1     | Активировано                                |


Изменение параметров вступает в силу немедленно.

## <a name="example"></a>Пример

Этот параметр включается в следующем примере.

```sql
sp_configure 'show advanced options', 1;
GO
RECONFIGURE;
GO
sp_configure 'allow polybase export', 0;
GO
RECONFIGURE;
GO
```

## <a name="next-steps"></a>Дальнейшие действия

 [Экспорт данных](../../relational-databases/polybase/polybase-configure-hadoop.md#exporting-data)