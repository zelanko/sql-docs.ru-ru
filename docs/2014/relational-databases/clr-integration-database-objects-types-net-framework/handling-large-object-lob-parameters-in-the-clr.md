---
title: Обработка параметров больших объектов (LOB) в среде CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
author: rothja
ms.author: jroth
ms.openlocfilehash: ee791c73a6610761c2086723f9e41c2351b37dd0
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84954754"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>Обработка параметров больших объектов в среде CLR
  Используйте `SqlBytes` и `SqlChars` для передачи параметров больших объектов (LOB) двоичного типа (`varbinary(max)`) и символьного типа (`nvarchar(max)`) соответственно. Эти типы позволяют передавать значения LOB в потоке из базы данных в процедуры среды CLR, не копируя все значение в управляемое пространство. Типы данных `SqlBinary` и `SqlString` должны использоваться только для небольших двоичных и строковых значений.  
  
## <a name="see-also"></a>См. также:  
 [Типы данных SQL Server в платформе .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
