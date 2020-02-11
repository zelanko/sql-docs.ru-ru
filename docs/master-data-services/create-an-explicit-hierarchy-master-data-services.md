---
title: Создание явной иерархии
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6b366c29412a3a698e793d3153784a8d1450bc81
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729516"
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a>Создание явной иерархии (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] явные иерархии создаются, если необходима неоднородная иерархия, элементы которой могут располагаться на любом уровне. Явные иерархии содержат элементы из одной сущности.  
  
 После создания явной иерархии в нее можно добавлять элементы в функциональной области **Обозреватель** .  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Для сущности необходимо разрешить использование явных иерархий и коллекций.  
  
### <a name="to-create-an-explicit-hierarchy"></a>Создание явной иерархии  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностью) выберите в сетке строку сущности, для которой необходимо создать явную иерархию.  
  
4.  Щелкните **явные иерархии**.  
  
5.  На странице **Manage Explicit Hierarchy** (Управление явной иерархией) нажмите **Добавить**.  
  
6.  Введите имя иерархии в поле **Имя** .  
  
7.  По желанию снимите флажок **Обязательная иерархия** для создания необязательной иерархии. Дополнительные сведения о типах иерархий см. в разделе [Explicit Hierarchies &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md).  
  
8.  Выберите команду **Сохранить**.  
  
## <a name="grid-columns"></a>Столбцы сетки  
 Для каждой создаваемой явной иерархии в сетке создается строка с семью столбцами. Ниже приведено описание этих столбцов.  
  
|Имя|Description|  
|----------|-----------------|  
|Состояние|Состояние сущности. После нажатия кнопки **Сохранить** появится следующее изображение, которое указывает на то, что сущность обновляется.<br /><br /> ![Значок обновления состояния](../master-data-services/media/mds-statusicon-updating.png "Значок обновления состояния")<br /><br /> При наличии ошибок во время создания или изменения сущности появляется следующее изображение.<br /><br /> ![Значок состояния ошибки](../master-data-services/media/mds-statusicon-error.png "Значок состояния ошибки")<br /><br /> Если ее состояние нормальное, появится следующее изображение.<br /><br /> ![Значок состояния "ОК"](../master-data-services/media/mds-statusicon-ok.png "Значок состояния "ОК"")|  
|Имя|Имя явной иерархии.|  
|Необязательно|Указывает, является ли явная иерархия обязательной.|  
|"Кем создано";|Имя пользователя, создавшего явную иерархию.|  
|Создана|Дата и время создания явной иерархии.|  
|Кем обновлена|Имя последнего пользователя, обновившего явную иерархию.|  
|Обновлено|Дата и время последнего обновления явной иерархии.|  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Создание &#40;объединенного элемента Master Data Services&#41;](../master-data-services/create-a-consolidated-member-master-data-services.md)  
  
  
  
## <a name="see-also"></a>См. также:  
 [Явные иерархии &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [Производные иерархии с явно заданными ограничениями &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Измените имя явной иерархии &#40;Master Data Services&#41;](../master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  

