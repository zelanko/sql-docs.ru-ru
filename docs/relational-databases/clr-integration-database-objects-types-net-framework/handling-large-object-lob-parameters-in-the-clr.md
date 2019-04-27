---
title: Обработка параметров больших объектов (LOB) в среде CLR | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
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
manager: craigg
ms.openlocfilehash: 6079766625633391e281b99751ba42bb772531e3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62760460"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>Обработка параметров больших объектов в среде CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Используйте **SqlBytes** и **SqlChars** для передачи больших объектов (LOB) двоичного типа (**varbinary(max)**) и символьного типа (**nvarchar(max)**) параметры, соответственно. Эти типы позволяют передавать значения LOB в потоке из базы данных в процедуры среды CLR, не копируя все значение в управляемое пространство. **SqlBinary** и **SqlString** следует использовать только для небольших двоичных и строковых значений.  
  
## <a name="see-also"></a>См. также  
 [Типы данных SQL Server в платформе .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
