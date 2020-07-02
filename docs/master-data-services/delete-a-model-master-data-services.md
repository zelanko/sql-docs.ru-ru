---
title: Удаление модели
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting models [Master Data Services]
- models [Master Data Services], deleting models
ms.assetid: f0ad3cc4-aed7-47c8-94bc-2971fe9fe871
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7badbd43fd526ff66b599f04e6aeb36443cd3684
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811549"
---
# <a name="delete-a-model-master-data-services"></a>Удаление модели (службы Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Эта операция используется для удаления модели и всех ее данных из [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
> [!NOTE]  
>  Когда процесс завершится, все объекты и все данные из всех версий модели будут безвозвратно удалены.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** .  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-delete-a-model"></a>Удаление модели  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Представление модели** в строке меню наведите указатель мыши на **Управление** и щелкните **Модели**.  
  
3.  На странице **Управление моделями** в сетке выберите строку модели, которую необходимо изменить.  
  
4.  Щелкните **Удалить**.  
  
5.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
6.  В дополнительном диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
 В столбце **Состояние** в сетке отображается состояние операции с моделью. При нажатии кнопки **сохранить модель** отображается изображение ![обновления](../master-data-services/media/mds-model-status-updating.png "Обновление") , которое указывает на то, что модель обновляется. При возникновении ошибок при создании или изменении модели отображается изображение ![ошибки](../master-data-services/media/mds-model-status-error.png "Ошибка") . В противном случае отображается состояние "ОК" и появляется изображение ![ОК](../master-data-services/media/mds-model-status-ok.png "OK") .  
  
## <a name="see-also"></a>См. также  
 [Модели &#40;Master Data Services&#41;](../master-data-services/models-master-data-services.md)   
 [Создание модели (службы Master Data Services)](../master-data-services/create-a-model-master-data-services.md)  
  
  
