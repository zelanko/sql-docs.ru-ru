---
title: Значение списка аргументов | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: a971da68a8f2a35df8fa513e68d1eba127e9c430
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208555"
---
# <a name="value-list-arguments"></a>Аргументы списка значений
Значение аргумента список состоит из списка значений с разделителями запятыми для сопоставления. Имеется только одно значение списка аргументов в функциях каталога ODBC: *TableType* аргумента в **SQLTables**. Установка *TableType* на указатель null одинаков как, если он становится равным SQL_ALL_TABLE_TYPES, который перечисляет все возможные члены списка значений. Этот аргумент не подвержены SQL_ATTR_METADATA_ID атрибут инструкции. Дополнительные сведения см. в разделе [SQLTables](../../../odbc/reference/syntax/sqltables-function.md) описание функции.
