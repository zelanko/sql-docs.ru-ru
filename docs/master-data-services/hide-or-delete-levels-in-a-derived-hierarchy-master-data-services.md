---
title: Скрытие или удаление уровней в производной иерархии (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: cb5728706d8781f0fec9f7ea4f6aab00cf84e82f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52760196"
---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a>Скрытие или удаление уровней в производной иерархии (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно скрыть уровень в производной иерархии, если он необходим для группирования, но отображать этот уровень нежелательно. Если этот уровень не нужен для группирования, то можно удалить его.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-hide-or-delete-levels-in-a-derived-hierarchy"></a>Скрытие и удаление уровней в производной иерархии  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  В строке меню наведите указатель на пункт **Управление** и выберите команду **Производные иерархии**.  
  
3.  На странице **Обслуживание производной иерархии** выберите модель из списка **Модель** .  
  
4.  Выберите строку для производной иерархии, которую необходимо изменить.  
  
5.  Нажмите кнопку **Изменить**.  
  
6.  На панели **Текущие уровни** :  
  
    -   Чтобы скрыть уровень, щелкните любой уровень (кроме верхнего и нижнего). В списке **Видимый** выберите **Нет**. Затем щелкните **Сохранить выбранный элемент иерархии**.  
  
    -   Чтобы удалить верхний уровень, щелкните **Удалить выбранный элемент иерархии**. В диалоговом окне подтверждения нажмите кнопку **ОК**. Можно удалить только верхний уровень.  
  
## <a name="see-also"></a>См. также:  
    
 [Производные иерархии (службы Master Data Services)](../master-data-services/derived-hierarchies-master-data-services.md)  
  
  
