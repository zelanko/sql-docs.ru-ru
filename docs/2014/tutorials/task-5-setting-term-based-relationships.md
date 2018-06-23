---
title: 'Задача 5: Задание на основе связей | Документы Microsoft'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b8450d3e77de578810bb57c35aafad6f90c8f19c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086477"
---
# <a name="task-5-setting-term-based-relationships"></a>Задача 5. Задание связей на основе параметров
  В этой задаче вы определите несколько связей на основе терма для значений для **имя поставщика** домена. Связь на основе терма позволяет исправить терм, являющийся частью значения в домене. Это позволяет считать идентичными синонимами несколько значений, идентичных по написанию во всем, кроме отдельных частей. Например **Inc.** можно исправить на **Incorporated**. Службы DQS используют эти связи при обнаружении знаний, очистке и сопоставлении. В разделе [создания связей на основе терма](http://msdn.microsoft.com/library/hh510404.aspx) для получения дополнительных сведений.  
  
1.  Выберите **имя поставщика** в **список доменов**.  
  
2.  Переключитесь в **связей на основе термина** вкладку на правой панели.  
  
3.  Нажмите кнопку **Добавление нового отношения** кнопку на панели инструментов, чтобы добавить отношение в таблице.  
  
4.  Тип **Co.** для **значение** поля и **компании** для **исправить на** поля.  
  
5.  Повторите предыдущие два шага для следующих значений:  
  
    |Значение|Исправить на|  
    |-----------|----------------|  
    |Corp.|Corporation|  
    |Inc.|Incorporated|  
  
     ![Связи на основе термина](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "связи на основе термина")  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 6. Задание синонимов](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  