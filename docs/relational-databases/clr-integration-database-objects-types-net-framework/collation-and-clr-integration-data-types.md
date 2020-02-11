---
title: Параметры сортировки и типы данных интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
author: rothja
ms.author: jroth
ms.openlocfilehash: 51345c498277cc7013bbc05784022f65d77aef65
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081338"
---
# <a name="collation-and-clr-integration-data-types"></a>Параметры сортировки и типы данных интеграции со средой CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]объект **CompareInfo** обрабатывает параметры сортировки. Строковые API-интерфейсы платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] используют свойство **CompareInfo** , связанное с объектом **CultureInfo** текущего потока, для сравнения строк. Настройка по умолчанию свойства **CultureInfo** основана на параметрах локали [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows для компьютера, на котором выполняется [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Она определяет семантику сравнения по умолчанию для сравнения значений типа **CultureInfo** , если свойство **System.String** не задано явно. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]не изменяет явно свойство **CompareInfo** на параметры сортировки базы данных или сервера. При необходимости пользователи должны самостоятельно устанавливать свойство **CompareInfo** в своих программах.  
  
## <a name="parameter-collation"></a>Параметр с параметрами сортировки  
 При создании подпрограммы среды CLR и параметра метода CLR, привязанного к подпрограммы типа **SqlString**, создает экземпляр параметра с параметрами сортировки по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, содержащей вызывающую подпрограммы. Если параметр имеет тип, отличный от **SqlType** (например, **String** , а не **SQLString**), сведения о параметрах сортировки из базы данных с этим параметром не связываются.  
  
## <a name="see-also"></a>См. также:  
 [Типы данных SQL Server в платформе .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
