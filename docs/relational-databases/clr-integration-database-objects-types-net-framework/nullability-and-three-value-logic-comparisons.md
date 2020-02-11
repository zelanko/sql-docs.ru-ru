---
title: Допустимость значений NULL и сравнение логики с тремя значениями | Документация Майкрософт
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
ms.openlocfilehash: e5dbdf757038abbf2c98d3987ee14a9cb9184a61
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081320"
---
# <a name="nullability-and-three-value-logic-comparisons"></a>Допустимость значений NULL и трехзначная логика сравнения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Если вы знакомы с типами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных, вы увидите схожую семантику и точность в пространстве имен **System. Data. SqlTypes** в. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Однако существуют определенные различия. В этом разделе описаны самые важные из них.  
  
## <a name="null-values"></a>Значения NULL  
 Главное различие между типами данных среды CLR и типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заключается в том, что первые не допускают значений NULL, а вторые реализуют полную семантику NULL.  
  
 Значения NULL влияют на результаты сравнений. При сравнении двух значений x и y, если x или y имеет значение NULL, то результатом некоторых логических сравнений будет значение UNKNOWN, а не TRUE или FALSE.  
  
## <a name="sqlboolean-data-type"></a>Тип данных SqlBoolean  
 Пространство имен **System. Data. SqlTypes** вводит тип **SqlBoolean** для представления этой логики из трех значений. Сравнения любых **sqltypes** возвращают тип значения **SqlBoolean** . Неизвестное значение представлено значением NULL типа **SqlBoolean** . Для проверки значения типа **SqlBoolean** предоставляются свойства **IsTrue**, **IsFalse**и **IsNull** .  
  
## <a name="operations-functions-and-null-values"></a>Операции, функции и значения NULL  
 Все арифметические операторы (+,- \*,,/,%), битовые операторы (~, & и |) и большинство функций возвращают значение null, если любой из операндов или аргументов **sqltypes** имеет значение null. Свойство **IsNull** всегда возвращает значение true или false.  
  
## <a name="precision"></a>Precision  
 Максимальные значения типов данных decimal в среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] отличаются от максимальных значений числовых типов и типов decimal в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Кроме того, типы данных decimal в среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] предполагают использование максимальной точности. Однако в CLR для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]среда **SqlDecimal** предоставляет такую же максимальную точность и масштаб и ту же семантику, что и тип данных Decimal в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="overflow-detection"></a>Обнаружение переполнений  
 В среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] сложение двух очень больших чисел не может вызвать исключение. При этом если не использовался оператор проверки, возвращенный результат может «обернуться по кругу» и превратиться в отрицательное целое число. В **System. Data. SqlTypes**исключения вызываются для всех ошибок переполнения и потери точности, а ошибки деления на ноль.  
  
## <a name="see-also"></a>См. также:  
 [Типы данных SQL Server в платформе .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
