---
title: Ограничения типа данных Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], data types
- data types [ODBC], desktop database drivers
- desktop database drivers [ODBC], data types
ms.assetid: 81c4eab7-1f6b-47a0-b940-89d6c6a14dae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4beaf91a4ead743e3e8a2e32578796baba3c17be
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280674"
---
# <a name="data-type-limitations"></a>Ограничения типов данных
Драйверы настольной базы данных Microsoft ODBC накладывают следующие ограничения на типы данных:  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|Все типы данных|Сбои преобразования типа могут привести к тому, что пострадавший столбец будет установлен в NULL.|  
|BINARY|Создание столбца BINARY нулевой длины фактически возвращает 255-байтBINARY столбец.|  
|DATE|Тип данных DATE не может быть преобразован в другой тип данных (или сам по себе) функцией CONVERT.|  
|DECIMAL (Точный число)|Не поддерживается.|  
|Типы данных из плавающей точки|Количество десятичных мест в номере плавающей точки может быть ограничено форматом числа, установленным в международной части панели управления Windows.|  
|NUMERIC|Поддерживает максимальную точность и шкалу 28.|  
|timestamp|Тип данных TIMESTAMP не может быть преобразован в себя функцией CONVERT.|  
|TINYINT|Значения TINYINT всегда не подписаны.|  
|Струны нулевой длины|При использовании dBASE, Microsoft Excel, Paradox или Textdriver вставляет строку нулевой длины в столбец.|
