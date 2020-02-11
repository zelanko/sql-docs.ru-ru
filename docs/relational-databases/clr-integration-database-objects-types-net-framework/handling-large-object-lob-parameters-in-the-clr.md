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
ms.openlocfilehash: 64b890f7b4dd801a43c85f0375987c6ff5f5cd1f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081332"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>Обработка параметров больших объектов в среде CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Используйте **SqlBytes** и **SqlChars** для передачи двоичного типа больших объектов (LOB) (**varbinary (max)**) и типов символов LOB (**nvarchar (max)**) соответственно. Эти типы позволяют передавать значения LOB в потоке из базы данных в процедуры среды CLR, не копируя все значение в управляемое пространство. **SqlBinary** и **SqlString** должны использоваться только для небольших двоичных и символьных строковых значений.  
  
## <a name="see-also"></a>См. также:  
 [Типы данных SQL Server в платформе .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
