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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915428"
---
# <a name="drivers"></a>Драйверы
*Драйверы* библиотеки, которые реализуют функции в API-Интерфейс ODBC. Каждый специфичен для конкретной СУБД; Например драйвер для Oracle не может напрямую обращаться к данных в СУБД с Informix. Драйверы доступ к функциям базовой СУБД; они не требуются для реализации возможностей, не поддерживаемых в СУБД. Например если базовой СУБД не поддерживает внешние соединения, то не следует драйвер. Единственным крупным исключением из этого является то, что драйверы для СУБД, у которых нет обработчиков автономную базу данных, таких как Xbase, должен реализовывать ядро СУБД, поддерживающий по крайней мере минимальный объем SQL.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Задачи драйвера](../../odbc/reference/driver-tasks.md)  
  
-   [Архитектура драйвера](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>См. также  
 [Драйверы ODBC, предоставляемые корпорацией Майкрософт](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
