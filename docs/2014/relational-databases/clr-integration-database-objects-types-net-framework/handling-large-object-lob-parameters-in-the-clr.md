---
title: Обработка параметров больших объектов (LOB) в среде CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
caps.latest.revision: 20
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f23f42a01ba5268c9165a79f5330fb0efcc538ce
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37353236"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>Обработка параметров больших объектов в среде CLR
  Используйте `SqlBytes` и `SqlChars` для передачи параметров больших объектов (LOB) двоичного типа (`varbinary(max)`) и символьного типа (`nvarchar(max)`) соответственно. Эти типы позволяют передавать значения LOB в потоке из базы данных в процедуры среды CLR, не копируя все значение в управляемое пространство. Типы данных `SqlBinary` и `SqlString` должны использоваться только для небольших двоичных и строковых значений.  
  
## <a name="see-also"></a>См. также  
 [Типы данных SQL Server в платформе .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
