---
title: Значение аргумента списка | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], value list
- value list arguments [ODBC]
ms.assetid: 863837be-603b-4c7a-8b96-b71014037ee5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14c78f543f959e091e52db6881d49e4221667273
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="value-list-arguments"></a>Значение список аргументов
Значение аргумента списка состоит из списка разделенных запятыми значений, используемый для сопоставления. Имеется только одно значение список аргументов в функции каталога ODBC: *TableType* аргумент в **SQLTables**. Установка *TableType* на указатель null совпадает как если бы оно было равно SQL_ALL_TABLE_TYPES, в котором перечислены все возможные члены списка значений. Этот аргумент не затрагивается атрибут SQL_ATTR_METADATA_ID инструкции. Дополнительные сведения см. в разделе [SQLTables](../../../odbc/reference/syntax/sqltables-function.md) описание функции.
