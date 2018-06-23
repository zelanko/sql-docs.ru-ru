---
title: Функция Level (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 3df298cda1e6439d9c539c125689a3687cdc97f8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192612"
---
# <a name="level-function-report-builder-and-ssrs"></a>Функция Level (построитель отчетов и службы SSRS)
  Возвращает текущий уровень глубины в рекурсивной иерархии.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a>Параметры  
 *область*  
 (`String`) (Необязательно) Имя набора данных, группы или области данных, содержащих элементы отчета, к которым применяется агрегатная функция. Если аргумент *scope* не задан, используется текущая область.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Возвращает `Integer`. Если *область* указывает набор данных, область данных или нерекурсивную (то есть группирование нет `Parent` элемент), `Level` возвращает 0. Если параметр *scope* не указан, то возвращается уровень текущей области.  
  
## <a name="remarks"></a>Примечания  
 Возвращаемые функцией `Level` значения отсчитываются от нуля, т. е. первым уровнем в иерархии является 0.  
  
 Функция `Level` может использоваться для обеспечения автоматического определения отступов в рекурсивной иерархии, такой как список сотрудников.  
  
 Дополнительные сведения о рекурсивных иерархиях см. в разделе [Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Пример  
 Следующий пример кода показывает уровень строки в группе «Сотрудники»:  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a>См. также  
 [Выражения используются в отчетах &#40;отчетов построителя отчетов и службы SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](expressions-report-builder-and-ssrs.md)   
 [Область выражения для итогов, статистических функций и встроенных коллекций &#40;отчетов построителя отчетов и службы SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  