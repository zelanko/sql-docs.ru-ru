---
title: Типы данных SQL Server в .NET Framework | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- System.Data library
- System.Data.SqlTypes namespace
- data types [CLR integration]
- SqlTypes library
- database objects [CLR integration], data types
- common language runtime [SQL Server], data types
- building database objects [CLR integration], data types
- mapping data types [CLR integration]
ms.assetid: c70d3ffe-2c32-45a5-849b-ef113dda09b9
caps.latest.revision: 38
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 09dff25c6f125c70a6304823ec98f80dfd744632
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193134"
---
# <a name="sql-server-data-types-in-the-net-framework"></a>Типы данных SQL Server в платформе .NET Framework
  Библиотека `SqlTypes` представляет собой часть библиотеки базового класса платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. Она предоставляет типы данных с той же семантикой и той же точностью, как те, что доступны в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Данный раздел предоставляет сведения о новой семантике для программистов, работающих на платформе .NET Framework, и описывает типы, реализованные в пространстве имен `System.Data.SqlTypes`, включенном в библиотеку `System.Data`.  
  
 В следующей таблице перечислены подразделы этого раздела.  
  
 [Допустимость значений NULL и трехзначная логика сравнения](nullability-and-three-value-logic-comparisons.md)  
 Описывает работу со значениями NULL в различных типах данных при интеграции со средой CLR.  
  
 [Параметры сортировки и типы данных интеграции со средой CLR](collation-and-clr-integration-data-types.md)  
 Описывает обработку параметров сортировки при интеграции со средой CLR.  
  
 [Обработка больших объектов &#40;LOB&#41; параметров в среде CLR](handling-large-object-lob-parameters-in-the-clr.md)  
 Описывает передачу типов LOB между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и средой CLR.  
  
 [Сопоставление данных о параметрах CLR](mapping-clr-parameter-data.md)  
 Описывает сопоставления типов данных между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], интеграцией со средой CLR и платформой .NET Framework.  
  
  