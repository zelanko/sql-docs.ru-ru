---
description: Пользовательские свойства назначения «Обучение модели интеллектуального анализа данных»
title: Пользовательские свойства назначения "Обучение модели интеллектуального анализа данных" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f0a70216-fdac-44ae-af29-35f65626217c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6427b808d31c9b1938b093da2bdf14d59bec90cc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88457369"
---
# <a name="data-mining-model-training-destination-custom-properties"></a>Пользовательские свойства назначения «Обучение модели интеллектуального анализа данных»

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Назначение «Обучение модели интеллектуального анализа данных» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Обучение модели интеллектуального анализа данных». Все свойства доступны для чтения и записи.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|ASConnectionId|Строка|Уникальный идентификатор диспетчера соединений.|  
|ASConnectionString|Строка|Строка соединения с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или с проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|ObjectRef|Строка|XML-тег, определяющий структуру интеллектуального анализа данных, которую использует преобразование.|  
  
 Ввод и входные столбцы назначения «Обучение модели интеллектуального анализа данных» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в разделе [Data Mining Model Training Destination](../../integration-services/data-flow/data-mining-model-training-destination.md).  
  
## <a name="see-also"></a>См. также  
 [Общие свойства](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
