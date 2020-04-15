---
title: Драйверы Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c8b40641be3db34fc6929edecdd5dd923700957
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294187"
---
# <a name="drivers"></a>Драйверы
*Драйверы* являются библиотеками, которые реализуют функции в API ODBC. Каждый из них специфичен для конкретного DBMS; например, драйвер Oracle не может напрямую получить доступ к данным в Informix DBMS. Драйверы разоблачают возможности базовых DBMS; они не обязаны реализовывать возможности, не поддерживаемые DBMS. Например, если базовый DBMS не поддерживает внешние соединения, то и водитель не должен. Единственным важным исключением является то, что драйверы dBMS, не имеющие автономных систем баз данных, таких как Xbase, должны внедрить движок базы данных, который, по крайней мере, поддерживает минимальное количество S'L.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Задачи драйвера](../../odbc/reference/driver-tasks.md)  
  
-   [Архитектура драйвера](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>См. также:  
 [Драйверы ODBC, предоставляемые корпорацией Майкрософт](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
