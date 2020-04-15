---
title: Подключка источников данных ODBC (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c5e97e643a78187b15e91833c832cd16ca435c7f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304064"
---
# <a name="odbc-data-sources-subkey"></a>Подключка odBC Data Sources

Значения подключки `ODBC Data Sources` перечисляют источники данных. Формат этих значений отображается в следующей таблице.

| Имя | Тип данных | Данные |
| :--- | :-------- | :--- |
| *имя источника данных* | REG_SZ | *водитель-описание* |
| &nbsp; | &nbsp; | &nbsp; |

Значение *имени источника данных* определяется программой администрирования (которая обычно подсказывает пользователю), а описание *драйвера* определяется разработчиком драйвера (обычно это имя DBMS, связанное с драйвером).

Например, предположим, что определены три источника данных: Инвентарь, в котором используется сервер S'L; Платежная ведомость, в которой используется dBASE; и персонал, который использует отформатированные текстовые файлы. Значения под ключом `ODBC Data Sources` могут быть следующими:

```console
Inventory : REG_SZ : SQL Server
Payroll : REG_SZ : dBASE
Personnel : REG_SZ : Text
```
