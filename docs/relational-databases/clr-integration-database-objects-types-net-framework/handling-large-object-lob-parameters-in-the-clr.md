---
title: Обработка параметров больших объектов (LOB) в среде CLR | Документация Майкрософт
description: В этой статье описывается, как управлять значениями больших объектов (LOB) для параметров в SQL Server интеграции со средой CLR. Используйте SqlBytes и SqlChars для типов LOB.
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
ms.openlocfilehash: 0b10ac8c1ac9ccba804b892617df0b8d6c0d2f14
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85637490"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>Обработка параметров больших объектов в среде CLR
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Используйте **SqlBytes** и **SqlChars** для передачи двоичного типа больших объектов (LOB) (**varbinary (max)**) и типов символов LOB (**nvarchar (max)**) соответственно. Эти типы позволяют передавать значения LOB в потоке из базы данных в процедуры среды CLR, не копируя все значение в управляемое пространство. **SqlBinary** и **SqlString** должны использоваться только для небольших двоичных и символьных строковых значений.  
  
## <a name="see-also"></a>См. также  
 [Типы данных SQL Server в платформе .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
