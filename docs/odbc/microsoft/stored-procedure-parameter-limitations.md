---
title: Хранимые процедуры ограничения параметров | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8b804bcf-4cce-4e6f-aa45-00bab9ef9921
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ecaf64ac29804034e47588e1686981f91a3fd16a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="stored-procedure-parameter-limitations"></a>Ограничения параметров хранимой процедуры
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 При под управлением Oracle хранимых процедур, использующих 10 или более выходных параметров, вызов хранимой процедуры завершится ошибкой, что приводит к ошибке нарушения прав доступа или объекты данных ActiveX (ADO). Это может произойти при использовании драйвера Microsoft ODBC для Oracle с версиями 8.0.4.0.0 и 8.0.4.0.4 клиентского программного обеспечения Oracle.  
  
 Чтобы устранить проблему, клиентское программное обеспечение Oracle должно находиться обновленные до версии 8.0.4.2.0 или выше. Обратитесь в службу корпорацией Oracle Дополнительные сведения о [исправлений](../../odbc/microsoft/oracle-software-patches.md).  
  
> [!NOTE]  
>  Эта проблема возникает с предыдущего выпуска Oracle версии клиентского программного обеспечения 8.0.3.0.0.
