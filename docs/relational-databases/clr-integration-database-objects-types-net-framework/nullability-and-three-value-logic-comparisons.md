---
title: Нулевость и трехзначениелогика Сравнения (ru) Документы Майкрософт
description: В этой статье рассказывается о том, как типы данных сервера S'L отличаются от типов в System.Data.SqlTypes в рамках .NET, которые имеют сходную семантику и точность.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- precision [CLR integration]
- overflow detections [CLR integration]
- null values [CLR integration]
- three-value logic comparisons [CLR integration]
- data types [CLR integration]
- SqlBoolean data type
ms.assetid: 13da4c7f-1010-4b2d-a63c-c69b6bfd96f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f016abf2113afef3e02f01fd9842b91b742d50a
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488479"
---
# <a name="nullability-and-three-value-logic-comparisons"></a>Допустимость значений NULL и трехзначная логика сравнения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Если вы знакомы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с типами данных, вы найдете аналогичную семантику и точность [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]в пространстве имен **System.Data.SqlTypes** в . Однако существуют определенные различия. В этом разделе описаны самые важные из них.  
  
## <a name="null-values"></a>Значения NULL  
 Главное различие между типами данных среды CLR и типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заключается в том, что первые не допускают значений NULL, а вторые реализуют полную семантику NULL.  
  
 Значения NULL влияют на результаты сравнений. При сравнении двух значений x и y, если x или y имеет значение NULL, то результатом некоторых логических сравнений будет значение UNKNOWN, а не TRUE или FALSE.  
  
## <a name="sqlboolean-data-type"></a>Тип данных SqlBoolean  
 В пространстве имен **System.Data.SqlTypes** вводится тип **SqlBoolean,** представляющий эту 3-ценную логику. Сравнения между **любыми SqlTypes** возвращают тип значения **SqlBoolean.** Значение UNKNOWN представлено нулевую стоимость типа **SqlBoolean.** Свойства **IsTrue**, **IsFalse**, и **IsNull** предоставляются для проверки стоимости **типа SqlBoolean.**  
  
## <a name="operations-functions-and-null-values"></a>Операции, функции и значения NULL  
 Все арифметические операторы (яп. -, -,, \*/ , %), bitwise операторов (я, &, и q), и большинство функций возвращения NULL, если какой-либо из operands или аргументы **SqlTypes** являются NULL. Свойство **IsNull** всегда возвращает истинное или ложное значение.  
  
## <a name="precision"></a>Точность  
 Максимальные значения типов данных decimal в среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] отличаются от максимальных значений числовых типов и типов decimal в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Кроме того, типы данных decimal в среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] предполагают использование максимальной точности. В CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]для , однако, **SqlDecimal** обеспечивает такую же максимальную точность и масштаб, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и ту же семантику, что и десятичная вбрасывательная информация.  
  
## <a name="overflow-detection"></a>Обнаружение переполнений  
 В среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] сложение двух очень больших чисел не может вызвать исключение. При этом если не использовался оператор проверки, возвращенный результат может «обернуться по кругу» и превратиться в отрицательное целое число. В **System.Data.SqlTypes**исключения выбрасываются для всех ошибок переполнения и недотека, а также ошибок «разделяй на ноль».  
  
## <a name="see-also"></a>См. также:  
 [Типы данных SQL Server в платформе .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
