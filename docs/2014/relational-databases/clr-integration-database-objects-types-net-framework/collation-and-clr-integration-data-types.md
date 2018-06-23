---
title: Параметры сортировки и типы данных интеграции со средой CLR | Документы Microsoft
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
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
caps.latest.revision: 38
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 71b0c61678bff1be69cbb761dd00067150a30b0d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192907"
---
# <a name="collation-and-clr-integration-data-types"></a>Параметры сортировки и типы данных интеграции со средой CLR
  В [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] объект `CompareInfo` обрабатывает параметры сортировки. Строковые API-интерфейсы платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] используют свойство `CompareInfo`, связанное с объектом `CultureInfo` текущего потока, для сравнения строк. Значение по умолчанию `CultureInfo` объект основан на [!INCLUDE[msCoName](../../includes/msconame-md.md)] языковой стандарт Windows для компьютера, на котором [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает. Она определяет семантику сравнения по умолчанию для сравнения значений типа `CultureInfo`, если свойство `System.String` не задано явно. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не изменяет явно свойство `CompareInfo` на параметры сортировки базы данных или сервера. При необходимости пользователи должны самостоятельно устанавливать свойство `CompareInfo` в своих программах.  
  
## <a name="parameter-collation"></a>Параметр с параметрами сортировки  
 При создании программы CLR, если параметр метода CLR, связанного с программой, имеет тип `SQLString`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает экземпляр параметра с параметрами сортировки по умолчанию базы данных, содержащей вызывающую программу. Если параметр имеет тип, отличный от `SqlType` (например, `String`, а не `SQLString`), сведения о параметрах сортировки из базы данных с этим параметром не связываются.  
  
## <a name="see-also"></a>См. также  
 [Типы данных SQL Server в платформе .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  