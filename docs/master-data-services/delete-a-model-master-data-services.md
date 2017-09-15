---
title: "Удаление модели (службы Master Data Services) | Документы Майкрософт"
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
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: f1ac3250d2d1f852ec43bf88fb206b2009fc0430
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

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
  
 В столбце **Состояние** в сетке отображается состояние операции с моделью. При нажатии кнопки **Сохранить модель** появляется изображение ![Обновляется](../master-data-services/media/mds-model-status-updating.png "Обновляется"), которое указывает, что модель обновляется. При наличии ошибок во время создания или изменения модели появляется изображение ![Ошибка](../master-data-services/media/mds-model-status-error.png "Ошибка"). В противном случае отображается состояние "ОК" и появляется изображение ![ОК](../master-data-services/media/mds-model-status-ok.png "ОК") .  
  
## <a name="see-also"></a>См. также:  
 [Модели (службы Master Data Services)](../master-data-services/models-master-data-services.md)   
 [Создание модели (службы Master Data Services)](../master-data-services/create-a-model-master-data-services.md)  
  
  
