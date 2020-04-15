---
title: Аргументы списка значений (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fd655bd745c3bb06923e047d4134b286cf64703e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306745"
---
# <a name="value-list-arguments"></a>Аргументы списка значений
Аргумент списка значений состоит из списка значений, разделенных значениями, которые будут использоваться для сопоставления. В функциях каталога ODBC есть только один аргумент списка значений: аргумент *TableType* в **S'LTables**. Установка *TableType* на нулевой указатель такая же, как если бы он установлен на SQL_ALL_TABLE_TYPES, который перечисляет все возможные члены списка значений. Этот аргумент не зависит от атрибута SQL_ATTR_METADATA_ID оператора. Для получения дополнительной информации ознакомьтесь с описанием функции [S'LTables.](../../../odbc/reference/syntax/sqltables-function.md)
