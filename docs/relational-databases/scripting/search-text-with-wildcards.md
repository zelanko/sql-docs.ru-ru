---
title: "Поиск текста с использованием подстановочных знаков | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: ssms
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.wildcards
- vswildcardsbuilder
helpviewer_keywords:
- searches [SQL Server Management Studio], wildcards
- Query Editor [SQL Server Management Studio], wildcard searches
- wildcard options [SQL Server Management Studio]
ms.assetid: 449600f8-cc87-4b3f-878a-59c158a88a40
caps.latest.revision: "23"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 97576c021e902fb460181124cbf21c24833cf7bf
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="search-text-with-wildcards"></a>Поиск текста с символами-шаблонами
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] С помощью приведенных ниже выражений можно заменять символы либо цифры в поле **Найти** в диалоговом окне **Найти и заменить** среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-search-using-wildcards"></a>Осуществление поиска с шаблонами  
  
1.  Чтобы включить использование шаблонов в поле **Найти** во время операций «Быстрый поиск», **Найти в файлах**, **Быстрая замена**или **Заменить в файлах** , выберите **Использовать** в области **Параметры поиска** , а затем установите флажок **Подстановочные знаки**.  
  
2.  В этом случае становится доступной треугольная кнопка **Список ссылок** , расположенная рядом с полем **Найти** . Нажмите эту кнопку, чтобы отобразить список доступных шаблонов. При выборе любого элемента в **Списке подстановки**он будет вставлен в строку **Найти** .  
  
 Следующая таблица содержит описание шаблонов, доступных через **Список подстановки**.  
  
|Выражение|Синтаксис|Описание|  
|----------------|------------|-----------------|  
|Любой отдельный символ|?|Соответствует любому отдельному символу.|  
|Любая отдельная цифра|#|Соответствует любой отдельной цифре. Например, выражение 7# соответствует числам, начинающимся с 7 и содержащим еще одну цифру, например 71, но не 17.|  
|Символы вне набора|[! ]|Соответствует любому символу, кроме заданных в наборе.|  
|Один или несколько символов|*|Соответствует одному или нескольким символам. Например, выражение new* соответствует любому тексту, включающему подстроку «new», например newfile.txt.|  
|Набор символов|[ ]|Соответствует любому из символов, заданных в наборе.|  
  
## <a name="see-also"></a>См. также:  
 [Поиск и замена](../../relational-databases/scripting/search-and-replace.md)   
 [Поиск текста с помощью регулярных выражений](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
  
  
