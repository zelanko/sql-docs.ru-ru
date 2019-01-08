---
title: Задача 5. Задание связей на основе | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: caf0cb1f3d22c41fdc551988556a49f12ee22f36
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53375256"
---
# <a name="task-5-setting-term-based-relationships"></a>Задача 5. Задание связей на основе терминов
  В этой задаче вы определите несколько связей на основе терма для значений **Supplier Name** домена. Связь на основе терма позволяет исправить терм, являющийся частью значения в домене. Это позволяет считать идентичными синонимами несколько значений, идентичных по написанию во всем, кроме отдельных частей. Например **Inc.** возможность исправления **Incorporated**. Службы DQS используют эти связи при обнаружении знаний, очистке и сопоставлении. См. в разделе [создания связей на основе терма](https://msdn.microsoft.com/library/hh510404.aspx) для получения дополнительных сведений.  
  
1.  Выберите **Supplier Name** в **список доменов**.  
  
2.  Переключиться в режим **отношения на основе термина** вкладку на правой панели.  
  
3.  Нажмите кнопку **добавить новое отношение** на панели инструментов, чтобы добавить связь с таблицей.  
  
4.  Тип **Co.** для **значение** поля и **компании** для **исправить на** поля.  
  
5.  Повторите предыдущие два шага для следующих значений:  
  
    |Значение|Исправить на|  
    |-----------|----------------|  
    |Corp.|Corporation|  
    |Inc.|Incorporated|  
  
     ![Связи на основе термина](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "связи на основе термина")  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 6. Задание синонимов](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  
