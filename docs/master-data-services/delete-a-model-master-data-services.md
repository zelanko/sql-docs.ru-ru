---
title: Удаление модели (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting models [Master Data Services]
- models [Master Data Services], deleting models
ms.assetid: f0ad3cc4-aed7-47c8-94bc-2971fe9fe871
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e669fea395253f15fab5c7f929826259dfbefa4
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="delete-a-model-master-data-services"></a>Удаление модели (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Эта операция используется для удаления модели и всех ее данных из [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
> [!NOTE]  
>  Когда процесс завершится, все объекты и все данные из всех версий модели будут безвозвратно удалены.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
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
  
  
