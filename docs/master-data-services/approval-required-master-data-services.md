---
title: Требуется утверждение
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b475a53d-269d-49f3-bb42-965c555f80be
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 448a8174acef464fa1badb5a25d019891dd53bc6
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85812067"
---
# <a name="approval-required-master-data-services"></a>Требуется утверждение (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]администратор может установить для сущности режим "Требуется утверждение". Все изменения в этой сущности требуют рассмотрения и утверждения одним из администраторов сущности.  
  
> [!NOTE]  
>  Изменения, внесенные в конечные элементы, требуют утверждения. Изменения, внесенные в устаревшие явные иерархии и коллекции, не проходят утверждение.  
>   
>  Изменения, внесенные процессом промежуточной таблицы, не проходят утверждение.  
>   
>  Изменения, внесенные бизнес-правилом, не проходят утверждение.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области "Администрирование системы";  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Сущность должна существовать. Дополнительные сведения см. в разделе [Создание сущности &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)  
  
## <a name="to-enable-approval-required-for-an-entity"></a>Включение режима "Требуется утверждение" для сущности  
  
1.  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностью) в сетке выберите строку сущности, для которой нужно включить режим  **Требуется утверждение** .  
  
4.  Нажмите кнопку **Изменить**, выберите **Требуется утверждение**, а затем нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также  
 [Наборы изменений (Master Data Services)](../master-data-services/changesets-master-data-services.md)  
  
  
