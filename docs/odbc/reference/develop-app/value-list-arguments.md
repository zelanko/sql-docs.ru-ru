---
title: Аргументы списка значений | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], value list
- value list arguments [ODBC]
ms.assetid: 863837be-603b-4c7a-8b96-b71014037ee5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 646d2724489140080a673f31e22429cc7ca39d4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68022116"
---
# <a name="value-list-arguments"></a>Аргументы списка значений
Аргумент списка значений состоит из списка значений с разделителями-запятыми, используемых для сопоставления. В функциях каталога ODBC имеется только один аргумент списка значений: аргумент *TableType* в **SQLTables**. Установка *TableType* в качестве пустого указателя выполняется так же, как если бы он был установлен в SQL_ALL_TABLE_TYPES, который перечисляет все возможные элементы списка значений. Атрибут инструкции SQL_ATTR_METADATA_ID не влияет на этот аргумент. Дополнительные сведения см. в описании функции [SQLTables](../../../odbc/reference/syntax/sqltables-function.md) .
