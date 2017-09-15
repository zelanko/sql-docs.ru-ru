---
title: "Значение аргумента списка | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], value list
- value list arguments [ODBC]
ms.assetid: 863837be-603b-4c7a-8b96-b71014037ee5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a8386d5ffbb4d492bc8489272596fb9f6d58d245
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="value-list-arguments"></a>Значение список аргументов
Значение аргумента списка состоит из списка разделенных запятыми значений, используемый для сопоставления. Имеется только одно значение список аргументов в функции каталога ODBC: *TableType* аргумент в **SQLTables**. Установка *TableType* на указатель null совпадает как если бы оно было равно SQL_ALL_TABLE_TYPES, в котором перечислены все возможные члены списка значений. Этот аргумент не затрагивается атрибут SQL_ATTR_METADATA_ID инструкции. Дополнительные сведения см. в разделе [SQLTables](../../../odbc/reference/syntax/sqltables-function.md) описание функции.
