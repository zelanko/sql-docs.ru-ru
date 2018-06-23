---
title: Включить режим разработки DirectQuery (табличные службы SSAS) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1ba954a8f296200070493625803aad263fa71520
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097611"
---
# <a name="enable-directquery-design-mode-ssas-tabular"></a>Включить режим разработки DirectQuery (табличные службы SSAS)
  Чтобы создать модель в режиме DirectQuery, следует сначала изменить среду времени разработки так, чтобы она поддерживала пользователя режима DirectQuery. Когда это будет сделано, конструктор также сделает следующее:  
  
-   Обеспечит использование свойств развертывания DirectQuery.  
  
-   Изменит запуск базы данных рабочей области на запуск в гибридном режиме, который использует кэш для разработки. При фактическом развертывании модели режим будет изменен обратно на любое значение, указанное в свойствах развертывания проекта.  
  
-   Отключит функции разработки, несовместимые с режимом DirectQuery.  
  
-   Проверит существующую модель.  
  
 В этой процедуре описывается, как включить режим DirectQuery в конструкторе.  
  
### <a name="to-enable-use-of-directquery-in-a-model"></a>Включение использования DirectQuery в модели  
  
1.  Откройте файл решения в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  В обозревателе объектов дважды щелкните файл Model.bim.  
  
3.  На панели **Свойства** задайте для свойства **DirectQueryMode**значение **Вкл**.  
  
4.  При наличии ошибок откройте в Visual Studio **Список ошибок** и устраните проблемы, мешающие перевести модель в режим DirectQuery.  
  
## <a name="see-also"></a>См. также  
 [Режим DirectQuery &#40;табличные службы SSAS&#41;](directquery-mode-ssas-tabular.md)  
  
  