---
title: Драйверы | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6460410488186c94713d859bf2912f2844ca2736
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915428"
---
# <a name="drivers"></a>Драйверы
*Драйверы* — это библиотеки, реализующие функции API ODBC. Каждый характерен для конкретной СУБД; Например, драйвер Oracle не может напрямую обращаться к данным в СУБД Informix. Драйверы предоставляют возможности базовых СУБД; они не являются обязательными для реализации возможностей, не поддерживаемых СУБД. Например, если базовая СУБД не поддерживает внешние объединения, то драйвер не должен указывать. Единственным основным исключением является то, что драйверы для СУБД, не имеющих изолированных ядер базы данных, например xbase, должны реализовать ядро СУБД, которое по крайней мере поддерживает минимальный объем SQL.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Задачи драйвера](../../odbc/reference/driver-tasks.md)  
  
-   [Архитектура драйвера](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>См. также:  
 [Драйверы ODBC, предоставляемые корпорацией Майкрософт](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
