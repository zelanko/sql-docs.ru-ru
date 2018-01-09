---
title: "Допустимость значений NULL и трехзначная логика сравнения | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- precision [CLR integration]
- overflow detections [CLR integration]
- null values [CLR integration]
- three-value logic comparisons [CLR integration]
- data types [CLR integration]
- SqlBoolean data type
ms.assetid: 13da4c7f-1010-4b2d-a63c-c69b6bfd96f1
caps.latest.revision: "38"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1ca7947c1b07478c43be0e0eaeb3f41d8ae2686d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="nullability-and-three-value-logic-comparisons"></a>Допустимость значений NULL и трехзначная логика сравнения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Если вы знакомы с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных, вы найдете сходную семантику и точность в **System.Data.SqlTypes** пространства имен в [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Однако существуют определенные различия. В этом разделе описаны самые важные из них.  
  
## <a name="null-values"></a>Значения NULL  
 Главное различие между типами данных среды CLR и типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заключается в том, что первые не допускают значений NULL, а вторые реализуют полную семантику NULL.  
  
 Значения NULL влияют на результаты сравнений. При сравнении двух значений x и y, если x или y имеет значение NULL, то результатом некоторых логических сравнений будет значение UNKNOWN, а не TRUE или FALSE.  
  
## <a name="sqlboolean-data-type"></a>Тип данных SqlBoolean  
 **System.Data.SqlTypes** представляет пространство имен **SqlBoolean** типа, представляющий этот трехзначной логики. Сравнения каких-либо **SqlTypes** возвращают **SqlBoolean** тип значения. Неизвестное значение, представленное значение null **SqlBoolean** типа. Свойства **IsTrue**, **IsFalse**, и **IsNull** предоставляются для проверки значения **SqlBoolean** типа.  
  
## <a name="operations-functions-and-null-values"></a>Операции, функции и значения NULL  
 Все арифметические операторы (+, -, \*, /, %), битовые операторы (~ &, и |), и большинство функций возвращают NULL, если любой из операндов или аргументов **SqlTypes** имеют значение NULL. **IsNull** свойство всегда возвращает значение true или false.  
  
## <a name="precision"></a>Точность  
 Максимальные значения типов данных decimal в среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] отличаются от максимальных значений числовых типов и типов decimal в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Кроме того, типы данных decimal в среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] предполагают использование максимальной точности. В среде CLR для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но при этом **SqlDecimal** обеспечивает такую же максимальную точность и масштаб и совпадает с семантикой типа данных decimal в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="overflow-detection"></a>Обнаружение переполнений  
 В среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] сложение двух очень больших чисел не может вызвать исключение. При этом если не использовался оператор проверки, возвращенный результат может «обернуться по кругу» и превратиться в отрицательное целое число. В **System.Data.SqlTypes**, исключения создаются для всех переполнения и потери значимости ошибки и ошибки деления на ноль.  
  
## <a name="see-also"></a>См. также:  
 [Типы данных SQL Server в платформе .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
