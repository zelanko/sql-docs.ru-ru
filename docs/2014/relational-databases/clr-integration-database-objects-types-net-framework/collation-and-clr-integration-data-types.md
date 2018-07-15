---
title: Параметры сортировки и типы данных интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
caps.latest.revision: 38
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 56206f6273b413a66a72b2a2c72ed3593b2f9a66
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37354686"
---
# <a name="collation-and-clr-integration-data-types"></a>Параметры сортировки и типы данных интеграции со средой CLR
  В [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] объект `CompareInfo` обрабатывает параметры сортировки. Строковые API-интерфейсы платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] используют свойство `CompareInfo`, связанное с объектом `CultureInfo` текущего потока, для сравнения строк. Значение по умолчанию `CultureInfo` основана на [!INCLUDE[msCoName](../../includes/msconame-md.md)] языковой стандарт Windows для компьютера, на котором [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запущена. Она определяет семантику сравнения по умолчанию для сравнения значений типа `CultureInfo`, если свойство `System.String` не задано явно. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не изменяет явно свойство `CompareInfo` на параметры сортировки базы данных или сервера. При необходимости пользователи должны самостоятельно устанавливать свойство `CompareInfo` в своих программах.  
  
## <a name="parameter-collation"></a>Параметр с параметрами сортировки  
 При создании программы CLR, если параметр метода CLR, связанного с программой, имеет тип `SQLString`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает экземпляр параметра с параметрами сортировки по умолчанию базы данных, содержащей вызывающую программу. Если параметр имеет тип, отличный от `SqlType` (например, `String`, а не `SQLString`), сведения о параметрах сортировки из базы данных с этим параметром не связываются.  
  
## <a name="see-also"></a>См. также  
 [Типы данных SQL Server в платформе .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
