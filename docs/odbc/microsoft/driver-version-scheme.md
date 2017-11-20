---
title: "Драйвер версии схемы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], versions
ms.assetid: e4a8d9d7-8aba-48ab-8be6-1a6129adfb8f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e3a8132d535b764818fb9dcab72b3cba8bb48154
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="driver-version-scheme"></a>Схема версии драйвера
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 В следующей таблице перечислены все выпущенные версии драйвера Microsoft ODBC для Oracle.  
  
|Версия драйвера|Номер сборки|Журнал доступности|  
|--------------------|------------------|--------------------------|  
|1.0|2.00.6235|Visual C++ 4.2 и Visual Basic 5.0, Enterprise Edition|  
|2.0|2.73.7269|Visual Studio 97 и MDAC 1 5a|  
|обновление 2.0|2.73.7283.01|IIS 4.0|  
|обновление 2.0|2.73.7283.03|Компоненты MDAC 1.5b и 1.5 c|  
|обновление 2.0|2.73.7356|ODBC 3.5 SDK|  
|2.5|2.573.2927|Visual Studio 6.0 и компоненты MDAC 2.0|  
|обновление версии 2.5|2.573.3513|SQL Server 7.0<br /><br /> SQL Server 6.5 SP5|  
  
 Построение 2.00.6235 (версия 1) был первый выпуск драйвера Microsoft ODBC для Oracle. После выпуска первой версии был принят новый соглашение об именовании.  
  
 Например 2.73.7283.03 можно разделить на следующие уникальные компоненты:  
  
-   2 = номер версии.  
  
-   73 = версия сервера Oracle, для которого предназначен этот драйвер.  
  
-   7283.03 = номер сборки драйвера.  
  
> [!NOTE]  
>  С помощью выпуска 2.573.2973, соглашение об именовании привело к путанице 2.573 является более ранней версии, чем 2,73, что каждый раздел номер сборки следует рассматривать отдельно. Номер 573 превышает 73, поэтому он является более новой версии. Кроме того «2.5» указывает номер версии драйвера.

