---
title: Удалить модель интеллектуального анализа данных из структуры интеллектуального анализа данных | Документы Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b17489213e0f057d8f291095f01b65f97a977ff1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34019321"
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>удалить модель интеллектуального анализа данных из структуры интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
  
-   [УДАЛЕНИЕ МОДЕЛИ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ & #40; РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ & #41;](../../dmx/drop-mining-model-dmx.md)  
  
## <a name="see-also"></a>См. также  
 [Задачи модели интеллектуального анализа данных и инструкции](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
