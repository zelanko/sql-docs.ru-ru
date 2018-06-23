---
title: Пользовательские свойства назначения "Модуль чтения данных" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c7fb15f3dda170c866bb95840a7a3cde4c19ffa1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101799"
---
# <a name="datareader-destination-custom-properties"></a>Пользовательские свойства назначения «Модуль чтения данных»
  Назначение «Модуль чтения данных» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Модуль чтения данных». Все свойства, за исключением `DataReader` доступны для чтения и записи.  
  
|Имя свойства|Тип данных|Описание|  
|-------------------|---------------|-----------------|  
|DataReader|String|Имя класса назначения «Модуль чтения данных».|  
|FailOnTimeout|Логическое значение|Показывает, завершать ли работу с ошибкой, когда истекает время ожидания чтения (`ReadTimeout`). Это свойство имеет значение по умолчанию **False**.|  
|ReadTimeout|Целочисленный|Количество миллисекунд до истечения времени ожидания. По умолчанию для этого свойства устанавливается значение 30000 (30 секунд).|  
  
 Ввод и входные столбцы назначения «Модуль чтения данных» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в статье [DataReader Destination](datareader-destination.md).  
  
## <a name="see-also"></a>См. также  
 [Common Properties](../common-properties.md)  
  
  