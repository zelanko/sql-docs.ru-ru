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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c8b40641be3db34fc6929edecdd5dd923700957
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81294187"
---
# <a name="drivers"></a>Драйверы
*Драйверы* — это библиотеки, реализующие функции API ODBC. Каждый характерен для конкретной СУБД; Например, драйвер Oracle не может напрямую обращаться к данным в СУБД Informix. Драйверы предоставляют возможности базовых СУБД; они не являются обязательными для реализации возможностей, не поддерживаемых СУБД. Например, если базовая СУБД не поддерживает внешние объединения, то драйвер не должен указывать. Единственным основным исключением является то, что драйверы для СУБД, не имеющих изолированных ядер базы данных, например xbase, должны реализовать ядро СУБД, которое по крайней мере поддерживает минимальный объем SQL.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Задачи драйвера](../../odbc/reference/driver-tasks.md)  
  
-   [Архитектура драйвера](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>См. также:  
 [Драйверы ODBC, предоставляемые корпорацией Майкрософт](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
