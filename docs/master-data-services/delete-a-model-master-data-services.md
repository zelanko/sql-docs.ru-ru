---
title: "Удаление модели (Master Data Services) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting models [Master Data Services]
- models [Master Data Services], deleting models
ms.assetid: f0ad3cc4-aed7-47c8-94bc-2971fe9fe871
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: be50aa7e9de502b0db2cb427bf894081196b579e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="delete-a-model-master-data-services"></a>Удаление модели (службы Master Data Services)
  Эта операция используется для удаления модели и всех ее данных из [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
> [!NOTE]  
>  Когда процесс завершится, все объекты и все данные из всех версий модели будут безвозвратно удалены.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-delete-a-model"></a>Удаление модели  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Представление модели** в строке меню наведите указатель мыши на **Управление** и щелкните **Модели**.  
  
3.  На странице **Управление моделями** в сетке выберите строку модели, которую необходимо изменить.  
  
4.  Щелкните **Удалить**.  
  
5.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
6.  В дополнительном диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
 В столбце **Состояние** в сетке отображается состояние операции с моделью. При нажатии кнопки **сохранить модель** кнопки, ![обновление](../master-data-services/media/mds-model-status-updating.png "обновление") изображение, указывает, что модель обновляется. При наличии ошибок при создании или изменении модели, ![ошибка](../master-data-services/media/mds-model-status-error.png "ошибка") изображение. В противном случае отображается состояние "ОК" и появляется изображение ![ОК](../master-data-services/media/mds-model-status-ok.png "ОК") .  
  
## <a name="see-also"></a>См. также:  
 [Модели &#40; Службы Master Data Services &#41;](../master-data-services/models-master-data-services.md)   
 [Создать модель &#40; Службы Master Data Services &#41;](../master-data-services/create-a-model-master-data-services.md)  
  
  
