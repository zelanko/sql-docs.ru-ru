---
title: Включить режим разработки DirectQuery (табличные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 965a3a7c1bfa9549793690e92760ce39f147e0d2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66067199"
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
 [Режим DirectQuery (табличные службы SSAS)](directquery-mode-ssas-tabular.md)  
  
  
