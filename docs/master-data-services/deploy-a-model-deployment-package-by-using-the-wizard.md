---
title: "Развертывание пакета развертывания модели с помощью мастера | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deployment packages [Master Data Services], deploying
- models [Master Data Services], deploying a package
ms.assetid: 4f65dc60-0ff8-46e6-9988-5bc5b9603ad0
caps.latest.revision: "16"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c990f1d988bec107c2be8f05fface0da7b021a04
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="deploy-a-model-deployment-package-by-using-the-wizard"></a>Развертывание пакета развертывания модели с помощью мастера
  Мастер развертывания модели [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] служит для развертывания пакетов, содержащих только объекты модели. Если нужно развернуть пакет с данными, см. раздел [Развертывание пакета развертывания модели при помощи MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
> [!IMPORTANT]  
>  Пакеты могут быть развернуты только в выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , в котором они были созданы. Это означает, что пакеты, созданные в среде [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] , не могут быть развернуты в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** в целевой среде служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ;  
  
-   должен существовать пакет развертывания модели. Дополнительные сведения см. в разделе [Создание пакета развертывания модели с помощью мастера](../master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).  
  
-   В среде, в которой выполняется развертывание модели, необходимо обладать правами администратора. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-deploy-a-model-deployment-package-of-model-objects-only"></a>Развертывание пакета развертывания модели, состоящего только из объектов модели  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Представление модели** в строке меню наведите курсор на пункт **Система** и выберите **Развертывание**.  
  
3.  В **Диспетчере развертывания модели**нажмите **Развернуть**.  
  
4.  Нажмите кнопку **Обзор**.  
  
5.  Найдите свой пакет развертывания (файл PKG) и нажмите кнопку **Открыть**.  
  
6.  Нажмите кнопку **Далее**.  
  
7.  После загрузки пакета нажмите кнопку **Далее**.  
  
8.  Если модель уже существует, ее можно обновить, выбрав **Обновить существующую модель**. Чтобы создать новую модель, выберите **Создать новую модель** и после нажатия кнопки **Далее** укажите имя новой модели.  
  
9. Чтобы завершить работу мастера, нажмите кнопку **Готово** .  
  
 **Примечания.**  
  
-   Если имя представления подписки в пакете совпадает с именем представления подписки в существующей модели, отображается предупреждение **Deployer subscription view renamed**(Представление подписки программы развертывания переименовано). Кроме того, создается представление *modelname.subscriptionviewname*. Если это имя уже используется, то представление подписки не создается.  
  
-   Процесс развертывания состоит из четырех шагов.  
  
    1.  Создаются объекты модели.  
  
    2.  Создаются представления подписки.  
  
    3.  Создаются бизнес-правила.  
  
-   Если при создании новой или клонированной модели процесс на любом этапе завершается ошибкой, модель удаляется.  
  
     При обновлении в случае неудачного завершения любого из первых трех шагов переход к следующему шагу не производится. Однако откат уже внесенных изменений также не выполняется.  
  
## <a name="next-steps"></a>Следующие шаги  
 Атрибуты файлов и разрешения для пользователей и групп не включаются в пакеты развертывания модели. При развертывании модели их нужно обновить вручную. Дополнительные сведения см. в разделе:  
  
-   [Назначение разрешения для объекта модели (службы Master Data Services)](../master-data-services/assign-model-object-permissions-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Развертывание моделей (службы Master Data Services)](../master-data-services/deploying-models-master-data-services.md)  
  
  
