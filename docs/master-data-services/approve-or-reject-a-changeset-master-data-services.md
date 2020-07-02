---
title: Утверждение или отклонение набора изменений
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 45bd01f9-ae15-4fc5-a2ba-eee565a26ef8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c0d7e090350fdaae094c8365d28a4e058bdfa62e
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85812819"
---
# <a name="approve-or-reject-a-changeset-master-data-services"></a>Утверждение или отклонение набора изменений (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Набор изменений — это совокупность ожидающих изменений основных данных. Если для изменений сущности требуется утверждение администратора, после отправки набора изменений на утверждение администратор может просмотреть и утвердить или отклонить его.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** . Дополнительные сведения см. в разделе [разрешения функциональной области &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Необходимо обладать правами администратора сущности.  
  
-   Изменения сущности должны требовать утверждения администратором.  
  
-   Набор изменений можно просмотреть, а затем утвердить или отклонить, если он находится в состоянии ожидания.  
  
-   Пользователи не могут утверждать свои собственные изменения. Если вы администратор сущности, необходимо назначить дополнительного администратора, чтобы утвердить свой набор изменений.  
  
## <a name="to-approve-or-reject-a-changeset"></a>Утверждение или отклонение набора изменений  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель и версию, а затем щелкните **Обозреватель**.  
  
2.  Щелкните сущность в меню **Сущности** .  
  
3.  В области справа выберите **Наборы изменений** и дважды щелкните набор изменений, который необходимо утвердить или отклонить.  
  
4.  Чтобы применить набор изменений и просмотреть ожидающие изменения, нажмите кнопку **Применить** .  
  
5.  Чтобы отклонить набор изменений и отправить его обратно владельцу, нажмите кнопку **Отклонить** .  
  
6.  Чтобы утвердить набор изменений, нажмите кнопку **Утвердить** . Набор изменений фиксируется автоматически.  
  
## <a name="see-also"></a>См. также  
 [Создание набора изменений &#40;Master Data Services&#41;](../master-data-services/create-a-changeset-master-data-services.md)   
 [Примените и обновите набор изменений &#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)   
 [Фиксация или отправка набора изменений (Master Data Services)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
  
