---
title: Пользовательские свойства назначения "Обучение модели интеллектуального анализа данных" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0a70216-fdac-44ae-af29-35f65626217c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 17b2b721a5c90009fabca15864b62e71e0677251
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098225"
---
# <a name="data-mining-model-training-destination-custom-properties"></a>Пользовательские свойства назначения «Обучение модели интеллектуального анализа данных»
  Назначение «Обучение модели интеллектуального анализа данных» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Обучение модели интеллектуального анализа данных». Все свойства доступны для чтения и записи.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|ASConnectionId|String|Уникальный идентификатор диспетчера соединений.|  
|ASConnectionString|String|Строка соединения с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или с проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|ObjectRef|String|XML-тег, определяющий структуру интеллектуального анализа данных, которую использует преобразование.|  
  
 Ввод и входные столбцы назначения «Обучение модели интеллектуального анализа данных» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в разделе [Data Mining Model Training Destination](data-mining-model-training-destination.md).  
  
## <a name="see-also"></a>См. также  
 [Common Properties](../common-properties.md)  
  
  