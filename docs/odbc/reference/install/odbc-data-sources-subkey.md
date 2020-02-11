---
title: Подраздел источников данных ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 09/23/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4d6d54d1fc7c7742bf94e91d7370f356e28b5624
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "71207690"
---
# <a name="odbc-data-sources-subkey"></a>Подраздел источников данных ODBC

В `ODBC Data Sources` подразделе перечислены значения источников данных. Формат этих значений приведен в следующей таблице.

| Имя | Тип данных | Данные |
| :--- | :-------- | :--- |
| *имя источника данных* | REG_SZ | *Описание драйвера* |
| &nbsp; | &nbsp; | &nbsp; |

Значение *Data-Source-Name* определяется программой администрирования (которая обычно запрашивает у пользователя), а *Описание драйвера* определяется разработчиком драйвера (обычно это имя СУБД, связанной с драйвером).

Например, предположим, что определены три источника данных: Inventory, в которой используется SQL Server; Заработная плата, использующая dBASE; и персонал, использующий форматированные текстовые файлы. Значения в `ODBC Data Sources` подразделе могут выглядеть следующим образом:

```console
Inventory : REG_SZ : SQL Server
Payroll : REG_SZ : dBASE
Personnel : REG_SZ : Text
```
