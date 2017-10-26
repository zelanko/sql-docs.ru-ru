---
title: "Пользовательские свойства назначения DataReader | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 44a9f26f1125f2c6b319653528aaa7eea04aa84f
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="datareader-destination-custom-properties"></a>Пользовательские свойства назначения «Модуль чтения данных»
  Назначение «Модуль чтения данных» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Модуль чтения данных». Все свойства, за исключением **DataReader** , доступны для чтения и записи.  
  
|Имя свойства|Тип данных|Description|  
|-------------------|---------------|-----------------|  
|DataReader|Строковые значения|Имя класса назначения «Модуль чтения данных».|  
|FailOnTimeout|Логическое значение|Показывает, завершать ли работу с ошибкой, когда истекает время ожидания чтения ( **ReadTimeout** ). Это свойство имеет значение по умолчанию **False**.|  
|ReadTimeout|Целочисленный|Количество миллисекунд до истечения времени ожидания. По умолчанию для этого свойства устанавливается значение 30000 (30 секунд).|  
  
 Ввод и входные столбцы назначения «Модуль чтения данных» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в статье [DataReader Destination](../../integration-services/data-flow/datareader-destination.md).  
  
## <a name="see-also"></a>См. также  
 [Общие свойства](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  

