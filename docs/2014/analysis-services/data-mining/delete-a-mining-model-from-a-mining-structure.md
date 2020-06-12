---
title: Удалить модель интеллектуального анализа данных из структуры интеллектуального анализа данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 72c79dcdccf6225b8e75144f8b090dcab7506c10
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84522706"
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>удалить модель интеллектуального анализа данных из структуры интеллектуального анализа данных
  Модели интеллектуального анализа данных можно удалять в конструкторе интеллектуального анализа данных с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]или инструкций расширений интеллектуального анализа данных.  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a>Удаление модели интеллектуального анализа данных с помощью SQL Server Data Tools  
  
1.  Перейдите на вкладку **Модели интеллектуального анализа данных** в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Щелкните правой кнопкой мыши модель, которую необходимо удалить, и выберите пункт **Удалить**.  
  
     Откроется диалоговое окно **Удаление объектов** .  
  
3.  Нажмите кнопку **ОК**.  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a>Удаление модели интеллектуального анализа данных с помощью среды SQL Server Management Studio  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте базу данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , содержащую модель.  
  
2.  Разверните **Структуры интеллектуального анализа данных**, затем **Модели интеллектуального анализа данных**.  
  
3.  Щелкните правой кнопкой мыши модель, которую необходимо удалить, и выберите пункт **Удалить**.  
  
     Удаление модели не приводит к удалению обучающих данных. Удаляются только метаданные и шаблоны, созданные при обучении модели.  
  
### <a name="delete-a-mining-model-using-dmx"></a>Удаление модели интеллектуального анализа данных с помощью расширений интеллектуального анализа данных  
  
-   [DROP MINING MODEL (расширения интеллектуального анализа данных)](/sql/dmx/drop-mining-model-dmx)  
  
## <a name="see-also"></a>См. также:  
 [Задачи и инструкции по модели интеллектуального анализа данных](mining-model-tasks-and-how-tos.md)  
  
  
