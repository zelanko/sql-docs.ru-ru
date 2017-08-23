---
title: "Требуется утверждение (Master Data Services) | Документы Microsoft"
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
ms.assetid: b475a53d-269d-49f3-bb42-965c555f80be
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f73510c38944126f65567dcb0e6a8b97ec2498e0
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="approval-required-master-data-services"></a>Требуется утверждение (Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]администратор может установить для сущности режим "Требуется утверждение". Все изменения в этой сущности требуют рассмотрения и утверждения одним из администраторов сущности.  
  
> [!NOTE]  
>  Изменения, внесенные в конечные элементы, требуют утверждения. Изменения, внесенные в устаревшие явные иерархии и коллекции, не проходят утверждение.  
>   
>  Изменения, внесенные процессом промежуточной таблицы, не проходят утверждение.  
>   
>  Изменения, внесенные бизнес-правилом, не проходят утверждение.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области "Администрирование системы";  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Сущность должна существовать. Дополнительные сведения см. в разделе [Создание сущности (службы Master Data Services)](../master-data-services/create-an-entity-master-data-services.md).  
  
## <a name="to-enable-approval-required-for-an-entity"></a>Включение режима "Требуется утверждение" для сущности  
  
1.  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностью) в сетке выберите строку сущности, для которой нужно включить режим  **Требуется утверждение** .  
  
4.  Нажмите кнопку **Изменить**, выберите **Требуется утверждение**, а затем нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также:  
 [Наборы изменений (Master Data Services)](../master-data-services/changesets-master-data-services.md)  
  
  
